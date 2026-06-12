---
title: "problems with ATI radeon 9250 graphics card"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by cailamaia on 2007-09-30
i'm trying to install my radeon 9250 by manually running the latest driver. but it refuses to run the install and gives me a strange error.


orell@Rufus:~$ cd /home/orell/Desktop
orell@Rufus:~/Desktop$ sh ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


i'm not exactly sure where to go from here. from what it looks like, there was some bad code in the driver file, but i can't be sure. anyone got a fix?

---

### Post by kellemes on 2007-09-30
[http://ubuntuforums.org/archive/index.php/t-243342.html]("http://ubuntuforums.org/archive/index.php/t-243342.html")

---

### Post by Stefanius on 2007-11-04
Hi, i follewed the instructions, but this stupido forgot the 'reverse' code to the orignal bash/dash/sh mode. I already created a post wich contain more info, so i will link to it:

[http://ubuntuforums.org/showthread.php?t=602388](http://ubuntuforums.org/showthread.php?t=602388)

I hope you can help me
Stef.

---

### Post by Yellow Pasque on 2007-11-04
Try running the installer with root privileges (i.e. put sudo in front of the command)

---

