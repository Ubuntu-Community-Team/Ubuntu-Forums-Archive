---
title: "Kworld - Saa7134 - ASUS TV-FM Compatible Card"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by LeonHeart on 2006-12-13
Hi guys,
Finally I got my TV-FM card working under Ubuntu 6.10.
Just found the compatible driver (ASUS TV-FM [card=16]).
kdetv works just fine and i can watch any local channel using the
antenna.
the problem is when i try to hear to radio.
i open gnomeradio and while everything shows to work fine,
i get no sound. the little antenna gnomeradio has to show you that it is
tuned to a station is led. and even so i get no sound.
i changed the sound input to line (the same kdetv uses and works fine) but
still nothing.
got any ideas?
i need help asap, it's urgent (it's about my cousin's pc, the one that i 
finally convinced to remove winxp)
so please gimme some answers here...

---

### Post by Fully216 on 2006-12-13
User aNTwNHs has described a similar problem as well.  If you try to record the radio, can you hear sound when you play back?  If this is the case, it might be possible that /dev/radio0 is muted.  

To check, open gnomeradio preferences and selected vol in mix source.  After unmuting the volume, check the output line for sound.  You should also check your alsa mixer or equivalent sound card configuration tool.

---

### Post by LeonHeart on 2006-12-14
Nope, nothing.
I don't know if this will help, but here is the output of dmesg:

