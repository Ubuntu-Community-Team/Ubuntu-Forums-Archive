---
title: "Nvidia Fan Speed"
date: 2012-08-26
forum: Multimedia Software
---

### Post by ThePol1 on 2012-08-26
My Ubuntu 12.04 HTPC is loud. I traced the noise down to the fan on the video card. The card is an Nvidia GT 430. It runs at 65% no matter what I do.

I am running the latest drivers from Nvidia: 304.37.

I have set Coolbits 4 in xorg.conf. This enabled the fan control sliding bar under Thermal Settings. Every time I try to move the slider to some other value and click Apply, it jumps back to 65.

I've tried setting the fan speed via command line but it doesn't work:
nvidia-settings -a [gpu:0]/GPUFanControlState=1
nvidia-settings -a [fan:0]/GPUCurrentFanSpeed=25

I can't use nvclock because it segfaults.

Please help!

---

### Post by ThePol1 on 2012-08-27
Bump

---

### Post by ThePol1 on 2012-08-28
Please help. :)

---

### Post by ThePol1 on 2012-09-04
One last bump. Any help would be appreciated!

---

### Post by ant_thomas on 2012-09-13
Shame no one has a solution.

I have exactly the same issue. I have a Nvidia GT 620 card which is the same as the GT 430.

Fan stuck at 65%, very loud. Temp is at 31C. Need to bring the fan speed down quite a bit.

---

### Post by ThePol1 on 2012-09-13
Let me know if you find a solution. I've been considering disabling the fan completely since the noise is really frustrating. I'd hate to fry my card...

---

### Post by ant_thomas on 2012-09-14
You're in luck. I've sorted it.

It requires a custom BIOS flash but it's not too hard.

You need a Windows machine to do it, or a least one to prepare the BIOS ROM.

What you need to do is...

1. Download nvflash
2. Make a bootable USB drive using HP Bootable USB tool
3. Copy nvflash files over
4. Boot the system with the 65% fan nvidia card off the USB drive
5. Dump the BIOS ROM - "nvflash --save origbios.rom"
6. Shutdown
7. Copy "origbios.rom" off the USB drive.
8. Download NiBiTor
9. Open ROM in NiBiTor. It will complain that it doesn't recognise the ROM. 
10. From the Device menu select your card, or if you have a GT 620 like I do just select GT 520 "Nvidia PCI-E 520 GT" because they're exactly the same card.
11. Under the Adv. Info tab click "Rescan Bios"
12. Go to Temperatures tab and change the Min to something reasonable. I picked "30".
13. File -> Save Bios. Save it to a new name.
14. Copy to USB drive.
15. Boot off the USB drive again.
16. Use command "nvflash --index=0 -5 -6 newbios.rom" - It might complain about which card it is, and saying something doesn't match, don't ignore the warnings, just make sure they're sensible. Mine had a warning maybe because the ROM was modified or maybe because I had selected 520 GT in NiBiTor. But it still worked fine.

That's pretty much what I did, after reading this link.....

[http://www.techpowerup.com/forums/showthread.php?t=119955](http://www.techpowerup.com/forums/showthread.php?t=119955)

My fan speed was initially at 31% at boot and has now settled at 42% and 60C which is much much quieter than a constant 65%.

So it's obvious that lower than 65% is safe and it can obviously self regulate so it's not like you're forcing it to run at 30% and overheat. If you want you can change the max fan speed too. Mine was set at 100% and I left it at that, I doubt it will ever even get to 65% again.

```
htpc@htpc:~$ nvidia-smi
Fri Sep 14 19:27:56 2012
+------------------------------------------------------+
| NVIDIA-SMI 4.304.43   Driver Version: 304.43         |
|-------------------------------+----------------------+----------------------+
| GPU  Name                     | Bus-Id        Disp.  | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap| Memory-Usage         | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 620           | 0000:01:00.0     N/A |                  N/A |
| 42%   60C  N/A     N/A /  N/A |   5%   53MB / 1023MB |     N/A      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+

```

I take no responsibility if you screw up your card!! But it seems fairly safe if you know what you're doing.

Read the link I posted first since that is more in depth, I just had to adapt it accordingly for my setup.

---

### Post by ant_thomas on 2012-09-14
And now it's back down to 31%. Seems to be working well.

```
htpc@htpc:~$ nvidia-smi
Fri Sep 14 20:57:59 2012
+------------------------------------------------------+
| NVIDIA-SMI 4.304.43   Driver Version: 304.43         |
|-------------------------------+----------------------+----------------------+
| GPU  Name                     | Bus-Id        Disp.  | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap| Memory-Usage         | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 620           | 0000:01:00.0     N/A |                  N/A |
| 31%   47C  N/A     N/A /  N/A |   6%   63MB / 1023MB |     N/A      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+

```

---

### Post by ThePol1 on 2012-09-14
Thank you *very* much! This fixed it for me. I set my low speed at 20 and the high at 30. It is significantly quieter. Yea!

---

### Post by ant_thomas on 2012-09-15
Glad to hear it worked!

I'd be careful with a max of 30% though. You might end up with some overheating issues.

The issue for me was that it should be a lower min. Keeping the max at 100% will make sure it never overheats.

---

### Post by jones27557 on 2012-09-15
thanks

---

### Post by Statia on 2012-10-03
I was googling for something similar and apart from this thread found this HOW-TO:

[http://ubuntuforums.org/showthread.php?t=1776188](http://ubuntuforums.org/showthread.php?t=1776188)

---

### Post by pmin00 on 2012-11-02
> **ThePol1 said:**
> My Ubuntu 12.04 HTPC is loud. I traced the noise down to the fan on the video card. The card is an Nvidia GT 430. It runs at 65% no matter what I do.

I have a similar problem with a GT440. It runs at 50% or higher, but not lower.

I started a thread about this on the nvidia forums:
[https://devtalk.nvidia.com/default/topic/522873/linux/gt440-fan-speed-can-not-be-lowered-below-50-/](https://devtalk.nvidia.com/default/topic/522873/linux/gt440-fan-speed-can-not-be-lowered-below-50-/)

Did someone ever get this resolved without reflashing the BIOS?

thanks,

Patrick

---

### Post by ant_thomas on 2012-11-05
> **pmin00 said:**
> For now I've connected the graphics card fan to a spare fan connector
on the motherboard, with a 120 Ohm resistor in one of the wires to slow it down.

So you're prepared to do that but not flash the BIOS?

From what I read after a lot of searching the coolbits method just wouldn't work for me and no other software/driver methods would do the job either.

Flashing the BIOS was obviously a last resort but it was fairly easy to do and worked perfectly.

---

