---
title: "Hardware help PVR-150 Not showing up in lspci :: ivtv, pvr-150 edgy mythtv"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by drenesh on 2007-03-03
Ok, I'm about at my wits end with this whole thing. I have a TiVo, I love open source most of the time and decided to build a MythTV box and try it out. I'm so frustrated with this whole process that I'm thinking its worth it to pay TiVo the 12 bucks a month so as not to have this frustration. 

Here's the story: My first attempt was with Edgy, and 0.20. I got video, I got sound, but couldn't for the life of me get the remote to work. I spent > 4 hours pounding away on the kb and testing various things to try and get it working.

Then I came across KnoppMyth and decided to give that a try. That was a joke. KnoppMyth didn't even recognise my usb keyboard and mouse on install. No go there. So then I decided to drop down to Breezy and MythTV 0.18.  That almost got working, but I couldn't get the PVR-150 card to be detected by lspci, thus MythTV wouldn't see it and I couldn't add it. 

So that's where I'm at now. I reinstalled Edgy and MythTV 0.20 and the PVR-150 STILL isn't seen by lspci or dmesg.  

Could my multiple installs and multiple firmware installs cause the card to bork out in linux? I put the card in my WinXP machine and it was detected and installed first time.  I don't want to put windows on that box, but that's what's going to happen if I can't get MythTV to work.

Please help!  Here is my lspci and dmesg outputs:

```
chris@myth:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
chris@myth:~$ 

```

