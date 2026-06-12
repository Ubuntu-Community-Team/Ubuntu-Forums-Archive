---
title: "Minidlna - cannot create database"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by Hans9 on 2013-03-02
Hi,
I needed some lightweight DLNA server for my TV to watch pictures in my PC. I chose minidlna, installed using this [http://ubuntuforums.org/showthread.php?t=1866520](http://ubuntuforums.org/showthread.php?t=1866520) and [https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA). My /etc/minidlna.config looks like this (without some commented and blank lines):
```
# If you want to restrict a media_dir to a specific content type, you can
# prepend the directory name with a letter representing the type (A, P or V),
# followed by a comma, as so:
#   * "A" for audio    (eg. media_dir=A,/var/lib/minidlna/music)
#   * "P" for pictures (eg. media_dir=P,/var/lib/minidlna/pictures)
#   * "V" for video    (eg. media_dir=V,/var/lib/minidlna/videos)
#
# WARNING: After changing this option, you need to rebuild the database. Either
#          run minidlna with the '-R' option, or delete the 'files.db' file
#          from the db_dir directory (see below).
#          On Debian, you can run, as root, 'service minidlna force-reload' instead.
#media_dir=/var/lib/minidlna
media_dir=/home/vladan/fotak

# Path to the directory that should hold the database and album art cache.
db_dir=/home/vladan/minidlna_webmin

# Path to the directory that should hold the log file.
#log_dir=/var/log

# Minimum level of importance of messages to be logged.
# Must be one of "off", "fatal", "error", "warn", "info" or "debug".
# "off" turns of logging entirely, "fatal" is the highest level of importance
# and "debug" the lowest.
#log_level=warn

# Use a different container as the root of the directory tree presented to
# clients. The possible values are:
#   * "." - standard container
#   * "B" - "Browse Directory"
#   * "M" - "Music"
#   * "P" - "Pictures"
#   * "V" - "Video"
# if you specify "B" and client device is audio-only then "Music/Folders" will be used as root
#root_container=.

# Network interface(s) to bind to (e.g. eth0), comma delimited.
#network_interface=

# IPv4 address to listen on (e.g. 192.0.2.1).
#listening_ip=

# Port number for HTTP traffic (descriptions, SOAP, media transfer).
port=8200

# URL presented to clients.
# The default is the IP address of the server on port 80.
#presentation_url=http://example.com:80

# Name that the DLNA server presents to clients.
friendly_name=Pracovna

# Serial number the server reports to clients.
serial=12345678

# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)

# Model number the server reports to clients.
model_number=1

# Automatic discovery of new files in the media_dir directory.
inotify=yes

# List of file names to look for when searching for album art. Names should be
# delimited with a forward slash ("/").
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# Strictly adhere to DLNA standards.
# This allows server-side downscaling of very large JPEG images, which may
# decrease JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no

# Support for streaming .jpg and .mp3 files to a TiVo supporting HMO.
enable_tivo=no

# Notify interval, in seconds.
notify_interval=895

# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock
```
But even though minidlna is running, using 

```
sudo service minidlna force-reload
```
 creates files.db, but with no database, log is:

```
[2013/03/02 23:13:22] minidlna.c:898: warn: Starting MiniDLNA version 1.0.24 [SQLite 3.7.13].
[2013/03/02 23:13:22] minidlna.c:926: warn: Creating new database...
[2013/03/02 23:13:22] minidlna.c:1006: warn: HTTP listening on port 8200
[2013/03/02 23:13:22] scanner.c:727: warn: Scanning /home/vladan/fotak
[2013/03/02 23:13:23] scanner.c:798: warn: Scanning /home/vladan/fotak finished (0 files)!
[2013/03/02 23:13:23] playlist.c:125: warn: Parsing playlists...
[2013/03/02 23:13:23] inotify.c:195: warn: WARNING: Inotify max_user_watches [8192] is low or close to the number of used watches [103] and I do not have permission to increase this limit.  Please do so manually by writing a higher value into /proc/sys/fs/inotify/max_user_watches.

```
It says 0 files. TV can browse only folders without files viewing.
I also tried 
```
minidlna -R
```
It creates in my database folder (/home/vladan/minidlna_webmin) another folder "art_cache" with previews of some pictures, but my TV still can't see anything.
It can still only browse folders, but doesn't see any files (because of no database). TV is Philips 55PFL5507K but I think the problem is in PC.
Do you know where could be the problem? Is it wrong that some of my pictures have suffix JPG and not jpg (don't know why)?
My lubuntu is 12.10. Thanks for help :).

---

