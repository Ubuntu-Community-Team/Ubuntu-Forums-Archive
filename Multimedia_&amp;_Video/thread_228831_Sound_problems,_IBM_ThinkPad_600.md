---
title: "Sound problems, IBM ThinkPad 600"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by Hirotama on 2006-08-03
I have a problem with the soundcard on my IBM ThinkPad 600.

> 
root@lsd:~/mp3# madplay test.mp3
MPEG Audio Decoder 0.15.2 (beta) - Copyright (C) 2000-2004 Robert Leslie et al.
audio: /dev/dsp: No such file or directory
root@lsd:~/mp3#


I readed
[http://www.thinkwiki.org/wiki/CS4237](http://www.thinkwiki.org/wiki/CS4237),
[http://alsa.opensrc.org/ThinkPad+Simple+Boot](http://alsa.opensrc.org/ThinkPad+Simple+Boot) ,
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and tried this this bash script [http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode](http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode) :)
and still can't solve my problem. 
I disabled QUICKBOOT. I made DSP and audio tests via BIOS. Sound card is enabled.

> 
root@lsd:~# cat /etc/modprobe.d/alsa-base |grep 4236
install snd-cs4236 modprobe --ignore-install snd-cs4236 && /lib/alsa/modprobe-post-install snd-cs4236
options snd-cs4236 snd_index=0 snd_port=0x530 snd_cport=0x538 snd_isapnp=0 snd_dma1=1 snd_dma2=0 snd_irq=5

Also i try to load them via console.

> 
root@lsd:~# modprobe snd-cs4236
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4236.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_cs4236
root@lsd:~# dmesg
[4298110.626000] snd_cs4236: Unknown parameter `snd_index'


Here is lspci -v output:
> 
root@lsd:~/mp3# lspci -v
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
        Flags: bus master, medium devsel, latency 64
        Memory at <unassigned> (32-bit, prefetchable)

0000:00:02.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
        Subsystem: IBM ThinkPad 600
        Flags: bus master, medium devsel, latency 168, IRQ 9
        Memory at 20301000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
        Memory window 0: 04000000-043ff000 (prefetchable)
        Memory window 1: 04400000-047ff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:00:02.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
        Subsystem: IBM ThinkPad 600
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at 20300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 04800000-04bff000 (prefetchable)
        Memory window 1: 04c00000-04fff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:00:03.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA])
        Subsystem: Neomagic Corporation MagicGraph 128XD
        Flags: bus master, medium devsel, latency 128, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=16M]
        Memory at 20000000 (32-bit, non-prefetchable) [size=2M]
        Memory at 20200000 (32-bit, non-prefetchable) [size=1M]

0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 48
        I/O ports at fcf0 [size=16]

0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 48, IRQ 9
        I/O ports at 8400 [size=32]

0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
        Flags: medium devsel, IRQ 9

I can't see the card but I am sure - card is enabled :)
EDIT: I'm using Ubuntu 5.10

---

### Post by butchd on 2006-08-04
What do you get when you type "aplay -l" in terminal?  Can you see the sound card when you go to volume preferences (rt clk on master volume control next to date/preferences)? Finding the correct drivers helped me---I had the same issue. Multimedia drivers from automatix:
[http://ubuntuforums.org/showthread.php?t=190025]("http://ubuntuforums.org/showthread.php?t=190025")

This is also a good troubleshooting guide:
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+audio+driver]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+audio+driver")

---

### Post by gotaserena on 2006-08-06
> ```
options snd-cs4236 snd_index=0...
```

I don't think that there's such an option in the snd-cs4236 module. Hence the error. For /dev/dsp you need to use ALSA's OSS compatibily layer. Look at this post [http://ubuntuforums.org/showthread.php?t=188736](http://ubuntuforums.org/showthread.php?t=188736) for instructions how to change the configuration files.

---

