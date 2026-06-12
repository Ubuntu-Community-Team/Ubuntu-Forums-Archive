---
title: "Sharp Viewcam DV capture (Help?)"
date: 2006-03-06
forum: Multimedia &amp; Video
---

### Post by Terry of Astoria on 2006-03-06
I got a second-hand Sharp Mini-DV "Digital Viewcam" real cheap. Boy have I always wanted to have a DV cam. Now I do, and it seems to work great, but I haven't been able to capture the video.
  So far my 1394 device module is loaded, and Kino stopped giving mesages about "can't write to /dev/raw1394" when I got that sorted. But now Kino says "No AV/C compliant camera or not switched on"
Here are some commands and the results
```
me@maestro:~$ ls -la /dev/raw1394
crw-rw----  1 root disk 171, 0 2006-03-06 05:16 /dev/raw1394

me@maestro:~$ sudo lsmod | grep 1394
Password:
video1394              18380  0
ohci1394               30644  1 video1394
raw1394                26348  4
ieee1394               90936  3 video1394,ohci1394,raw1394
me@maestro:~$ dmesg | grep 1394
[4294697.381000] ieee1394: Initialized config rom entry `ip1394'
[4294697.394000] ieee1394: raw1394: /dev/raw1394 device initialized
[4294697.439000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294697.453000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[4294697.502000] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/ 100]
[4294697.601000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[e00000 00-e00007ff]  Max Packet=[2048]
[4294697.601000] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/ 100]
[4294697.771000] video1394: Installed video1394 module
[4294698.752000] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/ 100]
[4294825.047000] ohci1394: fw-host0: IR legacy activated
[4294839.701000] ohci1394: fw-host0: IR legacy activated
[4295350.975000] ohci1394: fw-host0: IR legacy activated
[4295367.841000] ohci1394: fw-host0: IR legacy activated
[4295428.785000] ohci1394: fw-host0: IR legacy activated
[4295613.903000] ohci1394: fw-host0: IR legacy activated
[4296051.337000] ohci1394: fw-host0: IR legacy activated
[4296067.066000] ohci1394: fw-host0: IR legacy activated
[4296093.508000] ohci1394: fw-host0: IR legacy activated
[4296126.540000] ohci1394: fw-host0: IR legacy activated
[4297083.670000] ohci1394: fw-host0: IR legacy activated


```
kino does not report any problems with /dev/raw1394 permissions.
I hope I can get this to work in Ubuntu. Anyone have any information that might shed some light on this problem for me?
Maybe the Sharp just isn't supported. Anyway thanks for your consideration.

---

### Post by vificunero on 2006-12-21
My sharp viewcam Z works with dvgrab. No prob here.

---

