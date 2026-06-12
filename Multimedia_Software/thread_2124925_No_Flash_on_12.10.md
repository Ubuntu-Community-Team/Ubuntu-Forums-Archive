---
title: "No Flash on 12.10"
date: 2013-03-12
forum: Multimedia Software
---

### Post by Merritt.kr on 2013-03-12
This problem was present on Ubuntu 12.04.2 - then I installed Xubuntu 12.04.2, still present - then I upgraded to Xubuntu 12.10, still present.

I cannot use flash in either Firefox or Chrome. I installed xubuntu-restricted-extras and Firefox says in about:plugins

```
    File: libflashplayer.so
    Version: 
    Shockwave Flash 11.2 r202
```

In Google Chrome it says:

```
Adobe Flash Player - Version: 11.2 r202
```
and the chrome about:plugins has no entry for Pepper Flash, despite trying re-downloading the package, installing the dev build, etc...

In Firefox, on youtube, a video will show up as a simple black square, and flash to white and back. I tried Flash-Aid, but when it tries to download a Beta flash release it gets a 404 error, and when installing a stable release it simply installs the one I already had from the repos (which gives the same issues).

On Chrome it gives me an error stating "Could not load Shockwave Flash"
If I disable Adobe Flash in Chrome's about:plugins, it will now play HTML5 videos, and for flash only videos it states "The Adobe Flash Player is required for video playback."

I am at the end of my rope for troubleshooting, so any help or suggestions would be very much appreciated. Thanks in advance!

---

### Post by ManamiVixen on 2013-03-12
What CPU does your computer have? Flash in 12.10 requires SSE2 instructions to work.

---

### Post by Merritt.kr on 2013-03-12
It's an AMD Athlon XP 2600+, which no does not support SSE2. That's crazy...

My motherboard from my real PC had to be RMA'd, so I cobbled together this one out of spare parts for now...

So what is my best bet? Revert to *buntu from before 12.04 maybe?

---

### Post by Merritt.kr on 2013-03-12
Fixed. After your suggestion about SSE2, I found and followed this guide: [http://ubuntuforums.org/showthread.php?t=2111687](http://ubuntuforums.org/showthread.php?t=2111687)

Flash is now working. Just had to use an older version of flash. :)

Thanks for your help, ManamiVixen! :)

---

### Post by Merritt.kr on 2013-03-12
*

---

