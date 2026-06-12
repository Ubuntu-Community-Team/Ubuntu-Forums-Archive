---
title: "minidlna does not work with external drive"
date: 2022-09-06
forum: Multimedia Software
---

### Post by davidwillis on 2022-09-06
I have searched on here, and found a lot of instances where this is a problem, but I have tried all the solutions, and none seem to work.

 minidlna.c:670: error: Media directory "/media/david/storage/Videos" not accessible [Permission denied]

I have this drive mounted in fstab using the following: UUID=c1b49ab0-9e14-4435-8483-b6311ec47a3c /media/david/storage ext4 auto,nofail,rw,acl 0 2

I have also tried just plugging it in without the line in fsab, but it doesn't work.

I have user set to root in both minidlna.conf and /etc/default/minidlna

I have tried all kinds of permissions on the folder, but nothing helps.

I can change the directory to somewhere like /usr and the error goes away. For some reason it just won't work with my usb drive. I even tried plugging in a different drive formatted to exfat, and it also did not work.

The strange thing is that minidlna does work in mxlinux, just plugging in the drive, and changing the settings to root in the two configuration files. But I would really like this to work in Ubuntu.

I hope there is something I am missing.

---

### Post by ajgreeny on 2022-09-07
I am fairly certain that this will indeed be a permissions problem of some sort but so far we do not have enough info to help very much more.

As a start let's see the output of command ```
ls -l /media/david/storage/Videos
``` to see exactly what we're dealing with permissions-wise on that USB's mountpoint folder.
It may also help to see what is in your minidlna.conf file as there could be some clues there.

I have never used an external USB disk for any media I want to stream with minidlna but I think I can recall seeing somewhere that if the USB disk was formatted to NTFS and mounted to give full user read/write permissions that it was easier than ext4 to get working.
NTFS is not sensible for me as I have no Windows system to repair NTFS if it is ever required.

---

### Post by davidwillis on 2022-09-07
I agree.  I have also thought it must be something to do with the permissions, and I have tried a lot of settings.  But maybe I just have not used the correct one.   However I find it really strange that the same drive works fine in mx linux.  Would the permissions change from one OS to the other?  Would it help to have the same command from mxlinux too?

here are the permissions of the Videos folder too

drwxrwxrwx+  root  root   


```
$ ls -l /media/david/storage/Videos
total 34518332
-rwxrwxrwx+  1 root root 2596456189 Dec  5  2019 '2019-12-05 17-36-24.mp4'
-rwxrwxrwx+  1 root root 1546582289 Dec  7  2019 '2019-12-07 11-14-04.mp4'
-rwxrwxrwx+  1 root root 4288525248 Dec  7  2019 '2019-12-07 13-18-59.mp4'
-rwxrwxrwx+  1 root root   65878172 May 23  2021  2A800Meter.mkv
-rwxrwxrwx+  1 root root   55896006 May 23  2021  800_2019.mkv
drwxrwxrwx+ 93 root root      12288 Mar  5  2022  Adults
-rwxrwxrwx+  1 root root 2718437327 Dec  7  2019  Ashlyn_1_05_easter_05.mp4
drwxrwxrwx+  2 root root       4096 Jun 29  2018 "Ashlyn's Don't Play with Swords Video"
drwxrwxrwx+  2 root root       4096 Jun 29  2018 'Ashlyn singing'
drwxrwxrwx+  2 root root       4096 Apr 26 21:12  audio
-rwxrwxrwx+  1 root root  155365107 Jan 13  2020 'Be 100 Percent Responsible  Elder Lynn G. Robbins.mp4'
drwxrwxrwx+  2 root root       4096 Jun 29  2018  bible
-rwxrwxrwx+  1 root root 1427889826 Dec  7  2019  Christmas_2004.mp4
-rwxrwxrwx+  1 root root 4707570517 Dec  7  2019  Christmas_2005_Jan_May_2006.mp4
drwxrwxrwx+  3 root root       4096 Sep 16  2018  conference
drwxrwxrwx+  3 root root       4096 May 28 08:05  Documentaries
drwxrwxrwx+  5 root root       4096 Sep 28  2019 'Family Videos'
drwxrwxrwx+  2 root root       4096 Feb 20  2022  hawaii_pic
drwxrwxrwx+  3 root root       4096 Feb 20  2022  hawaii_vid
-rwxrwxrwx+  1 root root   45215178 Oct 20  2019 'How to practice emotional first aid - Guy Winch.mp4'
drwxrwxrwx+ 79 root root      20480 Mar  5  2022  Kids
-rwxrwxrwx+  1 root root  271022585 Nov 12  2018 'L10 Sandy Presentation(1).mp4'
-rwxrwxrwx+  1 root root 3371703885 Dec  7  2019  laketown_parade_Aaron_05_fall_winter.mp4
drwxrwxrwx+  6 root root       4096 Jul 21  2017  living
-rwxrwxrwx+  1 root root 4099722975 Dec  7  2019  May_06_Jan_07.mp4
-rwxrwxrwx+  1 root root   25326407 Nov 25  2018  mstroud_2018-10-16T14_25_27-07_00.mp3
-rwxrwxrwx+  1 root root   49396196 Nov 20  2018  mstroud_2018-11-19T21_10_40-08_00.mp3
-rwxrwxrwx+  1 root root  168934740 Feb 19  2020  MVI_3372.m4v
-rwxrwxrwx+  1 root root  200125168 Feb 19  2020  MVI_3373.m4v
drwxrwxrwx+ 62 root root       4096 Sep  5 20:06  New
-rwxrwxrwx+  1 root root  666154540 Jan 21  2021  sdi_owd_dvd_v1.avi
-rwxrwxrwx+  1 root root  221307904 Jan 10  2021  simplescreenrecorder-2021-01-10_13.04.16.mkv
-rwxrwxrwx+  1 root root  689665335 Mar  4  2022  simplescreenrecorder-2022-03-04_12.29.13.mkv
-rwxrwxrwx+  1 root root  671990810 Mar  4  2022  simplescreenrecorder-2022-03-04_12.46.10.mkv
-rwxrwxrwx+  1 root root  178563911 Mar  4  2022  simplescreenrecorder-2022-03-04_20.17.38.mkv
-rwxrwxrwx+  1 root root    2538828 Mar  5  2022  simplescreenrecorder-2022-03-05_13.56.32.mkv
-rwxrwxrwx+  1 root root    4587789 Mar  5  2022  simplescreenrecorder-2022-03-05_13.58.40.mkv
drwxrwxrwx+  4 root root       4096 Sep 28  2019 'Solid works'
-rwxrwxrwx+  1 root root     219208 Aug 28 20:13  test_screen3.mk4
-rwxrwxrwx+  1 root root  111643906 Mar 13  2020  timeline.mp4
drwxrwxrwx+  3 root root      12288 Mar  1  2020  vacation
drwxrwxrwx+  4 root root       4096 Sep 28  2019 'Workout videos'
drwxrwxrwx+  3 root root       4096 Jun 29  2018  Wrestling
drwxrwxrwx+  2 root root       4096 Mar  9  2019  writing
```

here is my minidlna.conf

```
# This is the configuration file for the MiniDLNA daemon, a DLNA/UPnP-AV media
# server.
#
# Unless otherwise noted, the commented out options show their default value.
#
# On Debian, you can also refer to the minidlna.conf(5) man page for
# documentation about this file.

