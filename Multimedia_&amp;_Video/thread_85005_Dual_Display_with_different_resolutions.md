---
title: "Dual Display with different resolutions"
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by Kjeldoran on 2005-11-01
My second day using linux and I have been trying to get dual display setup working. So far I have managed to get picture to both displays, but not with right resolution. 

From dvi I get the resolution I want, but from vga I can't get it (1280x768@60Hz). I have attached my xorg configuration file to this message. It's really annoing that I can't get 1280x768 resolution to work because the display is 16:9. 

[ATTACH]3303[/ATTACH]

Alltought 1280x768 is spesified in xorg it cannot be selected with unbutus resolution changer (might this have borked the settings somehow?). The 16:9 display is strict what refresh rates it accepts. Manual says that horizontal should be 47,40 or 47,78 kHz and vertical 60 Hz. In windows it works just fine when i select 60 Hz as refreshrate, but with ubuntu  i haven't been able to use higher resolution than 1024x768.

My graphics gard is raden 9500pro and i have installed the ATI fglrx driver 8.16.20.

---

### Post by Kjeldoran on 2005-11-02
No luck so far. Accordding to Xorg.log 16:9 display in vga port does not support edid info (alltought its lcd?!). 
[INDENT]
(II) fglrx(0): Connected Display1: CRT on primary DAC[/INDENT]
[INDENT](II) fglrx(0):  Display1: No EDID information from DDC.[/INDENT]

Later in the log is shown that resolutions are detected only up to 1024 x768:

[INDENT](II) fglrx(1): Total of 9 modes found for primary display.
(--) fglrx(1): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(1): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
(**) fglrx(1):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz
(II) fglrx(1): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 +hsync
(**) fglrx(1):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(1): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(1):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525 -hsync -vsync
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "400x300"   22.33  400 416 480 496  600 601 605 742 -hsync
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "320x240"   12.59  320 328 376 400  480 491 493 525 -hsync
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "320x200"   12.59  320 336 384 400  400 457 459 524 -hsync -vsync
(==) fglrx(1): DPI set to (75, 75)[/INDENT]

How can I make the display detected correctly? Is there a way to manually force 1280x768 resolution to the display? Does someone know?

---

### Post by Kamir on 2005-11-05
I have the same problem!
my second monitor doesnt show the 1280x1024 resolution which i specified in the xorg.conf. can't understand what the system does, as its not what is written down in the xorg.conf!
i can only choose between thos standardresolutions 800x600, 1024x768 etc. ...
i have a radeon-card and fglrx driver.
lets search some more in the forum, help would be much appreciated though!

---

### Post by Kamir on 2005-11-06
for me it finally worked out!

i put into the xorg.conf:
- horizontal and vertic refreshrate of my monitors 
- size of screen in mm
- and the option "ignoreEDID" "True" (careful here, it overrides max. settings, which the system gots from the monitor! could damage your monitor!)

somehow it needs all 3 of those in the file. for more questions message me...

---

