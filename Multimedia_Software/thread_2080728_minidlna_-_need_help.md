---
title: "minidlna - need help"
date: 2012-11-04
forum: Multimedia Software
---

### Post by flecos on 2012-11-04
Im not sure where to post this. I hope here is ok. Btw sry my english.

Im using ubuntu 12.04 32.

Here i show you the log from minidlna, i dont know what to do. This happened after i did sudo service minidlna force-reload

[2012/11/04 22:58:54] minidlna.c:935: warn: Creating new database...
[2012/11/04 22:58:54] minidlna.c:1002: warn: HTTP listening on port 8200
[2012/11/04 22:58:54] scanner.c:719: warn: Scanning /opt
[2012/11/04 22:58:54] scanner.c:790: warn: Scanning /opt finished (0 files)!
[2012/11/04 22:58:54] scanner.c:719: warn: Scanning /home/me/Música
[2012/11/04 22:58:54] tagutils/tagutils-mp3.c:49: error: Cannot open /home/me/Música/123.mp3
[2012/11/04 22:58:54] tagutils/tagutils-mp3.c:567: error: Could not open /home/me/Música/123.mp3 for reading
[2012/11/04 22:58:54] metadata.c:372: warn: Cannot extract tags from /home/me/Música/123.mp3!
[2012/11/04 22:58:54] scanner.c:498: warn: Unsuccessful getting details for /home/me/Música/123.mp3!
[2012/11/04 22:58:54] scanner.c:790: warn: Scanning /home/me/Música finished (0 files)!
[2012/11/04 22:58:54] scanner.c:719: warn: Scanning /home/me/Vídeos
[2012/11/04 22:58:54] metadata.c:677: warn: Opening /home/me/Vídeos/456.avi failed!
[2012/11/04 22:58:54] scanner.c:498: warn: Unsuccessful getting details for /home/me/Vídeos/456.avi!
[2012/11/04 22:58:54] scanner.c:790: warn: Scanning /home/me/Vídeos finished (0 files)!
[2012/11/04 22:58:54] scanner.c:719: warn: Scanning /home/me/Imágenes
[2012/11/04 22:58:55] inotify.c:182: warn: WARNING: Inotify max_user_watches [8192] is low or close to the number of used watches [0] and I do not have permission to increase this limit.  Please do so manually by writing a higher value into /proc/sys/fs/inotify/max_user_watches.

This is my configuration:

port=8200
network_interface=eth0
media_dir=/opt
media_dir=A,/home/flecos/Música
media_dir=V,/home/flecos/Vídeos
media_dir=P,/home/flecos/Imágenes
friendly_name=UBUNTU 12.04

# set this if you would like to specify the directory where you want MiniDLNA to store its database and album art cache
#db_dir=/var/cache/minidlna

# set this if you would like to specify the directory where you want MiniDLNA to store its log file
#log_dir=/var/log

# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

inotify=yes
enable_tivo=no
strict_dlna=no

# default presentation url is http address on port 80
#presentation_url=http://www.mylan/index.php

notify_interval=900
serial=12345678
model_number=1

---

### Post by cariboo on 2012-11-05
There is a couple of things I see in your minidlna.conf file, that are different from the way I have mine set up. The first thing I would do is enable logging, by uncommenting the following line:

```
#log_dir=/var/log
```

just remove the # from the start of the line. This way you can see what is causing the error. The log is /var/log/minidlna.log.

I have:

```
notify_interval=900
``` 

set to 895, and don't see any error messages. 

The last thing is to comment out the line that says:

```
media_dir=/opt
```

This seems to a default path, that isn't needed if you don't have any media located in /opt.

I followed this [howto]("https://help.ubuntu.com/community/MiniDLNA"), and haven't had any problems with either of the two minidlna servers I run.

---

### Post by Bucky Ball on 2012-11-05
[I]Thread moved to [B]Multimedia & Video

[/B][/I]Welcome to the forums.

---

### Post by flecos on 2012-11-05
Thanks a lot for the guide! Now all is working fine I decided to complete uninstall minidlna and remove some files manually. I instaled again but the minildna version of the guide, and now its working!
Sorry for posting at wrong place. Problem solved.

---

### Post by Bucky Ball on 2012-11-05
All good. To help others, please mark thread as Solved from Thread Tools at top right. Enjoy the learning curve, the OS and the forums. ;)

---

