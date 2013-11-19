Grok Command Line Interface
===========================

Command line interface (CLI) tools for interacting with a Grok server.

Requires: Python (2.6 or greater)

Installation
------------

- pip (recommended)

  `pip install grokcli`

- easy_install

  `easy_install grokcli`

- setup.py

  `python setup.py install`

Usage
-----

Grok CLI tools provides a single, high-level `grok` command, from which
a number of sub-commands can be invoked:

    grok [command] [options]

- `grok credentials`

  Use the `grok credentials` sub-command to add your AWS credentials to a
  running Grok server configuration:

      grok credentials SERVER_URL [options]

  The `SERVER_URL` positional argument is required and must be a url to a
  running Grok server.  For example: https://ec2-AA-BB-CC-DD.us-west-2.compute.amazonaws.com

  You can specify your credentials in one of three ways:

  - Specify `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` CLI options.

    ```
    grok credentials SERVER_URL --AWS_ACCESS_KEY_ID=... --AWS_SECRET_ACCESS_KEY=...
    ```

  - Read AWS credentials from a specific file using the `-d`, or `--data` CLI
    options.

    ```
    grok credentials SERVER_URL -d PATH_TO_FILE
    grok credentials SERVER_URL --data=PATH_TO_FILE
    ```

    You can read from stdin using `-`:

    ```
    grok credentials SERVER_URL -d - < PATH_TO_FILE
    grok credentials SERVER_URL --data=- < PATH_TO_FILE
    ```

    The credentials file should be formatted according to this template:

    ```
    AWS_ACCESS_KEY_ID=Your AWS access key ID here
    AWS_SECRET_ACCESS_KEY=Your AWS secret access key here
    ```

  - Use existing boto configuration.

    ```
    grok credentials SERVER_URL --use-boto
    ```
