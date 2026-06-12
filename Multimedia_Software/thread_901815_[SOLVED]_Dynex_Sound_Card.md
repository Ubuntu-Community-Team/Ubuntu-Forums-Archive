---
title: "[SOLVED] Dynex Sound Card"
date: 2008-08-26
forum: Multimedia Software
---

### Post by tad1073 on 2008-08-26
New sound card, no sound. Conected with digital optical to stereo reciever.

```
thomas@hp:~$ lspci -v
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
    Flags: bus master, medium devsel, latency 64

00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
    Flags: bus master, medium devsel, latency 64

00:01.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, medium devsel, latency 128
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=255
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: b0000000-b15fffff
    Prefetchable memory behind bridge: 0000000020000000-00000000201fffff
    Capabilities: <access denied>

00:02.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Unknown device 19f1:1679
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 26
    Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at b3000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 20200000 [disabled] [size=128K]
    Capabilities: <access denied>

[B][COLOR=Red]00:03.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
    Subsystem: MEDIATEK Corp. Unknown device 1705
    Flags: bus master, medium devsel, latency 64, IRQ 28
    I/O ports at 2080 [size=32]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>[/COLOR][/B]

00:04.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
    Subsystem: Netgear Unknown device 5e00
    Flags: bus master, medium devsel, latency 168, IRQ 30
    Memory at b1600000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 4f)
    Subsystem: Broadcom OSB4 South Bridge
    Flags: bus master, medium devsel, latency 0

00:0f.1 IDE interface: Broadcom OSB4 IDE Controller (prog-if 8a [Master SecP PriP])
    Flags: bus master, medium devsel, latency 64
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 20a0 [size=16]

01:04.0 SCSI storage controller: LSI Logic / Symbios Logic 53c895a (rev 01)
    Subsystem: Compaq Computer Corporation Unknown device 001b
    Flags: bus master, medium devsel, latency 66, IRQ 22
    I/O ports at 1000 [size=256]
    Memory at b1400000 (32-bit, non-prefetchable) [size=1K]
    Memory at b1100000 (32-bit, non-prefetchable) [size=8K]
    [virtual] Expansion ROM at 20100000 [disabled] [size=256K]
    Capabilities: <access denied>

01:05.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
    Subsystem: Compaq Computer Corporation NC3163 Fast Ethernet NIC (embedded, WOL)
    Flags: bus master, medium devsel, latency 66, IRQ 23
    Memory at b1200000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1c00 [size=64]
    Memory at b1000000 (32-bit, non-prefetchable) [size=1M]
    [virtual] Expansion ROM at 20000000 [disabled] [size=1M]
    Capabilities: <access denied>

01:06.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27) (prog-if 00 [VGA controller])
    Subsystem: Compaq Computer Corporation Proliant Rage XL
    Flags: bus master, stepping, medium devsel, latency 66, IRQ 24
    Memory at b0000000 (32-bit, non-prefetchable) [disabled] [size=16M]
    I/O ports at 1400 [disabled] [size=256]
    Memory at b1300000 (32-bit, non-prefetchable) [disabled] [size=4K]
    [virtual] Expansion ROM at 20140000 [disabled] [size=128K]
    Capabilities: <access denied>

01:07.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller
    Subsystem: Compaq Computer Corporation Unknown device b0f3
    Flags: medium devsel, IRQ 25
    I/O ports at 1800 [size=256]
    Memory at b1500000 (32-bit, non-prefetchable) [size=256]

thomas@hp:~$ sudo /etc/init.d/alsa-utils restart 
[sudo] password for thomas: 
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
thomas@hp:~$ alsamixer

thomas@hp:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
ICE1724

```

---

### Post by ericwait on 2008-11-23
How was this solved?  I am trying to do the same thing.

---

### Post by psyke83 on 2008-11-23
> **ericwait said:**
> How was this solved?  I am trying to do the same thing.

Although I'm not sure how the OP solved his issue, the proper way to solve this problem is to assign the default sink (playback device) in the PulseAudio Volume Control. PulseAudio ignores ALSA module indexes, so it may not choose the sound card you expect - until you manually specify the default yourself.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by tad1073 on 2008-12-25
> **ericwait said:**
> How was this solved?  I am trying to do the same thing.

I uninstalled Ubuntu and stayed with xp.   [old computer](http://ubuntuforums.org/album.php?albumid=796)

Also the issue was with the optical out, where as I did not have computer speakers at the time. When I got the speakers and reinstalled ubuntu every thing worked fine except for the optical out. But the only issue with that was playing flash and system sounds though.

---------------- Now playing: [Tool - The Pot]("http://www.foxytunes.com/artist/tool/track/the+pot") via [FoxyTunes]("http://www.foxytunes.com/signatunes/")

---

