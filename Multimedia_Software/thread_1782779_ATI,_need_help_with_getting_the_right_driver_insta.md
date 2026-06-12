---
title: "ATI, need help with getting the right driver installed"
date: 2011-06-15
forum: Multimedia Software
---

### Post by Doctorly on 2011-06-15
I used the command
```
 lspci -v 
```
and obtained these results for my gpu:

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0292
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]
    Memory at cfdf0000 (32-bit, non-prefetchable) [size=64K]
    Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon


Does the fact that it says radeon mean that I have no driver? Does the  fact that "Capabillites" says "access denied" a bad thing? I really hope  my problem is the driver!! It could fix some problems for me:smile:!

---

### Post by Yellow Pasque on 2011-06-15
You're using the open-source 'radeon' driver, which usually works best. There is a proprietary driver, which has faster 3D. If you want to try that, see: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)
> Does the fact that "Capabillites" says "access denied" a bad thing?
...
```
sudo lspci -v
```
;)

---

