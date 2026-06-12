---
title: "Inconsistent wi-fi"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by Lord Stig on 2009-11-13
Hi. I've had a problem with my wireless connection for months now and wouldn't know where to start.
I'm using Mint temporarily due to other problems I have with Xubuntu Karmic but the problems I have apply to both OSes (and Jaunty).
The issues may be related to my router (I just don't know - I'm pretty new to all this) but they are:
* almost totally inconsistent connections: will sometimes connect absolutely fine first time and stay connected for hours, other times refuse for hours. Usually leaving it till the next day gets the connection working for me!
* random periods of constant connections and drop outs
* most nights the connection will cut off between 1030pm and 1130pm. This happens on 90% of the days I use it. I cannot reconnect no matter how much I try if this happens - I have to leave it till the next day. It usually clears by morning (not today, though!)

Wired connections always work.

I've bought a pcmcia wifi card in the hope this will help (??) in case the wifi built in to my Toshiba Portege M100 is the problem. 

My question (at last): 
a) do you have any ideas and 
b) are there any commands I can type in to determine if it's my wi-fi in the laptop or the router itself?

Thanks in advance.

---

### Post by Lord Stig on 2009-11-14
Ok, well I have bought a Netgear WPN511 PCMCIA wireless card after checking the 'net for Linux support. I've downloaded the MadWifi driver and alkso the Windows driver. The two lights blink on and off in turn. I've searched through forums and seen similar problems setting up this card but they are either incomplete or I don't fully understand the instructions.

I can't understand the instructions bundled with MadWifi. If each command was tailored for me I could manage, but obviously they're not.All beyond my expertise and there wasn't a complete how to like there is with some wireless devices. Mint has a Windows Wireless Drivers utility and I loaded the Windows .inf driver file. When you start Windows Wireless Drivers, or if you attempt to change anything, the utility reports that it can't tell if the card is present or not. And yet the main screen of the utility reports the driver name and below this 'Hardware present: yes".

I'm confused.

---

### Post by Lord Stig on 2009-11-16
I've tried blacklisting ath5k (Madwifi driver) in case it was conflicting with my installed Windows driver. However, it's still being reported as the alternate driver.

Resorting to a wired connection for now...

80 people have taken the time to read my problem. Appreciate it is probably complex but can anyone help with any part of it or ask me for more info?

---

### Post by sanskaras on 2009-11-16
What's your built in wifi card?  Run lspci -v in the command line and post up the information about your network controller.

---

### Post by Lord Stig on 2009-11-17
Thanks for posting. Will get post info when I get home.
By the way, a live CD of Xubuntu Jaunty picked up the internal and PCMCIA wifi and for the first few attempts I got connection established but only for one or two seconds (nearly loaded a web page). It asks for my WPA key (which I input each time but it keeps changing to a very long string of what looks to me like hex when it next asks for the key).

I am happy to ditch Mint in favour of Xubuntu (I was using it before) if it makes everyone's life easier sorting this out?

---

### Post by Lord Stig on 2009-11-17
Hi. Output of 'lspci -v' here:
[INDENT][I]lspci -v
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Toshiba America Info Systems Device 0012
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Toshiba America Info Systems Device 0012
	Flags: fast devsel
	Memory at 30000000 (32-bit, prefetchable) [disabled] [size=128M]
	Memory at 40000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 18c0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 18e0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at 40080000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=07, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: cff00000-cfffffff
	Prefetchable memory behind bridge: 38000000-3fffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Memory at 40080400 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0243
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1000 [size=256]
	I/O ports at 1880 [size=64]
	Memory at 40080800 (32-bit, non-prefetchable) [size=512]
	Memory at 40080a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: medium devsel, IRQ 11
	I/O ports at 1400 [size=256]
	I/O ports at 1800 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at cff06000 (32-bit, non-prefetchable) [size=2K]
	Memory at cff00000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at cf40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100, eepro100

01:0a.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation Device 2581
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2100
	Kernel modules: ipw2100

01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
	Memory at cff04000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=03, sec-latency=0
	Memory window 0: 38000000-3bfff000 (prefetchable)
	Memory window 1: 44000000-47fff000
	I/O window 0: 0000c000-0000c0ff
	I/O window 1: 0000c400-0000c4ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

01:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
	Memory at cff05000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=04, subordinate=07, sec-latency=0
	Memory window 0: 3c000000-3ffff000 (prefetchable)
	Memory window 1: 48000000-4bfff000
	I/O window 0: 0000c800-0000c8ff
	I/O window 1: 0000cc00-0000ccff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

01:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: medium devsel, IRQ 255
	Memory at cff06800 (32-bit, non-prefetchable) [disabled] [size=512]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: Netgear Device 5d00
	Flags: bus master, fast Back2Back, medium devsel, latency 128, IRQ 11
	Memory at 44000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: ath_pci, ath5k[/I][/INDENT]

Thanks to anyone who can help.

---

### Post by sanskaras on 2009-11-18
I would try uninstalling ndiswrapper and getting the ath5k driver working for your atheros card first.

Heres a thread with some solutions, [http://ubuntuforums.org/showthread.php?t=1305812]("http://ubuntuforums.org/showthread.php?t=1305812")

Also, you can try this guide, says it's been tested on intrepid but just change linux-backports-modules-intrepid to linux-backports-modules-karmic and see if works.

---

### Post by Lord Stig on 2009-11-20
Thanks. I tried both but can't get it working. I've noticed wicd crashes sometimes as well! Not sure you posted the link to the guide.

I am thinking about installing Xubuntu tonight as it seems to 'see' various connections through this card, but failing that I'll wipe the whole hard drive, dust off my old and legitimate copy of XP, transfer the licence over and it'll no doubt work first time. I'd probably install Ubuntu after and use that when I don't need wifi on my laptop as haven't quite given up on Linux yet - I'm sure people are trying hard to get things to work and are stunted by proprietary code etc.

---

### Post by Lord Stig on 2009-11-20
Update: it works! Did a restart and it started working! wicd is using the wext driver (whatever that is) and I have a connection! I don't think it's using my PCMCIA card (the lights have gone off) but it does have a decent connection probably using the internal wi-fi, and I didn't have to get rid of Mint 7 XFCE!

Thanks to sanskaras for making this happen!

---

