---
title: "Newb Webcam ( hp w2448hc )"
date: 2011-02-20
forum: Multimedia Software
---

### Post by AzrinArius on 2011-02-20
Hello all,

I'm using 10.10 x64. Everything seems to be working well except for my webcam, which is built in to my monitor( hpw2448hc ). Ubuntu seems to have detected and installed drivers for the monitor just fine, but I don't have webcam usage. I'm a total newbie so I don't really even know where to start. I was reading this page: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

But drew a blank when it asked me to "ls /dev/video" -- I get no such file or directory.

You can see the problem here: [http://i.imgur.com/CUZ99.png](http://i.imgur.com/CUZ99.png)

Could somebody push me in the right direction?

Thank you. :)

---

### Post by no2498 on 2011-02-20
if you have a lap top most say you need to push the keys fn+f2 to start the cam

open a terminal type dmesg click enter
look to see if it finds the cam
if it did
in a terminal type lsusb click enter
use the number and name in google to see what driver it uses
most all the drivers are in the kernel now days
this program helps me at times xawtv
its in your package manager
try the cam in it
it shows up in sound and video

---

### Post by AzrinArius on 2011-02-20
It's not a laptop. I'm not really sure what I'm looking for exactly, so I posted the results of dmesg here: [http://pastebin.com/RDuEnV6H](http://pastebin.com/RDuEnV6H)

I tried xawtv and that complains about a lack of a device also.

```

This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.35-25-generic)
xinerama 0: 1920x1200+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such device or address
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device or address
v4l2: open /dev/video0: No such device or address
v4l: open /dev/video0: No such device or address
no video grabber device available

```

---

### Post by no2498 on 2011-02-20
ok try this
type webcam in a terminal click enter
after that look in the package manager search for webcam 
find a program that uses fire wire ( ieee 1394) looks some thing like that
as i do not use fire wire

---

