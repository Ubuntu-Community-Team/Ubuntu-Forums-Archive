---
title: "8800GT and Hardy"
date: 2008-06-21
forum: Multimedia Software
---

### Post by MitchellSchwitzer on 2008-06-21
Well my problem seems like it cannot be fixed; however, I have heard of people using their 8800GTs with Ubuntu so why can I not get mine to work?

I have the following hardware config:

Hardy Heron 8.04 i386 (32-bit)
AMD Athlon 5200+ @ 2.6GHz
XFX NVidia 8800GT Alpha Dog Edition <--- Is this particular card just picky for some reason?
Samsung 226BW 22" Widescreen Monitor

I have tried installing the 169.12 drivers on 32 and 64 bit Hardy manually, with the restricted drivers menu, and with Envy. No luck.
I have tried installing the 174.14.05 drivers on 32 and 64 bit Hardy both manually and with Envy. No luck.
I hate tried installing the 174.14.09 drivers on 32 and 64 bit Hardy manually. No luck.

My problem is that when booting Ubuntu after installing the drivers, I can see the splash screen fine. The Ubuntu logo pops up and the loading bar works fine. However, my problem arises when the X server is supposed to load. My monitor does not receive a signal from the video card. My monitor has two ports it can receive signals from, Analog and Digital (analog being VGA and Digital being DVI). The monitor will switch back and forth between these two modes trying to obtain a video signal. If it cannot after five or six times, the monitor goes into a power saving standby mode. My monitor is currently hooked into my video card with a DVI cable, so it should be finding the signal on the digital mode. If I hook it up with a VGA cable (and hook the cable into my video card with a VGA to DVI connector) it should be finding a signal on the analog mode. Neither happens.

I have a feeling my XOrg server isn't working properly because even though my monitor will not pick up a video signal, one should think everything else should work. This is not the case; however, as I do not hear the Ubuntu starting up sound (the drum beat).

I simply do not understand what is wrong! I have done each driver installation with a fresh install of Ubuntu (after I have let it update) and it does not work! What is the problem? It does not matter how I install the drivers, I simply get the same error. Help!

---

### Post by Fingel on 2008-06-21
Sounds like a not good situation. Maybe you should try the generic "nv" driver instead of the full nvidia drivers. You wont have 3d acceleration, but at least maybe it will work and you can try to figure it out from there.

---

### Post by Pjotr123 on 2008-06-21
1. Connect the monitor *only* to the analog port (safest option). 

2. Then install the restricted driver with Envy. 

3. Then do this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

Does this help?

---

### Post by MitchellSchwitzer on 2008-06-21
My video card doesn't have an analog port. The video card only has DVI for the out. Should I still use the analog part of my monitor (via a DVI to VGA converter)? As well, I cannot do step two because I cannot actually get a picture on my screen (unless I use the VESA driver like I am now).

---

### Post by Pjotr123 on 2008-06-21
> **MitchellSchwitzer said:**
> My video card doesn't have an analog port. The video card only has DVI for the out. Should I still use the analog part of my monitor (via a DVI to VGA converter)? As well, I cannot do step two because I cannot actually get a picture on my screen (unless I use the VESA driver like I am now).

No, better to use DVI then. Try this for a change:
[http://ubuntutip.googlepages.com/installationofubuntu](http://ubuntutip.googlepages.com/installationofubuntu)

---

### Post by MitchellSchwitzer on 2008-06-21
> **Pjotr123 said:**
> No, better to use DVI then. Try this for a change:
[http://ubuntutip.googlepages.com/installationofubuntu](http://ubuntutip.googlepages.com/installationofubuntu)

I am dual booting Windows and Linux. I'd like to also use my video card in Linux, but apparently this is impossible.

---

### Post by MitchellSchwitzer on 2008-06-21
Well if no one else has any advice I guess I'll be on my way. Thanks anyways to everyone who tried to help.

---

### Post by MitchellSchwitzer on 2008-06-21
Bump for great victory and potential success. I'm serious. I'm at my wits end. :(

---

### Post by romefolks on 2008-06-22
i have ubuntu 8.04 64bit and a PNY 8800GT 512, i am attempting a fresh install, but i wanted to know will this graphics card work. Does anyone have this working?

---

