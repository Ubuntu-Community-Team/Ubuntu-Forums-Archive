---
title: "No sound on Ubuntu 8.10"
date: 2008-12-15
forum: Multimedia Software
---

### Post by mxjosh on 2008-12-15
Hello, I am new to Linux/Ubuntu and i am having a sound problem. I have been searching forums and google for a few hours now trying various methods of troubleshooting for my problem without success. I have no sounds at all, no system sounds, in-game, or startup sounds. I still have sound on my windows xp platform too. Any help would be apreciated!

---

### Post by linux_tech on 2008-12-15
Does your card list in lspci?
In terminal type:
```
lspci
```
```
aplay -l
```

Here is a good reference for troubleshooting sound-
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by mxjosh on 2008-12-15
Thank you for your quick reply, Here are my Results:
josh@josh-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)

And 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
josh@josh-desktop:~$ 

Thanks in advance!

Okay i have read the great tutorial you linked me too and i am stuck, I went [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel) and was trying to see if my soundcard was supported but the family my soundcard belongs too (ICH8 Family) is not listed. Does the mean im out of luck?

---

### Post by linux_tech on 2008-12-15
Pls also post output of 
```
lspci -v
cat /proc/asound/cards
alsamixer
lsmod | grep snd
arecord -l
amixer info
amixer controls
amixer scontrols
amixer contents
dmesg | grep intel 
```

System->Preferences->Sound &#8211; test sound playback- has no sounds?

---

### Post by mxjosh on 2008-12-15
Thanks once again for the fast reply, I went into sounds and did the test sound playback, no sound was played. Here are the results from the tests.

josh@josh-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dd000000-dfefffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at dffe0000 (32-bit, non-prefetchable) [size=128K]
	Memory at dffdb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ecc0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Dell Device 01dd
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at dffdac00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: dcf00000-dcffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Dell Device 01dd
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 221
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fec0 [size=32]
	Memory at ff970000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Dell Device 01dd
	Flags: medium devsel, IRQ 10
	Memory at dffdab00 (32-bit, non-prefetchable) [size=256]
	I/O ports at ece0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
	Subsystem: Device 19f1:2207
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at de000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at dc80 [size=128]
	[virtual] Expansion ROM at dfe00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

josh@josh-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdffdc000 irq 16
josh@josh-desktop:~$ alsamixer

josh@josh-desktop:~$

---

### Post by linux_tech on 2008-12-15
also pls post
```
lspci -n
```

---

### Post by mxjosh on 2008-12-15
As always thanks for the quick reply!

josh@josh-desktop:~$ lspci -n
00:00.0 0600: 8086:29a0 (rev 02)
00:01.0 0604: 8086:29a1 (rev 02)
00:19.0 0200: 8086:104c (rev 02)
00:1a.0 0c03: 8086:2834 (rev 02)
00:1a.1 0c03: 8086:2835 (rev 02)
00:1a.7 0c03: 8086:283a (rev 02)
00:1b.0 0403: 8086:284b (rev 02)
00:1c.0 0604: 8086:283f (rev 02)
00:1d.0 0c03: 8086:2830 (rev 02)
00:1d.1 0c03: 8086:2831 (rev 02)
00:1d.2 0c03: 8086:2832 (rev 02)
00:1d.7 0c03: 8086:2836 (rev 02)
00:1e.0 0604: 8086:244e (rev f2)
00:1f.0 0601: 8086:2812 (rev 02)
00:1f.2 0104: 8086:2822 (rev 02)
00:1f.3 0c05: 8086:283e (rev 02)
01:00.0 0300: 10de:0295 (rev a1)

---

### Post by linux_tech on 2008-12-15
Your audio device is listed as compatible.
Please post output of
```
dmesg | grep intel
```
```
dmesg | grep alsa
```

---

### Post by mxjosh on 2008-12-15
hmm, i copied the code you gave me into the terminal and i got nothing back, am i doing something wrong?

---

### Post by linux_tech on 2008-12-15
Nope how about ```
dmesg
```
Also did ```
amixer info
```
return anything?

---

### Post by mxjosh on 2008-12-15
ah there we go! :) Its a long one though...

