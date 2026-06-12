---
title: "No sound in 10.04"
date: 2010-04-30
forum: Multimedia Software
---

### Post by The Switch Blade on 2010-04-30
Fresh install. Sony Vaio VPCF11NFX/B.

earl@earl-laptop:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:e3080000-e3083fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:e8e00000-e8e03fff

---

### Post by The Switch Blade on 2010-05-02
earl@earl-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

earl@earl-laptop:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at e8e00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e3080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

---

### Post by The Switch Blade on 2010-05-05
```
earl@earl-laptop:~$ uname -a
Linux earl-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```
```
earl@earl-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
```
```
earl@earl-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 275

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID a
```

---

### Post by lidex on 2010-05-05
Your best option is to upgrade alsa to 1.0.23. Use the info and link in this post:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

---

