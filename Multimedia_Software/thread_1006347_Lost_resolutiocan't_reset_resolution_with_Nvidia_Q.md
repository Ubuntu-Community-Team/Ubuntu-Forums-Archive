---
title: "Lost resolutio/can't reset resolution with Nvidia Quadro 2 card"
date: 2008-12-09
forum: Multimedia Software
---

### Post by don_m on 2008-12-09
I can't go above 640X480 with this setup. It was working great for the last 3 weeks. I did install the updates yesterday, but I don't recall one being a video card update. I had rebooted the computer to test for another problem and learned that I cannot change the screen resolution at all. 

I have installed the NVIDIA X Server Settings package, and I can't do anything to make it go to my higher res settings. I was able to copy the old xorg.conf settings and obtain the default 800X600, but could go no higher since even though higher resolutions were displayed.

Here is the xorg.conf file as it is now:
[PHP]
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
[/PHP]

I'm using a Dell Ultrascan P991 monitor (again this was working great up until yesterday). 

I've looked at other threads and tried some of the solutions. The lost monitor resolution issue seems to be a common problem.

---

### Post by don_m on 2008-12-09
Okay, I was able to remove the Nvidia graphics driver. I went ahead and rebooted and returned to default settings.

I went ahead and changed the resolution and had a good selection. I did find that you cannot resize the "Resolution" dialog box, so it is necessary to hide the bottom panel so you can press the Apply button after selecting a screen resolution setting.

So, at this point, I have the default settings I started out with, but still do not have the Nvidia driver installed. I'm going to try this later today.

I did install a couple of the racing games that do need the 3D functionality.

---

### Post by piratebill on 2008-12-09
Did you try to change the res from the nvidia app?  I find that when I use nvidia drivers, the default ubuntu screen resolution app is next to useless.

---

### Post by don_m on 2008-12-09
> **piratebill said:**
> Did you try to change the res from the nvidia app?  I find that when I use nvidia drivers, the default ubuntu screen resolution app is next to useless.

Yes. One of the things I did after persuing the forums was to use apt-get to install the application. It refused to go beyond the 640X480. 

I did not get a chance to try reinstalling the nvidia drivers again. But I'm still mystified how this occurred since I made no changes to the resolution settings or anything doing with video. 

I did install the guest additions for virtual box, which would have been the only thing having to do with video.

---

### Post by don_m on 2008-12-10
This morning, I went under System->Hardware and Enabled the Nvidia driver. 

It installed and I restarted and it kept my resolution settings that were present when running the default driver.

I now have the windowing effects back. I was able to go the nvidia package and have a selection of other monitor resolution settings.

We'll see how long this last. 

I guess this is solved - for now.):P

---

