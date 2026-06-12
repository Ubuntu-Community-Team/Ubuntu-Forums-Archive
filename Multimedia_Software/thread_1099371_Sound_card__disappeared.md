---
title: "Sound card  disappeared"
date: 2009-03-18
forum: Multimedia Software
---

### Post by griffink on 2009-03-18
hello all
I was trying to configure my sound card so as to make the media players work but after following some steps in  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and I rebooted and the volume control icon was blocked. 
When I try to open volume control it says no volume control Gstreamer plugin found.
The Totem player gives error as "Totem could not start up.Sound server connection was not made."

-----I ran the following commands.
       1.cat /proc/asound/card0/codec#* | grep Codec
       result-----Codec: Sigmatel STAC9221 A2
       2.[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

---

### Post by griffink on 2009-03-18
searched for the sound card  (line no. 989).
3.ran  options snd-hda-intel model=3stack
   I used MODEL  3stack as was for D945 3stack
4.reboot 
Then the problems started.

Earlier the result for aplay -l -----two soundcards  hdaintel and STAC9221 A2
....now no card found.
The cmd   ----lspci -v gives this
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 02)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation 945G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fea40000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at d880 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at d800 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at d480 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at d400 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 185
        Memory at fea37c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
        I/O ports at d080 [size=8]
        I/O ports at d000 [size=4]
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=16]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]

0000:01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Elitegroup Computer Systems: Unknown device 8139
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at e800 [size=256]
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

templar@templar-desktop:~$ esd
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


Plzzzzzzzzzzzzzz  Help........With the configuration.....

---

