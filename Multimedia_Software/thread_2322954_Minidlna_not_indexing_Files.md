---
title: "Minidlna not indexing Files"
date: 2016-05-01
forum: Multimedia Software
---

### Post by tlaporta on 2016-05-01
I'm having an issue getting minidlna to work since I upgraded to Xenial. The short version of the problem is that the miniDLNA server running on my Xenial laptop is seen by my Raspberry Pi running OSMC, but no files are showing up. In addition, when I check the web interface, no files are listed. I've checked the logs, and don't see any obvious error messages, and can't figure out why the files aren't being indexed. My config file is as below:

```
# This is the configuration file for the MiniDLNA daemon, a DLNA/UPnP-AV media
# server.
#
# Unless otherwise noted, the commented out options show their default value.
#
# On Debian, you can also refer to the minidlna.conf(5) man page for
# documentation about this file.


# Specify the user name or uid to run as.
#user=minidlna




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
media_dir=V,/home/fattom/Videos/Movies
media_dir=V,/home/fattom/Videos/TV


# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no


# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna


# Path to the directory that should hold the log file.
log_dir=/var/log


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
log_level=general=debug,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=warn


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
port=8201


# URL presented to clients (e.g. http://example.com:80).
#presentation_url=/


# Name that the DLNA server presents to clients.
# Defaults to "hostname: username".
#friendly_name=


# Serial number the server reports to clients.
# Defaults to 00000000.
serial=681019810597110


# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)


# Model number the server reports to clients.
# Defaults to the version number of minidlna.
#model_number=


# Automatic discovery of new files in the media_dir directory.
inotify=yes


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


# Notify interval, in seconds.
notify_interval=300


# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock


# Always set SortCriteria to this value, regardless of the SortCriteria
# passed by the client
# e.g. force_sort_criteria=+upnp:class,+upnp:originalTrackNumber,+dc:title
#force_sort_criteria=


# maximum number of simultaneous connections
# note: many clients open several simultaneous connections while streaming
#max_connections=50

```

After stopping the server, forcing a refresh and restarting, the log reads:

```
[2016/05/01 20:50:25] minidlna.c:154: warn: received signal 15, good-bye
[2016/05/01 20:50:38] minidlna.c:1041: warn: Starting MiniDLNA version 1.1.5.
[2016/05/01 20:50:38] minidlna.c:364: warn: Creating new database at /var/cache/minidlna/files.db
[2016/05/01 20:50:38] minidlna.c:1081: warn: HTTP listening on port 8201
[2016/05/01 20:50:38] getifaddr.c:338: info: Enabling interface 192.168.1.2/255.255.255.0
[2016/05/01 20:50:38] playlist.c:125: warn: Parsing playlists...
[2016/05/01 20:50:38] playlist.c:259: warn: Finished parsing playlists.
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39145
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39146
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39147
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39148
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39149
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39150
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39151
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39152
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39153
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39154
[2016/05/01 20:50:38] minidlna.c:1277: debug: HTTP connection from 192.168.1.5:39155

```

The folder /home/fattom/Videos is 777 and has two subfolders, Movies and TV, which contain a variety of folders and single files. It's killing me that I can't seem to find a single reason why minidlna is not indexing these files. Any ideas would be greatly appreciated.

---

### Post by SeijiSensei on 2016-05-02
You can try forcing minidlna to rebuild its database by deleting or renaming the file /var/cache/minidlna/files.db and running "sudo minidlnad -R" to rebuild.  I've had to do this once or twice as I recall.

---

### Post by tlaporta on 2016-05-04
Thanks for the response. Strangely enough, it seems to have fixed itself. I have no idea how, but I'm glad that it's working now.

---