[    0.761547] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.761547] pci 0000:00:1c.0: PME# disabled
[    0.761547] PCI: 0000:00:1d.0 reg 20 io port: [ff80, ff9f]
[    0.761547] PCI: 0000:00:1d.1 reg 20 io port: [ff60, ff7f]
[    0.761547] PCI: 0000:00:1d.2 reg 20 io port: [ff40, ff5f]
[    0.761547] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ff980800, ff980bff]
[    0.761547] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.761547] pci 0000:00:1d.7: PME# disabled
[    0.761547] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.761547] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.761547] PCI: 0000:00:1f.2 reg 10 io port: [fe00, fe07]
[    0.761547] PCI: 0000:00:1f.2 reg 14 io port: [fe10, fe13]
[    0.761547] PCI: 0000:00:1f.2 reg 18 io port: [fe20, fe27]
[    0.761547] PCI: 0000:00:1f.2 reg 1c io port: [fe30, fe33]
[    0.761547] PCI: 0000:00:1f.2 reg 20 io port: [fec0, fedf]
[    0.761547] PCI: 0000:00:1f.2 reg 24 32bit mmio: [ff970000, ff9707ff]
[    0.761547] pci 0000:00:1f.2: PME# supported from D3hot
[    0.761547] pci 0000:00:1f.2: PME# disabled
[    0.761547] PCI: 0000:00:1f.3 reg 10 32bit mmio: [dffdab00, dffdabff]
[    0.761547] PCI: 0000:00:1f.3 reg 20 io port: [ece0, ecff]
[    0.761547] PCI: 0000:01:00.0 reg 10 32bit mmio: [dd000000, ddffffff]
[    0.761547] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, cfffffff]
[    0.761547] PCI: 0000:01:00.0 reg 1c 64bit mmio: [de000000, deffffff]
[    0.761547] PCI: 0000:01:00.0 reg 24 io port: [dc80, dcff]
[    0.761547] PCI: 0000:01:00.0 reg 30 32bit mmio: [dfe00000, dfe1ffff]
[    0.764037] PCI: bridge 0000:00:01.0 io port: [d000, dfff]
[    0.764040] PCI: bridge 0000:00:01.0 32bit mmio: [dd000000, dfefffff]
[    0.764045] PCI: bridge 0000:00:01.0 64bit mmio pref: [c0000000, cfffffff]
[    0.764084] PCI: bridge 0000:00:1c.0 32bit mmio: [dcf00000, dcffffff]
[    0.764133] pci 0000:00:1e.0: transparent bridge
[    0.764153] bus 00 -> node 0
[    0.764159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.765039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.765625] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.766132] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    1.690052] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    1.690052] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.692420] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    1.693193] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    1.693960] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.694735] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.695517] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.696294] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    1.696508] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.696508] pnp: PnP ACPI init
[    1.696508] ACPI: bus type pnp registered
[    1.707308] pnp 00:01: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    1.707311] pnp 00:01: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    1.737799] pnp: PnP ACPI: found 9 devices
[    1.737799] ACPI: ACPI bus type pnp unregistered
[    1.737799] PnPBIOS: Disabled by ACPI PNP
[    1.740054] PCI: Using ACPI for IRQ routing
[    1.744041] NET: Registered protocol family 8
[    1.744045] NET: Registered protocol family 20
[    1.744067] NetLabel: Initializing
[    1.744067] NetLabel:  domain hash size = 128
[    1.744067] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.744076] NetLabel:  unlabeled traffic allowed by default
[    1.744082] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.744088] hpet0: 3 64-bit timers, 14318180 Hz
[    1.746800] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.746803]    actual entries 65620
[    1.746891] AppArmor: AppArmor Filesystem Enabled
[    1.746910] ACPI: RTC can wake from S4
[    1.748042] Switched to high resolution mode on CPU 0
[    1.748542] Switched to high resolution mode on CPU 1
[    1.752067] system 00:01: ioport range 0xc00-0xc7f has been reserved
[    1.752080] system 00:06: iomem range 0x0-0x9ffff could not be reserved
[    1.752084] system 00:06: iomem range 0x100000-0xffffff could not be reserved
[    1.752088] system 00:06: iomem range 0x1000000-0xbfe51bff could not be reserved
[    1.752091] system 00:06: iomem range 0xf0000-0xfffff could not be reserved
[    1.752095] system 00:06: iomem range 0xc0000-0xd7fff could not be reserved
[    1.752099] system 00:06: iomem range 0xfec00000-0xfecfffff could not be reserved
[    1.752103] system 00:06: iomem range 0xfee00000-0xfeefffff could not be reserved
[    1.752107] system 00:06: iomem range 0xffb00000-0xffbfffff could not be reserved
[    1.752111] system 00:06: iomem range 0xffc00000-0xffffffff could not be reserved
[    1.752118] system 00:07: ioport range 0x100-0x1fe has been reserved
[    1.752122] system 00:07: ioport range 0x200-0x277 has been reserved
[    1.752126] system 00:07: ioport range 0x280-0x2e7 has been reserved
[    1.752129] system 00:07: ioport range 0x2e8-0x2ef has been reserved
[    1.752133] system 00:07: ioport range 0x2f0-0x2f7 has been reserved
[    1.752136] system 00:07: ioport range 0x2f8-0x2ff has been reserved
[    1.752140] system 00:07: ioport range 0x300-0x377 has been reserved
[    1.752143] system 00:07: ioport range 0x380-0x3bb has been reserved
[    1.752147] system 00:07: ioport range 0x3c0-0x3e7 could not be reserved
[    1.752150] system 00:07: ioport range 0x3f6-0x3f7 has been reserved
[    1.752154] system 00:07: ioport range 0x400-0x4cf has been reserved
[    1.752157] system 00:07: ioport range 0x4d2-0x57f has been reserved
[    1.752161] system 00:07: ioport range 0x580-0x677 has been reserved
[    1.752164] system 00:07: ioport range 0x680-0x777 has been reserved
[    1.752168] system 00:07: ioport range 0x780-0x7bb has been reserved
[    1.752171] system 00:07: ioport range 0x7c0-0x7ff has been reserved
[    1.752175] system 00:07: ioport range 0x8e0-0x8ff has been reserved
[    1.752178] system 00:07: ioport range 0x900-0x9fe has been reserved
[    1.752182] system 00:07: ioport range 0xa00-0xafe has been reserved
[    1.752186] system 00:07: ioport range 0xb00-0xbfe has been reserved
[    1.752189] system 00:07: ioport range 0xc80-0xcaf has been reserved
[    1.752193] system 00:07: ioport range 0xcb0-0xcbf has been reserved
[    1.752196] system 00:07: ioport range 0xcc0-0xcf7 has been reserved
[    1.752200] system 00:07: ioport range 0xd00-0xdfe has been reserved
[    1.752204] system 00:07: ioport range 0xe00-0xefe has been reserved
[    1.752207] system 00:07: ioport range 0xf00-0xffe has been reserved
[    1.752211] system 00:07: ioport range 0x2000-0x20fe has been reserved
[    1.752215] system 00:07: ioport range 0x2100-0x21fe has been reserved
[    1.752218] system 00:07: ioport range 0x2200-0x22fe has been reserved
[    1.752222] system 00:07: ioport range 0x2300-0x23fe has been reserved
[    1.752226] system 00:07: ioport range 0x2400-0x24fe has been reserved
[    1.752230] system 00:07: ioport range 0x2500-0x25fe has been reserved
[    1.752233] system 00:07: ioport range 0x2600-0x26fe has been reserved
[    1.752237] system 00:07: ioport range 0x2700-0x27fe has been reserved
[    1.752241] system 00:07: ioport range 0x2800-0x28fe has been reserved
[    1.752245] system 00:07: ioport range 0x2900-0x29fe has been reserved
[    1.752248] system 00:07: ioport range 0x2a00-0x2afe has been reserved
[    1.752252] system 00:07: ioport range 0x2b00-0x2bfe has been reserved
[    1.752256] system 00:07: ioport range 0x2c00-0x2cfe has been reserved
[    1.752260] system 00:07: ioport range 0x2d00-0x2dfe has been reserved
[    1.752263] system 00:07: ioport range 0x2e00-0x2efe has been reserved
[    1.752267] system 00:07: ioport range 0x2f00-0x2ffe has been reserved
[    1.752271] system 00:07: ioport range 0x5000-0x50fe has been reserved
[    1.752274] system 00:07: ioport range 0x5100-0x51fe has been reserved
[    1.752278] system 00:07: ioport range 0x5200-0x52fe has been reserved
[    1.752282] system 00:07: ioport range 0x5300-0x53fe has been reserved
[    1.752296] system 00:07: ioport range 0x5400-0x54fe has been reserved
[    1.752299] system 00:07: ioport range 0x5500-0x55fe has been reserved
[    1.752302] system 00:07: ioport range 0x5600-0x56fe has been reserved
[    1.752305] system 00:07: ioport range 0x5700-0x57fe has been reserved
[    1.752308] system 00:07: ioport range 0x5800-0x58fe has been reserved
[    1.752310] system 00:07: ioport range 0x5900-0x59fe has been reserved
[    1.752313] system 00:07: ioport range 0x5a00-0x5afe has been reserved
[    1.752316] system 00:07: ioport range 0x5b00-0x5bfe has been reserved
[    1.752319] system 00:07: ioport range 0x5c00-0x5cfe has been reserved
[    1.752322] system 00:07: ioport range 0x5d00-0x5dfe has been reserved
[    1.752325] system 00:07: ioport range 0x5e00-0x5efe has been reserved
[    1.752328] system 00:07: ioport range 0x5f00-0x5ffe has been reserved
[    1.752330] system 00:07: ioport range 0x6000-0x60fe has been reserved
[    1.752333] system 00:07: ioport range 0x6100-0x61fe has been reserved
[    1.752336] system 00:07: ioport range 0x6200-0x62fe has been reserved
[    1.752339] system 00:07: ioport range 0x6300-0x63fe has been reserved
[    1.752342] system 00:07: ioport range 0x6400-0x64fe has been reserved
[    1.752345] system 00:07: ioport range 0x6500-0x65fe has been reserved
[    1.752348] system 00:07: ioport range 0x6600-0x66fe has been reserved
[    1.752351] system 00:07: ioport range 0x6700-0x67fe has been reserved
[    1.752354] system 00:07: ioport range 0x6800-0x68fe has been reserved
[    1.752356] system 00:07: ioport range 0x6900-0x69fe has been reserved
[    1.752363] system 00:07: ioport range 0x6a00-0x6afe has been reserved
[    1.752366] system 00:07: ioport range 0x6b00-0x6bfe has been reserved
[    1.752369] system 00:07: ioport range 0x6c00-0x6cfe has been reserved
[    1.752372] system 00:07: ioport range 0x6d00-0x6dfe has been reserved
[    1.752375] system 00:07: ioport range 0x6e00-0x6efe has been reserved
[    1.752377] system 00:07: ioport range 0x6f00-0x6ffe has been reserved
[    1.752380] system 00:07: ioport range 0xa000-0xa0fe has been reserved
[    1.752383] system 00:07: ioport range 0xa100-0xa1fe has been reserved
[    1.752386] system 00:07: ioport range 0xa200-0xa2fe has been reserved
[    1.752389] system 00:07: ioport range 0xa300-0xa3fe has been reserved
[    1.752392] system 00:07: ioport range 0xa400-0xa4fe has been reserved
[    1.752395] system 00:07: ioport range 0xa500-0xa5fe has been reserved
[    1.752398] system 00:07: ioport range 0xa600-0xa6fe has been reserved
[    1.752401] system 00:07: ioport range 0xa700-0xa7fe has been reserved
[    1.752404] system 00:07: ioport range 0xa800-0xa8fe has been reserved
[    1.752408] system 00:07: ioport range 0xa900-0xa9fe has been reserved
[    1.752411] system 00:07: ioport range 0xaa00-0xaafe has been reserved
[    1.752414] system 00:07: ioport range 0xab00-0xabfe has been reserved
[    1.752417] system 00:07: ioport range 0xac00-0xacfe has been reserved
[    1.752420] system 00:07: ioport range 0xad00-0xadfe has been reserved
[    1.752423] system 00:07: ioport range 0xae00-0xaefe has been reserved
[    1.752426] system 00:07: ioport range 0xaf00-0xaffe has been reserved
[    1.752429] system 00:07: iomem range 0xe0000000-0xefffffff could not be reserved
[    1.752432] system 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved
[    1.787517] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.787521] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    1.787524] pci 0000:00:01.0:   MEM window: 0xdd000000-0xdfefffff
[    1.787528] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.787532] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.787534] pci 0000:00:1c.0:   IO window: disabled
[    1.787539] pci 0000:00:1c.0:   MEM window: 0xdcf00000-0xdcffffff
[    1.787543] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.787548] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    1.787550] pci 0000:00:1e.0:   IO window: disabled
[    1.787555] pci 0000:00:1e.0:   MEM window: disabled
[    1.787558] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.787570] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.787574] pci 0000:00:01.0: setting latency timer to 64
[    1.787581] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.787585] pci 0000:00:1c.0: setting latency timer to 64
[    1.787591] pci 0000:00:1e.0: setting latency timer to 64
[    1.787594] bus: 00 index 0 io port: [0, ffff]
[    1.787596] bus: 00 index 1 mmio: [0, ffffffff]
[    1.787598] bus: 01 index 0 io port: [d000, dfff]
[    1.787600] bus: 01 index 1 mmio: [dd000000, dfefffff]
[    1.787602] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    1.787604] bus: 01 index 3 mmio: [0, 0]
[    1.787606] bus: 02 index 0 mmio: [0, 0]
[    1.787607] bus: 02 index 1 mmio: [dcf00000, dcffffff]
[    1.787609] bus: 02 index 2 mmio: [0, 0]
[    1.787611] bus: 02 index 3 mmio: [0, 0]
[    1.787613] bus: 03 index 0 mmio: [0, 0]
[    1.787615] bus: 03 index 1 mmio: [0, 0]
[    1.787616] bus: 03 index 2 mmio: [0, 0]
[    1.787618] bus: 03 index 3 io port: [0, ffff]
[    1.787620] bus: 03 index 4 mmio: [0, ffffffff]
[    1.787627] NET: Registered protocol family 2
[    1.800093] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.800363] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.800750] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.800976] TCP: Hash tables configured (established 131072 bind 65536)
[    1.800979] TCP reno registered
[    1.808138] NET: Registered protocol family 1
[    1.808265] checking if image is initramfs... it is
[    2.448704] Freeing initrd memory: 7993k freed
[    2.449037] Simple Boot Flag at 0x7a set to 0x1
[    2.449829] audit: initializing netlink socket (disabled)
[    2.449852] type=2000 audit(1229363072.448:1): initialized
[    2.455382] highmem bounce pool size: 64 pages
[    2.455388] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.457730] VFS: Disk quotas dquot_6.5.1
[    2.457813] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.457916] msgmni has been set to 1725
[    2.458037] io scheduler noop registered
[    2.458040] io scheduler anticipatory registered
[    2.458043] io scheduler deadline registered
[    2.458053] io scheduler cfq registered (default)
[    2.458179] pci 0000:01:00.0: Boot video device
[    2.458274] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    2.458307] pcieport-driver 0000:00:01.0: found MSI capability
[    2.458334] pci_express 0000:00:01.0:pcie00: allocate port service
[    2.458377] pci_express 0000:00:01.0:pcie03: allocate port service
[    2.458459] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.458490] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.458521] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.458563] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.458603] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.458914] isapnp: Scanning for PnP cards...
[    2.811701] isapnp: No Plug & Play device found
[    2.843244] hpet_resources: 0xfed00000 is busy
[    2.843294] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.845451] brd: module loaded
[    2.845516] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.845683] PNP: No PS/2 controller found. Probing ports directly.
[    2.848201] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.848207] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.848461] mice: PS/2 mouse device common for all mice
[    2.848581] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.848601] rtc0: alarms up to one day, hpet irqs
[    2.848726] EISA: Probing bus 0 at eisa.0
[    2.848729] EISA: Cannot allocate resource for mainboard
[    2.848735] Cannot allocate resource for EISA slot 2
[    2.848744] Cannot allocate resource for EISA slot 5
[    2.848746] Cannot allocate resource for EISA slot 6
[    2.848755] EISA: Detected 0 cards.
[    2.848758] cpuidle: using governor ladder
[    2.848760] cpuidle: using governor menu
[    2.849250] TCP cubic registered
[    2.849275] Using IPI No-Shortcut mode
[    2.849442] registered taskstats version 1
[    2.849565]   Magic number: 4:651:744
[    2.849654] rtc_cmos 00:05: setting system clock to 2008-12-15 17:44:33 UTC (1229363073)
[    2.849657] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.849659] EDD information not available.
[    2.849905] Freeing unused kernel memory: 424k freed
[    2.849940] Write protecting the kernel text: 2576k
[    2.849963] Write protecting the kernel read-only data: 936k
[    2.994013] fuse init (API version 7.9)
[    3.052973] processor ACPI0007:00: registered as cooling_device0
[    3.053047] processor ACPI0007:01: registered as cooling_device1
[    3.160428] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    3.160431] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    3.160467] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.160475] e1000e 0000:00:19.0: setting latency timer to 64
[    3.250484] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:07:6d:3a
[    3.250488] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    3.250510] 0000:00:19.0: eth0: MAC: 4, PHY: 7, PBA No: 1021ff-0ff
[    3.291641] usbcore: registered new interface driver usbfs
[    3.291663] usbcore: registered new interface driver hub
[    3.291699] usbcore: registered new device driver usb
[    3.294239] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.294250] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.294253] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.294293] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.298204] ehci_hcd 0000:00:1a.7: debug port 1
[    3.298209] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.298221] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xdffdac00
[    3.304059] USB Universal Host Controller Interface driver v3.0
[    3.312009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.312135] usb usb1: configuration #1 chosen from 1 choice
[    3.312162] hub 1-0:1.0: USB hub found
[    3.312170] hub 1-0:1.0: 4 ports detected
[    3.385564] No dock devices found.
[    3.399606] SCSI subsystem initialized
[    3.416238] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.416249] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.416253] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.416276] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[    3.416307] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[    3.416398] usb usb2: configuration #1 chosen from 1 choice
[    3.416424] hub 2-0:1.0: USB hub found
[    3.416432] hub 2-0:1.0: 2 ports detected
[    3.423086] libata version 3.00 loaded.
[    3.520261] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.520274] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.520278] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.520304] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[    3.520334] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
[    3.520424] usb usb3: configuration #1 chosen from 1 choice
[    3.520449] hub 3-0:1.0: USB hub found
[    3.520456] hub 3-0:1.0: 2 ports detected
[    3.624267] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.624286] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.624290] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.624317] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.628231] ehci_hcd 0000:00:1d.7: debug port 1
[    3.628237] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.628250] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff980800
[    3.644027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.644198] usb usb4: configuration #1 chosen from 1 choice
[    3.644234] hub 4-0:1.0: USB hub found
[    3.644243] hub 4-0:1.0: 6 ports detected
[    3.852212] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.852224] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.852228] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.852268] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.852292] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff80
[    3.852373] usb usb5: configuration #1 chosen from 1 choice
[    3.852397] hub 5-0:1.0: USB hub found
[    3.852404] hub 5-0:1.0: 2 ports detected
[    3.956195] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.956203] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.956207] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.956238] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.956262] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[    3.956353] usb usb6: configuration #1 chosen from 1 choice
[    3.956380] hub 6-0:1.0: USB hub found
[    3.956386] hub 6-0:1.0: 2 ports detected
[    4.164202] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.164210] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.164214] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.164244] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.164285] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    4.164370] usb usb7: configuration #1 chosen from 1 choice
[    4.164396] hub 7-0:1.0: USB hub found
[    4.164402] hub 7-0:1.0: 2 ports detected
[    4.268305] ahci 0000:00:1f.2: version 3.0
[    4.268320] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    4.268426] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x33 impl RAID mode
[    4.268429] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    4.268434] ahci 0000:00:1f.2: setting latency timer to 64
[    4.268690] scsi0 : ahci
[    4.270090] scsi1 : ahci
[    4.270158] scsi2 : ahci
[    4.270220] scsi3 : ahci
[    4.270276] scsi4 : ahci
[    4.270333] scsi5 : ahci
[    4.270380] ata1: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970100 irq 221
[    4.270383] ata2: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970180 irq 221
[    4.270386] ata3: DUMMY
[    4.270387] ata4: DUMMY
[    4.270389] ata5: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970300 irq 221
[    4.270392] ata6: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970380 irq 221
[    4.276028] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    4.448439] usb 6-1: configuration #1 chosen from 1 choice
[    4.560037] usb 6-2: new low speed USB device using uhci_hcd and address 3
[    4.588038] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.588591] ata1.00: ATA-7: WDC WD2500JS-75NCB3, 10.02E04, max UDMA/133
[    4.588594] ata1.00: 488281250 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.589213] ata1.00: configured for UDMA/133
[    4.736665] usb 6-2: configuration #1 chosen from 1 choice
[    4.739496] usbcore: registered new interface driver hiddev
[    4.754639] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input1
[    4.754869] input,hidraw0: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:1d.1-1
[    4.779788] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input2
[    4.780071] input,hiddev96,hidraw1: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:1d.1-1
[    4.795608] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input3
[    4.795831] input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2
[    4.795849] usbcore: registered new interface driver usbhid
[    4.795853] usbhid: v2.6:USB HID core driver
[    5.328030] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.361454] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H553A, DE04, max UDMA/33
[    5.361458] ata2.00: applying bridge limits
[    5.395307] ata2.00: configured for UDMA/33
[    5.728035] ata5: SATA link down (SStatus 0 SControl 300)
[    6.064037] ata6: SATA link down (SStatus 0 SControl 300)
[    6.080146] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JS-75N 10.0 PQ: 0 ANSI: 5
[    6.081782] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H553A DE04 PQ: 0 ANSI: 5
[    6.090343] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.090381] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    6.104842] Driver 'sr' needs updating - please use bus_type methods
[    6.109739] Driver 'sd' needs updating - please use bus_type methods
[    6.109824] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
[    6.109841] sd 0:0:0:0: [sda] Write Protect is off
[    6.109844] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.109872] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.109943] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
[    6.109959] sd 0:0:0:0: [sda] Write Protect is off
[    6.109961] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.109990] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.109993]  sda:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    6.114934] Uniform CD-ROM driver Revision: 3.20
[    6.115029] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.138897]  sda1 sda2 < sda5 sda6 >
[    6.184985] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.581997] PM: Starting manual resume from disk
[    6.582000] PM: Resume from partition 8:6
[    6.582002] PM: Checking hibernation image.
[    6.582093] PM: Resume from disk failed.
[    6.639301] kjournald starting.  Commit interval 5 seconds
[    6.639323] EXT3-fs: mounted filesystem with ordered data mode.
[   12.137675] udevd version 124 started
[   12.510355] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.542853] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.641137] Linux agpgart interface v0.103
[   12.665580] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   12.684028] ACPI: Power Button (FF) [PWRF]
[   12.684107] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.716023] ACPI: Power Button (CM) [VBTN]
[   13.132952] nvidia: module license 'NVIDIA' taints kernel.
[   13.406086] iTCO_vendor_support: vendor-support=0
[   13.434857] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.434865] nvidia 0000:01:00.0: setting latency timer to 64
[   13.435069] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   13.439693] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.441115] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   13.441126] iTCO_wdt: No card detected
[   13.512643] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.668156] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.703519] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.703541] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.173874] lp: driver loaded but no devices found
[   15.302128] Adding 4321444k swap on /dev/sda6.  Priority:-1 extents:1 across:4321444k
[   15.853449] EXT3 FS on sda5, internal journal
[   16.766267] type=1505 audit(1229384687.725:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3903
[   16.919288] type=1505 audit(1229384687.877:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3908
[   16.919465] type=1505 audit(1229384687.877:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3908
[   17.037273] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.576301] ACPI: WMI: Mapper loaded
[   18.505410] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.535316] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   18.535323] apm: disabled - APM is not SMP safe.
[   18.680791] ppdev: user-space parallel port driver
[   20.445384] Bluetooth: Core ver 2.13
[   20.445564] NET: Registered protocol family 31
[   20.445568] Bluetooth: HCI device and connection manager initialized
[   20.445571] Bluetooth: HCI socket layer initialized
[   20.454509] Bluetooth: L2CAP ver 2.11
[   20.454515] Bluetooth: L2CAP socket layer initialized
[   20.461461] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.461466] Bluetooth: BNEP filters: protocol multicast
[   20.494014] Bridge firewalling registered
[   20.494505] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   20.502499] Bluetooth: SCO (Voice Link) ver 0.6
[   20.502505] Bluetooth: SCO socket layer initialized
[   20.684696] Bluetooth: RFCOMM socket layer initialized
[   20.684930] Bluetooth: RFCOMM TTY layer initialized
[   20.684935] Bluetooth: RFCOMM ver 1.10
[   26.380765] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   26.380771] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   26.646639] NET: Registered protocol family 17
[   77.094729] NET: Registered protocol family 10
[   77.095885] lo: Disabled Privacy Extensions
[   88.024029] eth0: no IPv6 routers present
josh@josh-desktop:~$

