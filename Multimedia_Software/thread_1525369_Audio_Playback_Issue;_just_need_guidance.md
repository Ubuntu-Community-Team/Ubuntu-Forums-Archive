---
title: "Audio Playback Issue; just need guidance"
date: 2010-07-06
forum: Multimedia Software
---

### Post by sw0rn on 2010-07-06
I apologize in advance as I know this is a well documented issue.  However, I've tried several (and then several more) of the solutions presented in the Comprehensive Sound Problem Solution Guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) and Comprehensive Media & HowTo [(http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")). 

I will continue to read through and apply any pertinent changes that I can find from these guides. But, perhaps someone can steer me in the correct direction based upon the following screenshot?

[IMG]http://www-personal.umd.umich.edu/%7Ezbridges/audioError.jpeg[/IMG]

Also, I will post the output from an lspci when I get my machine charged again. 
Note: I cannot recall or find the thread I was reading in which a command was used to output lspci information and then send this information to **alsa** (where I viewed the output on a webpage stored on the alsa website) -- any ideas what that command was that I used?

Thanks in advance to any/alll replies.

---

### Post by sw0rn on 2010-07-06
Followup: 

aplay -l & arecord -l output: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
sw0rn@blacktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```And the output for an lspci -v.
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, fast devsel, latency 0
    Memory at b0100000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 64000000-641fffff
    Prefetchable memory behind bridge: 0000000064200000-00000000643fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 64400000-645fffff
    Prefetchable memory behind bridge: 0000000064600000-00000000647fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 64800000-649fffff
    Prefetchable memory behind bridge: 0000000064a00000-0000000064bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 64c00000-64dfffff
    Prefetchable memory behind bridge: 0000000064e00000-0000000064ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=56
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: b0300000-b03fffff
    Prefetchable memory behind bridge: 0000000060000000-0000000063ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: medium devsel, IRQ 10
    I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1000
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at 64000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at 2000 [size=256]
    Memory at b0300000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 168, IRQ 20
    Memory at b0301000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
    Memory window 0: 60000000-63fff000 (prefetchable)
    Memory window 1: 68000000-6bfff000
    I/O window 0: 00002400-000024ff
    I/O window 1: 00002800-000028ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Acer Incorporated [ALI] Device 0102
    Flags: bus master, medium devsel, latency 57, IRQ 20
    Memory at b0302000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

0a:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device 0094
    Flags: bus master, medium devsel, latency 57, IRQ 20
    Memory at b0300400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

```I hope this can help steer someone in a direction to help me.

Also, I've been using 'kill -9 processName' to kill Amarok or Firefox, whichever one is holding up my sound at the time; if that helps.

Thanks again to any and all responses.

---

### Post by lidex on 2010-07-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by sw0rn on 2010-07-20
Please excuse the lack of timeliness in my response. My sound now works and duplexes between all my programs -- I attribute this to magic. However, here is the output requested:

```

usw0rn@blacktop:~$ uname -a
Linux blacktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
sw0rn@blacktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
sw0rn@blacktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                  1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
sw0rn@blacktop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054
sw0rn@blacktop:~$ 


```



MOD: Should I change the title of this thread to "SOLVED" even though there is no solution given in this thread?

---

