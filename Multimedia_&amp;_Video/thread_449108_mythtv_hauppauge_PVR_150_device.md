---
title: "mythtv hauppauge PVR 150 device?"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by mmcmonster on 2007-05-19
Hi.
  I'm setting up a new system (running Fiesty, of course) and can't figure out which device name my hauppauge PVR 150 card is.

I checked /dev, and there is no /dev/video*.

Is there any way to probe the system and see the device name?

---

### Post by fenian on 2007-05-19
Its probably /dev/video0 to see if the card is working (it should work out of the box in Feisty) use mplayer with this command...

> mplayer /dev/video0

it may display only static if the channel its set to has no signal , don't panic use this command to change tuner channels...
> 
ivtv-tune -c # -d /dev/video0 

replace # with the channel number you want to tune (if you connect to a cable or sat settop box set the channel to 3 if you connect directly to an antennae or other analog source set it to a working channel number)

---

### Post by mmcmonster on 2007-05-19
That's not it. :-(  As you can see I have nothing close to /dev/video0. :-(
```

mythtv@myth:/dev$ ls /dev/v*
/dev/vcs   /dev/vcs3  /dev/vcs6  /dev/vcsa   /dev/vcsa3  /dev/vcsa6
/dev/vcs1  /dev/vcs4  /dev/vcs7  /dev/vcsa1  /dev/vcsa4  /dev/vcsa7
/dev/vcs2  /dev/vcs5  /dev/vcs8  /dev/vcsa2  /dev/vcsa5  /dev/vcsa8
mythtv@myth:/dev$ 

```I also have the ivtv drivers installed:
```
$ dpkg -l | grep ivtv
ii  ivtv-firmware                              0.20070217                             Firmware used by the IVTV project
ii  ivtv-utils                                 0.10.1-0ubuntu1                        utilities for use with the ivtv kernel drive
ii  libvideo-ivtv-perl                         0.13-3                                 Perl extension for using V4l2 in the ivtv pe

```

---

### Post by fenian on 2007-05-19
what do you get if you run the command...

> dmesg?

---

