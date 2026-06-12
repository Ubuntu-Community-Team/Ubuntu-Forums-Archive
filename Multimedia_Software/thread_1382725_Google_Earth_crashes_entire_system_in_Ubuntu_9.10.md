---
title: "Google Earth crashes entire system in Ubuntu 9.10"
date: 2010-01-16
forum: Multimedia Software
---

### Post by gabrieldiegoteixeira on 2010-01-16
Hello,

When I start Google Earth in my laptop, it runs normally but after from 10 seconds to several minutes the computer freezes completely or, in a few times, started to behave weirdly.
The version of Ubuntu that I have installed is the 32-bit Ubuntu 9.10 and the laptop is a Fujitsu Siemens Lifebook T4010, which has an Intel 855GME GPU.
Initially I suspected that was the video driver that was not working, so I tried to disable the 3D acceleration. To achieve this I created the file /etc/X11/xorg.conf and put in it:

Section "Module"
       Disable    "dri"
EndSection

Since by default, this file doesn't exist, so I had to create a new one. Anyway with this, the situation gets worse and the laptop doesn't boot anymore, so I had to boot with the Live CD and rename this file to /etc/X11/xorg.conf.marche_pas to be able to boot again, and the problem with the Google Earth remained not solved. I noticed that glxgears and glxheads work without crashing, but since they are much simpler and don't use texturing, very likely that they are not able to crash like Google Earth does. What should I do to stop Google Earth from crashing?

Thanks in advance for any help

---

### Post by testazio on 2010-03-13
Hello gabrieldiegoteixeira,
I got the same problem.
I have 9.10 currently updated, an old radeon 9200 and googleearth just downloaded from google web site.
Did you solve the problem?
If yes, how do you achieved this?
Thank you!

Ignazio

---

### Post by ether3al on 2010-03-21
I have found setting the graphics in GE to safe mode has stabilized it.

---