---

### Post by linux_tech on 2008-12-15
Did any of these commands return anything?
```

amixer info
amixer controls
amixer scontrols
amixer contents

```
```

sudo /etc/init.d/alsa-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start
```

---

### Post by mxjosh on 2008-12-15
Yep, Here are the results!

josh@josh-desktop:~$ amixer info
Card default 'pulse'/'PulseAudio'
  Mixer name	: 'PulseAudio'
  Components	: ''
  Controls      : 4
  Simple ctrls  : 2
josh@josh-desktop:~$ amixer controls
numid=0,iface=MIXER,name='Master Playback Switch'
numid=0,iface=MIXER,name='Master Playback Volume'
numid=0,iface=MIXER,name='Capture Switch'
numid=0,iface=MIXER,name='Capture Volume'
josh@josh-desktop:~$ amixer scontrols
Simple mixer control 'Master',0
Simple mixer control 'Capture',0
josh@josh-desktop:~$ amixer contents
numid=0,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=0,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw------,values=2,min=0,max=65536,step=1
  : values=59637,64881
numid=0,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=0,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw------,values=2,min=0,max=65536,step=1
  : values=60855,60855

---

### Post by linux_tech on 2008-12-15
Enter these commands
```

sudo /etc/init.d/asla-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start

```

then try testing sound

