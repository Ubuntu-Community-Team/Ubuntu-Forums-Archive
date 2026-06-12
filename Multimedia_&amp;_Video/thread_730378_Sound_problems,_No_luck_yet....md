---
title: "Sound problems, No luck yet..."
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by ThatGuyThere on 2008-03-20
Running linux on a Macbook pro 2.2ghz 2gb ram, if that makes a difference. Sounds are fine on OS X.I have been having sound issues ever since I have installed flashplayer for Firefox. Since then, My sound DOES NOT FUNCTION at all. No system sounds or anything. I get this error message from Amarok:
```

Audio output unavailable; the device is busy.
xine parameters:

```
It's pretty vague. I've tried the guide on installing sound, but it didn't work. Whenever I go into Apps-Settings-Mixer Settings, The dropdown bar only says default, and doesn't drop down. I get no options to change any other sounds. I have tried uninstalling flash and rebooting, and the comprehensive sound guide. I'm teetering on the edge of uninstalling linux alltogether and going back to Windows (Something I dread), because this is the 3rd time this problem has happened in 3 different Ubuntu installs (Standard, kUbuntu, and xUbuntu). ANY Help would be appreciated. I love the OS so far, but with serious problems like these, it's really deterring me. 

lspci -v output (Audio device bolded) :
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: 90000000-930fffff
        Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 60c0 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 60a0 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at 9b504c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
[B]
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at 9b500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>[/B]

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 9b400000-9b4fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=0a, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: 97400000-9b3fffff
        Prefetchable memory behind bridge: 0000000093100000-00000000970fffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Memory behind bridge: 97300000-973fffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 97200000-972fffff
        Prefetchable memory behind bridge: 000000009b600000-000000009b6fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 6080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 6060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6040 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at 9b504800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
        Memory behind bridge: 97100000-971fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 60e0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 60f8 [size=8]
        I/O ports at 6114 [size=4]
        I/O ports at 60f0 [size=8]
        I/O ports at 6110 [size=4]
        I/O ports at 6020 [size=16]
        I/O ports at 1000 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: medium devsel, IRQ 10
        Memory at 9b505000 (32-bit, non-prefetchable) [size=256]
        I/O ports at efa0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1) (prog-if 00 [VGA])
        Subsystem: Apple Computer Inc. Unknown device 00a0
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 92000000 (32-bit, non-prefetchable) [size=16M]
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        Memory at 90000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 5000 [size=128]
        [virtual] Expansion ROM at 93000000 [disabled] [size=128K]
        Capabilities: <access denied>

0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
        Subsystem: Apple Computer Inc. Unknown device 0087
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at 97300000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
        Subsystem: Marvell Technology Group Ltd. Unknown device 00ba
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 97200000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 3000 [size=256]
        Expansion ROM at 9b600000 [disabled] [size=128K]
        Capabilities: <access denied>

0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 248, IRQ 21
        Memory at 97104000 (32-bit, non-prefetchable) [size=2K]
        Memory at 97100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


```

aplay -l output :
```

aplay: device_list:204: no soundcards found...
```

---

### Post by ThatGuyThere on 2008-03-20
BUMP! I really need a solution!

---

### Post by wolfen69 on 2008-03-20
this [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda_intel%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda_intel%29) may shed some light. also this [http://ubuntuforums.org/showthread.php?t=729333&highlight=intel+hda](http://ubuntuforums.org/showthread.php?t=729333&highlight=intel+hda) good luck.

if nothing else works, give the Hardy Heron Beta a try. it cant hurt. a friends laptop whose sound never worked (intel) finally works with Hardy.

---

### Post by ThatGuyThere on 2008-03-20
The problem is, I can't find alsa drivers for my sound card. I've looked under the intel and apple sections, but there is no ICH8 series. Unless i'm looking at the wrong part, my sound card isnt' supported by alsa, but my sound was working before i installed flash.

---

### Post by wolfen69 on 2008-03-20
i personally would re-install and hope for the best. the way i see it, if i'm going to spend hours trying to fix something, why not spend that time re-installing? that's just me though.
> I'm teetering on the edge of uninstalling linux alltogether and going back to Windows
i would buy a new Dell pc with ubuntu on it before i would do that. or not use computers at all.

---

### Post by wolfen69 on 2008-03-20
just found this [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) 
very long though.

---

### Post by ThatGuyThere on 2008-03-20
Thanks for the link, but for 'does' work and 'does not' work, Macbook pro isn't listed anywhere. I would love to reinstall, but I fear that the same problem may afflict me again :(

---

### Post by Yellow Pasque on 2008-03-21
Try upgrading ALSA:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

The ICH8 is the South Bridge device, the actual driver is the hda-intel driver. You should also post the result of the the codec command if you're still having issues (there's a link in the link I gave above that tells you how to get the codec)

---