and here's dmesg (putting the whole thing in there so in case I'm not seeing something that someone else does):
```
root@myth:~# dmesg
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d4000 - 00000000000da000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fb830
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa250
[17179569.184000] ACPI: RSDT (v001 AMIINT VIA_P6   0x00000010 MSFT 0x00000097) @ 0x1fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT VIA_P6   0x00000011 MSFT 0x00000097) @ 0x1fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT VIA_P6   0x00000009 MSFT 0x00000097) @ 0x1fff00c0
[17179569.184000] ACPI: DSDT (v001    VIA APOLLO-P 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2400.595 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.772000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.772000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.788000] Memory: 510048k/524224k available (1911k kernel code, 13608k reserved, 1073k data, 308k init, 0k highmem)
[17179572.788000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.868000] Calibrating delay using timer specific routine.. 4805.28 BogoMIPS (lpj=9610560)
[17179572.868000] Security Framework v1.0.0 initialized
[17179572.868000] SELinux:  Disabled at boot.
[17179572.868000] Mount-cache hash table entries: 512
[17179572.868000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.868000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.868000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.868000] CPU: L2 cache: 512K
[17179572.868000] CPU: Hyper-Threading is disabled
[17179572.868000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.868000] Checking 'hlt' instruction... OK.
[17179572.884000] SMP alternatives: switching to UP code
[17179572.884000] Freeing SMP alternatives: 16k freed
[17179572.884000] checking if image is initramfs... it is
[17179573.408000] Freeing initrd memory: 5325k freed
[17179573.408000] ACPI: Core revision 20060707
[17179573.408000] ACPI: Looking for DSDT ... not found!
[17179573.412000] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[17179573.412000] Total of 1 processors activated (4805.28 BogoMIPS).
[17179573.412000] ENABLING IO-APIC IRQs
[17179573.412000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.556000] Brought up 1 CPUs
[17179573.556000] migration_cost=0
[17179573.556000] NET: Registered protocol family 16
[17179573.556000] EISA bus registered
[17179573.556000] ACPI: bus type pci registered
[17179573.556000] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[17179573.556000] PCI: Using configuration type 1
[17179573.556000] Setting up standard PCI resources
[17179573.572000] ACPI: Interpreter enabled
[17179573.572000] ACPI: Using IOAPIC for interrupt routing
[17179573.572000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.572000] PCI: Probing PCI hardware (bus 00)
[17179573.576000] PCI: device 0000:00:0b.0 has unknown header type 70, ignoring.
[17179573.576000] PCI quirk: region 0800-087f claimed by vt8235 PM
[17179573.576000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[17179573.576000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179573.576000] Boot video device is 0000:01:00.0
[17179573.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.592000] ACPI: Power Resource [URP1] (off)
[17179573.592000] ACPI: Power Resource [URP2] (off)
[17179573.592000] ACPI: Power Resource [FDDP] (off)
[17179573.592000] ACPI: Power Resource [LPTP] (off)
[17179573.592000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.592000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.596000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179573.596000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.596000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.596000] pnp: PnP ACPI init
[17179573.596000] pnp: PnP ACPI: found 7 devices
[17179573.596000] PnPBIOS: Disabled by ACPI PNP
[17179573.596000] PCI: Using ACPI for IRQ routing
[17179573.596000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.600000] PCI: Bridge: 0000:00:01.0
[17179573.600000]   IO window: disabled.
[17179573.600000]   MEM window: dde00000-dfefffff
[17179573.600000]   PREFETCH window: cdc00000-ddcfffff
[17179573.600000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.600000] NET: Registered protocol family 2
[17179573.632000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.632000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.632000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.632000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.632000] TCP reno registered
[17179573.632000] audit: initializing netlink socket (disabled)
[17179573.632000] audit(1172903069.632:1): initialized
[17179573.632000] VFS: Disk quotas dquot_6.5.1
[17179573.632000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.632000] Initializing Cryptographic API
[17179573.632000] io scheduler noop registered
[17179573.632000] io scheduler anticipatory registered
[17179573.632000] io scheduler deadline registered
[17179573.632000] io scheduler cfq registered (default)
[17179573.632000] isapnp: Scanning for PnP cards...
[17179573.988000] isapnp: No Plug & Play device found
[17179574.012000] Real Time Clock Driver v1.12ac
[17179574.012000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.012000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.016000] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.016000] mice: PS/2 mouse device common for all mice
[17179574.016000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.016000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.016000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.016000] PNP: No PS/2 controller found. Probing ports directly.
[17179574.016000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.016000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.016000] EISA: Probing bus 0 at eisa.0
[17179574.016000] EISA: Detected 0 cards.
[17179574.016000] TCP bic registered
[17179574.016000] NET: Registered protocol family 1
[17179574.016000] NET: Registered protocol family 8
[17179574.016000] NET: Registered protocol family 20
[17179574.016000] Using IPI No-Shortcut mode
[17179574.016000] ACPI: (supports S0 S1 S4 S5)
[17179574.016000] Freeing unused kernel memory: 308k freed
[17179575.168000] Capability LSM initialized
[17179575.208000] ACPI: Processor [CPU1] (supports 16 throttling states)
[17179575.208000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179575.208000] ACPI: Getting cpuindex for acpiid 0x2
[17179575.752000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179575.752000] ACPI: Unable to derive IRQ for device 0000:00:11.1
[17179575.752000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179575.752000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[17179575.752000] VP_IDE: chipset revision 6
[17179575.752000] VP_IDE: not 100% native mode: will probe irqs later
[17179575.752000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179575.752000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[17179575.752000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[17179575.752000] Probing IDE interface ide0...
[17179576.172000] hda: ST3250824A, ATA DISK drive
[17179576.852000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.852000] Probing IDE interface ide1...
[17179577.716000] hdc: HL-DT-STDVD-RAM GSA-H22L, ATAPI CD/DVD-ROM drive
[17179578.056000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.064000] hda: max request size: 512KiB
[17179578.104000] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(33)
[17179578.128000] hda: cache flushes supported
[17179578.128000]  hda: hda1 hda2 < hda5 >
[17179578.180000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179578.180000] Uniform CD-ROM driver Revision: 3.20
[17179578.384000] usbcore: registered new driver usbfs
[17179578.384000] usbcore: registered new driver hub
[17179578.384000] USB Universal Host Controller Interface driver v3.0
[17179578.384000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
[17179578.384000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
[17179578.384000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.384000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179578.384000] uhci_hcd 0000:00:10.0: irq 169, io base 0x0000e400
[17179578.384000] usb usb1: configuration #1 chosen from 1 choice
[17179578.384000] hub 1-0:1.0: USB hub found
[17179578.384000] hub 1-0:1.0: 2 ports detected
[17179578.492000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 169
[17179578.492000] PCI: Via IRQ fixup for 0000:00:10.1, from 5 to 9
[17179578.492000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.492000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.492000] uhci_hcd 0000:00:10.1: irq 169, io base 0x0000e800
[17179578.492000] usb usb2: configuration #1 chosen from 1 choice
[17179578.492000] hub 2-0:1.0: USB hub found
[17179578.492000] hub 2-0:1.0: 2 ports detected
[17179578.596000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
[17179578.596000] PCI: Via IRQ fixup for 0000:00:10.2, from 12 to 9
[17179578.596000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.600000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179578.600000] uhci_hcd 0000:00:10.2: irq 169, io base 0x0000ec00
[17179578.600000] usb usb3: configuration #1 chosen from 1 choice
[17179578.600000] hub 3-0:1.0: USB hub found
[17179578.600000] hub 3-0:1.0: 2 ports detected
[17179578.720000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
[17179578.720000] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 9
[17179578.720000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179578.720000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179578.720000] ehci_hcd 0000:00:10.3: irq 169, io mem 0xdfffff00
[17179578.720000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.720000] usb usb4: configuration #1 chosen from 1 choice
[17179578.720000] hub 4-0:1.0: USB hub found
[17179578.720000] hub 4-0:1.0: 6 ports detected
[17179578.732000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179578.908000] Attempting manual resume
[17179578.976000] kjournald starting.  Commit interval 5 seconds
[17179578.976000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.684000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[17179579.820000] usb 4-1: configuration #1 chosen from 1 choice
[17179580.428000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179580.636000] usb 2-1: configuration #1 chosen from 1 choice
[17179580.884000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17179581.064000] usb 2-2: configuration #1 chosen from 1 choice
[17179587.476000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179587.476000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179587.476000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179587.480000] eth0: VIA Rhine II at 0x1dc00, 00:0a:e6:dd:f8:ea, IRQ 177.
[17179587.480000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[17179587.608000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.612000] agpgart: Detected VIA PT800 chipset
[17179587.632000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179587.756000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.856000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179588.256000] FDC 0 is a post-1991 82077
[17179588.292000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.300000] input: PC Speaker as /class/input/input0
[17179588.452000] irda_init()
[17179588.452000] NET: Registered protocol family 23
[17179588.476000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.480000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179588.480000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.524000] NET: Registered protocol family 10
[17179588.524000] lo: Disabled Privacy Extensions
[17179588.524000] IPv6 over IPv4 tunneling driver
[17179588.540000] usbcore: registered new driver hiddev
[17179588.596000] input: HID 1241:1166 as /class/input/input1
[17179588.596000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:10.1-1
[17179588.612000] input: DELL DELL USB Keyboard as /class/input/input2
[17179588.612000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:10.1-2
[17179588.612000] usbcore: registered new driver usbhid
[17179588.612000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179588.656000] islusb: suitable configuration found for net2280 + PCI device
[17179588.832000] ts: Compaq touchscreen protocol output
[17179588.940000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 185
[17179588.940000] PCI: Via IRQ fixup for 0000:00:11.5, from 12 to 9
[17179588.940000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179589.092000] usbcore: registered new driver islusb
[17179589.736000] lp: driver loaded but no devices found
[17179589.776000] Adding 1510068k swap on /dev/disk/by-uuid/ed1bee66-6ab9-433f-91f1-50f9ee4ee7c0.  Priority:-1 extents:1 across:1510068k
[17179589.848000] EXT3 FS on hda1, internal journal
[17179591.212000] ACPI: Power Button (FF) [PWRF]
[17179591.212000] ACPI: Power Button (CM) [PWRB]
[17179591.212000] ACPI: Sleep Button (CM) [SLPB]
[17179591.332000] ibm_acpi: ec object not found
[17179591.360000] pcc_acpi: loading...
[17179598.288000] apm: BIOS not found.
[17179599.512000] eth0: no IPv6 routers present
[17179614.076000] Bluetooth: Core ver 2.8
[17179614.076000] NET: Registered protocol family 31
[17179614.076000] Bluetooth: HCI device and connection manager initialized
[17179614.076000] Bluetooth: HCI socket layer initialized
[17179614.088000] Bluetooth: L2CAP ver 2.8
[17179614.088000] Bluetooth: L2CAP socket layer initialized
[17179614.112000] Bluetooth: RFCOMM socket layer initialized
[17179614.112000] Bluetooth: RFCOMM TTY layer initialized
[17179614.112000] Bluetooth: RFCOMM ver 1.7
[17226574.536000] Linux video capture interface: v1.00
[17226574.548000] ivtv:  ==================== START INIT IVTV ====================
[17226574.548000] ivtv:  version 0.7.0 (tagged release) loading
[17226574.548000] ivtv:  Linux version: 2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
[17226574.548000] ivtv:  In case of problems please include the debug info between
[17226574.548000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17226574.548000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17226574.548000] ivtv:  ====================  END INIT IVTV  ====================
root@myth:~# 
```


