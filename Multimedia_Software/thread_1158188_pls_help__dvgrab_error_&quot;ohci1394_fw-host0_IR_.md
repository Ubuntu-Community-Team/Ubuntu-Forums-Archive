---
title: "pls help  dvgrab error &quot;ohci1394: fw-host0: IR DMA error - packet too long for buffer"
date: 2009-05-13
forum: Multimedia Software
---

### Post by serotta_rider on 2009-05-13
Please help.....I have been at this for a few days now...

I run the following and the camera starts up and begins to play for 10 seconds. It then hangs and stops.

dvgrab --format raw --duration 0:02:00 /home/djk/downloads/Found AV/C device with GUID 0x00008500014d3a5b
""     0.00 MiB 0 frames
Capture Stopped
Error: no DV

dmesg gives the the following...

[ 1270.531472] 
[ 1270.531478] ohci1394: fw-host0: IR DMA error - packet too long for buffer
[ 1270.531480] 
[ 1270.531484] ohci1394: fw-host0: IR DMA error - packet too long for buffer
[ 1270.531486] 
[ 1270.531489] ohci1394: fw-host0: IR DMA error - packet too long for buffer
[ 1270.531491] 

I think I have ohci1394 loaded correctly...

djk@djk-laptop:~$ lsmod | grep ohci
ohci1394               38576  2 video1394,dv1394
ieee1394               94660  4 video1394,raw1394,dv1394,ohci1394

---

### Post by t4thfavor on 2009-07-24
Same issue with a Sony dcr-ip5. 

I get nothing in the dmesg output though.

Wonder if there is a fix for this yet?

I lied, I get the same
ohci1394: fw-host0: IR DMA error - packet too long for buffer

It repeats like 500 times.

---

