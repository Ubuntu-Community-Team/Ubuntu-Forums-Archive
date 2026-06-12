---
title: "Logitech Quickcam Messenger Help"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by SodaNY on 2006-11-03
I think I have tried looking at every thread and help there is. I have a Logitech Quickcam Messenger Plus webcam and a AMD Turion x2 laptop.

I am running Dapper (2.6.15-27). Although I've even tried the new 2.6.18.1. Camorama gives me the usual "no such device 'dev/video0'". I've tried adding r/w permissions, I've tried adding spca5xx, I've tried xawtv... I think I've tried everything.

lsusb gives me:
Bus 002 Device 002: ID 046d:08f6 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

/dev/video or /dev/video0 is not there when I first boot, but after I create it using mknod it still will not reconize it.

HELP!

---

### Post by roderikk on 2006-11-03
Hi,

I have the exact same webcam as you have and used this thread with great succes: [http://ubuntuforums.org/showthread.php?t=191770](http://ubuntuforums.org/showthread.php?t=191770)

Be aware that he refers to a version 1.3 in the howto while last time I looked at the site the version changed to 1.4. Good luck!

---

### Post by SodaNY on 2006-11-03
yep, i've tried this one too. I get a "kernel source code not installed" if I use the kernel that came on ubuntu CD. Or I get "quickcam module not loaded" if I use 2.6.18.1. I can only load quickcam_messenger module on 2.6.18.1

Any other suggestions?

---

### Post by konst88 on 2006-11-03
this worked fine for me on dapper: [http://www.ubuntuforums.org/showthread.php?t=126053](http://www.ubuntuforums.org/showthread.php?t=126053)

---

### Post by SodaNY on 2006-11-04
Anyone know which kernel I should use? The original or the compiled one? Should it matter? Neither are working with the webcam ...

---