### Post by mmcmonster on 2007-05-20
```

$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fdf0000 end: 000000003fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fef0000 size: 0000000000003000 end: 000000003fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fef3000 size: 000000000000d000 end: 000000003ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f39d0
[    0.000000] Entering add_active_range(0, 0, 261872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7af0
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef30c0
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x3fef95c0
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef9700
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef9500
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] Detected 2210.155 MHz processor.
[   31.056881] Built 1 zonelists.  Total pages: 259827
[   31.056884] Kernel command line: root=UUID=a1fed7aa-681d-46de-8bda-1ba749f4aa5d ro quiet splash
[   31.056997] mapped APIC to ffffd000 (fee00000)
[   31.056999] mapped IOAPIC to ffffc000 (fec00000)
[   31.057001] Enabling fast FPU save and restore... done.
[   31.057003] Enabling unmasked SIMD FPU exception support... done.
[   31.057009] Initializing CPU#0
[   31.057052] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   31.059149] Console: colour VGA+ 80x25
[   31.059431] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.059748] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.075690] Memory: 1027052k/1047488k available (1992k kernel code, 19692k reserved, 893k data, 328k init, 129984k highmem)
[   31.075698] virtual kernel memory layout:
[   31.075699]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   31.075700]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.075701]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   31.075702]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   31.075703]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   31.075704]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   31.075705]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   31.075708] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.152994] Calibrating delay using timer specific routine.. 4424.09 BogoMIPS (lpj=8848197)
[   31.153026] Security Framework v1.0.0 initialized
[   31.153032] SELinux:  Disabled at boot.
[   31.153044] Mount-cache hash table entries: 512
[   31.153149] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   31.153156] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   31.153158] CPU: L2 Cache: 512K (64 bytes/line)
[   31.153160] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   31.153168] Compat vDSO mapped to ffffe000.
[   31.153172] Remapping vsyscall page to ffffe000
[   31.153180] Checking 'hlt' instruction... OK.
[   31.169084] SMP alternatives: switching to UP code
[   31.169232] Freeing SMP alternatives: 11k freed
[   31.169388] Early unpacking initramfs... done
[   31.428661] ACPI: Core revision 20060707
[   31.431931] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   31.437053] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 02
[   31.437068] Total of 1 processors activated (4424.09 BogoMIPS).
[   31.437368] ENABLING IO-APIC IRQs
[   31.437599] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   31.584734] Brought up 1 CPUs
[   31.584921] Booting paravirtualized kernel on bare hardware
[   31.584977] Time: 19:52:30  Date: 04/20/107
[   31.584996] NET: Registered protocol family 16
[   31.585056] EISA bus registered
[   31.585058] ACPI: bus type pci registered
[   31.591485] PCI: PCI BIOS revision 3.00 entry at 0xfa7c0, last bus=4
[   31.591486] PCI: Using configuration type 1
[   31.591488] Setting up standard PCI resources
[   31.601304] ACPI: Interpreter enabled
[   31.601306] ACPI: Using IOAPIC for interrupt routing
[   31.601748] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.601751] PCI: Probing PCI hardware (bus 00)
[   31.604409] Boot video device is 0000:03:00.0
[   31.604643] PCI: Transparent bridge - 0000:00:10.0
[   31.604675] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.712389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   31.713862] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[   31.714153] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[   31.714439] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[   31.714723] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[   31.715008] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
[   31.715293] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   31.715578] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   31.715863] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   31.716149] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   31.716434] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   31.716728] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   31.717013] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 *11 14 15)
[   31.717297] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   31.717586] ACPI: PCI Interrupt Link [LPMU] (IRQs *5 7 9 10 11 14 15)
[   31.717870] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   31.718156] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   31.718448] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   31.718734] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   31.719020] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[   31.719312] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[   31.719676] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   31.720027] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   31.720378] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   31.720735] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   31.721086] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   31.721440] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   31.721792] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   31.722142] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   31.722494] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   31.722847] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   31.723199] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   31.723551] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   31.723904] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   31.724256] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   31.724623] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   31.724975] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   31.725325] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   31.725680] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   31.726031] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   31.726381] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   31.726732] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   31.729490] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.729498] pnp: PnP ACPI init
[   31.736438] pnp: PnP ACPI: found 13 devices
[   31.736442] PnPBIOS: Disabled by ACPI PNP
[   31.736479] PCI: Using ACPI for IRQ routing
[   31.736482] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.826790] NET: Registered protocol family 8
[   31.826792] NET: Registered protocol family 20
[   31.827217] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[   31.827219] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   31.827222] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   31.827224] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[   31.827226] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   31.827228] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   31.827231] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[   31.827233] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[   31.827404] PCI: Bridge: 0000:00:02.0
[   31.827407]   IO window: 8000-8fff
[   31.827410]   MEM window: fdd00000-fddfffff
[   31.827412]   PREFETCH window: fdb00000-fdbfffff
[   31.827415] PCI: Bridge: 0000:00:03.0
[   31.827416]   IO window: a000-afff
[   31.827419]   MEM window: fda00000-fdafffff
[   31.827421]   PREFETCH window: fde00000-fdefffff
[   31.827426] PCI: Bridge: 0000:00:04.0
[   31.827427]   IO window: 9000-9fff
[   31.827430]   MEM window: fa000000-fcffffff
[   31.827432]   PREFETCH window: c0000000-cfffffff
[   31.827436] PCI: Bridge: 0000:00:10.0
[   31.827438]   IO window: b000-bfff
[   31.827441]   MEM window: d8000000-dfffffff
[   31.827444]   PREFETCH window: fdc00000-fdcfffff
[   31.827455] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.827461] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   31.827466] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   31.827473] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   31.827492] NET: Registered protocol family 2
[   31.864567] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.864679] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.865285] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.865617] TCP: Hash tables configured (established 131072 bind 65536)
[   31.865619] TCP reno registered
[   31.876604] checking if image is initramfs... it is
[   32.386051] Freeing initrd memory: 7011k freed
[   32.386349] audit: initializing netlink socket (disabled)
[   32.386359] audit(1179690750.416:1): initialized
[   32.386405] highmem bounce pool size: 64 pages
[   32.386445] VFS: Disk quotas dquot_6.5.1
[   32.386459] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.386495] io scheduler noop registered
[   32.386497] io scheduler anticipatory registered
[   32.386499] io scheduler deadline registered
[   32.386505] io scheduler cfq registered (default)
[   40.406564] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   40.406710] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   40.406730] assign_interrupt_mode Found MSI capability
[   40.406733] Allocate Port Service[0000:00:02.0:pcie00]
[   40.406783] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   40.406802] assign_interrupt_mode Found MSI capability
[   40.406808] Allocate Port Service[0000:00:03.0:pcie00]
[   40.406857] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   40.406877] assign_interrupt_mode Found MSI capability
[   40.406878] Allocate Port Service[0000:00:04.0:pcie00]
[   40.406958] isapnp: Scanning for PnP cards...
[   40.759817] isapnp: No Plug & Play device found
[   40.776215] Real Time Clock Driver v1.12ac
[   40.776253] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   40.776364] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   40.776511] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   40.776921] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   40.777078] mice: PS/2 mouse device common for all mice
[   40.777407] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   40.777556] input: Macintosh mouse button emulation as /class/input/input0
[   40.777577] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   40.777579] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   40.777742] PNP: No PS/2 controller found. Probing ports directly.
[   40.780591] serio: i8042 KBD port at 0x60,0x64 irq 1
[   40.780595] serio: i8042 AUX port at 0x60,0x64 irq 12
[   40.780733] EISA: Probing bus 0 at eisa.0
[   40.780740] Cannot allocate resource for EISA slot 1
[   40.780742] Cannot allocate resource for EISA slot 2
[   40.780756] Cannot allocate resource for EISA slot 8
[   40.780758] EISA: Detected 0 cards.
[   40.810810] TCP cubic registered
[   40.810815] NET: Registered protocol family 1
[   40.810831] Using IPI No-Shortcut mode
[   40.810865] ACPI: (supports S0 S3 S4 S5)
[   40.810905]   Magic number: 7:850:900
[   40.810971]   hash matches device ptyvd
[   40.811169] Freeing unused kernel memory: 328k freed
[   40.814536] Time: tsc clocksource has been installed.
[   42.018791] Capability LSM initialized
[   42.047748] ACPI: Fan [FAN] (on)
[   42.050488] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   42.051822] ACPI: Thermal Zone [THRM] (-10 C)
[   42.529842] usbcore: registered new interface driver usbfs
[   42.529863] usbcore: registered new interface driver hub
[   42.529878] usbcore: registered new device driver usb
[   42.530375] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   42.530800] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   42.530811] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   42.530822] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   42.530825] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   42.530927] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   42.530943] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
[   42.547559] SCSI subsystem initialized
[   42.551086] libata version 2.20 loaded.
[   42.586367] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   42.607244] usb usb1: configuration #1 chosen from 1 choice
[   42.607270] hub 1-0:1.0: USB hub found
[   42.607279] hub 1-0:1.0: 8 ports detected
[   42.686374] ieee1394: Initialized config rom entry `ip1394'
[   42.715193] sata_nv 0000:00:0e.0: version 3.3
[   42.715602] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[   42.715612] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[   42.715628] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   42.715665] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 17
[   42.720374] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 17
[   42.720394] scsi0 : sata_nv
[   42.758897] FDC 0 is a post-1991 82077
[   43.016746] usb 1-5: new low speed USB device using ohci_hcd and address 2
[   43.188648] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   43.196880] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   43.196884] ata1.00: ATA-7: ST3250823AS, 3.03, max UDMA/133
[   43.196886] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   43.208873] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   43.208876] ata1.00: configured for UDMA/133
[   43.208884] scsi1 : sata_nv
[   43.222759] usb 1-5: configuration #1 chosen from 1 choice
[   43.524396] ata2: SATA link down (SStatus 0 SControl 300)
[   43.534833] ATA: abnormal status 0x7F on port 0x00010977
[   43.534935] scsi 0:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[   43.535914] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[   43.535924] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 21 (level, low) -> IRQ 18
[   43.535943] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   43.535971] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001cc00 irq 18
[   43.535988] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001cc08 irq 18
[   43.536002] scsi2 : sata_nv
[   43.540386] usb 1-6: new full speed USB device using ohci_hcd and address 3
[   43.850328] usb 1-6: configuration #1 chosen from 1 choice
[   44.004091] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   44.013222] ata3.00: ata_hpa_resize 1: sectors = 490234752, hpa_sectors = 490234752
[   44.013227] ata3.00: ATA-7: Maxtor 6V250F0, VA111630, max UDMA/133
[   44.013229] ata3.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   44.025188] ata3.00: ata_hpa_resize 1: sectors = 490234752, hpa_sectors = 490234752
[   44.025191] ata3.00: configured for UDMA/133
[   44.025199] scsi3 : sata_nv
[   44.163952] usb 1-8: new low speed USB device using ohci_hcd and address 4
[   44.339832] ata4: SATA link down (SStatus 0 SControl 300)
[   44.350267] ATA: abnormal status 0x7F on port 0x00010967
[   44.350349] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6V250F0   VA11 PQ: 0 ANSI: 5
[   44.352210] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[   44.352221] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 19
[   44.352227] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   44.352233] forcedeth: using HIGHDMA
[   44.376948] usb 1-8: configuration #1 chosen from 1 choice
[   44.380000] usbcore: registered new interface driver hiddev
[   44.392978] input: Acer MCE Receiver as /class/input/input1
[   44.393011] input,hiddev96: USB HID v1.10 Keyboard [Acer MCE Receiver] on usb-0000:00:0b.0-5
[   44.397957] input: Logitech USB Receiver as /class/input/input2
[   44.397969] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0b.0-8
[   44.407960] input: Logitech USB Receiver as /class/input/input3
[   44.407988] input,hiddev97: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-8
[   44.407998] usbcore: registered new interface driver usbhid
[   44.408000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   44.408062] usbcore: registered new interface driver libusual
[   44.410834] Initializing USB Mass Storage driver...
[   44.410879] scsi4 : SCSI emulation for USB Mass Storage devices
[   44.410915] usbcore: registered new interface driver usb-storage
[   44.410917] USB Mass Storage support registered.
[   44.410980] usb-storage: device found at 3
[   44.410982] usb-storage: waiting for device to settle before scanning
[   44.875711] eth0: forcedeth.c: subsystem: 0105b:0caf bound to 0000:00:14.0
[   44.876327] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   44.876331] ACPI: PCI Interrupt 0000:00:0b.1[b] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
[   44.876341] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   44.876343] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   44.876369] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   44.876393] ehci_hcd 0000:00:0b.1: debug port 1
[   44.876396] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   44.876404] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xfe02e000
[   44.876411] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.876445] usb 1-5: USB disconnect, address 2
[   44.876503] usb usb2: configuration #1 chosen from 1 choice
[   44.876527] hub 2-0:1.0: USB hub found
[   44.876533] hub 2-0:1.0: 8 ports detected
[   44.983921] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   44.983932] ACPI: PCI Interrupt 0000:04:06.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[   45.033632] usb 1-6: USB disconnect, address 3
[   45.033834] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[dffff000-dffff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   45.034304] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   45.034312] ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   45.034317] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[   45.034322] 0000:04:07.0: 3Com PCI 3c905B Cyclone 100baseTx at f8856000.
[   45.056075] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   45.056088] NFORCE-MCP51: chipset revision 161
[   45.056090] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   45.056096] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   45.056103]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
[   45.056110]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:DMA
[   45.056116] Probing IDE interface ide0...
[   45.071706] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   45.072104] sda: Write Protect is off
[   45.072106] sda: Mode Sense: 00 3a 00 00
[   45.072119] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.072158] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   45.072164] sda: Write Protect is off
[   45.072165] sda: Mode Sense: 00 3a 00 00
[   45.072175] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.072177]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[   45.134817] sd 0:0:0:0: Attached scsi disk sda
[   45.134936] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
[   45.134945] sdb: Write Protect is off
[   45.134947] sdb: Mode Sense: 00 3a 00 00
[   45.134957] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.134985] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
[   45.134991] sdb: Write Protect is off
[   45.134993] sdb: Mode Sense: 00 3a 00 00
[   45.135002] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.135005]  sdb:<6>usb 1-8: USB disconnect, address 4
[   45.174131]  sdb1 < sdb5 >
[   45.174844] sd 2:0:0:0: Attached scsi disk sdb
[   45.178470] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   45.178555] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   45.445833] Attempting manual resume
[   45.445836] swsusp: Resume From Partition 8:6
[   45.445838] PM: Checking swsusp image.
[   45.446005] PM: Resume from disk failed.
[   45.468727] kjournald starting.  Commit interval 5 seconds
[   45.468736] EXT3-fs: mounted filesystem with ordered data mode.
[   45.626938] Probing IDE interface ide1...
[   45.718876] usb 2-6: new high speed USB device using ehci_hcd and address 3
[   45.945078] usb 2-6: configuration #1 chosen from 1 choice
[   45.945827] scsi5 : SCSI emulation for USB Mass Storage devices
[   45.945859] usb-storage: device found at 3
[   45.945861] usb-storage: waiting for device to settle before scanning
[   46.306556] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200012ce13]
[   46.366524] hdc: HL-DT-STDVDRRW GWA-4164B, ATAPI CD/DVD-ROM drive
[   46.434374] usb 1-5: new low speed USB device using ohci_hcd and address 5
[   46.640297] usb 1-5: configuration #1 chosen from 1 choice
[   46.658311] input: Acer MCE Receiver as /class/input/input4
[   46.658338] input,hiddev96: USB HID v1.10 Keyboard [Acer MCE Receiver] on usb-0000:00:0b.0-5
[   46.962008] usb 1-8: new low speed USB device using ohci_hcd and address 6
[   47.149982] hdd: HL-DT-STDVD-ROM GDR8164B, ATAPI CD/DVD-ROM drive
[   47.183908] usb 1-8: configuration #1 chosen from 1 choice
[   47.193922] input: Logitech USB Receiver as /class/input/input5
[   47.193930] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0b.0-8
[   47.203936] input: Logitech USB Receiver as /class/input/input6
[   47.203958] input,hiddev97: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-8
[   47.207325] ide1 at 0x170-0x177,0x376 on irq 15
[   50.943459] usb-storage: device scan complete
[   50.974561] scsi 5:0:0:0: Direct-Access     Generic  2.0 Reader-CF    1.00 PQ: 0 ANSI: 0 CCS
[   51.005535] scsi 5:0:0:1: Direct-Access     Generic  2.0 Reader-SM/xD 1.00 PQ: 0 ANSI: 0 CCS
[   51.036515] scsi 5:0:0:2: Direct-Access     Generic  2.0 Reader-SD    1.00 PQ: 0 ANSI: 0 CCS
[   51.067517] scsi 5:0:0:3: Direct-Access     Generic  2.0 Reader-MS    1.00 PQ: 0 ANSI: 0 CCS
[   51.069496] sd 5:0:0:0: Attached scsi removable disk sdc
[   51.069520] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   51.071487] sd 5:0:0:1: Attached scsi removable disk sdd
[   51.071507] sd 5:0:0:1: Attached scsi generic sg3 type 0
[   51.073548] sd 5:0:0:2: Attached scsi removable disk sde
[   51.073570] sd 5:0:0:2: Attached scsi generic sg4 type 0
[   51.075490] sd 5:0:0:3: Attached scsi removable disk sdf
[   51.075512] sd 5:0:0:3: Attached scsi generic sg5 type 0
[   52.262762] eth1:  setting half-duplex.
[   52.283874] eth0: no link during initialization.
[   53.617801] NET: Registered protocol family 17
[   53.817111] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   53.818588] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   54.377596] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   54.377619] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   54.521690] Linux agpgart interface v0.102 (c) Dave Jones
[   54.597586] ath_hal: module license 'Proprietary' taints kernel.
[   54.598114] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   54.637285] input: PC Speaker as /class/input/input7
[   54.885005] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   54.885013] Uniform CD-ROM driver Revision: 3.20
[   54.889688] hdd: ATAPI 48X DVD-ROM drive, 256kB Cache, UDMA(33)
[   54.950670] wlan: 0.8.4.2 (0.9.3)
[   54.965301] ath_pci: 0.9.4.5 (0.9.3)
[   54.965747] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   54.965757] ACPI: PCI Interrupt 0000:04:09.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 22
[   55.569225] parport: PnPBIOS parport detected.
[   55.569278] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   55.638993] ath_rate_sample: 1.2 (0.9.3)
[   55.640024] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   55.640030] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   55.640037] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   55.640042] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   55.640045] wifi0: mac 7.9 phy 4.5 radio 5.6
[   55.640048] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   55.640050] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   55.640052] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   55.640053] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   55.640055] wifi0: Use hw queue 8 for CAB traffic
[   55.640056] wifi0: Use hw queue 9 for beacons
[   55.647820] irda_init()
[   55.647838] NET: Registered protocol family 23
[   55.691754] wifi0: Atheros 5212: mem=0xdffe0000, irq=22
[   55.871175] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   55.871180] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   55.871200] PCI: Setting latency timer of device 0000:00:10.2 to 64
[   56.195625] intel8x0_measure_ac97_clock: measured 58688 usecs
[   56.195628] intel8x0: clocking to 46950
[   56.347843] fuse init (API version 7.8)
[   56.363066] lp0: using parport0 (interrupt-driven).
[   56.409999] Adding 1020088k swap on /dev/disk/by-uuid/0a7e2ebb-2f1e-4730-90a3-12fb6d18f359.  Priority:-1 extents:1 across:1020088k
[   56.601687] EXT3 FS on sda5, internal journal
[   60.495710] NET: Registered protocol family 10
[   60.495788] lo: Disabled Privacy Extensions
[   60.495832] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.495834] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   71.472995] ath0: no IPv6 routers present
[  350.947655] kjournald starting.  Commit interval 5 seconds
[  350.947902] EXT3 FS on sda7, internal journal
[  350.947906] EXT3-fs: mounted filesystem with ordered data mode.
[  350.991822] kjournald starting.  Commit interval 5 seconds
[  350.992032] EXT3 FS on sdb5, internal journal
[  350.992036] EXT3-fs: mounted filesystem with ordered data mode.
[  351.201441] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  351.243474] NTFS volume version 3.1.
[  355.952010] Using specific hotkey driver
[  356.008200] input: Power Button (FF) as /class/input/input8
[  356.008383] ACPI: Power Button (FF) [PWRF]
[  356.038002] input: Power Button (CM) as /class/input/input9
[  356.039565] ACPI: Power Button (CM) [PWRB]
[  356.053161] ibm_acpi: ec object not found
[  356.152120] No dock devices found.
[  356.183750] pcc_acpi: loading...
[  356.417248] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
[  356.417285] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[  356.417287] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[  356.417289] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[  356.417291] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[  359.916739] ppdev: user-space parallel port driver
[  364.430556] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  364.430560] apm: overridden by ACPI.
[  364.861248] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  365.167154] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  365.167702] NFSD: starting 90-second grace period
[  334.728000] Time: acpi_pm clocksource has been installed.
[  337.856000] Bluetooth: Core ver 2.11
[  337.856000] NET: Registered protocol family 31
[  337.856000] Bluetooth: HCI device and connection manager initialized
[  337.856000] Bluetooth: HCI socket layer initialized
[  337.912000] Bluetooth: L2CAP ver 2.8
[  337.912000] Bluetooth: L2CAP socket layer initialized
[  337.916000] Bluetooth: RFCOMM socket layer initialized
[  337.916000] Bluetooth: RFCOMM TTY layer initialized
[  337.916000] Bluetooth: RFCOMM ver 1.8
[ 2465.364000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 2479.152000] ath0: no IPv6 routers present