> [17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fc120
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa3c0
[17179569.184000] ACPI: RSDT (v001 AMIINT INTEL865 0x00000010 MSFT 0x00000097) @ 0x1fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT INTEL865 0x00000011 MSFT 0x00000097) @ 0x1fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT INTEL865 0x00000009 MSFT 0x00000097) @ 0x1fff00c0
[17179569.184000] ACPI: DSDT (v001  INTEL    I865G 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:3 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:3 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
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
[17179569.184000] Detected 3042.974 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.424000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.424000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.432000] Memory: 510056k/524224k available (1910k kernel code, 13564k reserved, 1070k data, 308k init, 0k highmem)
[17179569.432000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.512000] Calibrating delay using timer specific routine.. 6091.57 BogoMIPS (lpj=12183143)
[17179569.512000] Security Framework v1.0.0 initialized
[17179569.512000] SELinux:  Disabled at boot.
[17179569.512000] Mount-cache hash table entries: 512
[17179569.512000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[17179569.512000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[17179569.512000] monitor/mwait feature present.
[17179569.512000] using mwait in idle threads.
[17179569.512000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.512000] CPU: L2 cache: 1024K
[17179569.512000] CPU: Hyper-Threading is disabled
[17179569.512000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000180 0000041d 00000000 00000000
[17179569.512000] Checking 'hlt' instruction... OK.
[17179569.528000] SMP alternatives: switching to UP code
[17179569.528000] checking if image is initramfs... it is
[17179569.944000] Freeing initrd memory: 5257k freed
[17179569.944000] ACPI: Core revision 20060707
[17179569.944000] ACPI: Looking for DSDT ... not found!
[17179569.948000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179569.948000] SMP alternatives: switching to SMP code
[17179569.948000] Booting processor 1/1 eip 3000
[17179569.956000] Initializing CPU#1
[17179570.036000] Calibrating delay using timer specific routine.. 6085.70 BogoMIPS (lpj=12171404)
[17179570.036000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[17179570.036000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[17179570.036000] monitor/mwait feature present.
[17179570.036000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179570.036000] CPU: L2 cache: 1024K
[17179570.036000] CPU: Hyper-Threading is disabled
[17179570.036000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000180 0000041d 00000000 00000000
[17179570.036000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179570.036000] Total of 2 processors activated (12177.27 BogoMIPS).
[17179570.036000] ENABLING IO-APIC IRQs
[17179570.036000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.180000] checking TSC synchronization across 2 CPUs: passed.
[17179570.184000] Brought up 2 CPUs
[17179570.240000] migration_cost=4000
[17179570.240000] NET: Registered protocol family 16
[17179570.240000] EISA bus registered
[17179570.240000] ACPI: bus type pci registered
[17179570.244000] PCI: PCI BIOS revision 2.10 entry at 0xfdb81, last bus=2
[17179570.244000] PCI: Using configuration type 1
[17179570.244000] Setting up standard PCI resources
[17179570.264000] ACPI: Interpreter enabled
[17179570.264000] ACPI: Using IOAPIC for interrupt routing
[17179570.264000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.264000] PCI: Probing PCI hardware (bus 00)
[17179570.264000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179570.264000] PCI quirk: region 0400-043f claimed by ICH4 GPIO
[17179570.264000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.264000] Boot video device is 0000:01:00.0
[17179570.264000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.264000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.268000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.ICHB._PRT]
[17179570.272000] ACPI: Power Resource [URP1] (off)
[17179570.272000] ACPI: Power Resource [URP2] (off)
[17179570.272000] ACPI: Power Resource [FDDP] (off)
[17179570.272000] ACPI: Power Resource [LPTP] (off)
[17179570.272000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[17179570.272000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12 14 15)
[17179570.272000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[17179570.272000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12 14 15)
[17179570.272000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 12 14 15)
[17179570.272000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.272000] pnp: PnP ACPI init
[17179570.276000] pnp: PnP ACPI: found 12 devices
[17179570.276000] PnPBIOS: Disabled by ACPI PNP
[17179570.276000] PCI: Using ACPI for IRQ routing
[17179570.276000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.280000] PCI: Bridge: 0000:00:01.0
[17179570.280000]   IO window: b000-bfff
[17179570.284000]   MEM window: ffc00000-ffcfffff
[17179570.284000]   PREFETCH window: d7f00000-f7efffff
[17179570.284000] PCI: Bridge: 0000:00:1e.0
[17179570.284000]   IO window: c000-cfff
[17179570.284000]   MEM window: ffd00000-ffdfffff
[17179570.284000]   PREFETCH window: 30000000-300fffff
[17179570.284000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.284000] NET: Registered protocol family 2
[17179570.320000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.320000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.320000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.320000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.320000] TCP reno registered
[17179570.320000] audit: initializing netlink socket (disabled)
[17179570.320000] audit(1166096954.320:1): initialized
[17179570.320000] VFS: Disk quotas dquot_6.5.1
[17179570.320000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.320000] Initializing Cryptographic API
[17179570.320000] io scheduler noop registered
[17179570.320000] io scheduler anticipatory registered
[17179570.320000] io scheduler deadline registered
[17179570.320000] io scheduler cfq registered (default)
[17179570.320000] isapnp: Scanning for PnP cards...
[17179570.672000] isapnp: No Plug & Play device found
[17179570.700000] Real Time Clock Driver v1.12ac
[17179570.700000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.700000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.700000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.700000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.700000] 0000:02:04.0: ttyS1 at I/O 0xcc08 (irq = 169) is a 16450
[17179570.700000] 0000:02:04.0: ttyS2 at I/O 0xcc10 (irq = 169) is a 8250
[17179570.700000] 0000:02:04.0: ttyS3 at I/O 0xcc18 (irq = 169) is a 16450
[17179570.700000] Couldn't register serial port 0000:02:04.0: -28
[17179570.700000] mice: PS/2 mouse device common for all mice
[17179570.700000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.700000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.700000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.700000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.704000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.704000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.704000] EISA: Probing bus 0 at eisa.0
[17179570.704000] EISA: Detected 0 cards.
[17179570.704000] TCP bic registered
[17179570.704000] NET: Registered protocol family 1
[17179570.704000] NET: Registered protocol family 8
[17179570.704000] NET: Registered protocol family 20
[17179570.704000] Starting balanced_irq
[17179570.704000] Using IPI No-Shortcut mode
[17179570.704000] ACPI: (supports S0 S1 S4 S5)
[17179570.704000] Freeing unused kernel memory: 308k freed
[17179570.728000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.792000] Capability LSM initialized
[17179571.876000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179571.876000] ACPI: Processor [CPU2] (supports 8 throttling states)
[17179572.264000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179572.264000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179572.264000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[17179572.264000] ICH5: chipset revision 2
[17179572.264000] ICH5: not 100% native mode: will probe irqs later
[17179572.264000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[17179572.264000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[17179572.264000] Probing IDE interface ide0...
[17179572.552000] hda: ST380011A, ATA DISK drive
[17179572.832000] hdb: WDC WD2500JB-00REA0, ATA DISK drive
[17179572.888000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179572.892000] Probing IDE interface ide1...
[17179573.628000] hdc: _NEC DVD_RW ND-4550A, ATAPI CD/DVD-ROM drive
[17179574.436000] hdd: HL-DT-STDVD-ROM GDR8163B, ATAPI CD/DVD-ROM drive
[17179574.500000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.512000] hda: max request size: 512KiB
[17179574.512000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179574.512000] hda: cache flushes supported
[17179574.512000]  hda: hda1 hda2 < hda5 >
[17179574.552000] hdb: max request size: 512KiB
[17179574.560000] hdb: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[17179574.560000] hdb: cache flushes supported
[17179574.560000]  hdb: hdb1
[17179574.580000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.580000] Uniform CD-ROM driver Revision: 3.20
[17179574.588000] hdd: ATAPI 52X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179574.848000] usbcore: registered new driver usbfs
[17179574.848000] usbcore: registered new driver hub
[17179574.864000] USB Universal Host Controller Interface driver v3.0
[17179574.864000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.864000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.864000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.864000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.864000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000e000
[17179574.864000] usb usb1: configuration #1 chosen from 1 choice
[17179574.864000] hub 1-0:1.0: USB hub found
[17179574.864000] hub 1-0:1.0: 2 ports detected
[17179574.972000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17179574.972000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.972000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.972000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.972000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000e400
[17179574.972000] usb usb2: configuration #1 chosen from 1 choice
[17179574.972000] hub 2-0:1.0: USB hub found
[17179574.972000] hub 2-0:1.0: 2 ports detected
[17179575.080000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179575.080000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.080000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.080000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.080000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000e800
[17179575.080000] usb usb3: configuration #1 chosen from 1 choice
[17179575.080000] hub 3-0:1.0: USB hub found
[17179575.080000] hub 3-0:1.0: 2 ports detected
[17179575.188000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 169
[17179575.188000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179575.188000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179575.188000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179575.188000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000ec00
[17179575.188000] usb usb4: configuration #1 chosen from 1 choice
[17179575.188000] hub 4-0:1.0: USB hub found
[17179575.188000] hub 4-0:1.0: 2 ports detected
[17179575.236000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179575.296000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17179575.296000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.296000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.296000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179575.296000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.296000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179575.296000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xffeffc00
[17179575.300000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.300000] usb usb5: configuration #1 chosen from 1 choice
[17179575.300000] hub 5-0:1.0: USB hub found
[17179575.300000] hub 5-0:1.0: 8 ports detected
[17179575.496000] Attempting manual resume
[17179575.508000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179575.508000] EXT3-fs: write access will be enabled during recovery.
[17179575.768000] usb 1-1: device not accepting address 2, error -71
[17179577.328000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[17179577.572000] usb 1-1: configuration #1 chosen from 1 choice
[17179577.836000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[17179578.044000] usb 1-2: configuration #1 chosen from 1 choice
[17179578.300000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179578.488000] usb 2-1: configuration #1 chosen from 1 choice
[17179578.740000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[17179578.944000] usb 3-2: configuration #1 chosen from 1 choice
[17179578.944000] usbcore: registered new driver libusual
[17179578.956000] SCSI subsystem initialized
[17179578.960000] Initializing USB Mass Storage driver...
[17179578.960000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179578.960000] usb-storage: device found at 5
[17179578.960000] usb-storage: waiting for device to settle before scanning
[17179578.960000] usbcore: registered new driver usb-storage
[17179578.960000] USB Mass Storage support registered.
[17179582.920000] kjournald starting.  Commit interval 5 seconds
[17179582.920000] EXT3-fs: hda1: orphan cleanup on readonly fs
[17179582.920000] ext3_orphan_cleanup: deleting unreferenced inode 2474029
[17179582.920000] EXT3-fs: hda1: 1 orphan inode deleted
[17179582.920000] EXT3-fs: recovery complete.
[17179583.028000] EXT3-fs: mounted filesystem with ordered data mode.
[17179583.964000] usb-storage: device scan complete
[17179583.972000]   Vendor: HP        Model: photosmart 7600   Rev: 1.00
[17179583.972000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179591.444000] logips2pp: Detected unknown logitech mouse model 62
[17179591.560000] parport: PnPBIOS parport detected.
[17179591.560000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179591.616000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.616000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.648000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.652000] agpgart: Detected an Intel 865 Chipset.
[17179591.656000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179591.876000] input: PC Speaker as /class/input/input1
[17179591.928000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[17179592.040000] hw_random: RNG not detected
[17179592.172000] Floppy drive(s): fd0 is 1.44M
[17179592.212000] FDC 0 is a post-1991 82077
[17179592.664000] ts: Compaq touchscreen protocol output
[17179592.800000] Linux video capture interface: v1.00
[17179592.912000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0xB202
[17179592.912000] usbcore: registered new driver usblp
[17179592.912000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179592.964000] 8139too Fast Ethernet driver 0.9.27
[17179592.964000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179592.964000] eth0: RealTek RTL8139 at 0xe08fcb00, 00:11:09:5d:8f:61, IRQ 193
[17179592.964000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179592.976000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179593.020000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179593.036000] Bluetooth: Core ver 2.8
[17179593.036000] NET: Registered protocol family 31
[17179593.036000] Bluetooth: HCI device and connection manager initialized
[17179593.036000] Bluetooth: HCI socket layer initialized
[17179593.048000] Bluetooth: HCI USB driver ver 2.9
[17179593.052000] usbcore: registered new driver hci_usb
[17179593.092000] drivers/media/video/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Pixart PAC207BCA
[17179593.096000] usbcore: registered new driver spca5xx
[17179593.096000] drivers/media/video/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17179593.228000] sd 0:0:0:0: Attached scsi removable disk sda
[17179593.292000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179593.316000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179593.316000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 185
[17179593.316000] saa7134[0]: found at 0000:02:03.0, rev: 1, irq: 185, latency: 32, mmio: 0xffdffc00
[17179593.316000] saa7134[0]: subsystem: 1131:0000, board: ASUS TV-FM 7134 [card=16,insmod option]
[17179593.316000] saa7134[0]: board init: gpio is c0407f
[17179593.424000] saa7134[0]: Huh, no eeprom present (err=-5)?
[17179593.448000] saa7134[0]: i2c scan: found device @ 0xc0  [tuner (analog)]
[17179593.460000] saa7134[0]: i2c scan: found device @ 0xc2  [???]
[17179593.508000] tuner 0-0060: TEA5767 detected.
[17179593.508000] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[17179593.512000] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[17179593.520000] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[17179593.520000] tuner 0-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
[17179593.536000] saa7134[0]: registered device video1 [v4l2]
[17179593.536000] saa7134[0]: registered device vbi0
[17179593.536000] saa7134[0]: registered device radio0
[17179593.536000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179593.536000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179593.552000] saa7134 ALSA driver for DMA sound loaded
[17179593.552000] saa7134[0]/alsa: saa7134[0] at 0xffdffc00 irq 185 registered as card -1
[17179593.856000] intel8x0_measure_ac97_clock: measured 58714 usecs
[17179593.856000] intel8x0: clocking to 48000
[17179593.964000] lp0: using parport0 (interrupt-driven).
[17179593.992000] Adding 1510068k swap on /dev/disk/by-uuid/fa353ac3-7e43-47bd-9547-8d9a5dbc972e.  Priority:-1 extents:1 across:1510068k
[17179594.060000] EXT3 FS on hda1, internal journal
[17179598.096000] kjournald starting.  Commit interval 5 seconds
[17179598.112000] EXT3 FS on hdb1, internal journal
[17179598.112000] EXT3-fs: mounted filesystem with ordered data mode.
[17179598.224000] NET: Registered protocol family 10
[17179598.224000] lo: Disabled Privacy Extensions
[17179598.224000] IPv6 over IPv4 tunneling driver
[17179599.344000] NET: Registered protocol family 17
[17179603.608000] ACPI: Power Button (FF) [PWRF]
[17179603.608000] ACPI: Power Button (CM) [PWRB]
[17179603.732000] ibm_acpi: ec object not found
[17179603.776000] pcc_acpi: loading...
[17179606.656000] [drm] Initialized drm 1.0.1 20051102
[17179606.664000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179606.664000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179607.532000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179607.532000] apm: disabled - APM is not SMP safe.
[17179608.056000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179608.056000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179608.056000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179608.356000] [drm] Setting GART location based on new memory map
[17179608.356000] [drm] Loading R200 Microcode
[17179608.356000] [drm] writeback test succeeded in 1 usecs
[17179608.628000] serial8250: too much work for irq169
[17179608.640000] serial8250: too much work for irq169
[17179608.656000] serial8250: too much work for irq169
[17179608.668000] serial8250: too much work for irq169
[17179608.680000] serial8250: too much work for irq169
[17179608.696000] serial8250: too much work for irq169
[17179608.720000] ttyS2: LSR safety check engaged!
[17179608.724000] eth0: no IPv6 routers present
[17179608.748000] serial8250: too much work for irq169
[17179608.760000] serial8250: too much work for irq169
[17179608.776000] serial8250: too much work for irq169
[17179608.788000] serial8250: too much work for irq169
[17179608.800000] serial8250: too much work for irq169
[17179612.176000] Bluetooth: L2CAP ver 2.8
[17179612.176000] Bluetooth: L2CAP socket layer initialized
[17179612.188000] Bluetooth: RFCOMM socket layer initialized
[17179612.188000] Bluetooth: RFCOMM TTY layer initialized
[17179612.188000] Bluetooth: RFCOMM ver 1.7
[17179612.260000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!


---

### Post by LeonHeart on 2006-12-14
Here's a short piece refering only to my tuner (dmesg|grep tuner):

> 
[17179593.448000] saa7134[0]: i2c scan: found device @ 0xc0  [tuner (analog)]
[17179593.508000] tuner 0-0060: TEA5767 detected.
[17179593.508000] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[17179593.512000] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[17179593.520000] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[17179593.520000] tuner 0-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))


---

### Post by LeonHeart on 2006-12-17
Guys, please anybody.
No clues?

---