Any help at all would be greatly appreciated.

Edit to say: I also have a nVidia graphics card for TV-out.

---

### Post by superm1 on 2007-03-04
> **drenesh said:**
> Ok, I'm about at my wits end with this whole thing. I have a TiVo, I love open source most of the time and decided to build a MythTV box and try it out. I'm so frustrated with this whole process that I'm thinking its worth it to pay TiVo the 12 bucks a month so as not to have this frustration. 

Here's the story: My first attempt was with Edgy, and 0.20. I got video, I got sound, but couldn't for the life of me get the remote to work. I spent > 4 hours pounding away on the kb and testing various things to try and get it working.

Then I came across KnoppMyth and decided to give that a try. That was a joke. KnoppMyth didn't even recognise my usb keyboard and mouse on install. No go there. So then I decided to drop down to Breezy and MythTV 0.18.  That almost got working, but I couldn't get the PVR-150 card to be detected by lspci, thus MythTV wouldn't see it and I couldn't add it. 

So that's where I'm at now. I reinstalled Edgy and MythTV 0.20 and the PVR-150 STILL isn't seen by lspci or dmesg.  

Could my multiple installs and multiple firmware installs cause the card to bork out in linux? I put the card in my WinXP machine and it was detected and installed first time.  I don't want to put windows on that box, but that's what's going to happen if I can't get MythTV to work.

