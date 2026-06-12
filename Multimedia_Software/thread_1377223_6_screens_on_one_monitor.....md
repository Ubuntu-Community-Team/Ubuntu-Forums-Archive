---
title: "6 screens on one monitor...."
date: 2010-01-10
forum: Multimedia Software
---

### Post by Hobix on 2010-01-10
First off im pretty new to ubuntu, so bare with my slowness..

I have installed a dual boot of windows and ubuntu 9.10 onto my Asus a50v laptop. I have gotten everything to work.. sorta. I have an onboard GeForce 9800m GS 512mb gfx card. Using EnvyNG and downloaded the 185 driver. It installed just fine no errors etc. I restart my system, but when I Get back into ubuntu im faced with a wierd problem. 

I have 6 "desktops" as it were on one screen they are all running at 640x480. I can get into the Nvidia ctl panel just fine, but in there it says that 640x480 is the max resolution and that I have multiple displays.  

I have had ubuntu installed onto this computer before and had the drivers work just perfectly. Any clue how to fix it?

---

### Post by lukeiamyourfather on 2010-01-10
Did you install the driver from the "Hardware Drivers" or repositories, or was it downloaded directly from nVidia? Can you change the resolution using the nVidia utility?

---

### Post by Hobix on 2010-01-10
Well first I used the repos. from EnvyNG, tried every combo, then eventually downloaded the newist stale drivers from nvidia and installed them manually, getting the same results.

It seems as if my monitor is just not detected. When I view my xorg.config it is empty.

---

### Post by frogotronic on 2010-01-10
> **Hobix said:**
> Well first I used the repos. from EnvyNG, tried every combo, then eventually downloaded the newist stale drivers from nvidia and installed them manually, getting the same results.

It seems as if my monitor is just not detected. When I view my xorg.config it is empty.

An empty xorg.conf is normal on Karmic; your nVIDIA driver should be able to read your monitor.  If you are having problems you could try an open up the displays dialogue **System>Preferences>Display** and tell us what are your options in that dialogue.

---

### Post by Hobix on 2010-01-10
It says unknown as far as the monitor is concerned, which is so wierd because when the drivers are not installed it detects and works perfectly (besides teh fact that I have 0 gfx acceleration and cant use compbiz etc. etc.)

the only options are change from 640x480 to 320x240 RR is 50

If anyone has any clue..

---

### Post by frogotronic on 2010-01-10
okay, well you can force the card to read the monitor resolution correctly by *creating* an xorg.conf file.

Here how

```
$sudo gedit /etc/X11/xorg.conf
```

then paste this into it:


```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		**Virtual	2560 1024**
	EndSubSection
EndSection

Section "Module"
	Load "glx"
	Load "dbe"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

BUT in your case substitute the correct monitor size for the **other size**.  In other words, if your monitor resolution is 1280x1024 then your xorg.conf file should be:


```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		**Virtual	1280 1024**
	EndSubSection
EndSection

Section "Module"
	Load "glx"
	Load "dbe"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
        [COLOR="Red"]Driver          "nvidia[/COLOR]"
EndSection
```

Save the file (xorg.conf) & reboot.  

[COLOR="Red"]You *might* need to specify the nVIDIA driver, but I'd try it without the red text in the xorg.conf file first and then if that doesn't work, try it with.[/COLOR]

Now check what the nVIDIA Control Panel Settings options are & post back if this works.

- CH

---

### Post by realzippy on 2010-01-10
> **cement_head said:**
> okay, well you can force the card to read the monitor resolution correctly by *creating* an xorg.conf file.

Here how

```
$sudo gedit /etc/X11/xorg.conf
```

then paste this into it:


```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		**Virtual	2560 1024**
	EndSubSection
EndSection

Section "Module"
	Load "glx"
	Load "dbe"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

BUT in your case substitute the correct monitor size for the **other size**.  In other words, if your monitor resolution is 1280x1024 then your xorg.conf file should be:


```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		**Virtual	1280 1024**
	EndSubSection
EndSection

Section "Module"
	Load "glx"
	Load "dbe"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
        [COLOR="Red"]Driver          "nvidia[/COLOR]"
EndSection
```

Save the file (xorg.conf) & reboot.  

[COLOR="Red"]You *might* need to specify the nVIDIA driver, but I'd try it without the red text in the xorg.conf file first and then if that doesn't work, try it with.[/COLOR]

Now check what the nVIDIA Control Panel Settings options are & post back if this works.

- CH

Hm.
Sure that the virtual size has anything to do with his problem??
Isn't the "virtual size" option for 2 Monitors using xrandr??!

If dropped to shell after editing your xorg.conf as suggested(would not do so...)

sudo rm /etc/X11/xorg.conf

BTW
this problem was solved days ago in the forum google for
"ubuntuforums 6 screen"....

edit:
[http://ubuntuforums.org/showthread.php?t=1230528](http://ubuntuforums.org/showthread.php?t=1230528)

---

### Post by frogotronic on 2010-01-10
cool, thanks for the link to the solution.

---

### Post by Hobix on 2010-01-11
Sigh, this fix didnt help. I think im going to try using the 64bit ubuntu release to see if it helps any.

---

### Post by realzippy on 2010-01-13
Option "ExactModeTimingsDVI" "True"



...from:

[http://www.nvnews.net/vbulletin/showthread.php?t=134321#post2135663](http://www.nvnews.net/vbulletin/showthread.php?t=134321#post2135663)

---

