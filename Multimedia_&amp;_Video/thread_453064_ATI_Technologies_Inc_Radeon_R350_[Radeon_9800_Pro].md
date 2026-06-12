---
title: "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by kalmak on 2007-05-24
I have seen many postings regarding the "/dev/video0: No such file or directory" message and I have spent many hours going through them without finding a solution.  I have installed tvtime and xawtv both before and after installing the ATI driver for this card - all with the same result:

xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
WARNING: No DGA support available for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/lawrence/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory

The output from xawtv -hwscan is:
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
looking for available devices
port 59-59
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

After burning out my eyeballs, I have given up expecting to find a solution.  Any new insights that I may have missed in my travels through the forums?

---

### Post by kalmak on 2007-05-24
Information that I did not include in my previous post, running Ubuntu 7.04

Output from fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

