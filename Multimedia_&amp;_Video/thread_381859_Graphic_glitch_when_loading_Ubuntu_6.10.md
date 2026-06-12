---
title: "Graphic glitch when loading Ubuntu 6.10"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by PsionicSwallow on 2007-03-11
This is my first time installing any Linux distribution and I've come to a small snag.

I burned the LiveCD for Ubuntu and when I initially booted from the disc the image was scrambled (after getting past the menu). I found I could get it to load without the scramble if I set the resolution to 1024x768x32 (albiet without a cursor). I was able to install the OS, but now when I load Ubuntu the screen is just scrambled.

Is there a way I can set a resolution for Ubuntu before it loads? Or is there some other solution to this problem?

Also, the greatest resolution my monitor supports is 1024x768.

---

### Post by matburton on 2007-03-11
When ubuntu loads and you're screen is scrambled hit CTRL-ALT-F1

From here you can log into the terminal and edit the resolution
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```

And in the section with the resolution leave the one that you want e.g.
> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
EndSection


Hit CTRL-o to save and CTRL-x to quit I think.

Hit CRTL-ALT-F7 to get back to your scramble and then CRTL-ALT-backspace to restart gdm.

With any luck it should grab the correct resolution and be crystal clear ;)

---

### Post by PsionicSwallow on 2007-03-11
I will test this as soon as I get back to my computer at home. I got the impression I had to edit the xorg.conf file somehow and now I know how.

Thanks much!

---

### Post by PsionicSwallow on 2007-03-12
> **matburton said:**
> [Help]

Okay, I tried this once the scramble came up. Something did open when I hit Ctrl+Alt+F1, but it was still scrambled so I couldn't tell what I was doing. I tried typing in the code anyway, but it didn't seem to do anything.

I also tried loading Ubuntu with a different monitor (one that supports many resolutions), and I still got the scrambled image.

To anybody: Any other suggestions?

---

