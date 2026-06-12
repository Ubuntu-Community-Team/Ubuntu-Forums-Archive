---
title: "Getting Sound..help needed with last step"
date: 2010-01-09
forum: Multimedia Software
---

### Post by zzzmuzz on 2010-01-09
I have been following the Comprehensive Guide to Sound problems,as i couldnt get sound on my laptop  Asus M2N.  Sound goes fine under Windows.

I did the command to find sound cards and here is the section:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1713
    Flags: medium devsel
    I/O ports at e000 [size=256]
    I/O ports at e100 [size=64]
    Memory at 30000400 (32-bit, non-prefetchable) [size=512]
    Memory at 30000600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0

I downloaded the driver and installed it. 

I entered the command :  sudo modprobe snd-ac97-codec  but still cannot access sound.

Is the issue the <access denied>  ?

Or what should I try next?

Thanks folks.

---

