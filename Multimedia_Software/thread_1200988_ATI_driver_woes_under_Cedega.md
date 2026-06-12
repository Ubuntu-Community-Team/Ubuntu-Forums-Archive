---
title: "ATI driver woes under Cedega"
date: 2009-06-30
forum: Multimedia Software
---

### Post by kshandr on 2009-06-30
Hello all. Bit of a linux noob here - Windows programmer by day, fairly good at configuring stuff at the command line on servers but I've not played around with x/gnome to any great degree before.

I've got an installation of Ubuntu 9.04 here, and I think I'm working reasonably comfortably with it. I'm online, I've got multimedia, I've got all the apps I need and everything seems running correctly.

However, I'm having some trouble with my video configuration while trying to get Cedega to run stuff (my eventual aim is to run World of Warcraft, but I'm starting with something easier.) I have an ATI Radeon x1650 in the PC, and it's running two monitors (working fine!) 

I think I've got the wrong video drivers installed somewhere. When I run Cedega's diagnostics I get the following...

```
Starting test: videocard
videocard: error: unsupported videocard vendor: DRI R300 Project
videocard: Video cards from either NVIDIA or ATI are recommended.  Other video cards may not have enough hardware or driver support to run games under Cedega.
videocard: failed
Diagnostics complete
```

This doesn't stop me from being able to install and run Half-Life under Cedega, though not in OpenGL mode. I'm only able to select Software rendering. I suspect I should be able to run the game in OpenGL mode too, if everything was working correctly.

However - I *can* run glxgears, which I've seen people use to "benchmark" their OpenGL performance, so I'm thinking I have *some* degree of 3D acceleration with the drivers I've got? Here's the output from that:

```
nick@CALIGULA:~$ glxgears
10100 frames in 5.0 seconds = 2012.034 FPS
13047 frames in 5.0 seconds = 2603.870 FPS
13235 frames in 5.0 seconds = 2646.869 FPS
12933 frames in 5.0 seconds = 2586.596 FPS

```

So I've done some playing around with my video drivers. I know I've got xserver-xorg-video-ati and xserver-xorg-video-radeon packages installed, though if I try and install xorg-driver-fglrx I get a video mode than I can't display and I'm unable to see x at all. I'm not sure what driver I'm actually running, and my xorg.conf isn't very helpful... I'd have expected to see more than the following:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Can anyone give me any pointers? Would be much appreciated. Thanks.

Nick.

---

### Post by LepeKaname on 2009-07-01
Which version of Ubuntu are you running? It seems you are running the open source ATI driver. It seems it runs pretty well, but also seems that cedega does not support it. So, if you have Intrepid, try to install the ATI restricted drivers (fglrx). If you have Jaunty, you would not be able to install the fglrx drivers (so stay where you are).

---

### Post by alphacrucis2 on 2009-07-01
Can you let us know your actual card plus ubuntu version. Also when you installed the proprietary ATI Catalyst (FGRLX) driver, did you remember to run the following command from the terminal before restarting X.

```
sudo aticonfig --initial
```

---

### Post by kshandr on 2009-07-02
Thanks very much guys for the pointers. I think the problem's related to Cedega. I tried installing Half-Life under Wine instead, and was running in 1024x768 (windowed for greater control) and it fully ran Direct3D. I'm trying World of Warcraft now, and while I haven't managed to get it going successfully I'm having good results.

My current thinking therefore is that whatever driver Jaunty is installing isn't working with Cedega but Wine isn't as fussy. 

Thanks again!

---

