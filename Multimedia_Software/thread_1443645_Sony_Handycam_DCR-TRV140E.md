---
title: "Sony Handycam DCR-TRV140E"
date: 2010-03-31
forum: Multimedia Software
---

### Post by peterroots on 2010-03-31
There seem to have been loads of posts on this (or closly related issues)but none seem to answer the basic problem -
My video camera supports both firewire and USB but my laptop computer only has USB and no PCMCIA port so adding firewire is a non starter.

On pluging in the camera lsusb gives me this
```
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 054c:0045 Sony Corp. Digital Imaging Video
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0ab0:0001 Arrow Strong Electronics Co., Ltd
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
So the camera is at least being detected. dmesg does not report the camera and I can't find it in /proc anywhere
The camera is set to stream USB

I have tried kino (now uninstalled) kdenlive and VLC following several posts in various places that suggested one or the other would work.
kdenlive and VLC both can read the built in web cam on /dev/video0 but I have no idea how to get the camera to be recognised or mounted on /dev.

Can anybody suggest anything?

---

### Post by mocha on 2010-03-31
That camera needs Firewire to transfer video from the tape.  It's just the way it is.

---

### Post by lisati on 2010-03-31
I have a similar camera, but one which only has firewire. What the camera manual calls an "i.link" connection connects to the "DV" port on my laptop or desktop. (mine's a 147)

---

### Post by no2498 on 2010-03-31
anyway for you to turn off or unplug the built in web cam

i have 2 web cams and can not switch between them 

both use the same driver

and now that ubuntu put v4l1 and v4l2 together is the problem for you

you may go ask at the cheese site 

ubuntu give the settings for web cams to cheese

hope you find what you need

---

### Post by peterroots on 2010-04-01
mocha - the camera has firewire and USB, it came with a usb cable not a firewire cable, the windows software that came with it can use usb to get video from tape (and does not run under wine). So the camera does not 'need' firewire to transfer data, I just can't get kubuntu to use usb with the camera! That is the problem.

no2498 - I had never heard of cheese before (at least not in the computer context that is). Thanks for the idea but it does not really help much as I can't figure out how to make the camera appear as a device that I can tell any software to use.

Essentially the problem is - the camera gets detected but not mounted as a device. Anyone know how to get round this?

---

### Post by no2498 on 2010-04-01
you can try gstreamer-properties

open a terminal type gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

do not think it will help you
but it sets the dev video, aka 0, 1, 2. 3, and so on

---

