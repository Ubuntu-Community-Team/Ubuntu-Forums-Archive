---
title: "snd-ice1724 audio driver not loading for Shutle SN25P in 11.10"
date: 2011-10-20
forum: Multimedia Software
---

### Post by ibodog on 2011-10-20
I was expecting Ubuntu to automatically detect and load the sound driver on my Shuttle SN25P desktop PC.  But Sound in System Settings shows only a "dummy" device for output.

I scanned dmesg and see these lines.
```
[    8.865556] ICE1724 0000:06:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    8.897462] ice1724: Invalid EEPROM (size = 255)
[    8.897475] ICE1724 0000:06:06.0: PCI INT A disabled
[    8.897498] ICE1724: probe of 0000:06:06.0 failed with error -5
```

aplay -l lists no devices.

lspci (a couple of ways) shows this.

```

~# lspci -v | grep -A7 -i "audio"
06:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: VIA Technologies Inc. Albatron PX865PE 7.1
        Flags: medium devsel, IRQ 18
        I/O ports at a000 [size=32]
        I/O ports at a400 [size=128]
        Capabilities: [80] Power Management version 1
        Kernel modules: snd-ice1724

~# lspci -d 1412:1724 -nvx 
06:06.0 0401: 1412:1724 (rev 01)
        Subsystem: 1412:1724
        Flags: medium devsel, IRQ 18
        I/O ports at a000 [size=32]
        I/O ports at a400 [size=128]
        Capabilities: [80] Power Management version 1
        Kernel modules: snd-ice1724
00: 12 14 24 17 01 00 10 02 01 00 01 04 00 20 00 00
10: 01 a0 00 00 01 a4 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 12 14 24 17
30: 00 00 00 00 80 00 00 00 00 00 00 00 0c 01 00 00

```

If I try to load the snd-ice1724 module after boot nothing happens ("modprobe snd-ice1724"). I followed instructions on a few links I googled trying to fix this problem and came on an old page where someone hacked a source file somewhere and recompiled the driver.  Those instructions were a few years old and it seems to me that newer versions should just recognize this card and load the driver.

Any idea how to get Ubuntu to load the driver for this sound device?

---

### Post by ibodog on 2011-10-20
This is the source file hack.  [http://forum.soft32.com/linux2/Sound-Chip-IC-Ensemble-ICE1724-Envy24HT-ftopict23784.html](http://forum.soft32.com/linux2/Sound-Chip-IC-Ensemble-ICE1724-Envy24HT-ftopict23784.html)

I am not familiar with compiling the kernel, but I gave it a shot and got an error with the ubuntu sources I downloaded following (as best possible) instructions here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).  Something about not being configured to build with modules.  When I tried to do the config to enable the modules it started asking a lot of questions I didn't know the answers to. :(

Anyway, I did manage to get a look at the source file vt1720_mobo.c.  It appears that my Shuttle SN25P is already listed in there, but with the wrong ID!

```
#define VT1720_SUBDEVICE_SN25P          0x97123650
```

According to the source file hack the correct id of my sound card should be

```
#define VT1720_SUBDEVICE_SN25P          0x12142417
```

This seems like an Ubuntu and/or ALSA bug, no?  I don't really want to get involved in building a custom kernel every update, so it seems like this is a bug that could be fixed.  Maybe a 2nd configuration needs to be added for the SN25P?

---

