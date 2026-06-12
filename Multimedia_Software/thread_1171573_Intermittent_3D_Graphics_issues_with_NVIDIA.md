---
title: "Intermittent 3D Graphics issues with NVIDIA"
date: 2009-05-27
forum: Multimedia Software
---

### Post by Turambar25 on 2009-05-27
This has been difficult to search for and I haven't found anything close.

I am using a GeForce 6200 card and an hp L2035 monitor on a system that has had the same problem in both Intrepid and Jaunty(upgrade). I have compiled the 180.51 driver from NVIDIA. I configured the xorg.conf with NVIDIA as root and saved it. This is a dual boot with XP machine and it does not have any issues in XP. The problem started about a month ago, it was perfect before then.

The problem: when ever I run anything with 3D, and sometimes when I am not, after a random period the graphics.... go wonky (i.e. color swaps with elongated polygons, sprays of black lines emanating from one point, small blocks inverting and changing color; fully patternless). While its messed up and I leave it til the screensaver kicks in (GLMatrix in this case) the screen saver is fine but the desktop returns as screwy. I am still able to navigate and some portions will return to normal, for a short period, as the pointer passes over them. Changing the resolution or refresh rate fixes it until the next random failure and it never gets worse or better with any setting. No group of resolution/refresh settings changes anything. None of the regular system logs comes up with anything during the time of the failure.

I purged the nvidia and xserver installs and then reinstalled...several times.

I did not bother to roll back the driver as the issue started and then I updated the driver.

I do not know how to get any further data than the commonly known logs.

---

### Post by Turambar25 on 2009-06-19
Turns out the card was about to go bad and it showed up in Ubuntu first. A couple days ago I download the newest Nvidia driver thinking it might help and everything went down hill from there til I just had a bunch of 1 inch wide- 1/4 inch tall, random-color boxes that continued popping up all over the screen. I cold booted into windows to see if anyone had posted here and had the same problem. I re-installed my old GeForce Mx 420, loaded the proper driver and everything is perfect. Looking into a newer card now, will post when I install it.

---

