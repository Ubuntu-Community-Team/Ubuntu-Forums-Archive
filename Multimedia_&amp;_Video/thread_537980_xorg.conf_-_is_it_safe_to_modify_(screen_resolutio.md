---
title: "xorg.conf - is it safe to modify? (screen resolution problems)"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by dorkdork777 on 2007-08-29
I have just completed a successful reinstall of Feisty, and I have switched to the restricted NVIDIA drivers to enable 3D and desktop effects - however this has limited my screen resolution to 1024x768. I know that my monitor and graphics card support and work well with 1152x864 and 1280x960 (the latter of which is my preference on Windows). Looking at the xorg.conf file, there is a section which seems relevant, and lists the resolutions available to me in Ubuntu:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

Would it be safe to change this to:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

Also, could I change it by running these commands:
```

cd /
cd /etc/X11
cp xorg.conf xorg.conf.bak
sudo gedit xorg.conf

```
Then using the gedit window that pops up to add in the resolutions? Would that be a potential fix?

I have tried running the xorg config utility through the Terminal, but I must have set some options wrongly, as when I next rebooted my mouse buttons were really screwed up. I therefore thought that it would be a better idea to just change what I wanted in the xorg.conf file, and leave it at that.

So, my two questions - 
Q1: Would I be able to replace the part of my xorg.conf at the top of my post with the one directly underneath? If so, would that fix my resolution problems?
Q2: Would the commands I mentioned above work to backup and edit my xorg.conf file?

Please understand that I am still fairly new to Ubuntu, and though I know my way around, I still need my hand held for things that get more technical.

Thank you very much in advance for the replies.

---

### Post by fogNL on 2007-08-29
You're definitly on the right track.

The first thing you do is backup your original xorg.conf file to where ever you like.

You can go ahead and edit the xorg.conf file as you stated, adding in the resolutions that you know work for your graphics card.

One additional point, when you're manually editing the xorg.conf file, you may want to get your monitor settings right.  For me, this is the difference between 1280x1024 resolution @ 60Hz and 1280x1024 resolution @ 85Hz, big difference.

If you have your monitor documentation handy (or do a quick google search for your monitor's model), have a look for the "Horizontal Sync" range and "Vertical Refresh" range.  You will want to enter that range into xorg.conf.   Here is an example for my monitor (an AOC 9GLR): (note the section)

> 
Section "Monitor"
       Identifier       "Generic Monitor"
       Option           "DPMS"
       HorizSync       30-98
       VertRefresh    50-160
EndSection


Once you have this edited (along with your resolution settings), restart your xserver with

> 
sudo /etc/init.d/gdm restart


And everything should be good.

---

### Post by dorkdork777 on 2007-08-29
Thanks for the reply!

My monitor is a MAG Innovision 700P (or UK-713; it has these two names on the back). A search on Google only turns up [this]("http://ubuntuforums.org/archive/index.php/t-234043.html"), a post on which says that these are my monitor's specs - 

Synchronization Range - Vertical 60 - 75 Hz
Synchronization Range - Horizontal 31 - 80 kHz 

So that means that I should also change this - 

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60

```

to this - 
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	31-80
	Vertrefresh	60-75

```

and then it would work?

Sorry about all the questions, but I want to get this right.

---

### Post by wolfen69 on 2007-08-29
or just do this in terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by dorkdork777 on 2007-08-29
What would the differences be between that and if I had run it without the -phigh? I have tried it without the -phigh and I managed to screw up my mouse, so I'm trying to stay away from it.

---

### Post by wolfen69 on 2007-08-29
when you get to the mouse and keyboard settings, just ignore them and click ok and move on.

---

### Post by dorkdork777 on 2007-08-29
OK, I tried that, but it didn't ask me about keyboard and mouse. It only asked me about the graphic and monitor related stuff, which seemed good enough, but when I restrted X and gave it a shot, it used the new higher resolution, but had the same problems as before, which were that I had to use the middle mouse button with the left or right buttons, otherwise the left one just took screenshots and the right zoomed in.

Also, there was no toolbar on top of any of my windows - it wasn't even invisible, as when I started Firefox, the File menu was touching the Ubuntu logo in the top-left, instead of having the toolbar between them. (By toolbar, I mean the bar with the icon and title of the app you're using, with the minimise, maximise and close buttons - I forgot the proper term for it).

Anyway, I had to restart Ubuntu in recovery mode and use the command line to restore the backup of the xorg.conf.

EDIT: A new, more serious issue has arisen. I disabled Desktop Effects, and all my workspaces but one disappeared. I made a new one, and it worked fine. But when I re-enabled Desktop Effects, and when I switched desktops, I not only did not get the cube effect, both my panels disappeared. I restrted X, tried again and the same thing happened. When my panels go, sometimes my desktop icons follow. If I re-enable 'Desktops on a cube', it doesn't work and I get the same problem.

---

### Post by dorkdork777 on 2007-09-09
I don't normally do this, but I'm going to have to bump this. This issue is getting annoying.

---

### Post by Pharisee on 2007-09-09
Editing the file as you said should do the trick. Also make sure that this section:

```
Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
EndSection
```

Looks like that, and that the driver isn't "nv" This is right above the resolutions.

As for your desktop screwing up, that's most likely something to do with the desktop effects. I suggest removing them and then edit the xorg.conf file. After that works, re install them. I had a similar issue with my GUI all messing up, and that was because of compiz-fusion.

Good luck!

---

