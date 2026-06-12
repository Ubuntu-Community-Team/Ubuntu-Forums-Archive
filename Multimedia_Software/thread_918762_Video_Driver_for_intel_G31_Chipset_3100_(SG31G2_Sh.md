---
title: "Video Driver for intel G31 Chipset 3100 (SG31G2 Shuttle)"
date: 2008-09-13
forum: Multimedia Software
---

### Post by renesisspeed on 2008-09-13
Hi all! I'm hoping someone out there can help me with this....

I am running UbuntuStudio Hardy on a Shuttle SG31G2 barebone & can not get the intel drivers to work. I had been referencing this post ([http://ubuntuforums.org/showthread.php?t=808135&highlight=3100](http://ubuntuforums.org/showthread.php?t=808135&highlight=3100)) which indicated I should use the following command (gksudo displayconfig-gtk) To select the following driver (Intel Experimental Modesetting)

This all seemed to work fine, but any configuration changes I made were not saved, I am still stuck using the vesa drivers. Any ideas? Any help is much appreciated :smile:

The following is from my xrorg.conf:
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

I suppose I would need to manually edit the xorg.conf file, but I don't know what I need to add

TIA
Renesisspeed

---

### Post by renesisspeed on 2008-09-14
--BUMP--

So.. ehh... no ideas??

---

### Post by renesisspeed on 2008-09-17
I hate to bump this again, but really, no one knows what I need to do here?.... Please? Vesa sux

---

### Post by renesisspeed on 2008-10-15
So... for the past month I have been periodicaly scowering the web looking for drivers and am still stuck.... ](*,)

Does Anybody know where I need to look?

Ive looked here: [http://intellinuxgraphics.org/user.html](http://intellinuxgraphics.org/user.html)
but dont know if any of these will work.

Seriously, should I just consider buying an nvidia card and give up on getting the integrated intel pos to work?

---

### Post by jim-nf on 2008-10-31
Hi

I have an SG31G2 and am looking at video drivers - did you ever get the Intel G31/G33 working?

I cannot seem to select Intel Experimental drivers either.

I have seen some posts about using G31 drivers in prev installs to 8.04/.10 but they seem to be having problems.

Did you get another card in the end - I am thinking about an 8800GT....

TIA

---

### Post by renesisspeed on 2008-11-16
Never did get the experimental driver working, also haven't gotten around to installing another card yet, 8800 sounds good to me though

---

### Post by Arup on 2008-11-16
I have the Intel DG31PR motherboard and am using the G31 video out, by default I have my videos working and I can do glxgears as well. I thought the support was already built into the kernel.

---

### Post by renesisspeed on 2008-11-18
I don't think that provides the whole picture, if the intel driver is not functioning, good luck even playing tux racer on it. lol. thanks though

---

### Post by Arup on 2008-11-24
The grep command shows Intel driver is enabled and so is 3D, I would admit though that surprisingly the Ubuntu team has not done a good job with the xorg-intel as Google Earth doesn't work, also 3D apps in general are slow including glxgears which benchmarks with lower numbers compared to slower graphic chipesets. Ironically this is a common laptop graphic chipset and Ubuntu should spend a little time over this to make Ubuntu popular among laptop crowd.

---

