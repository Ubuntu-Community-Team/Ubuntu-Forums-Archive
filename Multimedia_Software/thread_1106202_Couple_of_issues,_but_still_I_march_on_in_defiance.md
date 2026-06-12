---
title: "Couple of issues, but still I march on in defiance of windows, help would be nice."
date: 2009-03-25
forum: Multimedia Software
---

### Post by yergeht on 2009-03-25
Ok hi guys, I'm pretty new to ubuntu, but have used linux in the past... I installed about a year ago but kept using my 'puter in dual boot XP :(
Until about a month ago... I just can't take windows anymore, I had a taste and now I'm back... I had to get a new HD so I could dual boot, and still have space left for my /swap, and /tmp


Now I'm back, but still having a couple of unsettling issues... mainly my video card, or at the least my xorg-config.

My problem(s) are these: 

Firstly, I can't seem to overwrite my xorg.config should I chmod it and if so where is it located in file structure?

Also, I have been reading this site almost religiously.... I'm DONE with windows, so I read on and try to suppress all those years learning my windows *sighs...(and I never even touched vista). Anyways when my log-in screen comes up, my screen resolution is a normal, 1600 * 1200, but after I log in, the screen goes black, redraws the screen in a less respectable 1280 *1024, and my cursor becomes my aero glass cursor, so something is being loaded after my log-in, is it connected to the xorg-config file? Whats strange is that sometimes I can change the screen resolution through the nvidia x-server console but then other times I can't, a reboot usually changes that.  Also I have two separate appearance settings, one through the emerald theme manager theme, and then the other trough the system -> preferences-> Appearance

How can I make one dominant, mainly my theme,

I have 4 separate desktop images,
[IMG]http://c2.ac-images.myspacecdn.com/images02/77/l_cfec025c7c5047e28dfa73cd76402921.jpg[/IMG] 
which means I had to stop letting  nautilus draw my desktop... I don't know if it's an issue or not.

 I am running gnome  version 2.24 and intrepid 8.10. I have an Nvidia 8500 GT(nvidia-glx-180), AMD 64x2 3Ghz, 1tb 7200 RPM sata drive, DVD-RW(which is another issue) Only works in read mode right now, is that because it's sata? maybe I need some driver or sumin, idk I'll start down that right after this.

If I have to I'd even resort to changing my video card because I've had some hanging issues with this card, either card or card and mobo, Even in windows... But I'm kinda broke, so that is my last option

---

### Post by ABCC on 2009-04-01
Such a long post deserves atleast a short answer...

The reason that you have 2 theme choices is simply because you have 2 theme managers. Emerald is a "window decorator". I've not played with it too much lately, when it was installed I tended to use it by starting it manually. The command I used was 'emerald --replace', you could probably get away with adding that to your session (system > prefs > session) as a startup item.

The X resizing thing I'm not sure about, you could try modifying your /etc/X11/xorg.conf as follows:
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1900 1200
	EndSubSection
EndSection

the trick here is to add the 'Subsection display', as for accessing the file you navigate to the folder with Nautilus, right click then Open with > ... other application > custom command > 'gksudo gedit'. Just enter your password and you can edit away.

hth

ABCC

---

### Post by aeiah on 2009-04-01
perhaps you can do your resolution thing through nvidia-settings. the reason it doesn't save it may very well be because you need to run it as root.

```

sudo nvidia-settings

```

yea. its not very clear that you have to and it never tells you when you're launching it from the menu.

oh, and make sure you back up your xorg.conf before using nvidia-settings or manually editing it.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

so if things all go wrong you can, from the cli, do:
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and it'll copy the backup over the one you just messed up

---