```

---

### Post by fenian on 2007-05-20
There seems to be a problem with ivtv not seeing your card, the dmesg output should have a section that looks something like this...
> 
[   41.286032] ivtv:  ==================== START INIT IVTV ====================
[   41.286037] ivtv:  version 0.9.1 (tagged release) loading
[   41.286039] ivtv:  Linux version: 2.6.20-9-generic SMP mod_unload 586 
[   41.286041] ivtv:  In case of problems please include the debug info between
[   41.286043] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   41.286045] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   41.286149] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   41.286403] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   41.286412] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 20
[   41.286424] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   41.451705] Floppy drive(s): fd0 is 1.44M
[   41.476958] FDC 0 is a post-1991 82077
[   41.488241] parport: PnPBIOS parport detected.
[   41.488303] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   42.061771] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   42.263289] **WARNING** I2C adapter driver [ivtv i2c driver #0] forgot to specify physical device; fix it!
[   42.328943] tveeprom 2-0050: Hauppauge model 26034, rev C197, serial# 8087217
[   42.328948] tveeprom 2-0050: tuner model is TCL 2002MB_3H (idx 97, type 55)
[   42.328952] tveeprom 2-0050: TV standards PAL(B/G) PAL(D/D1/K) (eeprom 0x44)
[   42.328955] tveeprom 2-0050: audio processor is CX25842 (idx 36)
[   42.328957] tveeprom 2-0050: decoder processor is CX25842 (idx 29)
[   42.328959] tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
[   42.328962] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   42.328964] ivtv0: reopen i2c bus for IR-blaster support
[   42.346564] **WARNING** I2C adapter driver [ivtv i2c driver #0] forgot to specify physical device; fix it!
[   42.436586] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   42.651234] cx25840 2-0044: cx25842-23 found @ 0x88 (ivtv i2c driver #0)
[   47.063772] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   47.189684] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   47.267206] ivtv0: Encoder revision: 0x02050032
[   47.267266] ivtv0: Registered device video0 for encoder MPEG
[   47.267494] ivtv0: Registered device video32 for encoder YUV
[   47.267685] ivtv0: Registered device vbi0 for encoder VBI
[   47.267801] ivtv0: Registered device video24 for encoder PCM audio
[   47.268244] tuner 2-0061: type set to 55 (TCL 2002MB)
[   47.629167] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   47.629189] ivtv:  ====================  END INIT IVTV  ====================

First see if the card is recognized run...

> lspci
 there should be a line that looks something like this...
> 
02:06.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)

If not you should check if the card is seated properly in the PCI slot.Sometimes it can become loose from plugging and unplugging cables.Take the card out and put it back in.
You can also try putting it in a different PCI slot if one is available.

---

### Post by mmcmonster on 2007-05-23
Sorry so long for the reply.
```

