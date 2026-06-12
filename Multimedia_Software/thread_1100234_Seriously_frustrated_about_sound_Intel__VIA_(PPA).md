---
title: "Seriously frustrated about sound: Intel / VIA (PPA)"
date: 2009-03-19
forum: Multimedia Software
---

### Post by stormzen on 2009-03-19
I can't begin to express how disappointed I am with the condition of sound in Ubuntu.  Due largely to sound being the number one issue that I've had with linux across all distros.  I really hope it's getting better... I've run linux for more than 8 years and spent 6+ without sound.  In Hardy, it looked like all of my problems were a thing of the past.  My SigmaTel STAC9271D Intel chip worked like a charm.  But that soon died with Intrepid, which ushered in a plethora of new sound issues.

I spent so much time 'fixing' the issue (over and over) with things that would work only until the next update, and randomly stop working after rebooting, that I got fed up and bought a new card, the simplest I could find, so that I wouldn't have this issue.  Guess what?  I now have two devices that aren't listed as compatible with ALSA.

My fault -- I didn't make sure that it worked with ALSA when I bought it.  I just thought with such a simple card, what could go wrong?  It even looked outdated... For the record, a PPA 1417v w/ VIA VT1723 ( Tremor ) chipset is not old ( [http://www.ppa-usa.com/products/soundcard/1431v.htm](http://www.ppa-usa.com/products/soundcard/1431v.htm) ).  Evidently, it's pretty new.

I even considered ditching ALSA and going with OSS4.1, as at least Intel ICH8 is listed in the supported hardware, there... but, alas, as unimportant as sound seems to be through my experience, ALSA is attached to everything...

I recognize that the problem is not the fault of the linux community, but I'm having such a horrible user experience with this, and it has lasted so long for me, that I want to be heard...  If anyone has any knowledge of why the situation is so bad, what happened between Gutsy and Intrepid, and most importantly, if it looks like it's going to get any better, I would be interested in hearing about it..

... ok, enough of that.

So, the symptom right now is that the speaker is turned all the way up, and I can hear only a faint beep when I go into the sound application (System/Preferences/Sound and Test for ALSA or ICE1724 (ALSA).  OSS isn't much better: I get a drop of static before the same results.)  Switching to the on-board sound chip (Intel ICH8) yields loud and constant static.

Here are the system details:


> cat lspci_2009_mar_18.txt 
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 50000000-51ffffff
	Prefetchable memory behind bridge: 0000000040000000-000000004fffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 52205100 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: heci
	Kernel modules: heci

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 40c0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 40a0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at 52204c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Intel Corporation Device 2504
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 52200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: 52300000-523fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 52100000-521fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: 52400000-524fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: 52500000-525fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: 52600000-526fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 4080 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 4060 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 4040 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 52204800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 52000000-520fffff
	Prefetchable memory behind bridge: 0000000052700000-00000000527fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 217
	I/O ports at 40e8 [size=8]
	I/O ports at 40f4 [size=4]
	I/O ports at 40e0 [size=8]
	I/O ports at 40f0 [size=4]
	I/O ports at 4020 [size=32]
	Memory at 52204000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Intel Corporation Device 514d
	Flags: medium devsel, IRQ 9
	Memory at 52205000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 4000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
	Subsystem: Giga-byte Technology Device 341a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 51000000 (32-bit, non-prefetchable) [size=16M]
	Memory at 40000000 (64-bit, prefetchable) [size=256M]
	Memory at 50000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at 3000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 2018 [size=8]
	I/O ports at 2024 [size=4]
	I/O ports at 2010 [size=8]
	I/O ports at 2020 [size=4]
	I/O ports at 2000 [size=16]
	Memory at 52100000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: pata_marvell
	Kernel modules: pata_marvell

07:00.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Subsystem: Artx Inc Device 2403
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at 1180 [size=32]
	I/O ports at 1100 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ICE1724
	Kernel modules: snd-ice1724

07:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
	Subsystem: Netgear Device 311a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 1000 [size=256]
	Memory at 52004800 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 52700000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Intel Corporation Device 514d
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at 52004000 (32-bit, non-prefetchable) [size=2K]
	Memory at 52000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

(and alsa-info):

[http://www.alsa-project.org/db/?f=6a2f8d7e0076328ea019e51cb71ac48ba0b74ef6](http://www.alsa-project.org/db/?f=6a2f8d7e0076328ea019e51cb71ac48ba0b74ef6)

---

### Post by markbuntu on 2009-03-19
Well, this is your sound card
```

07:00.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
Subsystem: Artx Inc Device 2403
Flags: bus master, medium devsel, latency 32, IRQ 21
I/O ports at 1180 [size=32]
I/O ports at 1100 [size=128]
Capabilities: <access denied>
Kernel driver in use: ICE1724
Kernel modules: snd-ice1724

```
This is what is listed in /usr/share/doc/alsa-base about that
```

 Module snd-ice1724
  ------------------

    Module for Envy24HT (VT/ICE1724), Envy24PT (VT1720) based PCI sound cards.
			* MidiMan M Audio Revolution 5.1
			* MidiMan M Audio Revolution 7.1
			* MidiMan M Audio Audiophile 192
			* AMP Ltd AUDIO2000
			* TerraTec Aureon 5.1 Sky
			* TerraTec Aureon 7.1 Space
			* TerraTec Aureon 7.1 Universe
			* TerraTec Phase 22
			* TerraTec Phase 28
			* AudioTrak Prodigy 7.1
			* AudioTrak Prodigy 7.1LT
			* AudioTrak Prodigy 192
			* Pontis MS300
			* Albatron K8X800 Pro II 
			* Chaintech ZNF3-150
			* Chaintech ZNF3-250
			* Chaintech 9CJS
			* Chaintech AV-710
			* Shuttle SN25P
			* Onkyo SE-90PCI
			* Onkyo SE-200PCI

    model       - Use the given board model, one of the following:
		  revo51, revo71, amp2000, prodigy71, prodigy71lt,
		  prodigy192, aureon51, aureon71, universe, ap192,
		  k8x800, phase22, phase28, ms300, av710, se200pci,
		  se90pci

    This module supports multiple cards and autoprobe.

    Note: The supported board is detected by reading EEPROM or PCI
	  SSID (if EEPROM isn't available).  You can override the
	  model by passing "model" module option in case that the
	  driver isn't configured properly or you want to try another
	  type for testing.

```
You need to get the alsa-tools-gui to get the control tool for the Envy24.



This is your on-board sound chip
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
Subsystem: Intel Corporation Device 2504
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at 52200000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

```

The snd-hda-intel has a zillion options that are all very machine specific. You can read about that here along with some basic troubleshooting and configuration help


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

