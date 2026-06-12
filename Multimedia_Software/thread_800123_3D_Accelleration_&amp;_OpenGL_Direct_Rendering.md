---
title: "3D Accelleration &amp; OpenGL Direct Rendering"
date: 2008-05-19
forum: Multimedia Software
---

### Post by The_Crow33 on 2008-05-19
Processor: AMD Athlon 64 3400+
Video Card: ATI Radeon 9800 SE
OS: Ubuntu 8.04 LTS

Hi, I recently installed this new version of Ubuntu, and must say it's the best version of linux I've tried yet. Anyway I also downloaded and installed the newest version of Cedega (windows emulator, or maybe windows layer, for games). Anyway I also went to ATI's site and downloaded the linux drivers for my graphics card. So the problem is, when I run the system tests from Cedega that test the audio and video performance, Both the 3D Acceleration and OpenGL Direct Rendering tests fail. After I installed the drivers for my graphics card it made the sound tests pass (for some reason). 

Anyway so the question is, what do I do to (enable/make work) 3D acceleration and OpenGL Direct Rendering? Please make your answers easy to understand, I'm not exactly new to linux, but I also get lost with a lot of the terminology. Thanks in Advanced.

---

### Post by twright on 2008-05-19
you need to use /system/administration/hardware drivers to install it

---

### Post by Gunman1982 on 2008-05-19
> **The_Crow33 said:**
>  Anyway I also went to ATI's site and downloaded the linux drivers for my graphics card.

I think it would be easier to install the ati driver through synaptic. Makes updating to new versions easier.

And don't forget to restart your xserver afterwards. (Just log off and log in again should do the trick)

---

### Post by The_Crow33 on 2008-05-20
I tried to install the drivers once before using the /system/administration/hardware drivers method you mentioned, but I have a feeling it downloaded a driver that was for windows or something... when I restarted the computer and logged in the screen turned a very light brown and nothing would load, I had a cursor, but the desktop never loaded.

As for using synaptic package manager... How would I find my driver without knowing the exact name of the package?

---

### Post by Gunman1982 on 2008-05-20
search for ati ;) the proprietary driver should support your card.

---

### Post by The_Crow33 on 2008-05-20
Ok, I opened synaptic package manager and searched until I found the fglrx driver for the ATI cards... the card I have (Radeon 9800 SE) was listed under the package description. So I installed it, logged out and back in, and once again my screen turned white with a cursor visible and no desktop loaded. The only way I have found to fix it is to reinstall ubuntu, so I'm back to square one :(. Any suggestions?

---

### Post by The_Crow33 on 2008-05-20
Alright, so I finally got the driver installed from the hardware drivers thing and with a little help from a post I got it to work... unfortunately for some reason fglrxinfo displays some wrong information...

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

and Like I said before I'm using an ATI card, and the hardware drivers say it's the ATI drivers that it's using, any ideas why this is?

---

### Post by markbuntu on 2008-05-20
The only way i got rid of mesa was to reinstall Ubuntu entirely and then get the ATI restricted driver immediately and use the ATI Catalyst Control Center to configure the driver and rebooted. It drove me crazy for 2 weeks before I bit the bullet and reinstalled but everything works great now.

No reason to use anything but synaptics to get the driver since the latest one is now in the repository and synaptics will do all the work for you. xorg-driver-fglrx is what you want and should get you the Catalyst Control Center also which you will find somewhere in your applicatons menu after you install the package. I also switched to the amd64 kernel. Things seem better so far and I have wickedly fast video even though compiz is defaulting to indirect rendering.

Your mileage may vary...

HP 1330n Media Center (modified)
ASUS A8AE-LE motherboard (OEM)
AMD Athlon64 3800+ 2.9GHZ 939 socket
3GB 3200 DDR RAM
ATI Radeon Express 200M (disabled in bios)
ATI HD3650 1GB DDR2  PCI Express
AC97 on board sound
Realtek 810L
SOYO 24 inch LCD wide screen monitor 1920x 1200
Samsung 930B 19 inch LCD 1280x1024


Ubuntu 8.04 "Hardy Heron" - Release amd64
Kernel Linux 2.6.24-16-generic
ATI Proprietary Linux Driver Version Identifier:8.47.3
Big Desktop, Compiz, Emerald

---

### Post by ZraS87 on 2008-05-20
hello, i'm new to ubuntu......I am having a small problem ....I am trying to get my 3-d acceleration to werk but i have a radeon express 200m ...and well yeah ..I have been to forums but nothing I tried from them really work......
I have installed a program called envy ....I was told that this program would get it up and running but .....well....it works but it just doesn't work very well at all ......everything tends to lag and blink...and I can't run blender at all!!!!.....s'crazy.....
I have also tried some of the stuff in the forums for terminal ....but still no success....Well if anyody can help me with this problem it would be greatly appreciated ....:confused:

---

### Post by The_Crow33 on 2008-05-21
Ok so I got the ATI Catalyst controller, and the same xorg-driver-fglrx package all installed, when I use the ATI Catalyst Control panel anything under the 3D section is greyed out, except "More Settings". The rest is unset able... anyway under info it says I have the same driver version you mentioned and it has the right card name and everything but there is still stuff there about mesa (under the OpenGL information)... is that supposed to be there?

Anyway I even rebooted and it's still running just like before. However, I didn't install the amd64 kernel... do you know the package name? I searched for it (both synaptic and google). And how did you install it? apt-get?

---

### Post by jmate24 on 2011-12-16
I am having the same problem but I installed the proprietary from the website and I also installed the latest xvba-video for it and I installed all of mesa and evas including the python-evas libraries and made sure that I had the lib?qt4? something or other that made the ATI:CCLE accessable and still no joy. I am half tempted to get the latest ppa for mesa evas and python-evas so I will try it and report back to you on this to see if it works and if it does, where to go get the ppa and how to install it w/o reinstalling the whole system.

---

