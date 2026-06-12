---
title: "Video and, sound dont match up."
date: 2015-10-01
forum: Multimedia Software
---

### Post by justyn4 on 2015-10-01
So I have been trying to watch some videos on my laptop and, the sound is off sync. I tried using VLC player and, other methods but, its ether the same issue or the video skips.

---

### Post by TheFu on 2015-10-02
We need more info to help.
* which audio and video codecs are used in the problem file? vlc info has this.
* what  is the video resolution?  vlc will show it.
* which GPU driver is  being used?  **sudo lshw -C video** (please copy/paste with "code tags")
* what CPU and RAM is in the laptop? **head /proc/cpuinfo** (please copy/paste with "code tags")

The answers to these questions will help us help you.

For example:
```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:59 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:1800(size=64)
```

```
$ head /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 69
model name      : Intel(R) Celeron(R) 2955U @ 1.40GHz
stepping        : 1
microcode       : 0x15
cpu MHz         : 800.296
cache size      : 2048 KB
physical id     : 0
```

---

