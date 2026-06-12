---
title: "Dual Monitors with Intel Graphics controller"
date: 2010-04-19
forum: Multimedia Software
---

### Post by conradin on 2010-04-19
Hi all,
I have a laptop and a lcd monitor and I'm trying to set up an extended desktop. Currently, the mirror displays option works fine with the default 
display program. Ive tried ARandR and some other programs but have yet to succeed in setting up an extended desktop. When I try it with the default disply program packaged with ubuntu or ARandR, both monitors show up, but as soon as i hit apply, my computer Freezes and i'm forced to hard boot out of it.  

The extended desktop works just fine with the Intel graphics controller on my widows XP partition, I would love to be able to do the same in Ubuntu, but Im not sure how to set it up. I have created a xorg.conf file. I am using Karmic Koala, 2.6.31-21-generic kernel, the graphics card is an Intel Mobile 915GM/GMS/910GML Express Graphics Controller.

Any help i can get on getting this to work would be GREATLY appreciated.

---

### Post by thebigob on 2010-04-19
System -> Perferences -> Display 

un-check mirror screens

Ive attached a screenshot of my working Display settings

---

### Post by conradin on 2010-04-19
I wish it was that simple! When I uncheck the mirror screens option, and hit apply, the computer freezes.

---

### Post by conradin on 2010-04-20
Bump.

Plus, I have tried this article :[http://ubuntuforums.org/showthread.php?t=875045](http://ubuntuforums.org/showthread.php?t=875045)

also, I tried placing the output VGA screen below the LVDS1 and that works. 
The trouble only seems to occur when I place the output tot the right of LVDS1.

can any one help me set up dual monitors extended desktop??

---

### Post by randalsage on 2010-07-26
I have recently a new issue in regards to the Intel video drivers.

I have an extended monitor with a Benq 22 inch LCD connected to the Laptop with the integrated Intel video card. It works fine except that the video does not display in dual monitor mode, there is audio though. 

Video so far only works with either the Laptop display panel or the Monitor, not both.Video however works for dual monitor in Mirror mode.

Is there anyway to have video in with an dual monitor in extended mode?


Ubuntu 10.04 LTS -  Lucid Lynx.
Lenovo Y400
Intel Centrino Duo
Integrated Intel PRO/Wireless LAN
Intel GMA950 Integrated Graphics

---

### Post by randalsage on 2010-07-26
Based on more reading, i found out that the issue was with OpenGL. I fixed the problem by disabling accelerated video output in OpenGL video output mode in VLC media player.

Sorry for the false alarm. The following were the hints i got from another forum posting:

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

[I]Xinerama is an extension to the X Window System which allows applications and window managers to use the two, or more, physical displays as one large virtual display.” --Wikipedia. In other words, it allows X, as we'll call the X Window System, to use more than one monitor for display.

    * Pros: Since Xinerama is an extension of X, most graphics cards, including Intel Integrated Cards and Matrox Cards, work well with it.
    * Cons: There are several known problems with Xinerama. It requires that the physical screens to have the same bit depth. Also in most implementations, OpenGL (3D) direct-rendering only works on one of the screns. Windows that should show 3D graphics on other screens tend to just appear black. However, the Solaris SPARC OpenGL implementation allows direct rendering to all screens in Xinerama mode.
[/I]

> **randalsage said:**
> I have recently a new issue in regards to the Intel video drivers.

I have an extended monitor with a Benq 22 inch LCD connected to the Laptop with the integrated Intel video card. It works fine except that the video does not display in dual monitor mode, there is audio though. 

Video so far only works with either the Laptop display panel or the Monitor, not both.Video however works for dual monitor in Mirror mode.

Is there anyway to have video in with an dual monitor in extended mode?


Ubuntu 10.04 LTS -  Lucid Lynx.
Lenovo Y400
Intel Centrino Duo
Integrated Intel PRO/Wireless LAN
Intel GMA950 Integrated Graphics

---

