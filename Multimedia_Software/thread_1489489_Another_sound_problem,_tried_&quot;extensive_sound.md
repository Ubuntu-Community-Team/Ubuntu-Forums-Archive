---
title: "Another sound problem, tried &quot;extensive sound&quot; sticky..."
date: 2010-05-21
forum: Multimedia Software
---

### Post by Antaios on 2010-05-21
i just did my first ubuntu installation :), 10.04, 32bit, 2 days ago.
the only problem i've had, is there's no sound...

i'm using dual boot with windows xp, on a Toshiba Satellite P100 (PSPA3Ablahblah...model number's not that common...)

as far as i can tell, with my fumbling around in the terminal based on loads of other posts, some probably on this forum, and also based on the "extensive sound guide" sticky thread, Ubuntu, and alsa (i think its called alsa) knows the sound card's there, and the sound is turned on as far as i can tell with alsamixer, so im stumped, no idea what to try next, as what i've tried has been only from bits and pieces from other threads...

if it helps, heres what "aplay -l" returns...

```
antaios@ENTERPRISE:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```and lspci -v:
```

antaios@ENTERPRISE:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: b1000000-b2ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 84000000-841fffff
    Prefetchable memory behind bridge: 0000000084200000-00000000843fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 84400000-845fffff
    Prefetchable memory behind bridge: 0000000084600000-00000000847fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 84800000-849fffff
    Prefetchable memory behind bridge: 0000000084a00000-0000000084bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: b3200000-b32fffff
    Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18b0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: medium devsel, IRQ 11
    I/O ports at 18c0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at 84000000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at 2000 [disabled] [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1040
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at 84400000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at b3200000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
    Memory window 0: 80000000-83fff000 (prefetchable)
    Memory window 1: 88000000-8bfff000
    I/O window 0: 00005000-000050ff
    I/O window 1: 00005400-000054ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at b3201000 (32-bit, non-prefetchable) [size=2K]
    Memory at b3204000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at b3202000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Toshiba America Info Systems Device ff31
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at b3201800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
```Any help would be greatly appreciated

EDIT: i should probably mention that the sound works fine on the windows xp boot...
[]("http://www.vampwarez.com/2010/05/linux-sound-problems-guide.html")

---

### Post by lidex on 2010-05-21
Some more info please. Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags (the # in toolbar)

---

### Post by Antaios on 2010-05-22
wow, never knew there was even more information you could retreive from the sound stuff...

the three outputs:
```
antaios@ENTERPRISE:~$ uname -a
Linux ENTERPRISE 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
antaios@ENTERPRISE:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
antaios@ENTERPRISE:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20551 (Waikiki)
```(Waikiki??)...

hope that helps

---

### Post by Yellow Pasque on 2010-05-22
The issue was supposedly fixed in newer kernels: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

You might have to update your BIOS. [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp?nav=Product%20Support](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp?nav=Product%20Support)

---

### Post by Antaios on 2010-05-22
> **Temüjin said:**
> The issue was supposedly fixed in newer kernels: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

You might have to update your BIOS. [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp?nav=Product%20Support]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp?nav=Product%20Support")

i had a look at that site.
since the "fix" was like 2-3 years ago, and in about v7(or so), shouldn't it be in V10.04?
I could be misinterpreting because i have no idea what they mean by "Hardy" or "Gutsy" (and quite a few other things)

i also couldn't find my model on the site you suggested for the BIOS update, but i found it on the AUS website (I'm Aussie) --http://www.mytoshiba.com.au/support/notebooks/satellite/p100/pspa3a-01r00p/download--, but I'm not sure which download to use, there's a BIOS V4.7 for windows xp, and one for vista... do those not make any difference?

EDIT: some spelling stuff

---

### Post by lidex on 2010-05-22
> **Antaios said:**
> i had a look at that site.
since the "fix" was like 2-3 years ago, and in about v7(or so), shouldn't it be in V10.04?
I could be misinterpreting because i have no idea what they mean by "Hardy" or "Gutsy" (and quite a few other things)

i also couldn't find my model on the site you suggested for the BIOS update, but i found it on the AUS website (I'm Aussie) --http://www.mytoshiba.com.au/support/notebooks/satellite/p100/pspa3a-01r00p/download--, but I'm not sure which download to use, there's a BIOS V4.7 for windows xp, and one for vista... do those not make any difference?

EDIT: some spelling stuff
Select the one for the version of windows you use as that is where you will install it.

---

### Post by Antaios on 2010-05-22
Woo! i can't believe it was something so small and simple...

i logged in after the bios update and this time i heard the log-in sound out of the speakers, I'm still going to test some music files and other things, but all looking good, Thanks!

EDIT: checked videos on you tube and stuff, music files and other things, all working fine, thanks heaps guys

---

