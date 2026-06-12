---
title: "Ubuntu Studio, Intel 950 graphics, correct resolutions"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by davideckels on 2007-05-18
I just got my new Gateway GM5442 to run Ubuntu Studio 7.04 with the low latency kernel and operate the Intel 950 graphics adaptor at a native resolution of 1680x1050.

Here is how:
Applications >> Accessories >> Terminal
In the terminal:

> sudo apt-get install xserver-xorg-video-intel

Then edit /etc/X11/xorg.conf:

> sudo cp /etc/X11/xorg.conf xorg.golden
> sudo vi /etc/X11/xorg.conf

in the Section ¨Device¨ Identifier ¨Generic Video Card¨ change ¨vesa¨ to ¨intel¨ and add a line VideoRam 128000 so the section looks like:

[INDENT]Section "Device"[/INDENT]
[INDENT][INDENT]Identifier "Generic Video Card"[/INDENT][/INDENT]
[INDENT][INDENT]Driver "intel"[/INDENT][/INDENT]
[INDENT][INDENT]BusID "PCI:0:2:0"[/INDENT][/INDENT]
[INDENT][INDENT]VideoRam 128000[/INDENT][/INDENT]
[INDENT]EndSection[/INDENT]

Then save and exit.
Reboot.
After logging back in, your System >> Preferences >> Screen Resolution chooser should show all the valid resolutions for your monitor.

---

### Post by vikramsharma on 2007-05-18
Have you tried installing the 915 resolution through Synaptic Package Manager.  I think it should solve your problem.

---

### Post by capdog on 2007-05-21
Hi Davideckels

I'm having problems getting this resolution, tell me, what is the reason for specifying the VideoRam option?

I have never seen this before and maybe it's the clue I'm missing - mine crashes for some reason...

Thanks
capdog

---

