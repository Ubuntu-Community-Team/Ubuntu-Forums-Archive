---
title: "HP DV6000 Webcam not getting detected in Ubuntu 10.04 (Lucid Lynx)"
date: 2010-05-09
forum: Multimedia Software
---

### Post by mithil_r on 2010-05-09
I have a HP DV6000 series laptop and its integrated webcam is not getting detected in Ubuntu 10.04
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I tried checking with :
xawtv /dev/video0
This gives me following error :

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-21-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such device or address
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device or address
v4l2: open /dev/video0: No such device or address
v4l: open /dev/video0: No such device or address
no video grabber device available

Could someone please help me on this?

-Mithil

---

### Post by niteshreddy on 2010-08-13
This post says it has been solved.

But i am not understanding it.

can you help me by understanding it.

[http://ubuntuforums.org/showthread.php?t=829203&highlight=hp+dv6000+integrated+webcam](http://ubuntuforums.org/showthread.php?t=829203&highlight=hp+dv6000+integrated+webcam)


Thanks.

---

### Post by no2498 on 2010-08-13
most webcams just work now days no need to install drivers
in/on 910 and up cheese webcam booth is installed
look in sound and video for it
try the cam in cheese first

hope this helps

---

### Post by Eenz on 2010-08-15
I have the exact same problem and can't find a solution anywhere.

I'm running Lucid Lynx 10.04 on a HP Pavillion DV6000 with a built in Ricoh Webcam

My lsusb gives me:
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Cheese says No Device Found.
It doesn't work on Skype and XawTV doesn't seem to work at all.

I tried to do
sudo apt-get install r5u87x
but nothing has changed

I've also tried a few other things to install r5u87x but no luck.

All the solved problems seems to only work for r5u870 devices. I don't know enough about computers to know if mine is different. I only know that those fixes don't work for me.

I'm new at linux, but if someone can give me some straight forward advice I think I'm competent enough to give it a shot. Let me know if more info is needed.

---

### Post by SteveMcQwark on 2010-08-26
I followed the directions on this page on Lucid Lynx, and now my camera works:
[https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa)

Hope this helps.

---

### Post by lidex on 2010-08-28
HP Dv series webcam help:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam)

---

### Post by Eenz on 2010-08-30
**SteveMcQwar**k
I have tried that solution a few times, but as I said, I don't think my camera is the R5U87x, but rather the 1000 (???)

**lidex**
I have just tried following those instructions (A) again and got this result:

sudo apt-get install luvcview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
luvcview is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo modprobe uvcvideo
luvcview -d /dev/video0 -f yuv -s 640x480
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory

(B) is again about the R5U87x webcam and a different HP model and has so far not worked.

I read somewhere that Windows might have 'blocked' access to the webcam, but Windows is not longer installed on this laptop - only Ubuntu. Any ideas about that?

Thank you both for trying!

---

### Post by no2498 on 2010-08-31
this is your webcam

Bus 001 Device 003: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000


type webcam
in a terminal see what comes up

---

### Post by lidex on 2010-09-03
Maybe installing this will help:
```
sudo apt-get install xserver-xorg-video-v4l
```

---

### Post by Eenz on 2011-03-01
Well, my laptop broke down so I never got to check out the latest suggestion. Shame.
Thank for the help though!

Now on to dual boot with Vista on my PC :)

---

### Post by 0z0ne on 2011-03-01
Hello friends,

I also have the exact same laptop with the exact same problem.
(HP DV6000, webcam not recognised)
I've tried everything everyone suggested above and cheese still says "no device found".
Please let me know if anyone has another idea...

cheers, 
ozone

ps.

The most promising thing i got happening was by following SteveMcQuarks link to
[https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa)
got to the last step and the last thing terminal told me was:

Downloading firmware...
cd: 78: can't cd to r5u87x

---

