---
title: "Sound stops working after 1-5 mins of playing sound"
date: 2010-12-14
forum: Multimedia Software
---

### Post by SoftwareExplorer on 2010-12-14
Playing a song works at first; then it quits after 1-5 minutes. If you select a different output device, it will work for another 1-5 minutes, but switching back to an already used up device will not play sound. Running 'sudo killall pulseaudio' resets everything and each output device works for another 1-5 minutes. 

This is on on 9.10.
```
lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: EPoX Computer Co., Ltd. Device 4002
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: e4000000-e5ffffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
	Subsystem: EPoX Computer Co., Ltd. Device 4002
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
	Subsystem: EPoX Computer Co., Ltd. Device 4002
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
	Subsystem: EPoX Computer Co., Ltd. Device 4002
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: EPoX Computer Co., Ltd. Device 4002
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at e6100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e6000000-e60fffff
	Prefetchable memory behind bridge: 20000000-200fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: EPoX Computer Co., Ltd. Device 4002
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 20100000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Subsystem: EPoX Computer Co., Ltd. Device 4002
	Flags: medium devsel, IRQ 5
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: EPoX Computer Co., Ltd. Device 4002
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e000 [size=256]
	I/O ports at e400 [size=64]
	Memory at e6101000 (32-bit, non-prefetchable) [size=512]
	Memory at e6102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Memory at d8000000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at d8080000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, rivafb

02:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: Linksys Device 0055
	Flags: bus master, slow devsel, latency 64, IRQ 19
	Memory at e6010000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: rt61pci

02:05.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
	Subsystem: EPoX Computer Co., Ltd. Device 3005
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at c000 [size=256]
	Memory at e6018000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 20000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine


```

---

### Post by SoftwareExplorer on 2011-01-06
Bump.

---

### Post by lidex on 2011-01-07
Need some more info please . Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by SoftwareExplorer on 2011-01-08
Ok, the link is [[COLOR="DeepSkyBlue"]http://www.alsa-project.org/db/?f=416b016654556a1ebac6ca112e930e6c4c43e7c9[/COLOR]]("http://www.alsa-project.org/db/?f=416b016654556a1ebac6ca112e930e6c4c43e7c9")

---

### Post by lidex on 2011-01-09
Wow that is an older kernel for sure. Have a walk through this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

BTW, any reason in particular you haven't upgraded? You can try a livecd of 
lucid or maverick to see if it works.

---

### Post by SoftwareExplorer on 2011-01-24
> **lidex said:**
> Wow that is an older kernel for sure. Have a walk through this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

BTW, any reason in particular you haven't upgraded? You can try a livecd of 
lucid or maverick to see if it works.

Ok, I upgraded it to 10.10. The problem still persists. The user of this computer noticed it's when you use the computer for other tasks that it stops. 
After trying this for myself with the system monitor, it appears that the sound stops about .5 sec before CPU usage hits 100% in the system monitor. I'm not sure if it is the sound system using up all the CPU, or if using all the CPU stops the sound and the system monitor display is just slightly delayed. The user discovered that if you change the sound output type to something else and then back again the sound will start.
I also noticed that if you are patient enough and wait long enough ~1-3 minutes, the sound will start again without any help.

---

### Post by lidex on 2011-01-25
What is the make and model of this computer?
Let's see what pulse is doing:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
And bios info:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

