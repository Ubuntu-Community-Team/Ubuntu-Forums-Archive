---
title: "Ekiga recognizes my webcam but does not show video"
date: 2011-03-27
forum: Multimedia Software
---

### Post by hetihe on 2011-03-27
hi,
I get the following information : "Your video driver doesn't support the requested video format" while trying to use video in Ekiga, using 10.04, please help!

---

### Post by Schugy on 2011-03-27
Try ```
sudo apt-get install libpt-1.11.2-plugins-alsa libpt-1.11.2-plugins-oss libpt-1.11.2-plugins-v4l libpt-1.11.2-plugins-v4l2
``` and restart ekiga.

---

### Post by hetihe on 2011-03-27
All the packages above are now installed, but no joy :  (

---

### Post by Schugy on 2011-03-27
Maybe there was a space or linebreak in this command.

But you can do it grafically with synaptic and others.

---

### Post by hetihe on 2011-03-28
All the packages above are now installed, but no joy  :   (

---

### Post by no2498 on 2011-03-28
did you set it to auto
try v4l or v4l2

---

### Post by hetihe on 2011-03-29
> **no2498 said:**
> did you set it to auto
try v4l or v4l2
"videodriver doesn't support the asked videoformat"

---

### Post by Schugy on 2011-03-29
Maybe we need more info:
```
lsusb -vv > lsusb.txt
```
and post the usb id of the webcam.

```

dpkg-query -W |grep libpt
libpt-1.11.2-plugins-alsa       1.11.2-2ubuntu1
libpt-1.11.2-plugins-oss        1.11.2-2ubuntu1
libpt-1.11.2-plugins-v4l        1.11.2-2ubuntu1
libpt-1.11.2-plugins-v4l2       1.11.2-2ubuntu1
libpt2.6.4      2.6.4-1ubuntu2
libpt2.6.5      2.6.5-1ubuntu1
libpt2.6.5-plugins      2.6.5-1ubuntu1
libpth20        2.0.7-14

```

```

dpkg-query -W |grep v4l
lib32v4l-0      0.6.4-1ubuntu1
libpt-1.11.2-plugins-v4l        1.11.2-2ubuntu1
libpt-1.11.2-plugins-v4l2       1.11.2-2ubuntu1
libv4l-0        0.6.4-1ubuntu1
v4l-conf        3.95.dfsg.1-8.1ubuntu1
xserver-xorg-video-v4l  1:0.2.0-4

```

---

### Post by no2498 on 2011-03-29
try this

open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto

just seeing if your cam works is all

---

### Post by hetihe on 2011-04-01
timo@tytotkolme:~$ dpkg-query -W |grep libpt
libpt-1.11.2	1.11.2-2ubuntu1
libpt-1.11.2-plugins-alsa	1.11.2-2ubuntu1
libpt-1.11.2-plugins-oss	1.11.2-2ubuntu1
libpt-1.11.2-plugins-v4l	1.11.2-2ubuntu1
libpt-1.11.2-plugins-v4l2	1.11.2-2ubuntu1
libpt2.6.5	2.6.5-1ubuntu1
libpt2.6.7	2.6.7-1~webupd8~lucid
libpth20	2.0.7-14
timo@tytotkolme:~$ dpkg-query -W |grep v4l
libpt-1.11.2-plugins-v4l	1.11.2-2ubuntu1
libpt-1.11.2-plugins-v4l2	1.11.2-2ubuntu1
libv4l-0	0.6.4-1ubuntu1
xserver-xorg-video-v4l	1:0.2.0-4

hello,
I tried gstreamer-properties, but it doesnot seem to rocognize webcam.
id: 046d:081d ptlib/v4l
:(

---

### Post by no2498 on 2011-04-01
open a terminal type dmesg click enter
did it load a grabber

---

### Post by Matt 6:27 on 2011-05-13
I had the same issue with a Logitech C250... loaded the plugins and got no relief even in Auto.  I then looked at the settings I used for Cheese and noted the default was 640x480. Back in Ekiga, I changed the default from 320x... to 640x480 and my camera came on.  Not really sure how/why, but it works.  Note that once it worked, I could drop it back down to the smaller setting without a problem.  Thanks, Schugy!

---

