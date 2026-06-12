---
title: "/etc/ati/ati-fglrx.sh file missing after ati driver module installation"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by super7 on 2007-02-23
I followed the howto [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) about compiling the ati module using the newest drivers ati fglrx drivers (8.34.8  ) and everything worked out quite nicely.

although after reboot I get the message that the file /etc/ati/ati-fglrx.sh is missing (which is called in /etc/profile). to be able to login again I just commented the line and finally I have a somehow acceptable dual-head system with an x200m card (see below). but since the installation I can't just restart my X with Ctrl-Alt-Backspace (this gets me to a blank screen without function from where I have to reset).

secondly my config is not perfect:
1) still no xinerama, I have two independent desktops which share mouse and keyboard (is okay for now ...)
2) the "mouse cursor" bug which I had before too with the ati drivers is still there but only on the second screen ... (instead of the mouse cursor I have a ugly square block of the different colors)

frankly currently I didn't found time to digg into the aticonfig possibility so probably I find solutions to my two problems but I would be very grateful if somebody could lead me to the missing file (doesn't seem to be on my hdd) or just post it here so I can copy it into my /etc/ati/ folder.

but probably there is more missing? the folder /etc/ati/ contains the following:
-r-xr-xr-x 1 root root  2769 2007-02-23 12:21 authatieventsd.sh
-rw-r--r-- 1 root root 30704 2007-02-23 12:21 control
-r--r--r-- 1 root root   545 2007-02-23 12:21 fglrxprofiles.csv
-r--r--r-- 1 root root   838 2007-02-23 12:21 fglrxrc
-r--r--r-- 1 root root 12902 2007-02-23 12:21 logo_mask.xbm.example
-r--r--r-- 1 root root 12887 2007-02-23 12:21 logo.xbm.example


thank you all for your support,

claus

---

### Post by KaMZaTa on 2007-06-23
For me the same error. Help!

---

### Post by dopeking on 2008-03-06
Hy Guys
After trying to install the 8.3 Ati driver, my gdm/Xorg was broken and i could not start Gnome.
Just delete the old /etc/ati/ati-fglrx.sh and replace it with a empty file.
OR
the elegant solution is to comment it out at the bottom /etc/profile
This worked for me!

---