---

### Post by mxjosh on 2008-12-15
The command: sudo /etc/init.d/asla-utils stop could not be found.

josh@josh-desktop:~$ sudo /etc/init.d/asla-utils stop
sudo: /etc/init.d/asla-utils: command not found
josh@josh-desktop:~$ 

I really apreciate all this time you have been helping me by the way!

---

### Post by linux_tech on 2008-12-15
anything happen with:
```
sudo alsa force-reload
```

---

### Post by linux_tech on 2008-12-15
Open a terminal window and type ```
alsamixer  
```
```
gnome-alsamixer
```
 then make sure sound is unmuted and that the volume is turned up. (Unmute everything)

---

### Post by mxjosh on 2008-12-15
Here are the results from the code sudo alsa force-reload

josh@josh-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/josh/.gvfs
      Output information may be incomplete.
Terminating processes: 6794lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/josh/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/josh/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/josh/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

and now when i try to run alsamixer i get 

ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
josh@josh-desktop:~$

---

### Post by linux_tech on 2008-12-15
Try to install gnome-alsamixer

```
sudo apt-get install gnome-alsamixer
```

---

### Post by mxjosh on 2008-12-15
** (gnome-alsamixer:7314): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Digital Input Source"!

** (gnome-alsamixer:7314): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:7314): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:7314): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!
 
