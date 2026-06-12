---
title: "Frustrated: how do I make Ubuntu use the right video driver?"
date: 2009-03-22
forum: Multimedia Software
---

### Post by litlfrog on 2009-03-22
OK, this is apparently the video card I have:
VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)

From what I understand, a lot of video settings are controlled by the text configuration file /etc/x11/xorg.conf. My file there is really minimal: 

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I take it that this file is currently just using some kind of system defaults. When I look in the Synaptic Package Manager, the drivers for my video card are installed on my system, but they're apparently not being used. What do I have to do to make this work?! I've tried uninstalling and reinstalling the drivers in the hopes that would help. Apologies for the cross-post--I started this topic in Absolute Beginner Talk, but I'm not getting any responses after a couple of days.

---

### Post by sisco311 on 2009-03-22
backup the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
and try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

if it doesn't work, edit xorg.conf manually:
```
gksu mousepad /etc/X11/xorg.conf
```
> Section "Device"
Identifier "Configured Video Device"
**Driver "savage"**
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

to restore the original file:
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

---

### Post by litlfrog on 2009-03-22
Thanks so much! I figured it was something like that. The automated step didn't work, but changing the configuration manually did. I haven't received any error messages and video seems to play at least a little better on this poor old system. Is there any way to confirm that the system is using the driver correctly?

---

### Post by ronocdh on 2009-03-22
I remember when **sudo dpkg-reconfigure xserver-xorg** allowed the user to manually select a video driver. How the heck is this possible anymore? the high priority flag just autoconfigures the xorg.conf, and doesn't ask the user any thing.

Without downgrading X, how can this functionality be regained?

---

