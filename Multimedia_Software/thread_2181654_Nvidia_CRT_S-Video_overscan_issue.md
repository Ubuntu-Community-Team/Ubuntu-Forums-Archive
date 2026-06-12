---
title: "Nvidia CRT S-Video overscan issue"
date: 2013-10-18
forum: Multimedia Software
---

### Post by QuintS on 2013-10-18
Hi ever since the new drivers from nvidia came, my PC hooked up to my CRT TV with an S-Video cable (yeah that old) has an overscan issue. I used to be able to use the well know overcan slider in the GUI of nvidia-settings and it worked. After that went away I tried lots of stuff. Alternate versions of the drivers and really getting to know the xorg.conf file. But to no avail.

My PC is directly connected to the CRT, so it is the only and primary monitor. The board is a GeForce 8500 GT. I've tried:

adding in xorg.conf:
Option "metamodes" "TV-0: 1024x768 {viewportin=1024x768, viewportout=924x718+50+25}"
logging out, restarting and using all kind of names in stead of TV-0 (like DFP-0, but this is how it's called in nvidia-settings), but no...

in terminal:
sudo nvidia-settings --assign CurrentMetaMode="TV-0: 1024x768 {ViewPortIn=1024x768, ViewPortOut=924x728+50+20 }"
screen flickers the first time when I use TV-0, but nothing changes. Nothing happens when I use for instance DFP-1.

Using the new nvidia driver settings (319) an underscan slider is now shown. I use this, and also save it to xorg.conf, but also no show. Doing the same but in the advanced settings of the nvidia-settings also does not work.

All other applications of this issue found on forums is about a monitor and a secondary CRT TV connected. Many solved, but I have to find one that meets my requirements yet. Using Ubuntu 12.04.3.

---

