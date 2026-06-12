---
title: "Video files won't play"
date: 2008-12-01
forum: Multimedia Software
---

### Post by Ehwin on 2008-12-01
everytime i try to open a video file such as .avi or .mpeg. 
the program i open it with just closes.
i've tried VLC, MPlayer, and the default video player
but they all close when i try to play a video file
i believe i installed the codecs. 
i'm not sure what's wrong?

---

### Post by Ehwin on 2008-12-01
is there anyone that can help me?

---

### Post by binbash on 2008-12-01
did you install w32codecs ? sudo apt-get install w32codecs

---

### Post by Ehwin on 2008-12-01
i just installed it and it said 

w32codecs is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 kdelibs-data linux-headers-2.6.27-7-generic
  amarok-common liblualib50 libavahi-qt3-1 libtunepimp5 libifp4 liblua50
  libnjb5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
edwin@edwin-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


but the movies still don't work

---

### Post by binbash on 2008-12-01
please start the video player at terminal, and give the output after crash.

---

### Post by Ehwin on 2008-12-01
sorry i'm not sure how you start the video player at terminal

---

### Post by binbash on 2008-12-01
alt + f2
write gnome-terminal there
when terminal comes, write vlc

---

### Post by Ehwin on 2008-12-01
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

---

### Post by binbash on 2008-12-01
Those ppl got same error alike you : 

[http://ubuntuforums.org/archive/index.php/t-194746.html](http://ubuntuforums.org/archive/index.php/t-194746.html)

Your solution (last post) : 

[http://forums.debian.net/viewtopic.php?p=184359&highlight=&sid=b809106686ef1855f8eb2443db36bd10](http://forums.debian.net/viewtopic.php?p=184359&highlight=&sid=b809106686ef1855f8eb2443db36bd10)

more : 

[http://forums.opensuse.org/applications/389147-x-error-failed-request-badalloc-insufficient-resources.html](http://forums.opensuse.org/applications/389147-x-error-failed-request-badalloc-insufficient-resources.html)

---

### Post by Ehwin on 2008-12-01
awesome! it works now
thank you

---

