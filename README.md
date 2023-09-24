# aws-auto-nuke

![Build Status](https://github.com/ppmathis/aws-auto-nuke/workflows/CI/badge.svg?branch=main)

This is a maintained fork of [aws-nuke](https://github.com/rebuy-de/aws-nuke)
from [rebuy recommerce GmbH](https://github.com/rebuy-de/aws-nuke). While the
original software is a very useful piece of software, the authors decided to
implement various safety measures for preventing someone from accidentaly nuking
their production AWS account.

While this is a good idea, it also makes it impossible to use the software in an
automated environment, e.g. for cleaning up test accounts. This fork removes
most of the especially annoying safety measures, while still keeping the more
sane ones intact.

Specifically, these safety measures have been dropped:

- By default, `aws-auto-nuke` is deleting all found resources. To only list the
  resources that would be deleted, use the `--dry-run` flag.
- Unlike the original, `aws-auto-nuke` does not contain any confirmation prompts
  or forced sleeps. All actions will be executed immediately.
- There is no need to have any associated account alias anymore. Simply
  specifying an AWS Account ID is sufficient to run `aws-auto-nuke`.
- It is no longer necessary to have any account alias associated with the
  account. Additionally, the check if an account alias contains `prod` has been
  removed as well.

Just like the original, the availability of a configuration file is still a
required and it must contain a blocklist with at least one AWS Account ID. Such
a file can easily be provided within an automated environment and still provides
some protection for not nuking critical accounts. Additionally, the default is
still to simply list resources, and requires you to provide `--no-dry-run` to
actually nuke resources.

Further information and usage instructions can be found in
the [official README](https://github.com/rebuy-de/aws-nuke/blob/main/README.md).
