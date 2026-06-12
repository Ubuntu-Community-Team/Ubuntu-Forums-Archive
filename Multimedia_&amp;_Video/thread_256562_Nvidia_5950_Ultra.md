---
title: "Nvidia 5950 Ultra"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by ART_Adventures on 2006-09-13
Hello People,

If I try to run a live Ubuntu CD on a a system I have (p4 2GB RAM Nvidia 5950 Ultra) I find that ubuntu cannot start properly. I see all kinds of multicoloured rubbish on the screen as it attempts to start and it seems to remain there.

Can anybody help.

Thanks.

---

### Post by tseliot on 2006-09-13
Try booting in Safe Mode

---

### Post by ART_Adventures on 2006-09-13
Yes, safe mode works; though it appears to boot in a lower resolution. Can this be changed in Live safe mode? Also, if I were to install Ubuntu on this machine, does it mean I would continually need to boot into safe mode?

Thanks.

---

### Post by tseliot on 2006-09-13
> **ART_Adventures said:**
> Yes, safe mode works; though it appears to boot in a lower resolution. Can this be changed in Live safe mode?
yes, by modifying your xorg.conf, setting the resolution and Pressing CTRL+ALT+Backspace

But I suggest you to install Ubuntu instead.

> **ART_Adventures said:**
> Also, if I were to install Ubuntu on this machine, does it mean I would continually need to boot into safe mode?

Thanks.

No, you should follow these instructions:
1) Install Ubuntu

2) After the installation the xserver might crash

3) If it does, you will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine



And might also want to install the Nvidia proprietary driver (so as to use your card at its full):
follow method 1 of this guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by ART_Adventures on 2006-09-13
Thanks for the help. I'm quite new to GNU/Linux and I've not really edited a xorg.conf before. However, I managed to find a file with this name after searching some forums in profile/etc/x11. I can see the different settings, although I'm not sure where I'm supposed to actually define the resolution I am to use, say, 1024x768. Can anybody help? Which part ofthis file am I supposed to change? The relevant part (I think) of the file follows:


Section "Device"
	Identifier	"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tseliot on 2006-09-13
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by ART_Adventures on 2006-09-13
Thank you for your help. The problem is now resolved :)

---

