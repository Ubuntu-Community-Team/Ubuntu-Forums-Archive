---
title: "Install video card"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by interse on 2007-10-02
I have a 17" LCD monitor connected to a Asus Motherboard A7S8X-MX
I am using Feisty 7.04.  The highest resolution that Ubuntu presents to me is 1024 x 768, which is just fine.

Considering a larger LCD monitor, I would need resolutions of 1280 x 1024 and have a Graphic Rage 128 Pro which I have tested with the
LIVE Feisty 7.04 on this motherboard.  

However, when I plug in the card, my installed Ubuntu does not recognize it and xorg. crashes.

How do I install the card so that it is recognized?  I know that I can reinstall 7.04 and it will be recognized, but I would like to avoid this option.

---

### Post by valkarin on 2007-10-02
Do you have the correct drivers installed?

---

### Post by interse on 2007-10-02
The correct drivers were to be detected when I ran the LiVE CD with the card installed.  I had 9 resolutions that I could use, the highest being 1280 x 1024.  This test led me to believe that the drivers were available on the LIVE CD and were selected automatically.   If I leave the card in and boot the system to the installed 7.04, the drivers are not appropriate.

---

### Post by valkarin on 2007-10-02
Run this and post the output:

```
gedit /etc/X11/xorg.conf
```

---

### Post by haden9 on 2007-10-02
Hello there,

1. After replacing the old card with the ATI one, restart Ubuntu in safe mode.

2. Type in the command:

sudo apt-get update

3. Then followed by:

sudo apt-get dist-upgrade

4. Next:

sudo apt-get install xorg-driver-fglrx

5. Then:

sudo depmod -a

6. And:

sudo aticonfig --initial

7. Finally:

sudo aticonfig --overlay-type=Xv

All that is left to do is just reboot, or you can type:

sudo shutdown -r now


Let me know how it goes! Good luck!:popcorn:

---

### Post by interse on 2007-10-02
This is the result of gedit:   

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) SiS Default Card"
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

---

### Post by haden9 on 2007-10-02
The current drivers that your Ubuntu install has are the ones for your integrated graphics card, so a good deal would be to try to install the fglrx drivers (which is usually done in safe mode) which are for ati and try it out. I noticed as well that you use version 6.06 s perhaps we can try something like this in safe mode:

sudo dpkg --configure xserver-xorg

then restart!

Hope this helps!

---

### Post by interse on 2007-10-02
Actually I am using 7.04.

---

### Post by interse on 2007-10-02
Hi Haden9

Curious.  Since I am using  7.04, are steps 2) and 3) in your instructions needed?  Seems to me that I would only need to update the driver.    My system is up-to-date.

---

### Post by jacob01 on 2007-10-02
when you put the new card in did you dissable the integrated graphic in the bios? because you need to do that when adding a new card

---

### Post by haden9 on 2007-10-02
Hello again Interse!

Steps 2 and 3 are a must for "precaution", and well if your system is up to date then it wont take long :).

Anyhow, in this case then due to a bug, I would suggest going with the first method mentioned above (steps 1 to 7), also jacob made a really good point, since i assume the system is running with the integrated graphics card, before you install the ati card you need to disable through the BIOS the integrated card. Once thats done, pop in the ATI card and please perform the steps I detailed earlier. Let me know how it goes please!

---

### Post by interse on 2007-10-02
Thank you to everyone for the prompt responses.  Over the next few days, I will install the new video card.

---

