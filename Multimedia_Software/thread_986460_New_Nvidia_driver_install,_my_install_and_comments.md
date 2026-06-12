---
title: "New Nvidia driver install, my install and comments."
date: 2008-11-18
forum: Multimedia Software
---

### Post by slinkey1981 on 2008-11-18
So I have been having a LOT (read- nearly all) of the problems that could be attributed to my Nvidia 6200 card, running the 169.12 drivers that Envy installed.

I know it's old, but hey, it's what I have. I had some HORRIBLE frame rate issues, and even running one video while compiz was up seriously degraded playback quality.

Flying around the net, I found that Nvidia has released a ***BETA!*** drive (180.06) that is supposed to take care of a few issues.

From the Nvidia site:
>     *  Added support for CUDA 2.1.
    * Added initial support for PureVideo-like features on Linux via the new VDPAU API (see the vdpau.h header file installed with the driver).
    * Added new workstation performance optimizations.
    * Enabled the X Render "GlyphCache" by default.
    * Disabled shared memory X pixmaps by default; see the&#8220;AllowSHMPixmaps" option.
    * Fixed a regression that could result in window decorationcorruption when running Compiz using Geforce 6 and 7 series GPUs.
    * Improved X pixmap placement on GeForce 8 series and later GPUs.
    * Improved compatibility with recent Linux kernels.
    * Improved stability on some GeForce 8 series and newer GPUs.


And, well, I was just using an old driver and felt it was time to take a stab at installing something that didn't come in a .deb or through a package manager.

For me, the install and setup went as easy as pie... Wait, that's not exactly true. I have some other problems with my system, but you probably don't have the same junk, so I'll just say everything I tried, and how when it didn't work, I did something else until it did.

1. I downloaded the driver from [here]("http://www.nvidia.com/object/linux_display_ia32_180.06.html") (I don't know where the 64bit drives are, sorry)

2. I right clicked and made it executable (don't ask me why, I'm not sure if it helped me at all)

3. I used the "run in terminal" command, and was told NO, because I wasn't root.

4. I alt-F2'd a "gksudo nautilus" and did the same thing, and was told NO, because X-server was running (Doh!)

5. I opened a terminal and 
```
/etc/init.d/gdm stop
```
which just locked with a flashy cursor when uShare told it that a song didn't fit the text selection.

6. I rebooted into terminal as root@mycomputer, and was told (thankfully) that I shouldn't run the program as a level 1 user.

7. I did a ```
telinit 3
```
Which was rather silly, as it just booted back into what I had exited (ie-GNOME)

8. I got upset, and went:
System>Administration>Services 
and killed the "Graphical User Login (GDM)" which FINALLY got me into a user level terminal.

9. I typed in ```
sh /home/user/Desktop/NVIDIA-Linux-x86-180.06-pkg1.run
```
and was told that I needed to be root (Somewhat contradictory to what it told me in step 6)

10. I did a ```
sudo sh /home/user/Desktop/NVIDIA-Linux-x86-180.06-pkg1.run
```
and it ran, telling me that a backup was being created, it tried to download a compatible kernal, but couldn't find one, so it made one (Just For Me!) and then told me that it was finished.

11. I typed in my super-special
```
gdm start
```
and was rewarded with a "New" Nvidia splash screen (yes, I have it enabled) that looks blatantly like the previous one, the only difference being a nice little red "Beta" on it now.


In summation, it's working great, a little faster on some things (Decorations don't tear) but my CPU *is* running about 5% higher, but memory usage is down about 10%, so it may have absolutely nothing to do with the driver...

AND, I had fun doing something that I wouldn't have thought about, just because of a random website. I am not a "Beta" user, because when things break, I don't know how to fix them, but, by searching the forums on how to do things before I started, I had all kinds of options for when I started my little "Project", so a "thank you" is in order for all the great tips and tricks I have seen.

Please don't ask me for help installing this, because (as should be plain to see) I won't be able to help you. I just wanted to share my installation steps and maybe have some of the long time users laugh at my feeble attempts at installing a simple display driver.

PS: I now have "NVIDIA Xserver Settings" listed under System Tools...

EDIT: My card now correctly detects my Monitor, and the resolution isn't from some hack-job. The settings actually seem to work, and in the NVIDIA Settings, the changes I make also seem to make an impact, setting everything to high performance (from quality) has reduced my cpu and memory usage to levels a little lower than they were before.

---

### Post by obsrv on 2008-12-23
Nice :) I have problems about downloading kernel for me :( and driver install fails. Current stable drivers does not support my GTX 280, I will wait I think.

---

