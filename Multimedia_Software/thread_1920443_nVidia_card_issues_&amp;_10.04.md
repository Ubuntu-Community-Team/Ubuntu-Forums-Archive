---
title: "nVidia card issues &amp; 10.04"
date: 2012-02-04
forum: Multimedia Software
---

### Post by SimonOnSite on 2012-02-04
Good evening,

I am running Ubuntu 10.04 on an AMD64 Athlon, with a nVidia Geforce FX 5900XT. I am using the old 96 driver, as the newer ones give display issues if I switch on screen effects (no big issue, but using them does not fix my issue, so I have stuck with the older driver. Scrren effects are now off, so if I need to install a newer driver for any reason, it wont be a problem).
After instillation, I could only use very low resolutions, but this was fixed from help in the forum (Changing xorg.conf to HorizSync       30.0 - 83.0 and VertRefresh 55.0 - 75.0).
Now I can choose any res I need, from 320x240 to 1920x1200 - my preferred choice is 1152x864.
Every time I reboot, it resets to a lower resolution, and the desktop is bigger than my actual monitor, so I cannot see everything. It is easily fixed by going into the nVidia X server and choosing my resolution again, but gets annoying. I have tried reading loads of forums, but I have not found a fix. (Tried running x server from the terminal as SU and saving xorg, I manually edited x server, but then couldnt boot - I had to use the live cd and remove nVidia divers with purge).
If it helps, the boot screen is a low resolution. I did finf a post to follow to write a script to change it (#!/bin/sh   xrandr --output default --primary --mode 1152x864) and save as lightdmxrandr.sh) but I guess this was for an older version of Ubuntu as the process failed at some point (cannot remember where but something did not exist - I can try re-create if needed).
I can run this script manually when I log in as a temporary fix, but its still annoying. I also read some people fixed it by changing the display res somewhere else (not nVidia's x server) but it was only explained as 'change the monitor setting' which I didn't understand.
Sorry if I have missed anything out - If anyone can help, please do - I am a newb so will need pretty simple explanation im afraid, but I am dedicated - Its the only OP I now have installed and following other posts has just given me problems. If I am better just running the script, please say, but I am getting on so well with Ubuntu, id love to have it running 'just right'.

Thank you.

---