Please help!  Here is my lspci and dmesg outputs:

```
chris@myth:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
chris@myth:~$ 

```and here's dmesg (putting the whole thing in there so in case I'm not seeing something that someone else does):
```
root@myth:~# dmesg
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d4000 - 00000000000da000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fb830
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa250
[17179569.184000] ACPI: RSDT (v001 AMIINT VIA_P6   0x00000010 MSFT 0x00000097) @ 0x1fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT VIA_P6   0x00000011 MSFT 0x00000097) @ 0x1fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT VIA_P6   0x00000009 MSFT 0x00000097) @ 0x1fff00c0
[17179569.184000] ACPI: DSDT (v001    VIA APOLLO-P 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2400.595 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.772000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.772000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.788000] Memory: 510048k/524224k available (1911k kernel code, 13608k reserved, 1073k data, 308k init, 0k highmem)
[17179572.788000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.868000] Calibrating delay using timer specific routine.. 4805.28 BogoMIPS (lpj=9610560)
[17179572.868000] Security Framework v1.0.0 initialized
[17179572.868000] SELinux:  Disabled at boot.
[17179572.868000] Mount-cache hash table entries: 512
[17179572.868000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.868000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.868000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.868000] CPU: L2 cache: 512K
[17179572.868000] CPU: Hyper-Threading is disabled
[17179572.868000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.868000] Checking 'hlt' instruction... OK.
[17179572.884000] SMP alternatives: switching to UP code
[17179572.884000] Freeing SMP alternatives: 16k freed
[17179572.884000] checking if image is initramfs... it is
[17179573.408000] Freeing initrd memory: 5325k freed
[17179573.408000] ACPI: Core revision 20060707
[17179573.408000] ACPI: Looking for DSDT ... not found!
[17179573.412000] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[17179573.412000] Total of 1 processors activated (4805.28 BogoMIPS).
[17179573.412000] ENABLING IO-APIC IRQs
[17179573.412000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.556000] Brought up 1 CPUs
[17179573.556000] migration_cost=0
[17179573.556000] NET: Registered protocol family 16
[17179573.556000] EISA bus registered
[17179573.556000] ACPI: bus type pci registered
[17179573.556000] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[17179573.556000] PCI: Using configuration type 1
[17179573.556000] Setting up standard PCI resources
[17179573.572000] ACPI: Interpreter enabled
[17179573.572000] ACPI: Using IOAPIC for interrupt routing
[17179573.572000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.572000] PCI: Probing PCI hardware (bus 00)
[17179573.576000] PCI: device 0000:00:0b.0 has unknown header type 70, ignoring.
[17179573.576000] PCI quirk: region 0800-087f claimed by vt8235 PM
[17179573.576000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[17179573.576000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179573.576000] Boot video device is 0000:01:00.0
[17179573.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.592000] ACPI: Power Resource [URP1] (off)
[17179573.592000] ACPI: Power Resource [URP2] (off)
[17179573.592000] ACPI: Power Resource [FDDP] (off)
[17179573.592000] ACPI: Power Resource [LPTP] (off)
[17179573.592000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.592000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.596000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179573.596000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.596000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.596000] pnp: PnP ACPI init
[17179573.596000] pnp: PnP ACPI: found 7 devices
[17179573.596000] PnPBIOS: Disabled by ACPI PNP
[17179573.596000] PCI: Using ACPI for IRQ routing
[17179573.596000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.600000] PCI: Bridge: 0000:00:01.0
[17179573.600000]   IO window: disabled.
[17179573.600000]   MEM window: dde00000-dfefffff
[17179573.600000]   PREFETCH window: cdc00000-ddcfffff
[17179573.600000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.600000] NET: Registered protocol family 2
[17179573.632000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.632000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.632000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.632000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.632000] TCP reno registered
[17179573.632000] audit: initializing netlink socket (disabled)
[17179573.632000] audit(1172903069.632:1): initialized
[17179573.632000] VFS: Disk quotas dquot_6.5.1
[17179573.632000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.632000] Initializing Cryptographic API
[17179573.632000] io scheduler noop registered
[17179573.632000] io scheduler anticipatory registered
[17179573.632000] io scheduler deadline registered
[17179573.632000] io scheduler cfq registered (default)
[17179573.632000] isapnp: Scanning for PnP cards...
[17179573.988000] isapnp: No Plug & Play device found
[17179574.012000] Real Time Clock Driver v1.12ac
[17179574.012000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.012000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.016000] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.016000] mice: PS/2 mouse device common for all mice
[17179574.016000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.016000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.016000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.016000] PNP: No PS/2 controller found. Probing ports directly.
[17179574.016000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.016000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.016000] EISA: Probing bus 0 at eisa.0
[17179574.016000] EISA: Detected 0 cards.
[17179574.016000] TCP bic registered
[17179574.016000] NET: Registered protocol family 1
[17179574.016000] NET: Registered protocol family 8
[17179574.016000] NET: Registered protocol family 20
[17179574.016000] Using IPI No-Shortcut mode
[17179574.016000] ACPI: (supports S0 S1 S4 S5)
[17179574.016000] Freeing unused kernel memory: 308k freed
[17179575.168000] Capability LSM initialized
[17179575.208000] ACPI: Processor [CPU1] (supports 16 throttling states)
[17179575.208000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179575.208000] ACPI: Getting cpuindex for acpiid 0x2
[17179575.752000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179575.752000] ACPI: Unable to derive IRQ for device 0000:00:11.1
[17179575.752000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179575.752000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[17179575.752000] VP_IDE: chipset revision 6
[17179575.752000] VP_IDE: not 100% native mode: will probe irqs later
[17179575.752000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179575.752000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[17179575.752000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[17179575.752000] Probing IDE interface ide0...
[17179576.172000] hda: ST3250824A, ATA DISK drive
[17179576.852000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.852000] Probing IDE interface ide1...
[17179577.716000] hdc: HL-DT-STDVD-RAM GSA-H22L, ATAPI CD/DVD-ROM drive
[17179578.056000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.064000] hda: max request size: 512KiB
[17179578.104000] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(33)
[17179578.128000] hda: cache flushes supported
[17179578.128000]  hda: hda1 hda2 < hda5 >
[17179578.180000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179578.180000] Uniform CD-ROM driver Revision: 3.20
[17179578.384000] usbcore: registered new driver usbfs
[17179578.384000] usbcore: registered new driver hub
[17179578.384000] USB Universal Host Controller Interface driver v3.0
[17179578.384000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
[17179578.384000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
[17179578.384000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.384000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179578.384000] uhci_hcd 0000:00:10.0: irq 169, io base 0x0000e400
[17179578.384000] usb usb1: configuration #1 chosen from 1 choice
[17179578.384000] hub 1-0:1.0: USB hub found
[17179578.384000] hub 1-0:1.0: 2 ports detected
[17179578.492000] ACPI: PCI Interrupt 0000:00:10.1[b] -> GSI 21 (level, low) -> IRQ 169
[17179578.492000] PCI: Via IRQ fixup for 0000:00:10.1, from 5 to 9
[17179578.492000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.492000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.492000] uhci_hcd 0000:00:10.1: irq 169, io base 0x0000e800
[17179578.492000] usb usb2: configuration #1 chosen from 1 choice
[17179578.492000] hub 2-0:1.0: USB hub found
[17179578.492000] hub 2-0:1.0: 2 ports detected
[17179578.596000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
[17179578.596000] PCI: Via IRQ fixup for 0000:00:10.2, from 12 to 9
[17179578.596000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.600000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179578.600000] uhci_hcd 0000:00:10.2: irq 169, io base 0x0000ec00
[17179578.600000] usb usb3: configuration #1 chosen from 1 choice
[17179578.600000] hub 3-0:1.0: USB hub found
[17179578.600000] hub 3-0:1.0: 2 ports detected
[17179578.720000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
[17179578.720000] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 9
[17179578.720000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179578.720000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179578.720000] ehci_hcd 0000:00:10.3: irq 169, io mem 0xdfffff00
[17179578.720000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.720000] usb usb4: configuration #1 chosen from 1 choice
[17179578.720000] hub 4-0:1.0: USB hub found
[17179578.720000] hub 4-0:1.0: 6 ports detected
[17179578.732000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179578.908000] Attempting manual resume
[17179578.976000] kjournald starting.  Commit interval 5 seconds
[17179578.976000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.684000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[17179579.820000] usb 4-1: configuration #1 chosen from 1 choice
[17179580.428000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179580.636000] usb 2-1: configuration #1 chosen from 1 choice
[17179580.884000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17179581.064000] usb 2-2: configuration #1 chosen from 1 choice
[17179587.476000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179587.476000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179587.476000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179587.480000] eth0: VIA Rhine II at 0x1dc00, 00:0a:e6:dd:f8:ea, IRQ 177.
[17179587.480000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[17179587.608000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.612000] agpgart: Detected VIA PT800 chipset
[17179587.632000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179587.756000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.856000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179588.256000] FDC 0 is a post-1991 82077
[17179588.292000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.300000] input: PC Speaker as /class/input/input0
[17179588.452000] irda_init()
[17179588.452000] NET: Registered protocol family 23
[17179588.476000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.480000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179588.480000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.524000] NET: Registered protocol family 10
[17179588.524000] lo: Disabled Privacy Extensions
[17179588.524000] IPv6 over IPv4 tunneling driver
[17179588.540000] usbcore: registered new driver hiddev
[17179588.596000] input: HID 1241:1166 as /class/input/input1
[17179588.596000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:10.1-1
[17179588.612000] input: DELL DELL USB Keyboard as /class/input/input2
[17179588.612000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:10.1-2
[17179588.612000] usbcore: registered new driver usbhid
[17179588.612000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179588.656000] islusb: suitable configuration found for net2280 + PCI device
[17179588.832000] ts: Compaq touchscreen protocol output
[17179588.940000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 185
[17179588.940000] PCI: Via IRQ fixup for 0000:00:11.5, from 12 to 9
[17179588.940000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179589.092000] usbcore: registered new driver islusb
[17179589.736000] lp: driver loaded but no devices found
[17179589.776000] Adding 1510068k swap on /dev/disk/by-uuid/ed1bee66-6ab9-433f-91f1-50f9ee4ee7c0.  Priority:-1 extents:1 across:1510068k
[17179589.848000] EXT3 FS on hda1, internal journal
[17179591.212000] ACPI: Power Button (FF) [PWRF]
[17179591.212000] ACPI: Power Button (CM) [PWRB]
[17179591.212000] ACPI: Sleep Button (CM) [SLPB]
[17179591.332000] ibm_acpi: ec object not found
[17179591.360000] pcc_acpi: loading...
[17179598.288000] apm: BIOS not found.
[17179599.512000] eth0: no IPv6 routers present
[17179614.076000] Bluetooth: Core ver 2.8
[17179614.076000] NET: Registered protocol family 31
[17179614.076000] Bluetooth: HCI device and connection manager initialized
[17179614.076000] Bluetooth: HCI socket layer initialized
[17179614.088000] Bluetooth: L2CAP ver 2.8
[17179614.088000] Bluetooth: L2CAP socket layer initialized
[17179614.112000] Bluetooth: RFCOMM socket layer initialized
[17179614.112000] Bluetooth: RFCOMM TTY layer initialized
[17179614.112000] Bluetooth: RFCOMM ver 1.7
[17226574.536000] Linux video capture interface: v1.00
[17226574.548000] ivtv:  ==================== START INIT IVTV ====================
[17226574.548000] ivtv:  version 0.7.0 (tagged release) loading
[17226574.548000] ivtv:  Linux version: 2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
[17226574.548000] ivtv:  In case of problems please include the debug info between
[17226574.548000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17226574.548000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17226574.548000] ivtv:  ====================  END INIT IVTV  ====================
root@myth:~# 
```
Any help at all would be greatly appreciated.

Edit to say: I also have a nVidia graphics card for TV-out.

If your card isn't being seen by lspci, then have you tried moving it to another PCI slot?

---

### Post by rsambuca on 2007-03-04
You could try Feisty.  IVTV is pre-compiled in the kernel so you don't have to mess around with it.  My 150 worked out of the box!

---

### Post by tgm4883 on 2007-03-04
I just installed edgy and a pvr-150 using this guide
[http://www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150](http://www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150)

Everything works great, only changes I made were I didn't change the sources.list file as in the guide, I used the one from here instead
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Also, I had to change the root password for mysql from the command line as I didn't have a place to change it in phpmyadmin

And I had to google a couple things to get mythweb working properly, but all very easy.  I ordered a HD-5500 that should be here this week, then it will rock.

---

