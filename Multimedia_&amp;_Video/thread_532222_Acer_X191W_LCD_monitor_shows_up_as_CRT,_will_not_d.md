---
title: "Acer X191W LCD monitor shows up as CRT, will not display 960x600"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by CatastrophicToad on 2007-08-22
I have an Acer X191W LCD monitor.  The monitor works with Ubuntu fine, and I got it to work at full 1440x900 resolution by editing xorg.conf.  The problem is that when I play Guild Wars, I want to play at the same resolution that I use on Windows, on the same computer, 960x600.  When Guild Wars tries to use 960x600, and when I change the screen resolution to 960x600, the display says "Input Not Supported".

When I run XServer-Xorg, part of the logfile is:

"(II) NVIDIA(0): NVIDIA GPU GeForce 6100 nForce 405 at PCI:0:13:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.61.32.25.04
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6100 nForce 405 at
(--) NVIDIA(0):     PCI:0:13:0:
(--) NVIDIA(0):     Acer X191W (CRT-0)
(--) NVIDIA(0): Acer X191W (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900"

It looks to me like it is detecting the monitor as a CRT.  I think the problem might be that it is trying to use a sync/refresh rate that the monitor won't display.  On Windows with Guild Wars at 960x600, the monitor reports it is at "H:47KHz V:75Hz".  When Ubuntu tries to do 960x600, the monitor won't tell me what it is, but Ubuntu says it's either "61Hz" with Screen Resolution Preferences or "60Hz(doublescan)" (does "doublescan" mean "interlaced"?  I noticed the xorg logfile says "interlaced video modes supported") with NVIDIA X Server Settings.

How can I make Ubuntu see the display as a LCD instead of CRT, or how can I change the horizontal sync and vertical refresh rate specifically at 960x600, or how do I disable interlacing?  if that's the problem.  Thanks.

---

### Post by livestockPimp on 2007-08-22
xorg is crap at detecting some screens, especially if you are going through a KVM, ect. there is a command you can use to force xorg to use the exact settings you want, you need to use the "modeline" command in the xorg.conf.

There is some info in this thread about it, not alot though.

[http://ubuntuforums.org/showthread.php?t=372209&page=2](http://ubuntuforums.org/showthread.php?t=372209&page=2)

---

### Post by CatastrophicToad on 2007-08-22
Thanks livestockPimp, I used [http://zaph.com/Modeline/](http://zaph.com/Modeline/) to generate a modline.  The screen wasn't exactly centered on the monitor, but at least it didn't display "Input Not Supported".  I'll try tweaking the modline to get the rates right, and it should work.

---