$ lspci | grep video
04:08.0 Multimedia video controller: Conexant Unknown device 5b7a

```
I'm not sure if this means there is a problem with my device or if it's a system problem. :-(

---

### Post by mmcmonster on 2007-05-24
According to [this thread]("http://www.gossamer-threads.com/lists/ivtv/users/34967"), I apparently don't have a PVR-150???!!!

I bought the card from New Egg.  Should I contact them, or am I jumping the gun?

---

### Post by tgm4883 on 2007-05-24
Sounds like you have the HVR-1600.  Hauppauge "Upgraded" people because they didn't have enough PVR-150's to fill demand so they put HVR-1600's in the PVR-150 boxes.  You can contact them and they should replace it, although I didn't think they were "upgrading" people anymore.  

First things first though, take the card out and make sure it's not a PVR-150.

There is also HVR-1600 support in the works, although I don't know how far along they are.  You could try emailing hauppauge to see.

[http://www.hauppauge.com/pages/support/support_hvr1600.html](http://www.hauppauge.com/pages/support/support_hvr1600.html)
See the bottom of the page

---

### Post by gruvsyco on 2007-05-24
> **fenian said:**
> Its probably /dev/video0 to see if the card is working (it should work out of the box in Feisty) use mplayer with this command...



it may display only static if the channel its set to has no signal , don't panic use this command to change tuner channels...


replace # with the channel number you want to tune (if you connect to a cable or sat settop box set the channel to 3 if you connect directly to an antennae or other analog source set it to a working channel number)

Just wanted to say thanks for that little tidbit.  I knew my tuner was working, as when I had installed the MythTV packages that take over your install, I could get TV but the standalone front end didn't (even with the same backend).  This little piece at least allows me to watch some TV.

---

### Post by tgm4883 on 2007-05-24
So your card is working in Linux?  Can you check your card to see if it is in fact a HVR-1600.

---

### Post by mmcmonster on 2007-05-24
I have the HVR-1600, and it most decidedly does _**not**_ work in Fiesty. :-(

I'm kind of annoyed, since I've been slowly building this setup for the last year (more because of my lack of free time rather than cost issues) and now have to wait longer.

I guess if I keep the ivtv repository and wait it out, I'll eventually get updated to the right firmware for my capture card?

BTW, I contacted New Egg, and they said that since I had waited too long to notice that I had the wrong video card, I'm out of luck.

---

### Post by tgm4883 on 2007-05-24
Try emailing hauppauge.  Perhaps they have something that you could test fully knowing that it may not work

---

### Post by mmcmonster on 2007-05-25
This is what I sent to [EMAIL="techsupport@hauppauge.com"]techsupport@hauppauge.com[/EMAIL][INDENT][I]To whom it may concern.
  I had purchased a PVR150 from [www.newegg.com]("http://www.newegg.com/") in early March of this year.  I had particularly chosen the PVR 150 because of many forums stating the excellent support for the video card in Linux.  Imagine my surprise when I found out that I was "upgraded" to an HVR 1600.  While I am sure that Microsoft Windows users would consider such an exchange as a benefit, you must realize that the PVR 150 card in particular is quite commonly used in Linux systems with it's excellent support via the IVTV firmware drivers. 

  I am asking here when IVTV support is expected for the HVR 1600.  If not soon, what recourse can be made for someone such as myself who would not consider the HVR 1600 as an upgrade, since it does not even work in my chosen computer or operating system? 

Thank you for your prompt response.

[/I][/INDENT]

---

### Post by mmcmonster on 2007-05-27
I received an email from Hauppauge.  They will replace my card with a PVR-150.

Too bad the IVTV drivers aren't available yet for the newer model. :-(

---

### Post by tgm4883 on 2007-05-28
Sweet.  What do you mean the new model's of PVR-150's aren't supported?

---

### Post by mmcmonster on 2007-05-28
I meant the HVR1600.

---

### Post by mmcmonster on 2007-06-16
Just to give everyone a followup:  I send emails to both newegg.com and Hauppauge.  They both agreed to take the card back and send me a real PVR-150.  I just got my replacement from Hauppauge.  So far it seems to work great!

---

