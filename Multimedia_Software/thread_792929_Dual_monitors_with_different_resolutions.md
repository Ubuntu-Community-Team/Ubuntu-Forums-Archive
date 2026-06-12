---
title: "Dual monitors with different resolutions"
date: 2008-05-13
forum: Multimedia Software
---

### Post by coolclayton on 2008-05-13
Hi, i'm trying to set up dual monitors on my Ubuntu setup. I want to be able to drag stuff from one over to the other, as I can do on my Windows setup. I'm able to get Big Desktop working through the ATI Catalyst config utility, but the resolution is forced to 2048x768 or something, splitting the two monitors between the two resolutions, meaning stuff looks fine on my CRT, but everything is stretched on my widescreen. Is there a way to have 2 different resolutions?

I tried removing the fglrx drivers and reinstalling, using the [Dual Monitor Support With Binary, ATI-Only Big-Desktop]("http://ubuntuforums.org/showthread.php?t=301941&highlight=big+desktop") tutorial as a tutorial to install with Big-Desktop support, but when I try to input my two resolutions (I want to use 1280x1024 and 1680x1050) it won't add it to the xorg.conf file.  

I'm a linux rookie, but I'm picking it up pretty quick... but this is leaving me pretty stumped. Hopefully someone can help me with this, because 2 functional monitors is one of the reasons i like using Windows right now... and if I can, I'd like to make the full switch to Ubuntu

I have an ATI Radeon 9600 with two outputs, which are connected to a 17" CRT and a 22" widescreen. Any help would be appreciated. If you need any more info, let me know

---

### Post by wkulecz on 2008-05-13
Are you using DVI or analog as the connection to the monitors?  I ask as I'm finding it impossible to get the wide screen native resolution (1920x1200) using DVI but it works great using analog.  Best I can get with DVI is 1600x1200.

--wally.

---

### Post by coolclayton on 2008-05-13
I'm using the DVI connection for the LCD and the VGA for the CRT monitor. My Radeon card comes with DVI, VGA, and S-Video outputs

---

### Post by coolclayton on 2008-05-14
Has anyone had any luck getting dual monitors with different resolutions working properly?

---

### Post by wkulecz on 2008-05-14
I'd suggest trying two analog VGA cables if you can.  You may be having a version of the bug I mentioned earlier that prevents your DVI monitor from getting the widescreen resolutions, hence its stuck at 1280x1024 instead of the 1680x1050 you want.

DVI to VGA adaptors are pretty cheap and one may have come with your video card.

I know trying to setup a pair of 1920x1200 LCD panels, one analog and the other DVI limited me to 1600x1200 on both panels with an Nvidia 5500 card.

I filed a bug report on launchpad because if I only use the analog cable I can get 1920x1200, but nothing better than 1600x1200 using a DVI cable

--wally.

---

### Post by amites on 2009-08-17
I've read elsewhere that the DVI-I port itself is limited to 1600x1200 res

there are a vew more pins on a VGA port, 

doesn't offer much support but does explain the upper screen limit, different resolutions will be nice once ready

---

### Post by mahavishnu on 2012-01-28
bump

---

### Post by overdrank on 2012-01-29
Hi and please start a new thread with your issue. Back to sleep thread. Thread closed.

---

