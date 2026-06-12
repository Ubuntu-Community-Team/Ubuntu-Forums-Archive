---
title: "Nvidia TNT2, Feisty, Full res and acceleration - How I did it"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by Smaug067 on 2007-05-04
This is a brief synopsis of how I got my Nvidia Riva TNT2 graphics card to work at full resolution with full acceleration: Full instructions can be found [HERE]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

First, run > sudo ddcprobe | grep monitorrange

This will return two numeric values. In my case, they were 30-83, 50-75

The first number range is my HorizSync rate, and the second is my VertRefresh rate.

Using this information, I opened my xorg.conf using > gksudo gedit /etc/X11/xorg.conf

and inserted these two lines under the section labeled "Monitor" as shown below:

> Section "Monitor"
     Identifier         "FLATRON 995F"
     Option             "DPMS"
     **HorizSync          30-83**
     **VertRefresh        50-77**
EndSection

Then saved my xorg.conf and pressed Ctrl-Alt-Backspace to restart X.

Upon restarting, all my available resolutions were selectable from the System -> Preferences -> Screen Resolution dropdown menu.

Hope this helps others with this same problem. It is soooooooooooooooo nice to run everything as it should be, thanks to some very simple tweaking. Now I'm off to fix Compiz so my screenlets don't look so clunky![-o<

---