okay good news! i unmuted everything and turned everything up in the gnome-alsamixer and i have sound, but only out of one speaker haha hmm, no biggie though as long as i have sound! TYVM!
tryed sound out in-game and didnt have sound in game kind of weird.

---

### Post by linux_tech on 2008-12-15
Ok sorry it took a little while to get going, but better than
reinstalling alsa

---

### Post by mxjosh on 2008-12-15
I have system sounds now just not sounds like say in a game, but hopefully i can figure it out from here, i can't thank you enough for all the help you have given me!

---

### Post by linux_tech on 2008-12-16
I think I have another solution.  What make and model is this?

---

### Post by mxjosh on 2008-12-16
Sorry for the delayed post linux tech. After testing my settings and playing around with them, my problem is now i have sounds for a little bit, but after a few minutes the sound slowly dies out, like it's fading out eventually just going mute :S

---

### Post by mesman00 on 2008-12-16
i have the same audio chipset and the same problem.  everything is unmuted in alsamixer but I am getting no sound output at all.  i get the same warnings you do when trying runing alsa force-reload.  i have had 8.10 installed for a while now and sound was working fine.  i noticed it stop working after performing an update, so i am guessing something broke it.

---

### Post by linux_tech on 2008-12-16
> **mxjosh said:**
> Sorry for the delayed post linux tech. After testing my settings and playing around with them, my problem is now i have sounds for a little bit, but after a few minutes the sound slowly dies out, like it's fading out eventually just going mute :S

