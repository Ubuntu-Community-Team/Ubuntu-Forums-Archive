---
title: "Video Playback on Dell Laptop"
date: 2010-01-15
forum: Multimedia Software
---

### Post by Taterade on 2010-01-15
I have a Dell Latitude CPi that has 400MHz Intel Processor and 256 MB of ram. It has a Neomagic Corporation NM2360 [MagicMedia 256ZX]. I have it set to 16 bit color depth and it is using the neomagic driver. My problem is that it cannot play any video of any size flash, or saved to hard drive. It has a fps so low that I can see it rendering each frame going across the screen. It doesn't seem to have a problem with animated pictures, just actual video files. I don't know whether or not this matters but the card set is known to not support 3d acceleration. I can run any commands in terminal and have a good understanding of the linux environment. This problem has occurred under Ubuntu and Xubuntu and still happens if I use a light weight WM like fluxbox.

---

### Post by Taterade on 2010-02-02
*BUMP* Still no manageable video playback, glxgears reports that in a maximized window the laptop renders 12-15 frames per 5.2 seconds. This of course gets much faster as the window gets smaller.

---

### Post by efflandt on 2010-02-03
Good luck.  I bought a Sony laptop in Jan 2000 that has 500 MHz PIII and Neomagic video (I think 4.5 MB of video RAM).  It ran SuSE 8.0 snappy enough on 192 MB of RAM (which at the time, I thought was so much that I did not need swap).  I booted it up recently and the old SuSE still worked fine, but I have not tried a newer Linux version on it (not enough RAM to run Ubuntu live CD).

I think Neomagic went out of business shortly after that (almost 10 years ago), so accelerated support was dropped from X long ago.  So you end up with whatever speed you get from generic vesafb.

Even a PIII 550 desktop with ATI video card and fglrx driver was marginal playing flash video (Ubuntu 9.04 or 9.10).  Sound was smooth, but slow video frame rate.  I didn't have a DVD player in it to test.  So I installed Qimo for kids on it (based on Ubuntu 8.10) and gave it to my niece for her 4 year old twins.  The learning games work fine.

---

