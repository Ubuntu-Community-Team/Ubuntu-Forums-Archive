---
title: "After upgrading, networking works for about 2 secs"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by King Big Ben on 2006-06-10
Networking worked fine for breezy badger, but after upgrading it stopped. I cannot access my router, yet for some reason the internet works for a couple sec upon boot. I had it set up where gaim starts upon boot so i twould login and it even received a message one time but then the connection closed. I've tried deactivating and reactivating eth0 and nothing. I even tried removing gaim and unplugging for several minutes. The computer also boots windows, and the connection from windows still works...so the hardware is still fine...
I'm still a relative newbie to linux, although i have used several versions of redhat and fedora in the past without problems.
The only thing i can think of to do now is to download the cd images and try reinstalling from there (i used the updater to upgrade from breezy) but i really don't want to do that
so any help getting my networking to work will be much appreciated
thanks,
Ben

---

### Post by ns2048 on 2006-06-11
Can you run the following commands in a terminal (Applications->Accessories->Terminal) and post the output here.

* lspci -vv
* dmesg
* ifconfig
* lsmod

--ns2048

---

### Post by King Big Ben on 2006-06-11
[QUOTE=ns2048]Can you run the following commands in a terminal (Applications->Accessories->Terminal) and post the output here.

* lspci -vv
* dmesg
* ifconfig
* lsmod

--ns2048[/QUOTE]

bigben@ubuntu:~$ lspci -vv
0000:00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
        Subsystem: Dell: Unknown device 010c
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort+ <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff
        BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fe100000-fe2fffff
        Prefetchable memory behind bridge: 20000000-200fffff
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04) (prog-if 80 [Master])
        Subsystem: Dell: Unknown device 010c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 4: I/O ports at ffa0 [size=16]

0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 010c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 177
        Region 4: I/O ports at ff80 [size=32]

0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
        Subsystem: Dell: Unknown device 010c
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 4: I/O ports at dcd0 [size=16]

0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 010c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 185
        Region 4: I/O ports at ff60 [size=32]

0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation: Unknown device 015a
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 248 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 193
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Region 2: Memory at f3f80000 (32-bit, prefetchable) [size=512K]
        Expansion ROM at f0000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
        Subsystem: Unknown device 4554:434e
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (5000ns min, 10000ns max)
        Interrupt: pin A routed to IRQ 193
        Region 0: I/O ports at ec00 [size=256]
        Region 1: Memory at fe1ffc00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at 20000000 [disabled] [size=256K]
        Capabilities: <available only to root>

0000:02:08.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02) (prog-if 00 [Generic])
        Subsystem: Dell: Unknown device 0001
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at fe1fe000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at e8f0 [size=16]
        Capabilities: <available only to root>

0000:02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs CT4780 SBLive! Value
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 201
        Region 0: I/O ports at e8c0 [size=32]
        Capabilities: <available only to root>

0000:02:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
        Subsystem: Creative Labs Gameport Joystick
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Region 0: I/O ports at e8e8 [size=8]
        Capabilities: <available only to root>

0000:02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns max), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 177
        Region 0: Memory at fe1ff000 (32-bit, non-prefetchable) [size=2K]
        Region 1: I/O ports at e800 [size=128]
        Capabilities: <available only to root>