Is this a laptop?  What is the make and model?
What is output of
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by linux_tech on 2008-12-16
> **mesman00 said:**
> i have the same audio chipset and the same problem.  everything is unmuted in alsamixer but I am getting no sound output at all.  i get the same warnings you do when trying runing alsa force-reload.  i have had 8.10 installed for a while now and sound was working fine.  i noticed it stop working after performing an update, so i am guessing something broke it.

What is the make and model?
What is output of
```
cat /proc/asound/card0/codec#* | grep Codec
```
```
aplay -l 
```

---

### Post by zazimuth on 2008-12-17
> **linux_tech said:**
> Enter these commands
```

sudo /etc/init.d/asla-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start

```

then try testing sound

Thanks a lot, that worked for me. I used to randomly lose sound after some period of uptime after I upgraded to 8.10.
By the way, there's a typo on the 1st line. It's "alsa" not "asla".

---

### Post by linux_tech on 2008-12-18
> **zazimuth said:**
> Thanks a lot, that worked for me. I used to randomly lose sound after some period of uptime after I upgraded to 8.10.
By the way, there's a typo on the 1st line. It's "alsa" not "asla".

Thanks for the correction

---

### Post by markbuntu on 2008-12-18
Once you get your sound working somewhere, you can do this to get it properly dialed in


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by CarltonBixby on 2009-01-27
Im having the same issue with no sound on 8.10 when i input lspci, i get:

carlton@carlton-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

and aplay -l gives me:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

any help on this would be greatly appreciated. Thanks in advance.

---

