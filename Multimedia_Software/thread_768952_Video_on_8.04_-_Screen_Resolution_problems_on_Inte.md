---
title: "Video on 8.04 - Screen Resolution problems on Intel GM965"
date: 2008-04-26
forum: Multimedia Software
---

### Post by dirkoid on 2008-04-26
For those of you having problems with Intel GM965 cards and xcreen resolution this config change worked for me.

I did a fresh installation of 8.04 on my Gateway T6815 that has an Intel gm965 VGA controller.

From lspci

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

My screen was actually 1280x800 but both KDE and GNOME both saw only 1024x768 available for menu bars etc... I could actually move app windows into the rest of the screen area but could not get the 'viewport' changed to use the full screen.

The problem apparently stems from the Video output function of this card and it doesn't matter whether the machine actually has a video output port or not.

A bugpost at:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/201257]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/201257")

has a workaround for your xorg.conf.

Since dpkg-reconfigure xserver-xorg no longer seems to work, I guess I would recommend editing the file by hand using your favorite editor.

Add the following line to the section "Section "Device""

    ```
Option "monitor-TV" "TV"
```

Then add a new section:

```
    Section "Monitor"
        Identifier "TV"
        Option "Ignore" "True"
    EndSection

```

My full xorg.conf for those interested is:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	[COLOR="Red"]Option		"monitor-TV" "TV"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

[COLOR="Red"]Section "Monitor"
	Identifier	"TV"
	Option		"Ignore" "True"
EndSection[/COLOR]

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Making the changes and logging out brought the screen resolution back in line with what it was supposed to be, 1280x800 @ 60Hz.

This is an absolutely ridiculous Out-Of-Box video problem. Personally I feel this problem is a show-stopper and the release should never have gone out with such a fatal flaw. But, that's for others to debate.

However, I would not recommend upgrading to 8.04 for at least a month. That way perhaps they can get 8.04 SP1 out. Oddly I never thought I would have to say that about a Linux release.

---

### Post by tpnerdcore on 2008-05-13
DirKoid is da man!!

Thanks man! This fixed my issue with ... well everything.
I use Arch linux and Gentoo on my GateWay One, and this was the only thing making me cry :*( ... thanks to you its good. 

Question... 
Do you have any more documentation on GM965 or the xf86-video-intel driver??

Thanks man, you Rock.
Anthony

---

### Post by fencer on 2009-02-23
uh man you are th best, I was looking for this shortcut weeks ago in my [http://www.vit.com.ve/vit/index.php?option=com_content&view=article&id=51&Itemid=60](http://www.vit.com.ve/vit/index.php?option=com_content&view=article&id=51&Itemid=60) which is a non standard laptop

---

### Post by JMiles_T on 2009-07-11
Thanks for posting this.  I wouldn't have though of it.

---

