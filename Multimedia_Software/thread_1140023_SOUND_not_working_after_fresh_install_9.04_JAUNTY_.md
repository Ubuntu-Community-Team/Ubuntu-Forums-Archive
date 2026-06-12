---
title: "SOUND not working after fresh install 9.04 JAUNTY 64bit"
date: 2009-04-27
forum: Multimedia Software
---

### Post by davidfdr on 2009-04-27
Hi!

Notebook model: GATEWAY P-6831FX SERIES / 4gb RAM / 500HD RAID0 Stripe / 8800 M GTS Video / IDT HDA Intel SOUND CARD.

UBUNTU 9.04 JAUNTY 64bit


Apears that ubuntu detected my sound card, but no sound is played on the speakers.

On the SOUND PREFERENCES I tested all options displayed on the tabs (SYSTEM > SOUND PREFERENCES) and no sound was played.

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800M GTS (rev a2)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

```

lspci -v
```

root@gamer:~# lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Gateway 2000 Device 0690
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f4604800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: f4000000-f40fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 0690
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f4100000-f41fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 0690
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f4200000-f42fffff
	Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 0690
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 0690
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: f2000000-f3ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 0690
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f4604c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
	Memory behind bridge: f4300000-f43fffff
	Capabilities: [50] Subsystem: Gateway 2000 Device 0690

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2297
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f4604000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: medium devsel, IRQ 10
	Memory at c2100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800M GTS (rev a2)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1100
	Flags: bus master, fast devsel, latency 0, IRQ 2295
	Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 65-95-45-ff-ff-e0-1d-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f4102000 (64-bit, non-prefetchable) [size=128]
	Memory at f4100000 (64-bit, non-prefetchable) [size=8K]
	I/O ports at 3000 [size=128]
	Capabilities: [54] Power Management version 2
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: sata_sil24

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, fast devsel, latency 0, IRQ 2296
	I/O ports at 4000 [size=256]
	Memory at f4200000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data <?>
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] Express Endpoint, MSI 00
	Capabilities: [84] Vendor Specific Information <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [12c] Virtual Channel <?>
	Capabilities: [148] Device Serial Number 68-81-ec-10-00-00-00-21
	Capabilities: [154] Power Budgeting <?>
	Kernel driver in use: r8169
	Kernel modules: r8169

0c:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
	Subsystem: Agere Systems FW323
	Flags: bus master, fast Back2Back, medium devsel, latency 96, IRQ 16
	Memory at f4300000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

```


aplay -l
```

root@gamer:~# aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Dispositivo secundÃ¡rio: 1/1
  Dispositivo secundÃ¡rio #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
  Dispositivo secundÃ¡rio: 1/1
  Dispositivo secundÃ¡rio #0: subdevice #0
root@gamer:~# 

```


On ubuntu 8.04/8.10 everything worked FINE (64bit too)

---

### Post by The Mad Mule on 2009-04-27
Join the club. At least it works through the headphone jack.

---

### Post by redenex on 2009-04-27
> **The Mad Mule said:**
> Join the club.

:lolflag:

---

### Post by davidfdr on 2009-04-27
> **The Mad Mule said:**
> Join the club. At least it works through the headphone jack.

:lolflag:

Really, my sound just works with tje headphone jack.

Does not work with the speakers / digital output or HDMI.

Anybody knows hows to fix it?

---

### Post by davidfdr on 2009-04-27
After reading the following thread:
[http://ubuntuforums.org/showthread.php?p=7163503#post7163503](http://ubuntuforums.org/showthread.php?p=7163503#post7163503)

I´ve managed to solve the problem with some issues, but now I´m able to hear something from my laptop speakers.

I´ve edited the file: /etc/modprobe.d/alsa-base.conf
 And I put the following lines:

```

options snd-hda-intel model=laptop enable=1 index=0
options snd-hda-intel enable_msi=1

```

Worked too with

```

options snd-hda-intel model=stac92xx enable=1 index=0
options snd-hda-intel enable_msi=1

```

BUT the playback level still very low. Anybody has any hint to rise the sound volume? My sound level is on maximum, but still low.

My notebook model is a GATEWAY P-6831FX Series.

I still need to test the HDMI output.

---

### Post by The Mad Mule on 2009-04-27
Congrats on making it work. Have you typed "alsamixer -c0" into the Terminal? Maybe something is low in volume there. For what it's worth, no sound comes out of Ubuntu until you're at around 70%, and then it ramps up *very* quickly to 100%. I have the exact Gateway laptop model as you. :)

When I tested the HDMI output on 9.04 beta, it worked fine for me. You just need to raise the Digital-1 volume level (you may hve to dig a little bit to find it) all the way, then control the volume level on the TV.

---

### Post by Askar450 on 2009-08-05
Hello, I have the same laptop as you but your commands aren't working for me :/ both laptop and stac92... I've gone to Alsamixer nothing is muted (or I believe) any advice?

---

