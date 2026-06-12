---
title: "Intel Sound Card not working wtih fresh Ubuntu install"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by jcorlew on 2007-04-29
Hello!  I'm completely new to this, installed Ubuntu on my laptop and am having problems getting my sound to work.  I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
and got to the point of recompiling the drivers myself, but got an error with the module assistant.  From what I've been able to gather from other posts here is the info I think might be helpful:

**lspci -v output: **

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0380000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at eff0 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0300000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ef20 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ef40 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ef80 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at e02ffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=05, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e0000000-e00fffff
        Prefetchable memory behind bridge: 20000000-25ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Memory at 26000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e400 [size=256]
        I/O ports at ee80 [size=64]
        Memory at e02ff800 (32-bit, non-prefetchable) [size=512]
        Memory at e02ff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Rioworks Unknown device 202f
        Flags: medium devsel, IRQ 16
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at e00ff800 (32-bit, non-prefetchable) [size=2K]
        Memory at e00f8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Rioworks Unknown device 202f
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at e0000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 28000000-2bfff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Rioworks Unknown device 2029
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at e00fc000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at 24000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Unknown device 17f9:0002
        Flags: bus master, fast devsel, latency 64, IRQ 19
        Memory at e00f6000 (32-bit, non-prefetchable) [size=8K]

**aplay -l output**
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any more information I can give to help out?  Thanks!

---

### Post by jcorlew on 2007-04-29
Also, the error I got from the module assistant was a long output in a box I couldn't copy easily out of.  Is that written to a log file somewhere?  I didn't see it in my /var/log/messages file.

---

### Post by jcorlew on 2007-04-29
Found the problem, it was an alsamixer setting.   Apparently External has to be muted in order for the sound to work.  Any ideas on how that can be done automatically so I don't have to do it every reboot?

---

