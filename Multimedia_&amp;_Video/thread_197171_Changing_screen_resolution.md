---
title: "Changing screen resolution"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by scratched on 2006-06-15
When I run certain games in wine, instead of changing the screen resolution to run at 640x480, the game is displayed using 640x480 pixels of my 1280x800 monitor in the top left corner of the screen.

I was thinking I could just change the resolution manually before I ran the game, but the only resolutions I can choose from are 1280x800 and 1280x768. How can I add resolutions to choose from?

I've tried editing /etc/X11/xorg_conf, but that doesn't allow me to change the resolutions from the GUI like I thought it would. I'm relatively new to linux so I'm not sure if I even changed the right thing. 

This the part of my xorg_conf that I changed. The part I added is in bold.

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24

[...]

	SubSection "Display"
		Depth		24
		Modes		"1280x800" **"768x480"**
	EndSubSection
EndSection
```

---

### Post by vigleik on 2006-06-15
[QUOTE=scratched]I've tried editing /etc/X11/xorg_conf, but that doesn't allow me to change the resolutions from the GUI like I thought it would. I'm relatively new to linux so I'm not sure if I even changed the right thing. 
[/QUOTE]

You don't want to edit the xorg_conf file manually. (It's the last resort.) Here's one thing you can try: Type "sudo dpkg-reconfigure xserver-xorg". It will ask you a bunch of questions, but you can answer the default for most of them. When it comes to reconfiguring your monitor you get a list of resolutions to choose from, choosing the ones you want here should give you more choices. (After you restart X, ctrl-alt-backspace.)

Vigleik

---

### Post by scratched on 2006-06-15
I just tried reconfiguring xserver-xorg, and it almost did what I wanted. I selected the resolutions to use for the xserver. When I restarted X, I only had one new resolution to chose from, 960x600. Unfortunately I wanted 768x480 (equivalent to 640x480 but my monitor is a widescreen). 960x600 was not one of the options I chose from in the xserver reconfiguration though.

I have 915resolution installed on my computer for widescreen support and I added 768x480 along with 960x600 to 855resolution. I don't really know anything about the program though so I don't know what this is changing (if anything)

It seems like 915resolution is having some effect on my choices though since it did add 960x600 when I chose 800x600 in my xserver configuration.

---

