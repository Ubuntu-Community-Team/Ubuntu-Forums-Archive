---
title: "No sound, please Help!"
date: 2009-07-13
forum: Multimedia Software
---

### Post by tizmoz on 2009-07-13
Hi, i hope someone cold help me. After installing Ubuntu and installing the propriety Nvidia drive to get me out of 800x600 Res i thought all had gone well until i realized i had no sound. I've checked that it isn't muted using alsamixer, which it wasn't and followed the steps in a very good thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but got nowhere. I believe my sound card/chipset may not be supported but as i'm a complete N00B to Ubuntu,  i thought i would ask. Heres some info i think maybe helpful too help me:

tim@tim-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

tim@tim-laptop:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Unknown device 015e
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

tim@tim-laptop:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

Thanks in advance! I hope i can get this sorted as so far i've been impressed with Ubuntu and even got my Mobile Broadband working :KS. Maybe  i never go back to Vista and its problems.

---

