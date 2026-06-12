---
title: "Can't run unity with intel i915 graphics"
date: 2011-10-01
forum: Multimedia Software
---

### Post by queendeagle on 2011-10-01
I had a full install of ubuntu and didn't have any problems. I reinstalled to a LVM so I had to use the alternate CD.

I installed a CLI then after grub it would go to a black screen. I rebooted into debug mode and did sudo tasksel and installed ubuntu desktop. When I first booted, I got a warning message up stating that my hardware couldn't handle 3D acceleration.

It's frustrating because it was working fine from a full cd iso, but just isn't happy from the alternate CD.

I've tried re-installing xserver-xorg-video-intel to no effect.

```
user@home:~$ sudo lshw -C video
[sudo] password for user: 
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:41 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4050(size=8)

```

```
user@home:~$ lsmod | grep 915
i915                  451068  7 
drm_kms_helper         40745  1 i915
drm                   184164  3 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```

---

