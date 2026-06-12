---
title: "Averatec 2150 (MSI s270) video flicker"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by maliath on 2007-05-03
I have an Averatec 2150 notebook (which is the same as the MSI s270). It has an AMD Turion 64 with ATI Radeon XPRESS 200m video card. From time to time the screen kind of flickers. The flickering occurs more often if I'm doing more things and using more memory. It occured before I activated the restricted drivers, and it is still happening after. It does NOT happen in Windows, however. Any ideas? It's VERY annoying.

---

### Post by balak on 2007-05-26
Hi,

I also have the same issue. I thought it has something to do with my particular X setup. Maybe it is common with all averatecs. What did you set your video memory to be (in the BIOS?).

The flicker happens for me at random times - I haven't been able to correlate it to any usage.

---

### Post by shipsnbolts on 2007-06-28
> **maliath said:**
> I have an Averatec 2150 notebook (which is the same as the MSI s270). It has an AMD Turion 64 with ATI Radeon XPRESS 200m video card. From time to time the screen kind of flickers. The flickering occurs more often if I'm doing more things and using more memory. It occured before I activated the restricted drivers, and it is still happening after. It does NOT happen in Windows, however. Any ideas? It's VERY annoying.
Hi! 
had the same issue, solved it by manualy instaling ATI Latest drivers from it's website,

here is an HOWTO:
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by mozzwald on 2007-09-19
I have the same problem with my Averatec 2150 and manually installing the ATI proprietary drivers doesn't help.  It actually sometimes makes it worse.  I started using Ubuntu 6.10 Edgy back in Nov 2006.  In Jan 07 I switched to Kubuntu 6.10 and the problem seemed to get worse. Since May I've been battling Feisty with this problem. 

The default drivers with all versions of Ubuntu cause the problem. I have tried several different versions of the ATI Proprietary drivers on fresh installs of Ubuntu.  I have tried the default Ubuntu fglrx drivers.  I have tried different modelines for the 1280x800 lcd screen as suggested by  [this site]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#HP_zt3000_.2F_Compaq_nx7000").  I am at a loss here.  Is there anyone with something else that I could try? Here's some detailed info on my system:

lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
02:05.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
02:05.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
02:05.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
02:09.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
```

dmesg:
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001be40000 end: 000000001bf40000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001bf40000 size: 0000000000010000 end: 000000001bf50000 type: 3
[    0.000000] copy_e820_map() start: 000000001bf50000 size: 00000000000b0000 end: 000000001c000000 type: 4
[    0.000000] copy_e820_map() start: 000000001c000000 size: 0000000004000000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bf40000 (usable)
[    0.000000]  BIOS-e820: 000000001bf40000 - 000000001bf50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bf50000 - 000000001c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001c000000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 114496) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114496
[    0.000000]   HighMem    114496 ->   114496
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114496
[    0.000000] On node 0 totalpages: 114496
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 862 pages used for memmap
[    0.000000]   Normal zone: 109538 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 MSI                                   ) @ 0x000f83d0
[    0.000000] ACPI: RSDT (v001 MSI    1013     0x01092006 MSFT 0x00000097) @ 0x1bf40000
[    0.000000] ACPI: FADT (v002 MSI    1013     0x01092006 MSFT 0x00000097) @ 0x1bf40200
[    0.000000] ACPI: MADT (v001 MSI    OEMAPIC  0x01092006 MSFT 0x00000097) @ 0x1bf40300
[    0.000000] ACPI: WDRT (v001 MSI    MSI_OEM  0x01092006 MSFT 0x00000097) @ 0x1bf40360
[    0.000000] ACPI: MCFG (v001 MSI    OEMMCFG  0x01092006 MSFT 0x00000097) @ 0x1bf403b0
[    0.000000] ACPI: SSDT (v001 OEM_ID OEMTBLID 0x00000001 INTL 0x02002026) @ 0x1bf43750
[    0.000000] ACPI: OEMB (v001 MSI    MSI_OEM  0x01092006 MSFT 0x00000097) @ 0x1bf50040
[    0.000000] ACPI: DSDT (v001    MSI     1013 0x01092006 INTL 0x02002026) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[    0.000000] Detected 1591.936 MHz processor.
[    8.891574] Built 1 zonelists.  Total pages: 113602
[    8.891578] Kernel command line: root=UUID=1394cd01-d709-4121-83b2-de262d694f90 ro quiet
[    8.891726] mapped APIC to ffffd000 (fee00000)
[    8.891729] mapped IOAPIC to ffffc000 (fec00000)
[    8.891732] Enabling fast FPU save and restore... done.
[    8.891735] Enabling unmasked SIMD FPU exception support... done.
[    8.891744] Initializing CPU#0
[    8.891812] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    8.892782] Console: colour VGA+ 80x25
[    8.893092] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.893344] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.902887] Memory: 442936k/457984k available (1993k kernel code, 14456k reserved, 900k data, 328k init, 0k highmem)
[    8.902899] virtual kernel memory layout:
[    8.902900]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.902902]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.902903]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[    8.902905]     lowmem  : 0xc0000000 - 0xdbf40000   ( 447 MB)
[    8.902906]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    8.902908]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[    8.902909]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[    8.902913] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.979788] Calibrating delay using timer specific routine.. 3187.16 BogoMIPS (lpj=6374332)
[    8.979831] Security Framework v1.0.0 initialized
[    8.979837] SELinux:  Disabled at boot.
[    8.979854] Mount-cache hash table entries: 512
[    8.979983] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[    8.979992] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    8.979995] CPU: L2 Cache: 512K (64 bytes/line)
[    8.979998] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[    8.980008] Compat vDSO mapped to ffffe000.
[    8.980012] Remapping vsyscall page to ffffe000
[    8.980022] Checking 'hlt' instruction... OK.
[    8.995905] SMP alternatives: switching to UP code
[    8.996077] Freeing SMP alternatives: 11k freed
[    8.996285] Early unpacking initramfs... done
[    9.343033] ACPI: Core revision 20060707
[    9.343533] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    9.345531] CPU0: AMD Turion(tm) 64 Mobile Technology MT-28 stepping 02
[    9.345550] Total of 1 processors activated (3187.16 BogoMIPS).
[    9.345718] ENABLING IO-APIC IRQs
[    9.345912] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.385627] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    9.385670] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[    9.385673] ...trying to set up timer as Virtual Wire IRQ... works.
[    9.531617] Brought up 1 CPUs
[    9.531843] Booting paravirtualized kernel on bare hardware
[    9.531928] Time: 12:38:30  Date: 08/19/107
[    9.531957] NET: Registered protocol family 16
[    9.532038] EISA bus registered
[    9.532042] ACPI: bus type pci registered
[    9.532819] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    9.532821] PCI: Using configuration type 1
[    9.532823] Setting up standard PCI resources
[    9.542557] ACPI: Interpreter enabled
[    9.542560] ACPI: Using IOAPIC for interrupt routing
[    9.542972] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.542978] PCI: Probing PCI hardware (bus 00)
[    9.543967] Boot video device is 0000:01:05.0
[    9.544560] PCI: Transparent bridge - 0000:00:14.4
[    9.544636] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[    9.544639] Please report the result to linux-kernel to fix this permanently
[    9.544662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.551970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    9.558317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP2._PRT]
[    9.560503] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.560709] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.560912] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.561114] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.561315] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.561518] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.561722] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.561924] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.562027] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.562037] pnp: PnP ACPI init
[    9.565526] pnp: PnP ACPI: found 11 devices
[    9.565530] PnPBIOS: Disabled by ACPI PNP
[    9.565582] PCI: Using ACPI for IRQ routing
[    9.565586] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.569318] PCI: Device 0000:02:03.0 not found by BIOS
[    9.569452] PCI: Device 0000:02:05.0 not found by BIOS
[    9.569584] PCI: Device 0000:02:05.2 not found by BIOS
[    9.569718] PCI: Device 0000:02:05.3 not found by BIOS
[    9.569851] PCI: Device 0000:02:05.4 not found by BIOS
[    9.569985] PCI: Device 0000:02:09.0 not found by BIOS
[    9.570015] NET: Registered protocol family 8
[    9.570017] NET: Registered protocol family 20
[    9.570791] PCI: Bridge: 0000:00:01.0
[    9.570794]   IO window: d000-dfff
[    9.570798]   MEM window: fbe00000-fbefffff
[    9.570801]   PREFETCH window: f0000000-faffffff
[    9.570813] PCI: Bus 3, cardbus bridge: 0000:02:05.0
[    9.570816]   IO window: 0000e000-0000e0ff
[    9.570821]   IO window: 0000e400-0000e4ff
[    9.570828]   PREFETCH window: 30000000-33ffffff
[    9.570834]   MEM window: 38000000-3bffffff
[    9.570839] PCI: Bridge: 0000:00:14.4
[    9.570843]   IO window: e000-efff
[    9.570850]   MEM window: fbf00000-fbffffff
[    9.570855]   PREFETCH window: 30000000-35ffffff
[    9.570898] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 19 (level, low) -> IRQ 16
[    9.570929] NET: Registered protocol family 2
[    9.595643] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    9.595732] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    9.595871] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    9.595941] TCP: Hash tables configured (established 16384 bind 8192)
[    9.595944] TCP reno registered
[    9.607670] checking if image is initramfs... it is
[   10.294881] Freeing initrd memory: 6772k freed
[   10.295336] audit: initializing netlink socket (disabled)
[   10.295352] audit(1190205510.448:1): initialized
[   10.295470] VFS: Disk quotas dquot_6.5.1
[   10.295488] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.295536] io scheduler noop registered
[   10.295539] io scheduler anticipatory registered
[   10.295542] io scheduler deadline registered
[   10.295551] io scheduler cfq registered (default)
[   10.343515] isapnp: Scanning for PnP cards...
[   10.697886] isapnp: No Plug & Play device found
[   10.721942] Real Time Clock Driver v1.12ac
[   10.721993] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.722602] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   10.722612] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   10.722681] mice: PS/2 mouse device common for all mice
[   10.723244] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.723465] input: Macintosh mouse button emulation as /class/input/input0
[   10.723495] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.723499] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.723765] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   10.724111] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.724187] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.724191] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.724194] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.724197] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.724200] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.724310] EISA: Probing bus 0 at eisa.0
[   10.724332] Cannot allocate resource for EISA slot 4
[   10.724352] EISA: Detected 0 cards.
[   10.754531] TCP cubic registered
[   10.754543] NET: Registered protocol family 1
[   10.754563] Using IPI No-Shortcut mode
[   10.754630] ACPI: (supports S0 S1 S3 S4 S5)
[   10.754677]   Magic number: 7:299:633
[   10.754752]   hash matches device ptycc
[   10.755119] Time: tsc clocksource has been installed.
[   10.755235] Freeing unused kernel memory: 328k freed
[   10.757154] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.946607] Capability LSM initialized
[   10.981858] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.985657] ACPI: Thermal Zone [THRM] (40 C)
[   11.430835] usbcore: registered new interface driver usbfs
[   11.430879] usbcore: registered new interface driver hub
[   11.430902] usbcore: registered new device driver usb
[   11.431593] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   11.431629] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[   11.431644] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   11.431819] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   11.431843] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfbdfd000
[   11.527364] usb usb1: configuration #1 chosen from 1 choice
[   11.527394] hub 1-0:1.0: USB hub found
[   11.527408] hub 1-0:1.0: 4 ports detected
[   11.562603] 8139too Fast Ethernet driver 0.9.28
[   11.607101] ieee1394: Initialized config rom entry `ip1394'
[   11.630968] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[   11.630988] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   11.631010] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   11.631030] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfbdfe000
[   11.690909] usb usb2: configuration #1 chosen from 1 choice
[   11.690937] hub 2-0:1.0: USB hub found
[   11.690954] hub 2-0:1.0: 4 ports detected
[    2.752000] Time: acpi_pm clocksource has been installed.
[    2.756000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[    2.756000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.756000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    2.756000] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfbdff000
[    2.756000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.756000] usb usb3: configuration #1 chosen from 1 choice
[    2.756000] hub 3-0:1.0: USB hub found
[    2.756000] hub 3-0:1.0: 8 ports detected
[    2.860000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    2.860000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    2.860000] ATIIXP: chipset revision 0
[    2.860000] ATIIXP: not 100% native mode: will probe irqs later
[    2.860000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[    2.860000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[    2.860000] Probing IDE interface ide0...
[    3.148000] hda: WDC WD800VE-00HDT0, ATA DISK drive
[    3.820000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.100000] Probing IDE interface ide1...
[    4.836000] hdc: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[    5.172000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.180000] SCSI subsystem initialized
[    5.188000] libata version 2.20 loaded.
[    5.188000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 18 (level, low) -> IRQ 19
[    5.192000] eth0: RealTek RTL8139 at 0xdc824c00, 00:13:d3:af:6f:54, IRQ 19
[    5.192000] eth0:  Identified 8139 chip type 'RTL-8101'
[    5.192000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.192000] ACPI: PCI Interrupt 0000:02:05.4[A] -> GSI 19 (level, low) -> IRQ 16
[    5.248000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fbffe000-fbffe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    5.256000] hda: max request size: 128KiB
[    5.256000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[    5.268000] hda: cache flushes supported
[    5.268000]  hda: hda1 hda2 hda3 < hda5 > hda4
[    5.612000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    5.612000] Uniform CD-ROM driver Revision: 3.20
[    6.004000] Attempting manual resume
[    6.004000] swsusp: Resume From Partition 3:4
[    6.004000] PM: Checking swsusp image.
[    6.004000] PM: Resume from disk failed.
[    6.052000] kjournald starting.  Commit interval 5 seconds
[    6.052000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.524000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc1000e358c000]
[   16.536000] eth0: link down
[   18.116000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.164000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.176000] NET: Registered protocol family 17
[   18.460000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   18.464000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.912000] Yenta: CardBus bridge found at 0000:02:05.0 [1462:0221]
[   18.912000] Yenta O2: res at 0x94/0xD4: 00/ea
[   18.912000] Yenta O2: enabling read prefetch/write burst
[   19.004000] sdhci: Secure Digital Host Controller Interface driver
[   19.004000] sdhci: Copyright(c) Pierre Ossman
[   19.040000] Yenta: ISA IRQ mask 0x0eb8, PCI irq 16
[   19.040000] Socket status: 30000006
[   19.040000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   19.040000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[   19.040000] cs: IO port probe 0xe000-0xefff: clean.
[   19.040000] pcmcia: parent PCI bridge Memory window: 0xfbf00000 - 0xfbffffff
[   19.040000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   19.040000] sdhci: SDHCI controller found at 0000:02:05.2 [1217:7120] (rev 1)
[   19.040000] ACPI: PCI Interrupt 0000:02:05.2[A] -> GSI 19 (level, low) -> IRQ 16
[   19.040000] sdhci:slot0: Unknown controller version (16). You may experience problems.
[   19.040000] mmc0: SDHCI at 0xfbfff800 irq 16 PIO
[   19.488000] input: PC Speaker as /class/input/input2
[   19.508000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 22 (level, low) -> IRQ 20
[   19.508000] rt61 1.1.0 CVS CVS http://rt2x00.serialmonkey.com
[   19.508000] RT61: Vendor = 0x1814, Product = 0x0302 
[   19.696000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   19.920000] RT61: RfIcType= 3
[   20.092000] cs: IO port probe 0x100-0x3af: clean.
[   20.092000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   20.092000] cs: IO port probe 0x820-0x8ff: clean.
[   20.096000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   20.096000] cs: IO port probe 0xa00-0xaff: clean.
[   20.212000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   20.280000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   20.512000] lp: driver loaded but no devices found
[   20.560000] Adding 1253060k swap on /dev/disk/by-uuid/51aa29bc-8869-47c4-ac53-dfb429210ba4.  Priority:-1 extents:1 across:1253060k
[   20.720000] EXT3 FS on hda1, internal journal
[   26.268000] NET: Registered protocol family 10
[   26.268000] lo: Disabled Privacy Extensions
[   26.268000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.352000] No dock devices found.
[   31.456000] ACPI: Battery Slot [BAT1] (battery present)
[   31.492000] Using specific hotkey driver
[   31.528000] ibm_acpi: ec object not found
[   31.564000] ACPI: AC Adapter [ADP1] (on-line)
[   31.640000] input: Power Button (FF) as /class/input/input4
[   31.644000] ACPI: Power Button (FF) [PWRF]
[   31.684000] input: Lid Switch as /class/input/input5
[   31.688000] ACPI: Lid Switch [LID0]
[   31.724000] input: Sleep Button (CM) as /class/input/input6
[   31.724000] ACPI: Sleep Button (CM) [SLPB]
[   31.744000] input: Power Button (CM) as /class/input/input7
[   31.744000] ACPI: Power Button (CM) [PWRB]
[   31.908000] pcc_acpi: loading...
[   32.116000] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MT-28 processors (version 2.00.00)
[   32.116000] ACPI: Invalid package argument
[   32.116000] ACPI Exception (acpi_processor-0270): AE_BAD_PARAMETER, Invalid _PSS data [20060707]
[   32.124000] powernow-k8:    0 : fid 0x0 (800 MHz), vid 0x16
[   32.124000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xa
[   32.128000] powernow-k8: ph2 null fid transition 0x8
[   36.980000] ra0: no IPv6 routers present
[   37.160000] ppdev: user-space parallel port driver
[   37.976000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   37.976000] apm: overridden by ACPI.
[   38.952000] Bluetooth: Core ver 2.11
[   38.952000] NET: Registered protocol family 31
[   38.952000] Bluetooth: HCI device and connection manager initialized
[   38.952000] Bluetooth: HCI socket layer initialized
[   38.988000] Bluetooth: L2CAP ver 2.8
[   38.988000] Bluetooth: L2CAP socket layer initialized
[   39.152000] Bluetooth: RFCOMM socket layer initialized
[   39.152000] Bluetooth: RFCOMM TTY layer initialized
[   39.152000] Bluetooth: RFCOMM ver 1.8
[   62.296000] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   62.508000] usb 1-2: configuration #1 chosen from 1 choice
[   62.660000] usbcore: registered new interface driver hiddev
[   62.672000] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /class/input/input8
[   62.672000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:13.0-2
[   62.672000] usbcore: registered new interface driver usbhid
[   62.672000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
```

xorg.conf:
```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by wildcard on 2007-10-18
It's not just an *buntu issue, from my experience. I have the same flicker with Mint (well, yeah, still sort of the *buntu family), PCLinuxOS 2007, Sabayon 3.3 & 3.4, and Mepis 6.5 and 7.0beta.Trying different modelines didn't fix it for me either. I get the flickering with Beryl AND Compiz Fusion, regardless of whether Emerald or Metacity is the window manager. I get the flicker with the 'ati', 'radeon', and the 'fglrx' drivers, so I don't think it's driver related. I don't have the problem in windows, but I do have an issue with the brightness level of the screen randomly changes, and occasionally the power reports that the AC is unplugged momentarily. I had similar issues with the power/brightness (though I don't remember if there was flicker or not) with an MSI-1029 laptop-that one had an ATI X700 card in it, but both laptops have the same RS480 chipset on them.

---

### Post by maliath on 2007-10-18
I am experiencing NO video flicker in Gutsy 7.10 fresh install. It should also be known that I upgraded my RAM before my fresh installation to 1.5 GB.

---

### Post by mozzwald on 2007-10-19
I can confirm that the flicker is gone with Gutsy (upgrad from Feisty, not fresh install).  Several weeks ago I tested the Gutsy Tribe 5 LiveCD which still had the problem, but the official release seems to work fine.  Also note that the rt61 pci wireless card is properly detected and works with NetworkManager.  Suspend and Hibernate are no longer working (hibernate never worked for me, but suspend did).

---

### Post by balak on 2007-10-21
I can also confirm that the flicker is gone in gutsy.
Thanks whoever!

But I am having issues connecting to wireless. Did you guys have to change anything to get it working?

network manager connects to my network and gets an IP but thats about it.

---

### Post by mozzwald on 2007-10-22
> **balak said:**
> I can also confirm that the flicker is gone in gutsy.
Thanks whoever!

But I am having issues connecting to wireless. Did you guys have to change anything to get it working?

network manager connects to my network and gets an IP but thats about it.

I am having similar problems with the wifi card.  The card gets an IP and works occasionally , but will slow down or not connect to servers.  I've tried blacklisting ipv6 and have changed my DNS servers to opendns.com's with no avail.  Not sure what to try next.

Found some info on the suspend/hibernate problems, but haven't tried compiling my own kernel yet. [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653")

---

### Post by balak on 2007-10-22
Actually networkmanager seems to work fine now. 

First, I installed wicd (the 1.3.4 release which is 'testing' and has support for ralink cards). That didn't help either.

I removed that and reinstalled networkmanager and it seems to connect properly on networks with WEP. Right now, I am working on getting it to connect to WPA2 network.

[I had compiled my own version of wpa_supplicant with support for rt61 card in feisty. I am hoping that I don't have to do that again in gutsy..]

---

