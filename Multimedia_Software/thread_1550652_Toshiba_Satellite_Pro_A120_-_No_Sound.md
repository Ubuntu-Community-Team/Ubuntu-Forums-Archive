---
title: "Toshiba Satellite Pro A120 - No Sound"
date: 2010-08-11
forum: Multimedia Software
---

### Post by df3n5 on 2010-08-11
Hi,

I'm running Xubuntu 10.04, and everything works fine except for the audio.
```

aoife@aoife-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm a bit worried about the Modem being on the same card, could this be causing the problem?

```

aoife@aoife-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: ffd00000-ffdfffff
	Prefetchable memory behind bridge: f0000000-f7ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: ffc00000-ffcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at bff8 [size=8]
	I/O ports at bff4 [size=4]
	I/O ports at bfe8 [size=8]
	I/O ports at bfe4 [size=4]
	I/O ports at bfa0 [size=16]
	Memory at ffaffe00 (32-bit, non-prefetchable) [size=512]
	Expansion ROM at ffa00000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at ffafe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at ffafd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at ffafc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: 66MHz, medium devsel
	I/O ports at d880 [size=16]
	Memory at 24004000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 88 [Master SecP])
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bf70 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at 24000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: ff900000-ff9fffff
	Prefetchable memory behind bridge: 20000000-23ffffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at ce00 [size=256]
	Memory at ffdf0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at ffd00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeonfb, radeon

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7106
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at ffcf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

03:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 168, IRQ 23
	Memory at ff900000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 28000000-2bfff000
	I/O window 0: 0000a000-0000a0ff
	I/O window 1: 0000a400-0000a4ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at ff901000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Device 0003
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at ae00 [size=256]
	Memory at ff9fff00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

```

I've tried the guide at [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and [http://https://help.ubuntu.com/community/HdaIntelSoundHowto]("http://https://help.ubuntu.com/community/HdaIntelSoundHowto") but to no avail. I've tried reinstalling alsa from sources but that didn't work. I've tried headphones and everything else I could think of. 

If anyone could point me in the right direction I would be grateful.

Thanks,
df3n5.

---