# Specify the user name or uid to run as (root by default).
# On Debian system command line option (from /etc/default/minidlna) overrides this.
user=root


# Path to the directory you want scanned for media files.
#
# This option can be specified more than once if you want multiple directories
# scanned.
#
# If you want to restrict a media_dir to a specific content type, you can
# prepend the directory name with a letter representing the type (A, P or V),
# followed by a comma, as so:
#   * "A" for audio    (eg. media_dir=A,/var/lib/minidlna/music)
#   * "P" for pictures (eg. media_dir=P,/var/lib/minidlna/pictures)
#   * "V" for video    (eg. media_dir=V,/var/lib/minidlna/videos)
#   * "PV" for pictures and video (eg. media_dir=PV,/var/lib/minidlna/digital_camera)
media_dir=/media/david/storage/Videos

# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no

# Path to the directory that should hold the database and album art cache.
#db_dir=/var/cache/minidlna

# Path to the directory that should hold the log file.
#log_dir=/var/log/minidlna

# Type and minimum level of importance of messages to be logged.
#
# The types are "artwork", "database", "general", "http", "inotify",
# "metadata", "scanner", "ssdp" and "tivo".
#
# The levels are "off", "fatal", "error", "warn", "info" or "debug".
# "off" turns of logging entirely, "fatal" is the highest level of importance
# and "debug" the lowest.
#
# The types are comma-separated, followed by an equal sign ("="), followed by a
# level that applies to the preceding types. This can be repeated, separating
# each of these constructs with a comma.
#
# The default is to log all types of messages at the "warn" level.
#log_level=general,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=warn

