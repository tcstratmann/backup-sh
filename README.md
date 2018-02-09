# backup-sh

A backup shell script for Archlinux - backs up list of installed packages, home directory and content of connected android phone to destination of choice. Include/exclude paths are configurable.

by tcstratmann - 2018

## Dependencies

- pacman (Archlinux package manager)
- adb (Android Debug Bridge)
- rdiff-backup (backup software)

## Configuration

You can configure a default backup path and the home directory to backup in the backup-sh file itself. Files and folders to exclude from backup, aswell as files and folders outside the home directory to include in the backup can be specified in configuration files in the .backup folder.

### Initial Configuration
In backup-sh:

```sh
...

# set log file name
LOG_FILE="backup.log"

# set home directory to backup
HOME="/home/USER/"

# set backup storage path
if [ $# -eq 0 ]
then
	BACKUP_PATH="/media/HDD/" # default backup storage

...
```

### Include/exclude Paths

Configuration folder: $HOME/.backup/

backup.exclude | backup.include

## Usage

To run the script at low  I/O and CPU priority call:

`sudo nice -n 19 ionice -c2 -n7 ./backup-sh`

For external backup storage different from the default backup path supply path as argument (with trailing slash):

e.g. `./backup-sh /media/PENDRIVE/`

log file: backup.log
