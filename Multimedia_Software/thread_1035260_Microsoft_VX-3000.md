---
title: "Microsoft VX-3000"
date: 2009-01-09
forum: Multimedia Software
---

### Post by JGT on 2009-01-09
Hi

My webcam Microsoft VX-3000 worked fine out of the box on Cheese in 8.04, but it hasn't worked ever in 8.10.

I don't know what this means but the camera is being detected:

[PHP]john@john-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 006: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/PHP]

Any ideas?

John

---

### Post by albinootje on 2009-01-09
> **JGT said:**
>  My webcam Microsoft VX-3000 worked fine out of the box on Cheese in 8.04, but it hasn't worked ever in 8.10.
[PHP]john@john-desktop:~$ lsusb
Bus 002 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000.


See here for more information :
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657

---

