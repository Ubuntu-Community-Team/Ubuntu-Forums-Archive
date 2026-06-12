---
title: "Adjusting Screen Placement"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by zzneonzz on 2006-08-07
I'm new to the linux world as i used it years ago but and currently trying to use it again i'm having some problems.  I have a 26" LCD running at 1280x768 resolution on a NVIDIA 6800.  This configuration works fine in Windows XP but in Ubuntu it moves the screen off to the left.  If i had an old CRT i would just adjust it on the monitor but this LCD does not have that ability.  Is there a way to move the position of the screen?  In Windows the NVIDIA drives came with a tool to move it any direction but i'm not seeing a way to do this in linux.

Thanks

---

### Post by pdub on 2006-08-07
Does the LCD have an 'auto configure' option?

All of my LCD's have this option and it will automatically adjust the monitor. 

If the monitor works fine in XP then check the horizontal and vertical frequencies and then add them to your /etc/X11/xorg.conf file.

Make sure you backup the xorg.conf file first.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

sudo gedit /etc/X11/xorg.conf or sudo vi /etc/X11/xorg.conf if the screen is not readable in X.

There will be a section in the xorg.conf file that says:

Section "Monitor"

You want to add the appropriate setting for your monitor. An example might look like this.

Section "Monitor"
[INDENT][B]Identifier     "BenQ FP2091" # your monitor name here
Option         "DPMS"
HorizSync    30-71
VertRefresh  50-160[/B][/INDENT]
EndSection

---