# Use a different container as the root of the directory tree presented to
# clients. The possible values are:
#   * "." - standard container
#   * "B" - "Browse Directory"
#   * "M" - "Music"
#   * "P" - "Pictures"
#   * "V" - "Video"
#   * Or, you can specify the ObjectID of your desired root container
#     (eg. 1$F for Music/Playlists)
# If you specify "B" and the client device is audio-only then "Music/Folders"
# will be used as root.
#root_container=.

# Network interface(s) to bind to (e.g. eth0), comma delimited.
# This option can be specified more than once.
#network_interface=

# Port number for HTTP traffic (descriptions, SOAP, media transfer).
# This option is mandatory (or it must be specified on the command-line using
# "-p").
port=8200

# URL presented to clients (e.g. [http://example.com:80](http://example.com:80)).
#presentation_url=/

# Name that the DLNA server presents to clients.
# Defaults to "hostname: username".
#friendly_name=

# Serial number the server reports to clients.
# Defaults to the MAC address of nework interface.
#serial=

# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)

# Model number the server reports to clients.
# Defaults to the version number of minidlna.
#model_number=

# Automatic discovery of new files in the media_dir directory.
#inotify=yes

# List of file names to look for when searching for album art.
# Names should be delimited with a forward slash ("/").
# This option can be specified more than once.
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg
album_art_names=AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg
album_art_names=Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# Strictly adhere to DLNA standards.
# This allows server-side downscaling of very large JPEG images, which may
# decrease JPEG serving performance on (at least) Sony DLNA products.
#strict_dlna=no

# Support for streaming .jpg and .mp3 files to a TiVo supporting HMO.
#enable_tivo=no

# Which method to use for registering in TiVo: 'bonjour' (default) or
# legacy 'beacon'
#tivo_discovery=bonjour

# SSDP notify interval, in seconds.
#notify_interval=895

# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock

# Always set SortCriteria to this value, regardless of the SortCriteria
# passed by the client
# e.g. force_sort_criteria=+upnp:class,+upnp:originalTrackNumber,+dc:title
#force_sort_criteria=

# maximum number of simultaneous connections
# note: many clients open several simultaneous connections while streaming
#max_connections=50

# set this to yes to allow symlinks that point outside user-defined media_dirs.
#wide_links=no
friendly_name=David_DLNA
```

and here is my /etc/default/minidlna

```
# Defaults for minidlna initscript
# sourced by minidlna.service and /etc/init.d/minidlna
#
# WARNING: This file is used for compatibility with sysv init only.
# If you are using systemd (Debian default), please override minidlna.service
# unit instead of modifying these variables.


# These options can be set to modify the behavior of the minidlna init script.
# The options commented out show the default values.

# Path to the configuration file
#CONFIGFILE="/etc/minidlna.conf"

# Path to the log file
#LOGFILE="/var/log/minidlna/minidlna.log"

# User and group the daemon should run as
# only for sysV init, for systemd please override minidlna.service
USER="root"
#GROUP="minidlna"

# Additional options that are passed to the daemon
# We pass -r option to do soft non-destructive rebuild on every start-up.
# If your systerm restarts often, you might want to remove this.
#DAEMON_OPTS="-r"
```

---

### Post by ajgreeny on 2022-09-07
I can not see any really obvious things wrong in your minidlna.conf file but there are differences between yours and mine.
I have uncommented both the ***inotify=yes*** line so that it is active and also the interval line ***notify_interval=895*** but I am not sure they are the cause of the problem you have.

---

### Post by davidwillis on 2022-09-07
> **ajgreeny said:**
> I can not see any really obvious things wrong in your minidlna.conf file but there are differences between yours and mine.
I have uncommented both the ***inotify=yes*** line so that it is active and also the interval line ***notify_interval=895*** but I am not sure they are the cause of the problem you have.

I made those changed to my minidlna.conf file, but it didn't make any difference.

I also tried using a flash drive that is formatted to ntfs, but that also did not work.

---

### Post by ajgreeny on 2022-09-07
You may have already seen this thread but if not it cold be helpful to you suggesting that the problem results from the automount to /media/david/storage/Videos. Try mounting it to some other folder in for example /mnt rather than /media.
[https://askubuntu.com/questions/1044674/minidlna-doesnt-see-anything-on-external-usb-hdd](https://askubuntu.com/questions/1044674/minidlna-doesnt-see-anything-on-external-usb-hdd)

---

### Post by davidwillis on 2022-09-07
That did it!   Changing the mount location to mnt rather than media fixed the problem.   I had tried mounting it in my home directory, but that also did not work.

Thanks!  I have been trying to figure this out for weeks.

---

### Post by ajgreeny on 2022-09-08
Brilliant!
And thanks for marking the thread as SOLVED.

---