bigben@ubuntu:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000ff77000 (usable)
[4294667.296000]  BIOS-e820: 000000000ff77000 - 000000000ff79000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000000ff79000 - 0000000010000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 255MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fe710
[4294667.296000] On node 0 totalpages: 65399
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 61303 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fd560
[4294667.296000] ACPI: RSDT (v001 DELL    8200    0x00000008 ASL  0x00000061) @ 0x000fd574
[4294667.296000] ACPI: FADT (v001 DELL    8200    0x00000008 ASL  0x00000061) @ 0x000fd5a8
[4294667.296000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffe5d85
[4294667.296000] ACPI: MADT (v001 DELL    8200    0x00000008 ASL  0x00000061) @ 0x000fd61c
[4294667.296000] ACPI: BOOT (v001 DELL    8200    0x00000008 ASL  0x00000061) @ 0x000fd678
[4294667.296000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:2 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda3 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 2387.467 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.701000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294670.701000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.707000] Memory: 248628k/261596k available (1976k kernel code, 12344k reserved, 606k data, 288k init, 0k highmem)
[4294670.707000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.767000] Calibrating delay using timer specific routine.. 4776.09 BogoMIPS (lpj=2388047)
[4294670.767000] Security Framework v1.0.0 initialized
[4294670.767000] SELinux:  Disabled at boot.
[4294670.767000] Mount-cache hash table entries: 512
[4294670.767000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.767000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.767000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.767000] CPU: L2 cache: 512K
[4294670.767000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[4294670.767000] mtrr: v2.0 (20020519)
[4294670.767000] CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 04
[4294670.767000] Enabling fast FPU save and restore... done.
[4294670.767000] Enabling unmasked SIMD FPU exception support... done.
[4294670.767000] Checking 'hlt' instruction... OK.
[4294670.771000] checking if image is initramfs... it is
[4294671.382000] Freeing initrd memory: 6608k freed
[4294671.398000] ACPI: Looking for DSDT ... not found!
[4294671.421000] ENABLING IO-APIC IRQs
[4294671.421000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294671.532000] NET: Registered protocol family 16
[4294671.532000] EISA bus registered
[4294671.532000] ACPI: bus type pci registered
[4294671.545000] PCI: PCI BIOS revision 2.10 entry at 0xfbeae, last bus=2
[4294671.545000] PCI: Using configuration type 1
[4294671.545000] ACPI: Subsystem revision 20051216
[4294671.568000] ACPI: Interpreter enabled
[4294671.568000] ACPI: Using IOAPIC for interrupt routing
[4294671.572000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.572000] PCI: Probing PCI hardware (bus 00)
[4294671.572000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.584000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[4294671.584000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[4294671.584000] Boot video device is 0000:01:00.0
[4294671.585000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.585000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.681000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294671.700000] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 9 10 11 12 15)[4294671.701000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)[4294671.701000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294671.702000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294671.703000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294671.704000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294671.705000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294671.705000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)[4294671.705000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.705000] pnp: PnP ACPI init
[4294671.734000] pnp: PnP ACPI: found 11 devices
[4294671.734000] PnPBIOS: Disabled by ACPI PNP
[4294671.734000] PCI: Using ACPI for IRQ routing
[4294671.734000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.748000] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[4294671.748000] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[4294671.748000] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[4294671.748000] PCI: Bridge: 0000:00:01.0
[4294671.748000]   IO window: disabled.
[4294671.748000]   MEM window: fc000000-fdffffff
[4294671.748000]   PREFETCH window: f0000000-f7ffffff
[4294671.748000] PCI: Bridge: 0000:00:1e.0
[4294671.748000]   IO window: e000-efff
[4294671.748000]   MEM window: fe100000-fe2fffff
[4294671.748000]   PREFETCH window: 20000000-200fffff
[4294671.748000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294671.748000] Simple Boot Flag at 0x7a set to 0x1
[4294671.749000] audit: initializing netlink socket (disabled)
[4294671.749000] audit(1150050143.748:1): initialized
[4294671.749000] VFS: Disk quotas dquot_6.5.1
[4294671.749000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.749000] Initializing Cryptographic API
[4294671.749000] io scheduler noop registered
[4294671.749000] io scheduler anticipatory registered
[4294671.749000] io scheduler deadline registered
[4294671.749000] io scheduler cfq registered
[4294671.749000] isapnp: Scanning for PnP cards...
[4294672.106000] isapnp: No Plug & Play device found
[4294672.122000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294672.125000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.125000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.125000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294672.125000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.128000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.128000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 169
[4294672.128000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.128000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.128000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.129000] mice: PS/2 mouse device common for all mice
[4294672.129000] EISA: Probing bus 0 at eisa.0
[4294672.129000] EISA: Detected 0 cards.
[4294672.129000] NET: Registered protocol family 2
[4294672.139000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294672.139000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.139000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.139000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.139000] TCP reno registered
[4294672.139000] TCP bic registered
[4294672.139000] NET: Registered protocol family 1
[4294672.139000] NET: Registered protocol family 8
[4294672.139000] NET: Registered protocol family 20
[4294672.139000] Using IPI Shortcut mode
[4294672.139000] ACPI wakeup devices:
[4294672.139000] VBTN PCI0 USB0 USB1 PCI1  KBD
[4294672.139000] ACPI: (supports S0 S1 S3 S4 S5)
[4294672.139000] Freeing unused kernel memory: 288k freed
[4294672.174000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.191000] vga16fb: initializing
[4294672.191000] vga16fb: mapped to 0xc00a0000
[4294672.340000] Console: switching to colour frame buffer device 80x25
[4294672.340000] fb0: VGA16 VGA frame buffer device
[4294673.410000] Capability LSM initialized
[4294674.130000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294674.130000] ICH2: chipset revision 4
[4294674.130000] ICH2: not 100% native mode: will probe irqs later
[4294674.130000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294674.131000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:DMA
[4294674.131000] Probing IDE interface ide0...
[4294674.395000] hda: WDC WD800BB-75CAA0, ATA DISK drive
[4294675.007000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.012000] Probing IDE interface ide1...
[4294675.378000] hdc: LITEON DVD-ROM LTD163, ATAPI CD/DVD-ROM drive
[4294675.786000] hdd: SAMSUNG CD-R/RW SW-240B, ATAPI CD/DVD-ROM drive
[4294675.837000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.849000] hda: max request size: 128KiB
[4294675.870000] hda: Host Protected Area detected.
[4294675.870000]        current capacity is 156250000 sectors (80000 MB)
[4294675.870000]        native  capacity is 156301488 sectors (80026 MB)
[4294675.873000] hda: Host Protected Area disabled.
[4294675.873000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294675.873000] hda: cache flushes not supported
[4294675.873000]  hda: hda1 hda2 hda3 hda4 < hda5 >
[4294675.915000] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[4294675.915000] Uniform CD-ROM driver Revision: 3.20
[4294675.921000] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294676.258000] ieee1394: Initialized config rom entry `ip1394'
[4294676.260000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294676.260000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 19 (level, low) -> IRQ 177
[4294676.260000] PCI: Via IRQ fixup for 0000:02:0a.0, from 11 to 1
[4294676.289000] usbcore: registered new driver usbfs
[4294676.289000] usbcore: registered new driver hub
[4294676.291000] USB Universal Host Controller Interface driver v2.3
[4294676.291000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 177
[4294676.291000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294676.291000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[4294676.291000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294676.291000] uhci_hcd 0000:00:1f.2: irq 177, io base 0x0000ff80
[4294676.292000] hub 1-0:1.0: USB hub found
[4294676.292000] hub 1-0:1.0: 2 ports detected
[4294676.346000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[177]  MMIO=[fe1ff000-fe1ff7ff]  Max Packet=[2048]
[4294676.393000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 185
[4294676.393000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[4294676.393000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[4294676.393000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[4294676.393000] uhci_hcd 0000:00:1f.4: irq 185, io base 0x0000ff60
[4294676.393000] hub 2-0:1.0: USB hub found
[4294676.393000] hub 2-0:1.0: 2 ports detected
[4294676.572000] Attempting manual resume
[4294676.599000] EXT3-fs: mounted filesystem with ordered data mode.
[4294676.618000] kjournald starting.  Commit interval 5 seconds
[4294677.616000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00d04b4c16056fda][4294677.617000] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0011060000004543][4294689.353000] SCSI subsystem initialized
[4294689.373000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294689.373000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)[4294689.373000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294689.373000] scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4294690.476000] ieee1394: sbp2: Logged into SBP-2 device
[4294690.476000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048][4294690.478000]   Vendor: WDC WD80  Model: 0BB-00FJA0        Rev: 13.0
[4294690.478000]   Type:   Direct-Access-RBC                  ANSI SCSI revision: 04
[4294690.927000] Linux agpgart interface v0.101 (c) Dave Jones
[4294690.929000] agpgart: Detected an Intel i850 Chipset.
[4294690.935000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294690.984000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294691.005000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.129000] Floppy drive(s): fd0 is 1.44M
[4294691.142000] FDC 0 is a post-1991 82077
[4294691.236000] Real Time Clock Driver v1.12
[4294691.248000] hw_random hardware driver 1.0.0 loaded
[4294691.664000] Driver 'sd' needs updating - please use bus_type methods
[4294691.669000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294691.670000] SCSI device sda: drive cache: write back
[4294691.738000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294691.777000] gameport: EMU10K1 is pci0000:02:09.1/gameport0, io 0xe8e8, speed 1046kHz
[4294691.782000] SCSI device sda: drive cache: write back
[4294691.782000]  sda: sda1
[4294691.827000] sd 0:0:0:0: Attached scsi disk sda
[4294691.835000] Linux Tulip driver version 1.1.13 (December 15, 2004)
[4294691.835000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 16 (level, low) -> IRQ 193
[4294691.867000] tulip0:  EEPROM default media type Autosense.
[4294691.867000] tulip0:  Index #0 - Media MII (#11) described by a 21140 MII PHY (1) block.
[4294691.867000] tulip0:  Index #1 - Media 10baseT (#0) described by a 21140 non-MII (0) block.
[4294691.867000] tulip0:  Index #2 - Media 100baseTx (#3) described by a 21140 non-MII (0) block.
[4294691.867000] tulip0:  Index #3 - Media 10baseT-FDX (#4) described by a 21140 non-MII (0) block.
[4294691.867000] tulip0:  Index #4 - Media 100baseTx-FDX (#5) described by a 21140 non-MII (0) block.
[4294691.869000] tulip0:  MII transceiver #1 config 3100 status 7809 advertising 01e1.
[4294691.876000] eth0: Davicom DM9102/DM9102A rev 49 at 0001ec00, 00:08:A1:05:66:01, IRQ 193.
[4294691.890000] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[4294691.897000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input1
[4294691.901000] parport: PnPBIOS parport detected.
[4294691.901000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294691.942000] nvidia: module license 'NVIDIA' taints kernel.
[4294691.947000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[4294691.948000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[4294691.997000] sd 0:0:0:0: Attached scsi generic sg0 type 14
[4294692.732000] ts: Compaq touchscreen protocol output
[4294692.764000] input: PC Speaker as /class/input/input2
[4294693.249000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 18 (level, low) -> IRQ 201
[4294693.891000] Intel ISA PCIC probe: not found.
[4294693.965000] NET: Registered protocol family 17
[4294694.123000] lp0: using parport0 (interrupt-driven).
[4294694.250000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[4294694.391000] EXT3 FS on hda3, internal journal
[4294694.591000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.591000] md: bitmap version 4.39
[4294695.163000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294695.879000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[4294698.618000] ACPI: Power Button (FF) [PWRF]
[4294698.618000] ACPI: Power Button (CM) [VBTN]
[4294698.744000] ibm_acpi: ec object not found
[4294698.767000] pcc_acpi: loading...
[4294700.245000] NET: Registered protocol family 10
[4294700.246000] lo: Disabled Privacy Extensions
[4294700.246000] IPv6 over IPv4 tunneling driver
[4294711.178000] eth0: no IPv6 routers present
[4294712.372000] ppdev: user-space parallel port driver
[4294714.098000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294714.098000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294714.099000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294716.483000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294716.483000] apm: overridden by ACPI.
[4294717.043000] Bluetooth: Core ver 2.8
[4294717.043000] NET: Registered protocol family 31
[4294717.043000] Bluetooth: HCI device and connection manager initialized
[4294717.043000] Bluetooth: HCI socket layer initialized
[4294717.071000] Bluetooth: L2CAP ver 2.8
[4294717.071000] Bluetooth: L2CAP socket layer initialized
[4294717.095000] Bluetooth: RFCOMM socket layer initialized
[4294717.095000] Bluetooth: RFCOMM TTY layer initialized
[4294717.095000] Bluetooth: RFCOMM ver 1.7
[4294728.555000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294728.839000] ISO 9660 Extensions: RRIP_1991A
[4294730.881000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294935.315000] usb 2-2: new full speed USB device using uhci_hcd and address 2[4294935.834000] Initializing USB Mass Storage driver...
[4294935.834000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294935.835000] usb-storage: device found at 2
[4294935.835000] usb-storage: waiting for device to settle before scanning
[4294935.835000] usbcore: registered new driver usb-storage
[4294935.835000] USB Mass Storage support registered.
[4294940.839000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4294940.839000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294940.844000] SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
[4294940.849000] sdb: Write Protect is off
[4294940.849000] sdb: Mode Sense: 64 00 00 08
[4294940.849000] sdb: assuming drive cache: write through
[4294940.859000] SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
[4294940.863000] sdb: Write Protect is off
[4294940.863000] sdb: Mode Sense: 64 00 00 08
[4294940.863000] sdb: assuming drive cache: write through
[4294940.863000]  sdb: sdb1 sdb2
[4294940.885000] sd 1:0:0:0: Attached scsi removable disk sdb
[4294940.885000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[4294940.886000] usb-storage: device scan complete
[4294942.408000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

bigben@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:A1:05:66:01
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe05:6601/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:156 dropped:0 overruns:0 frame:0
          TX packets:65 errors:4 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000
          RX bytes:53325 (52.0 KiB)  TX bytes:4975 (4.8 KiB)
          Interrupt:193 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1057530 (1.0 MiB)  TX bytes:1057530 (1.0 MiB)

---

### Post by King Big Ben on 2006-06-11
bigben@ubuntu:~$ lsmod
Module                  Size  Used by
usb_storage            74176  1
nls_utf8                2176  2
vfat                   13440  2
fat                    53020  1 vfat
nls_cp437               5888  3
isofs                  37688  2
udf                    88452  0
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
autofs4                20100  0
ppdev                   9220  0
ipv6                  265600  6
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
lp                     11844  0
af_packet              22920  2
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           117156  2 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         92704  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
snd                    55268  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10208  1 snd
pcspkr                  2180  0
tsdev                   8000  0
sg                     37920  0
nvidia               4550772  12
i2c_core               21904  2 i2c_acpi_ec,nvidia
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
dmfe                   21532  0
tulip                  51872  0
serio_raw               7300  0
emu10k1_gp              3840  0
gameport               15496  2 emu10k1_gp
sd_mod                 19984  4
psmouse                36228  0
hw_random               5652  0
rtc                    13492  0
floppy                 62148  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
sbp2                   24196  2
scsi_mod              139496  5 usb_storage,sr_mod,sg,sd_mod,sbp2
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               129668  3 usb_storage,uhci_hcd
ohci1394               35124  1
ieee1394              299832  2 sbp2,ohci1394
ide_cd                 33028  2
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

---

### Post by ns2048 on 2006-06-11
Thanks for posting the output of those commands. It looks like two different kernel modules are getting loaded for your network adapter (i.e., tulip, dmfe). Try the following.

# Add 'blacklist tulip' to '/etc/modprobe.d/blacklist'

# Add 'alias eth0 dmfe' to '/etc/modprobe.d/aliases'

# Reboot your system

With these changes (theoretically) only the 'dmfe' module should be loaded and you'll have network connectivity.

In case that doesn't work, try the reverse (i.e., loading the 'tulip' module instead of 'dmfe').

# Change 'blacklist tulip' to 'blacklist dmfe' in '/etc/modprobe.d/blacklist'

# Change 'alias eth0 tulip' to 'alias eth0 dmfe' in '/etc/modprobe.d/aliases'

# Reboot your system

--ns2048

---

### Post by King Big Ben on 2006-06-12
awesome, that worked, thanks :)

---

### Post by bathhm on 2006-06-12
Worked for me, too!  

My symptoms were that I couldn't get on line after upgrading from 5.10 to 6.06, tho I had just used the internet for the update [ using System > Administration > Update Manager ]  ifconfig said that eth0 was up, tho it showed that system was having nothing but Rx errors, and the line giving inet addr, etc was missing, and the line containing UP BROADCAST did not contain the word RUNNING.  System > Administration > Networking said that eth0 was up.  Of course, I could get on line using the Dapper Live CD without problems.

Came across Reply #6, thought it might pertain to my problems, tried the first option, and lo, success. Thanks a heap.

---

