---
title: "ushare works...but no media"
date: 2011-02-12
forum: Multimedia Software
---

### Post by hurtaxis on 2011-02-12
I am trying to stream my music and videos to my xbox 360 from ubuntu 10.10, and I have set up ushare to do that. Ushare seems to be workign correctly, it starts up and the xbox recognises the share from the media menu, but there is no videos or music! For some reason ushare doesnt find any media in the folders I specified, and I double checked and the paths look correct to me. This is the error I get in the terminal:

> tim@TimComputer:~$ ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.6:49160
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/tim/torrents
scandir: No such file or directory
Looking for files in content directory : /media/Vistax64/DocumentsandSettings/Tim/Desktop/Torrents
scandir: No such file or directory
Looking for files in content directory : /media/Vistax64/DocumentsandSettings/Tim/Desktop/Archos/Video
scandir: No such file or directory
Looking for files in content directory : /media/Vistax64/DocumentsandSettings/Tim/Music/Media
scandir: No such file or directory
Found 4 files and subdirectories.

Does anyone have any idea how to fix this?

---

### Post by hurtaxis on 2011-02-21
bump

---

### Post by nubias on 2011-02-21
I had a problem similar to this.

It seemed to be a problem with sharing multiple dirs in the ushare.conf file.

What I ended up doing is making a folder with virtual links to all my shares and just putting a link to that one entry in my ushare.conf file.

---

### Post by hurtaxis on 2011-02-21
So how would I go about making these virtual links?

---

### Post by nubias on 2011-02-21
Right click on one of your media folders and click "Make Link"

Move that newly created link to your common virtual dirs folder.

Do this for all your media folders.

Then edit your /etc/ushare.conf file and point it to your vdirs folder.

---

### Post by comthre3 on 2011-05-05
can someone help us with that? im still facing the same issue, PS3 sees the directories, but no content is being pushed by ushare, I can see the whole directory tree but no media files. im using 11.04. any help would be much appreciated.

---

### Post by devind25 on 2011-05-14
Nubias can you please explain in more detail how to go about moving the link to the folder to the virtual directory because I am stuck after I create the link to the folder I want to share.

---

