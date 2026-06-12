---
title: "Triton VGA to USB driver installed, but not functioning?"
date: 2011-08-23
forum: Multimedia Software
---

### Post by Desh Banks on 2011-08-23
Hi all,

I'm running Ubuntu 10.04 (LTS), and am trying to get my Triton USB/VGA adapter to work to allow me to use three monitors.

I have the driver **X.Org X server -- SiS USB display driver** installed, but I cannot select my third display (the one connected via the USB/VGA) in system->preferences->monitors.

I have tried '**sudo modprobe sisusbv**', but it returns with no message and nothing happens.

Is there something else I need to do? I have googled around this topic for a couple days now, but have not found any solution.

My GFX card: Mobility Radeon HD 4500 series.

lsusb returns the following:

apertur3@0verwatch:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 003: ID 0711:5100 Magic Control Technology Corp. **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

4th from the bottom is the USB that is the VGA/Triton adapter.

One thing I noticed after reading other posts on this issue is that xorg.conf does not exist in the newer versions of ubuntu, will I have to create this file?

Thanks for any help on this issue...

---

### Post by Desh Banks on 2011-08-29
Bump... Still not having any luck here... Has anyone been able to do this successfully?

---

