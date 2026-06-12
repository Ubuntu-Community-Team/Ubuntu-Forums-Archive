---
title: "Sound issues with a new Toshiba P305-SS820"
date: 2008-06-17
forum: Multimedia Software
---

### Post by firemagican2845 on 2008-06-17
O.K. I'm not sure if this question has been asked before, but I did try searching first. I have a brand new Toshiba laptop. Everything worked out of the box (even the built in webcam!) However my problem lies with the sound card. Only one program can access the soundcard. What is even more funny is that the system itself is unable to access the soundcard if another program is using it. (I.E Ubuntu cannot even give an warning beep with something else open). I tried using the "aoss" command as that worked in the past with my old HP laptop. Any ideas on how to fix this? I'll post the lspci -v and aplay -l

```
root@jclark80-umf:~# lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0
	Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f0704800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: f0300000-f03fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0200000-f02fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0704c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: f0400000-f04fffff
	Capabilities: [50] Subsystem: Gammagraphx, Inc. Unknown device 0000

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 508
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f0704000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: medium devsel, IRQ 10
	Memory at c2000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1040
	Flags: bus master, fast devsel, latency 0, IRQ 507
	Memory at f0300000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: [48] Power Management version 3
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [c0] Express Legacy Endpoint IRQ 0

0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 16
	Memory at f0400000 (32-bit, non-prefetchable) [size=4K]
	Memory at f0402000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [60] Power Management version 2

0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f0402800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a0] Power Management version 2

0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: slow devsel, IRQ 5
	Memory at f0401000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2

root@jclark80-umf:~# 
```

```

root@jclark80-umf:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@jclark80-umf:~# 

```

Thanks!

---

### Post by blackduck on 2008-06-17
> **firemagican2845 said:**
> O.K. I'm not sure if this question has been asked before, but I did try searching first. I have a brand new Toshiba laptop. Everything worked out of the box (even the built in webcam!) However my problem lies with the sound card. Only one program can access the soundcard. What is even more funny is that the system itself is unable to access the soundcard if another program is using it. (I.E Ubuntu cannot even give an warning beep with something else open). I tried using the "aoss" command as that worked in the past with my old HP laptop. Any ideas on how to fix this? I'll post the lspci -v and aplay -l

```
root@jclark80-umf:~# lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0
	Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f0704800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: f0300000-f03fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0200000-f02fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0704c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: f0400000-f04fffff
	Capabilities: [50] Subsystem: Gammagraphx, Inc. Unknown device 0000

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 508
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f0704000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: medium devsel, IRQ 10
	Memory at c2000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1040
	Flags: bus master, fast devsel, latency 0, IRQ 507
	Memory at f0300000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: [48] Power Management version 3
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [c0] Express Legacy Endpoint IRQ 0

0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 16
	Memory at f0400000 (32-bit, non-prefetchable) [size=4K]
	Memory at f0402000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [60] Power Management version 2

0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f0402800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a0] Power Management version 2

0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: slow devsel, IRQ 5
	Memory at f0401000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2

root@jclark80-umf:~# 
```

```

root@jclark80-umf:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@jclark80-umf:~# 

```

Thanks!
You may find a path in my experience:
Realtek ALC268 Sound Fix 
I take little credit for this fix, other than the hours of searching the forums for tips, hints, etc. There were many trial & nil results but thru' the generous help of others I finally got excellent sound on both machines. I'm running Hardy on both dsktop (AMD64 Athlon) & Acer Travelmate 6492. There was no problem w/ snd in dsktop as the Realtek ALC850 was recognized w/o any tweaking.

head -n 1 /proc/asound/card0/codec*

results:



==> /proc/asound/card0/codec#0 <==

Codec: Realtek ALC268



==> /proc/asound/card0/codec#1 <==

Codec: Generic 11c1 ID 1040

which showed the notebook with a Realtek ALC268, then 
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz produced the 

Advanced Linux Sound Architecture - Driver Configuration guide
I scrolled down (a long way) to find 
ALC268

          3stack        3-stack model

          toshiba       Toshiba A205

          acer          Acer laptops

          dell          Dell OEM laptops (Vostro 1200)

          zepto         Zepto laptops

          test          for testing/debugging purpose, almost all controls can

                        adjusted.  Appearing only when compiled with

                        $CONFIG_SND_DEBUG=y

          auto          auto-config reading BIOS (default)

Then, sudo gedit /etc/modprobe.d/alsa-base where I added, options snd-hda-intel model=acer, ****as the very last line.

I saved the file, rebooted and voila, 6 months of static crackling sound ended.

---

### Post by firemagican2845 on 2008-06-17
> **blackduck said:**
> You may find a path in my experience:
Realtek ALC268 Sound Fix 
I take little credit for this fix, other than the hours of searching the forums for tips, hints, etc. There were many trial & nil results but thru' the generous help of others I finally got excellent sound on both machines. I'm running Hardy on both dsktop (AMD64 Athlon) & Acer Travelmate 6492. There was no problem w/ snd in dsktop as the Realtek ALC850 was recognized w/o any tweaking.

head -n 1 /proc/asound/card0/codec*

results:



==> /proc/asound/card0/codec#0 <==

Codec: Realtek ALC268



==> /proc/asound/card0/codec#1 <==

Codec: Generic 11c1 ID 1040

which showed the notebook with a Realtek ALC268, then 
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz produced the 

Advanced Linux Sound Architecture - Driver Configuration guide
I scrolled down (a long way) to find 
ALC268

          3stack        3-stack model

          toshiba       Toshiba A205

          acer          Acer laptops

          dell          Dell OEM laptops (Vostro 1200)

          zepto         Zepto laptops

          test          for testing/debugging purpose, almost all controls can

                        adjusted.  Appearing only when compiled with

                        $CONFIG_SND_DEBUG=y

          auto          auto-config reading BIOS (default)

Then, sudo gedit /etc/modprobe.d/alsa-base where I added, options snd-hda-intel model=acer, ****as the very last line.

I saved the file, rebooted and voila, 6 months of static crackling sound ended.

I'm not sure what you are directing me to do. I did the:
```

head -n 1 /proc/asound/card0/codec*
```

It came back with this:
```

root@jclark80-umf:~# head -n 1 /proc/asound/card0/codec*
Codec: Conexant CX20561 (Hermosa)
root@jclark80-umf:~# 
```

But I am completely unsure which what I am to do with this. Clearly I think this isn't a Realtek ALC268 as it is coming back as a Conexant CX20561. Anyways maybe I am just not getting you.

---

### Post by blackduck on 2008-06-17
Sorry, I wasn't clear but you are on the path. You know your card (Conexant). Now find it. Code:
ken@ken-laptop:~$ zless /user/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

---

