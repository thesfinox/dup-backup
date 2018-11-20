# BACKUP SCRIPT

This is a simple backup script to use with [Duplicity](http://duplicity.nongnu.org/), which must be installed on the system. The script is supposed to backup the user's **home directory**, **encrypt it** with the user's key and upload it to a **WebDAV** service such as [Nextcloud](https://nextcloud.com/) or [Owncloud](https://owncloud.org/).

## Installation

You can install the script simply by `install backup` (to install it in the default position, usually _/usr/local/bin_ in Linux distributions) or by `install backup path/to/custom/dir` to install it in a custom directory.

## Setup

Once you have installed the script (and your encryption keys have been imported into the keyring), you should create a new directory using `mkdir ~/.duplicity`. The you should create two files:
- **~/.duplicity/server** containing:

```bash
DEST="the URL of the WebDAV"
USR="the username"
PSW="the password"
```

- **~/.duplicity/gpg** containing:

```bash
KEY="the ID of the encryption key"
PASSPHRASE="the passphrase for the encryption key"
```

Remember to properly setup the file permissions: `chmod 600 ~/.duplicity/server ~/.duplicity/gpg`.

## Crontab

You can edit the user's cron jobs with `crontab -e` (use `crontab -l` to view the cron jobs) and then insert the script at the end of it. E.g.: the entry `00 3 * * * /usr/local/bin/backup` will execute the script every day of every month at 3 a.m.

## License

This is free software released under the **MIT License**: feel free to distibute and modify the content of the script.
