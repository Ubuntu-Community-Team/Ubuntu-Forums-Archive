---
title: "LIRC-No Output with irw or ircat"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by basketcase on 2007-02-10
General Specs: 
Shuttle XPC SN41G2
AMD 2400+
512MB RAM
PVR-350
Hauppauge Remote
Ubuntu 6.06

Myth Finally works, but I can't get the remote to work to change the channel and all that great jazz.  

Lirc starts w/o errors, using the lircd.conf from the wiki, have an lircrc.conf (again from the wiki).  

I start lirc, do an irw and it outputs nothing.  Do an ircat mythtv, and it outputs nothing (initially it gave an error regarding no lircrc, but I fixed that, and now it outputs nothing).  

I've followed the wiki for dapper, for edgy, I've compiled lirc from source from a topic here on the forums.  I just cannot get LIRC to work.  

pasted below is the entire output of dmesg, if there is something else you need, just say it.  

Thanks! 

btw, I have also reseated the PVR-350 card.  The computer had been powered down for about 3 minutes.  

```
root@mythtv:/etc/lirc# dmesg
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4. 0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map: 
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) 
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data) 
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved) 
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 479MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 122864
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0 
[17179569.184000]   Normal zone: 118768 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x0 00f6e00 
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x1dff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x1dff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x1dff7200 
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000d) @  0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000 ] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored. 
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information 
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e 0c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000 ] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000 ] Detected 1997.206 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.248000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes ) 
[17179569.248000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.260000] Memory: 476724k/491456k available (1977k kernel code, 14164k r eserved, 605k data, 288k init, 0k highmem)
[17179569.260000 ] Checking if this processor honours the WP bit even in supervis or mode... Ok.
[17179569.340000] Calibrating delay using timer specific routine.. 3998.49 BogoM IPS (lpj=7996984)
[17179569.340000] Security Framework  v1.0.0 initialized
[17179569.340000] SELinux:  Disabled at boot.
[17179569.340000] Mount-cache hash table entries: 512
[17179569.340000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 
[17179569.340000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 0 0000000 00000000 00000000 00000000
[17179569.340000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/li ne)
[17179569.340000 ] CPU: L2 Cache: 256K (64 bytes/line)
[17179569.340000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 0000042 0 00000000 00000000 00000000
[17179569.340000] mtrr: v2.0 (20020519)
[17179569.340000] CPU: AMD Athlon(tm) XP 2400+ stepping 01 
[17179569.340000] Enabling fast FPU save and restore... done.
[17179569.340000] Enabling unmasked SIMD FPU exception support... done.
[17179569.340000] Checking 'hlt' instruction... OK.
[17179569.356000 ] checking if image is initramfs... it is
[17179569.880000] Freeing initrd memory: 6616k freed
[17179569.896000] ACPI: Looking for DSDT ... not found!
[17179569.900000] ENABLING IO-APIC IRQs
[17179569.900000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1 
[17179570.044000] NET: Registered protocol family 16
[17179570.044000] EISA bus registered
[17179570.044000] ACPI: bus type pci registered
[17179570.060000] PCI: PCI BIOS revision 2.10 entry at 0xfb770, last bus=2 
[17179570.060000] PCI: Using configuration type 1
[17179570.060000] ACPI: Subsystem revision 20051216
[17179570.072000] ACPI: Interpreter enabled
[17179570.072000] ACPI: Using IOAPIC for interrupt routing
[17179570.072000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.072000] PCI: Probing PCI hardware (bus 00)
[17179570.076000] PCI: nForce2 C1 Halt Disconnect fixup
[17179570.076000] Boot video device is 0000:02: 00.0
[17179570.076000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.144000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.144000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT] 
[17179570.148000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15 ) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15 ) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 6 7 10 11 12 14 1 5) 
[17179570.148000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 10 11 12 14 15 ) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 *10 11 12 14 1 5)
[17179570.148000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 10 *11 12 14 1 5) 
[17179570.148000] ACPI: PCI Interrupt Link [LUBB] (IRQs *3 4 5 6 7 10 11 12 14 1 5)
[17179570.148000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 1 5)
[17179570.148000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 *11 12 14 1 5) 
[17179570.152000] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 6 7 10 11 12 14 1 5)
[17179570.152000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15 ) *0, disabled.
[17179570.152000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 11 12 14 15 ) *0, disabled. 
[17179570.152000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 10 11 12 14 1 5)
[17179570.152000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 *10 11 12 14 1 5)
[17179570.152000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15 ) *0, disabled. 
[17179570.152000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15 ) *0, disabled.
[17179570.152000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179570.152000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled. 
[17179570.152000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179570.152000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179570.152000] ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled. 
[17179570.152000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled. 
[17179570.156000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled. 
[17179570.156000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179570.156000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled. 
[17179570.156000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179570.160000] Linux Plug and Play Support v0.97  (c) Adam Belay
[17179570.160000] pnp: PnP ACPI init
[17179570.168000] pnp: PnP ACPI: found 13 devices
[17179570.168000] PnPBIOS: Disabled by ACPI PNP
[17179570.168000] PCI: Using ACPI for IRQ routing
[17179570.168000 ] PCI: If a device doesn't work, try "pci=routeirq".  If it help s, post a report
[17179570.212000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179570.212000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved 
[17179570.212000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179570.212000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179570.212000] pnp: 00:00: ioport range 0x4200-0x427f has been reserved 
[17179570.212000] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[17179570.212000] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[17179570.212000] pnp: 00:01: ioport range 0x5100-0x513f has been reserved 
[17179570.212000] PCI: Bridge: 0000:00:08.0
[17179570.212000]   IO window: disabled.
[17179570.212000]   MEM window: disabled.
[17179570.212000]   PREFETCH window: d4000000-d7ffffff
[17179570.212000] PCI: Bridge: 0000:00: 1e.0
[17179570.212000]   IO window: disabled.
[17179570.212000]   MEM window: e0000000-e1ffffff
[17179570.212000]   PREFETCH window: d8000000-dfffffff
[17179570.212000] PCI: Setting latency timer of device 0000:00: 08.0 to 64
[17179570.216000] audit: initializing netlink socket (disabled)
[17179570.216000] audit(1171123101.216:1): initialized
[17179570.216000] VFS: Disk quotas dquot_6.5.1
[17179570.216000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[17179570.216000] Initializing Cryptographic API
[17179570.216000] io scheduler noop registered
[17179570.216000] io scheduler anticipatory registered
[17179570.216000] io scheduler deadline registered
[17179570.216000 ] io scheduler cfq registered
[17179570.216000] isapnp: Scanning for PnP cards...
[17179570.572000] isapnp: No Plug & Play device found
[17179570.588000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[17179570.588000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.588000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.588000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar ing enabled 
[17179570.588000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.592000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.592000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b locksize 
[17179570.592000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.592000] ide: Assuming 33MHz system bus speed for PIO modes; override w ith idebus=xx
[17179570.592000] mice: PS/2 mouse device common for all mice 
[17179570.592000] EISA: Probing bus 0 at eisa.0
[17179570.592000] Cannot allocate resource for EISA slot 4
[17179570.592000] Cannot allocate resource for EISA slot 5
[17179570.592000] EISA: Detected 0 cards.
[17179570.592000] NET: Registered protocol family 2
[17179570.620000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.632000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes )
[17179570.632000] TCP established hash table entries: 16384 (order: 4, 65536 byt es)
[17179570.632000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.632000] TCP: Hash tables configured (established 16384 bind 16384) 
[17179570.632000] TCP reno registered
[17179570.632000] TCP bic registered
[17179570.632000] NET: Registered protocol family 1
[17179570.632000] NET: Registered protocol family 8
[17179570.632000] NET: Registered protocol family 20 
[17179570.632000] Using IPI Shortcut mode
[17179570.632000] ACPI wakeup devices:
[17179570.632000] HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
[17179570.632000] ACPI: (supports S0 S1 S4 S5)
[17179570.632000 ] Freeing unused kernel memory: 288k freed
[17179570.676000] vga16fb: initializing
[17179570.676000] vga16fb: mapped to 0xc00a0000
[17179570.812000] Console: switching to colour frame buffer device 80x25
[17179570.812000 ] fb0: VGA16 VGA frame buffer device
[17179571.880000] Capability LSM initialized
[17179572.016000] ACPI: Fan [FAN] (on)
[17179572.020000] ACPI: Thermal Zone [THRM] (40 C)
[17179572.584000] SCSI subsystem initialized 
[17179572.588000] ACPI: bus type scsi registered
[17179572.588000] libata version 1.20 loaded.
[17179572.592000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179572.592000] NFORCE2: chipset revision 162 
[17179572.592000] NFORCE2: not 100% native mode: will probe irqs later
[17179572.592000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workar ound.
[17179572.592000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller 
[17179572.592000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb :DMA
[17179572.592000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd :DMA
[17179572.592000] Probing IDE interface ide0... 
[17179572.880000] hda: QUANTUM FIREBALLP AS40.0, ATA DISK drive
[17179573.552000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.560000] Probing IDE interface ide1...
[17179574.296000] hdc: SONY CD-RW CRX320E, ATAPI CD/DVD-ROM drive 
[17179574.968000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.976000] hda: max request size: 128KiB
[17179574.984000] hda: 78177792 sectors (40027 MB) w/1902KiB Cache, CHS=65535/16 /63, UDMA(100)
[17179574.984000 ] hda: cache flushes not supported
[17179574.984000]  hda: hda1 hda2 < hda5 > hda3
[17179575.012000] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.012000] Uniform CD-ROM driver Revision:  3.20
[17179575.616000] usbcore: registered new driver usbfs
[17179575.616000] usbcore: registered new driver hub
[17179575.620000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI) 
[17179575.620000] **** SET: Misaligned resource pointer: dda980e2 Type 07 Len 0
[17179575.620000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179575.620000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 ( level, high) -> IRQ 177 
[17179575.620000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179575.620000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179575.620000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus nu mber 1 
[17179575.620000] ohci_hcd 0000:00:02.0: irq 177, io mem 0xe2080000
[17179575.660000] ieee1394: Initialized config rom entry `ip1394'
[17179575.676000] hub 1-0:1.0: USB hub found
[17179575.676000] hub 1-0: 1.0: 3 ports detected
[17179575.780000] **** SET: Misaligned resource pointer: dc877b02 Type 07 Len 0
[17179575.780000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179575.780000] ACPI: PCI Interrupt 0000:00: 02.1[b] -> Link [APCG] -> GSI 21 ( level, high) -> IRQ 185
[17179575.780000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179575.780000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179575.780000 ] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus nu mber 2
[17179575.780000] ohci_hcd 0000:00:02.1: irq 185, io mem 0xe2083000
[17179575.836000] hub 2-0:1.0: USB hub found
[17179575.836000] hub 2-0:1.0 : 3 ports detected
[17179575.940000] **** SET: Misaligned resource pointer: dc877802 Type 07 Len 0
[17179575.940000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179575.940000] ACPI: PCI Interrupt 0000:00: 02.2[C] -> Link [APCL] -> GSI 20 ( level, high) -> IRQ 193
[17179575.940000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179575.940000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179575.940000 ] ehci_hcd 0000:00:02.2: debug port 1
[17179575.940000] PCI: cache line size of 64 is not supported by device 0000:00: 02.2
[17179575.940000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus nu mber 3
[17179575.940000] ehci_hcd 0000:00:02.2: irq 193, io mem 0xe2086000
[17179575.940000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 D ec 2004
[17179575.940000] hub 3-0:1.0: USB hub found
[17179575.940000 ] hub 3-0:1.0: 6 ports detected
[17179576.044000] ohci1394: $Rev: 1313 $ Ben Collins <[EMAIL="bcollins@debian.org"]bcollins@debian.org[/EMAIL]>
[17179576.044000] **** SET: Misaligned resource pointer: dc877502 Type 07 Len 0 
[17179576.044000] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 22
[17179576.044000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [APCM] -> GSI 22 ( level, high) -> IRQ 177
[17179576.044000] PCI: Setting latency timer of device 0000:00: 0d.0 to 64
[17179576.100000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[e208 4000-e20847ff]  Max Packet=[2048]
[17179576.160000] Attempting manual resume
[17179576.196000] EXT3-fs: mounted filesystem with ordered data mode. 
[17179576.212000] kjournald starting.  Commit interval 5 seconds
[17179577.216000] ohci1394: fw-host0: SelfID received outside of bus reset seque nce
[17179577.512000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000301bade4f3 ] 
[17179585.480000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.492000] agpgart: Detected NVIDIA nForce2 chipset
[17179585.496000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179585.588000] forcedeth.c : Reverse Engineered nForce ethernet driver. Versio n 0.54.
[17179585.588000] **** SET: Misaligned resource pointer: ddd77b22 Type 07 Len 0
[17179585.588000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[17179585.588000 ] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 21 ( level, high) -> IRQ 185
[17179585.588000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179585.948000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000 
[17179585.948000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
[17179586.108000] eth0: forcedeth.c: subsystem: 01297:f541 bound to 0000:00:04.0
[17179586.140000] input: PC Speaker as /class/input/input1
[17179586.148000] **** SET: Misaligned resource pointer: ddd77722 Type 07 Len 0
[17179586.148000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[17179586.148000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 20 ( level, high) -> IRQ 193 
[17179586.148000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179586.156000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.204000] Floppy drive(s): fd0 is 1.44M
[17179586.236000] Real Time Clock Driver  v1.12
[17179586.236000] FDC 0 is a post-1991 82077
[17179586.456000] parport: PnPBIOS parport detected.
[17179586.456000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179586.472000] intel8x0_measure_ac97_clock: measured 55816 usecs 
[17179586.472000] intel8x0: clocking to 48000
[17179586.472000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.644000] nvidia: module license 'NVIDIA' taints kernel.
[17179586.712000 ] **** SET: Misaligned resource pointer: d9facac2 Type 07 Len 0
[17179586.712000] ACPI: PCI Interrupt Link [APCE] enabled at IRQ 16
[17179586.712000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APCE] -> GSI 16 ( level, high) -> IRQ 201 
[17179586.712000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
[17179586.908000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179586.932000] ts: Compaq touchscreen protocol output 
[17179587.352000] Linux video capture interface: v1.00
[17179587.460000] ivtv:  ==================== START INIT IVTV ================== ==
[17179587.460000] ivtv:  version 0.4.8 (tagged release) loading
[17179587.460000 ] ivtv:  Linux version: 2.6.15-28-386 preempt 486 gcc-4.0
[17179587.460000] ivtv:  In case of problems please include the debug info betwe en
[17179587.460000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with 
[17179587.460000] ivtv:  any module options, when mailing the ivtv-users mailing list.
[17179587.460000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[17179587.460000] **** SET: Misaligned resource pointer: d88ad902 Type 07 Len 0 
[17179587.460000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179587.460000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 ( level, high) -> IRQ 209
[17179587.460000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32) 
[17179587.520000] tveeprom: ivtv version
[17179587.520000] tveeprom: Hauppauge: model = 48132, rev = K268, serial# = 8603 000
[17179587.520000] tveeprom: tuner = LG TAPE H001F MK3 (idx = 68, type = 47)
[17179587.520000 ] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x0000100 0)
[17179587.520000] tveeprom: audio processor = MSP4448 (type = 1b)
[17179587.520000] tveeprom: decoder processor = SAA7115 (type = 13)
[17179587.520000 ] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179587.536000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17179587.536000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61 ] 
[17179587.760000] saa7115 2-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179587.920000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[17179587.980000] saa7127 2-0044: ivtv driver
[17179587.984000 ] saa7127 2-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[17179587.988000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[17179588.024000] msp3400 2-0040: chip=MSP4448G-B3 +nicam +simple +simpler +radi o mode=simpler 
[17179588.024000] msp3400 2-0040: msp34xxg daemon started
[17179588.052000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-B3, addr=40]
[17179588.072000] tda9887 2-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0) 
[17179588.072000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17179588.508000] NET: Registered protocol family 17
[17179588.780000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179588.832000 ] NET: Registered protocol family 10
[17179588.832000] lo: Disabled Privacy Extensions
[17179588.832000] IPv6 over IPv4 tunneling driver
[17179588.876000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[17179589.100000] ivtv0: Encoder revision: 0x02050032
[17179589.108000] ivtv0: Decoder revision: 0x02020023
[17179589.108000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers ( 4096KB total)
[17179589.108000 ] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2 048KB total)
[17179589.108000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2 048KB total)
[17179589.108000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffe rs (2048KB total) 
[17179589.108000] ivtv0: Create encoder radio stream
[17179589.108000] ivtv0: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (1 024KB total)
[17179589.108000] ivtv0: Allocate DMA decoder VBI stream: 512 x 2048 buffers (10 24KB total) 
[17179589.108000] ivtv0: Create decoder VOUT stream
[17179589.108000] ivtv0: Allocate DMA decoder YUV stream: 24 x 43200 buffers (10 24KB total)
[17179589.180000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes) 
[17179589.292000] tuner: type set to 47 (LG NTSC (TAPE series)) by ivtv i2c driv er #0
[17179589.488000] ivtv0: Initialized WinTV PVR 350, card #0
[17179589.488000] ivtv:  ====================  END INIT IVTV  ================== == 
[17179589.904000] lp0: using parport0 (interrupt-driven).
[17179589.936000] sbp2: $Rev: 1306 $ Ben Collins <[EMAIL="bcollins@debian.org"]bcollins@debian.org[/EMAIL]>
[17179589.936000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1 ) 
[17179589.936000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179590.008000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 acro ss:1413680k
[17179590.164000] EXT3 FS on hda1, internal journal 
[17179590.348000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179590.348000] md: bitmap version 4.39
[17179590.832000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@ [ redhat.com]("http://redhat.com/")
[17179591.548000] cdrom: open failed.
[17179592.208000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179592.208000] SGI XFS Quota Management subsystem
[17179592.236000] XFS mounting filesystem hda3
[17179592.320000] Ending clean XFS mount for filesystem: hda3
[17179593.492000] ACPI: Power Button (FF) [PWRF]
[17179593.492000] ACPI: Power Button (CM) [PWRB]
[17179593.596000 ] ibm_acpi: ec object not found
[17179593.628000] pcc_acpi: loading...
[17179599.588000] eth0: no IPv6 routers present
[17179601.984000] ppdev: user-space parallel port driver
[17179602.208000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179602.212000] lirc_i2c: no version for "lirc_unregister_plugin" found: kerne l tainted.
[17179602.280000] bttv: disagrees about version of symbol tveeprom_hauppauge_ana log
[17179602.280000] bttv: Unknown symbol tveeprom_hauppauge_analog 
[17179602.348000] cx88xx: disagrees about version of symbol tveeprom_hauppauge_a nalog
[17179602.348000] cx88xx: Unknown symbol tveeprom_hauppauge_analog
[17179602.352000] cx8800: Unknown symbol cx88_reset
[17179602.352000 ] cx8800: Unknown symbol cx88_call_i2c_clients
[17179602.352000] cx8800: Unknown symbol cx88_wakeup
[17179602.352000] cx8800: Unknown symbol cx88_risc_stopper
[17179602.352000] cx8800: Unknown symbol cx88_print_irqbits 
[17179602.352000] cx8800: Unknown symbol cx88_set_scale
[17179602.352000] cx8800: Unknown symbol cx88_shutdown
[17179602.352000] cx8800: Unknown symbol cx88_vdev_init
[17179602.352000] cx8800: Unknown symbol cx88_core_put 
[17179602.352000] cx8800: Unknown symbol cx88_audio_thread
[17179602.352000] cx8800: Unknown symbol cx88_core_irq
[17179602.352000] cx8800: Unknown symbol cx88_core_get
[17179602.352000] cx8800: Unknown symbol cx88_get_stereo 
[17179602.352000] cx8800: Unknown symbol cx88_set_tvnorm
[17179602.352000] cx8800: Unknown symbol cx88_risc_buffer
[17179602.352000] cx8800: Unknown symbol cx88_set_stereo
[17179602.352000] cx8800: Unknown symbol cx88_sram_channels 
[17179602.352000] cx8800: Unknown symbol cx88_set_tvaudio
[17179602.352000] cx8800: Unknown symbol cx88_sram_channel_dump
[17179602.352000] cx8800: Unknown symbol cx88_sram_channel_setup
[17179602.352000] cx8800: Unknown symbol cx88_print_ioctl 
[17179602.352000] cx8800: Unknown symbol cx88_free_buffer
[17179602.352000] cx8800: Unknown symbol cx88_boards
[17179602.352000] cx8800: Unknown symbol cx88_newstation
[17179602.372000] lirc_i2c: chip found @ 0x18 (Hauppauge IR) 
[17179602.372000] ivtv0: i2c attach to card #0 ok [client=Hauppauge IR, addr=18]
[17179602.372000] lirc_dev: lirc_register_plugin: sample_rate: 10
[17179602.616000] apm: BIOS version 1.2 Flags 0x07 (Driver version  1.16ac)
[17179602.616000] apm: overridden by ACPI.
[17179604.820000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179604.820000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179604.820000 ] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
[17179605.784000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179605.784000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode 
[17179605.784000] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
[17179613.592000] Bluetooth: Core ver 2.8
[17179613.592000] NET: Registered protocol family 31
[17179613.592000] Bluetooth: HCI device and connection manager initialized 
[17179613.592000] Bluetooth: HCI socket layer initialized
[17179613.620000] Bluetooth: L2CAP ver 2.8
[17179613.620000] Bluetooth: L2CAP socket layer initialized
[17179613.624000] Bluetooth: RFCOMM socket layer initialized 
[17179613.624000] Bluetooth: RFCOMM TTY layer initialized
[17179613.624000] Bluetooth: RFCOMM ver 1.7

```

---

### Post by basketcase on 2007-02-10
Well per the Wiki, I had to irrecord my remote.  Missed a few buttons, now that I know how to work it, as I get more time in Myth, I'll know what I want my videos to be.

---

