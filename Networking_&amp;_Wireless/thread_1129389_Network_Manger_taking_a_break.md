---
title: "Network Manger taking a break"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by andywhoa on 2009-04-18
Ubuntu 8.04
Little Linux experience


I woke up this morning with no internet connection.  I restarted my machine and Network Manager (start up program) didn't boot.  I tried starting it manually and "nothing" happens.

The only additional information I can give at this point is that I was screwing around with uninstalling PulseAudio last night to try and get Skype to work.  Terminal was complaining about something or other and I gave up.  I finally got Skype working (through Skype options) and I had net all night (until some time while I was sleeping).


Could anyone help me out?  Help is much appreciated.  Thanks

---

### Post by khelben1979 on 2009-04-18
Have you tried this(?):

```
cd /etc/init.d/
sudo networking restart
```

And if this doesn't work, then you can try using the dhclient command instead.

```
man dhclient
```
to read about how to use the command.

---

### Post by andywhoa on 2009-04-18
```
sudo: networking: command not found
```


I tried restarting the DHCP Client...
```
SIOCSIFADDR: No such device
restart: ERROR while getting interface flags: No such device
restart: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
```

---

### Post by andywhoa on 2009-04-18
The only Network device I have in Network Tools is the Loopback Interface

In Network Settings, "Wired connection" and "Point to point connection" are the only two connections listed (I've been using wireless) and both are disabled

---

### Post by mosburn on 2009-04-18
try 

```
sudo /etc/init.d/networking restart
```

---

### Post by khelben1979 on 2009-04-18
Hmm.. I meant:

```
sudo ./networking restart
```

On my Debian system I have the networking script in the /etc/init.d/ file path. I'm not sure about Ubuntu, but I think it might be the same.

On some laptops, you have the ability to turn off or on the wireless network through a hardware switch. Maybe you need to activate this?

---

### Post by andywhoa on 2009-04-18
> **mosburn said:**
> try 

```
sudo /etc/init.d/networking restart
```

I tried this and "nothing" seems to happen.  I hit enter, it brings up the next line to type something and that's it...

---

### Post by andywhoa on 2009-04-18
> **khelben1979 said:**
> Hmm.. I meant:

```
sudo ./networking restart
```

On my Debian system I have the networking script in the /etc/init.d/ file path. I'm not sure about Ubuntu, but I think it might be the same.

On some laptops, you have the ability to turn off or on the wireless network through a hardware switch. Maybe you need to activate this?
My Lenovo has one, but I'm using a Mini 9 and I see no such switch.

Also, I was sleeping when this happened.  I was on my laptop talking on line, put it on my desk, rolled over and went to bed.  When I woke up, my connection was gone, I restarted and Network Manager won't show up.

Just in case, I hit Fn + 2 (The wireless function key) and after prompting me for my pw, nothing seems to have happened.  I also manually tried to launch Network Manager again, but nothing opens.

---

### Post by andywhoa on 2009-04-18
Any other ideas? :(

---

### Post by Windsurfer619 on 2009-04-18
It's 
sudo /etc/init.d/NetworkManager restart
on ubuntu. 

andywhoa, can you paste the output of "dmesg" here?

---

### Post by andywhoa on 2009-04-18
> **Windsurfer619 said:**
> It's 
sudo /etc/init.d/NetworkManager restart
on ubuntu. 

andywhoa, can you paste the output of "dmesg" here?
```

[    0.000000] Linux version 2.6.24-19-lpia (root@macbook) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 3 15:25:26 UTC 2008 (Unofficial)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6e2000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f6e2000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7fa0
[    0.000000] Entering add_active_range(0, 0, 521936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521936
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521936
[    0.000000] On node 0 totalpages: 521936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2285 pages used for memmap
[    0.000000]   HighMem zone: 290275 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F70 checksum 0
[    0.000000] ACPI: RSDP 000F7F70, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 7F6DC059, 006C (r1 PTLTD  	 XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 7F6E1D48, 00F4 (r3 INTEL  CALISTGA  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7F6DCF3E, 4D96 (r1 INTEL  CALISTGA  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 7F6E2FC0, 0040
[    0.000000] ACPI: APIC 7F6E1E3C, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7F6E1EA4, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7F6E1EDC, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7F6E1F18, 0032 (r1 PTLTD  CALISTGA  6040000  PTL        1)
[    0.000000] ACPI: TMOR 7F6E1F4A, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: APIC 7F6E1F70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7F6E1FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7F6DC0C5, 04F6 (r2  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:12 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 7:12 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517859
[    0.000000] Kernel command line: ro root=/dev/sda2 hpet=disabled quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.073 MHz processor.
[    8.846188] Console: colour VGA+ 80x25
[    8.846194] console [tty0] enabled
[    8.846568] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.847348] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.021107] Memory: 2061400k/2087744k available (3046k kernel code, 25116k reserved, 1315k data, 296k init, 1170240k highmem)
[    9.021122] virtual kernel memory layout:
[    9.021124]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.021126]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.021128]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    9.021130]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    9.021133]       .init : 0xc054b000 - 0xc0595000   ( 296 kB)
[    9.021135]       .data : 0xc03f9831 - 0xc05424bc   (1315 kB)
[    9.021137]       .text : 0xc0100000 - 0xc03f9831   (3046 kB)
[    9.021143] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.021211] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    9.101175] Calibrating delay using timer specific routine.. 3196.41 BogoMIPS (lpj=6392838)
[    9.101221] Security Framework initialized
[    9.101229] SELinux:  Disabled at boot.
[    9.101257] AppArmor: AppArmor initialized
[    9.101264] Failure registering capabilities with primary security module.
[    9.101279] Mount-cache hash table entries: 512
[    9.101464] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    9.101480] monitor/mwait feature present.
[    9.101483] using mwait in idle threads.
[    9.101489] CPU: L1 I cache: 32K, L1 D cache: 24K
[    9.101493] CPU: L2 cache: 512K
[    9.101499] CPU: Physical Processor ID: 0
[    9.101503] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00003940 0040c39d 00000000 00000001 00000000
[    9.101514] Intel machine check architecture supported.
[    9.101520] Intel machine check reporting enabled on CPU#0.
[    9.101528] Compat vDSO mapped to ffffe000.
[    9.101543] Checking 'hlt' instruction... OK.
[    9.117628] SMP alternatives: switching to UP code
[    9.119835] Early unpacking initramfs... done
[    9.317458] ACPI: Core revision 20070126
[    9.317562] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.325915] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.325944] SMP alternatives: switching to SMP code
[    9.326688] Booting processor 1/1 eip 3000
[    9.336719] Initializing CPU#1
[    9.416892] Calibrating delay using timer specific routine.. 3192.23 BogoMIPS (lpj=6384464)
[    9.416905] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    9.416916] monitor/mwait feature present.
[    9.416922] CPU: L1 I cache: 32K, L1 D cache: 24K
[    9.416927] CPU: L2 cache: 512K
[    9.416931] CPU: Physical Processor ID: 0
[    9.416935] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00003940 0040c39d 00000000 00000001 00000000
[    9.416946] Intel machine check architecture supported.
[    9.416953] Intel machine check reporting enabled on CPU#1.
[    9.417265] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.417306] Total of 2 processors activated (6388.65 BogoMIPS).
[    9.417513] ENABLING IO-APIC IRQs
[    9.417733] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.564979] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    9.584983] Brought up 2 CPUs
[    9.585025] CPU0 attaching sched-domain:
[    9.585030]  domain 0: span 03
[    9.585033]   groups: 01 02
[    9.585039]   domain 1: span 03
[    9.585042]    groups: 03
[    9.585046] CPU1 attaching sched-domain:
[    9.585049]  domain 0: span 03
[    9.585052]   groups: 02 01
[    9.585057]   domain 1: span 03
[    9.585060]    groups: 03
[    9.585450] net_namespace: 64 bytes
[    9.585462] Booting paravirtualized kernel on bare hardware
[    9.586419] Time: 23:35:39  Date: 04/18/09
[    9.586512] NET: Registered protocol family 16
[    9.586863] No dock devices found.
[    9.587043] ACPI: bus type pci registered
[    9.587863] PCI: PCI BIOS revision 3.00 entry at 0xfde5f, last bus=5
[    9.587868] PCI: Using configuration type 1
[    9.587881] Setting up standard PCI resources
[    9.592721] ACPI: EC: Look up EC in DSDT
[    9.595296] ACPI: BIOS _OSI(Linux) query ignored
[    9.595301] ACPI: DMI System Vendor: Dell Inc.
[    9.595305] ACPI: DMI Product Name: Inspiron 910
[    9.595308] ACPI: DMI Product Version: A04
[    9.595311] ACPI: DMI Board Name: CN0J14
[    9.595314] ACPI: DMI BIOS Vendor: Dell Inc.
[    9.595317] ACPI: DMI BIOS Date: 12/29/2008
[    9.595320] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[    9.595324] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    9.596123] ACPI: Interpreter enabled
[    9.596128] ACPI: (supports S0 S3 S4 S5)
[    9.596154] ACPI: Using IOAPIC for interrupt routing
[    9.597461] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.669622] ACPI: Device [J380] status [0000000a]: functional but not present; setting present
[    9.713805] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    9.713812] ACPI: EC: driver started in interrupt mode
[    9.713894] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.714827] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.714835] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.716742] PCI: Transparent bridge - 0000:00:1e.0
[    9.716798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.717372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.717617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.717844] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    9.718096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.730314] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    9.730497] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.730675] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.730853] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    9.731029] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.731207] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    9.731385] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.731562] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    9.731815] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.731880] pnp: PnP ACPI init
[    9.731894] ACPI: bus type pnp registered
[    9.753131] pnp: PnP ACPI: found 11 devices
[    9.753137] ACPI: ACPI bus type pnp unregistered
[    9.753491] SCSI subsystem initialized
[    9.753568] libata version 3.00 loaded.
[    9.753886] usbcore: registered new interface driver usbfs
[    9.753959] usbcore: registered new interface driver hub
[    9.754040] usbcore: registered new device driver usb
[    9.754665] PCI: Using ACPI for IRQ routing
[    9.754672] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.844754] NET: Registered protocol family 8
[    9.844759] NET: Registered protocol family 20
[    9.844871] AppArmor: AppArmor Filesystem Enabled
[    9.848525] Time: tsc clocksource has been installed.
[    9.864800] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.864808] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    9.864814] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    9.864819] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    9.864825] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    9.864831] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    9.864837] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    9.864843] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    9.864857] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    9.864868] system 00:06: ioport range 0x680-0x69f has been reserved
[    9.864873] system 00:06: ioport range 0x800-0x80f has been reserved
[    9.864879] system 00:06: ioport range 0x1000-0x107f has been reserved
[    9.864884] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    9.864889] system 00:06: ioport range 0x1640-0x164f has been reserved
[    9.864895] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[    9.864900] system 00:06: ioport range 0xff00-0xff7f has been reserved
[    9.864909] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    9.864914] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    9.895815] PCI: Bridge: 0000:00:1c.0
[    9.895820]   IO window: disabled.
[    9.895829]   MEM window: f0100000-f01fffff
[    9.895836]   PREFETCH window: 88000000-880fffff
[    9.895844] PCI: Bridge: 0000:00:1c.1
[    9.895847]   IO window: disabled.
[    9.895854]   MEM window: f0200000-f02fffff
[    9.895860]   PREFETCH window: disabled.
[    9.895869] PCI: Bridge: 0000:00:1c.2
[    9.895874]   IO window: 2000-2fff
[    9.895882]   MEM window: 88100000-881fffff
[    9.895889]   PREFETCH window: f0600000-f06fffff
[    9.895896] PCI: Bridge: 0000:00:1e.0
[    9.895899]   IO window: disabled.
[    9.895906]   MEM window: disabled.
[    9.895912]   PREFETCH window: disabled.
[    9.895959] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.895970] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.896001] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    9.896010] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.896039] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.896048] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.896066] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.896088] NET: Registered protocol family 2
[    9.932778] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.933235] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.934278] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.934832] TCP: Hash tables configured (established 131072 bind 65536)
[    9.934837] TCP reno registered
[    9.944910] checking if image is initramfs... it is
[   10.327764] Freeing initrd memory: 2699k freed
[   10.328040] Simple Boot Flag at 0x36 set to 0x80
[   10.329283] audit: initializing netlink socket (disabled)
[   10.329304] audit(1240097739.188:1): initialized
[   10.329629] highmem bounce pool size: 64 pages
[   10.333401] VFS: Disk quotas dquot_6.5.1
[   10.333548] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.334433] io scheduler noop registered
[   10.334438] io scheduler anticipatory registered
[   10.334442] io scheduler deadline registered
[   10.334556] io scheduler cfq registered (default)
[   10.334576] Boot video device is 0000:00:02.0
[   10.334868] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.334935] assign_interrupt_mode Found MSI capability
[   10.334993] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.335063] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.335210] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.335275] assign_interrupt_mode Found MSI capability
[   10.335328] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.335410] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.335553] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   10.335617] assign_interrupt_mode Found MSI capability
[   10.335670] Allocate Port Service[0000:00:1c.2:pcie00]
[   10.335737] Allocate Port Service[0000:00:1c.2:pcie02]
[   10.340964] ACPI: AC Adapter [ACAD] (on-line)
[   10.396040] Switched to high resolution mode on CPU 0
[   10.396239] Switched to high resolution mode on CPU 1
[   10.480147] ACPI: Battery Slot [BAT1] (battery present)
[   10.480460] input: Power Button (FF) as /devices/virtual/input/input0
[   10.480467] ACPI: Power Button (FF) [PWRF]
[   10.480585] input: Lid Switch as /devices/virtual/input/input1
[   10.480664] ACPI: Lid Switch [LID0]
[   10.480786] input: Power Button (CM) as /devices/virtual/input/input2
[   10.480792] ACPI: Power Button (CM) [PWRB]
[   10.480908] input: Sleep Button (CM) as /devices/virtual/input/input3
[   10.480915] ACPI: Sleep Button (CM) [SLPB]
[   10.492397] ACPI: device:01 is registered as cooling_device0
[   10.492776] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   10.492786] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.493487] ACPI: SSDT 7F6DCC25, 0245 (r2  PmRef  Cpu0Ist     3000 INTL 20050624)
[   10.493823] ACPI: SSDT 7F6DC5BB, 05E5 (r2  PmRef  Cpu0Cst     3001 INTL 20050624)
[   10.494521] Monitor-Mwait will be used to enter C-1 state
[   10.494527] Monitor-Mwait will be used to enter C-2 state
[   10.494531] Monitor-Mwait will be used to enter C-3 state
[   10.494608] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.494691] ACPI: ACPI0007:00 is registered as cooling_device1
[   10.494699] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.495182] ACPI: SSDT 7F6DCE6A, 00D4 (r2  PmRef  Cpu1Ist     3000 INTL 20050624)
[   10.495498] ACPI: SSDT 7F6DCBA0, 0085 (r2  PmRef  Cpu1Cst     3000 INTL 20050624)
[   10.496382] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   10.496465] ACPI: ACPI0007:01 is registered as cooling_device2
[   10.496474] ACPI: Processor [CPU1] (supports 8 throttling states)
[   10.521764] ACPI: LNXTHERM:01 is registered as thermal_zone0
[   10.526078] ACPI: Thermal Zone [TZ01] (51 C)
[   10.652686] Real Time Clock Driver v1.12ac
[   10.653193] hpet_acpi_add: no address or irqs in _CRS
[   10.653222] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.655409] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.656018] loop: module loaded
[   10.656103] Driver 'sd' needs updating - please use bus_type methods
[   10.656170] Driver 'sr' needs updating - please use bus_type methods
[   10.656372] ata_piix 0000:00:1f.1: version 2.12
[   10.656402] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   10.656454] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   10.656568] scsi0 : ata_piix
[   10.656705] scsi1 : ata_piix
[   10.657618] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   10.657625] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   10.820198] ata1.00: ATA-6: STEC PATA 32GB, E5221-10, max UDMA/133
[   10.820204] ata1.00: 60188688 sectors, multi 1: LBA 
[   10.828074] ata1.00: configured for UDMA/100
[   10.828132] ata2: port disabled. ignoring.
[   10.828345] scsi 0:0:0:0: Direct-Access     ATA      STEC PATA 32GB   E522 PQ: 0 ANSI: 5
[   10.828602] sd 0:0:0:0: [sda] 60188688 512-byte hardware sectors (30817 MB)
[   10.828630] sd 0:0:0:0: [sda] Write Protect is off
[   10.828637] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.828684] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.828780] sd 0:0:0:0: [sda] 60188688 512-byte hardware sectors (30817 MB)
[   10.828809] sd 0:0:0:0: [sda] Write Protect is off
[   10.828815] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.828861] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.828869]  sda: sda1 sda2
[   10.829476] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.829616] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   10.830032] USB Universal Host Controller Interface driver v3.0
[   10.830140] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   10.830155] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.830162] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.830327] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.830370] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   10.830701] usb usb1: configuration #1 chosen from 1 choice
[   10.830787] hub 1-0:1.0: USB hub found
[   10.830799] hub 1-0:1.0: 2 ports detected
[   10.931642] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   10.931659] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.931666] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.931825] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.931864] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   10.932135] usb usb2: configuration #1 chosen from 1 choice
[   10.932219] hub 2-0:1.0: USB hub found
[   10.932231] hub 2-0:1.0: 2 ports detected
[   11.035536] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.035550] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.035556] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.035709] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.035747] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   11.036021] usb usb3: configuration #1 chosen from 1 choice
[   11.036103] hub 3-0:1.0: USB hub found
[   11.036115] hub 3-0:1.0: 2 ports detected
[   11.139437] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   11.139450] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.139457] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.139626] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.139666] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   11.139932] usb usb4: configuration #1 chosen from 1 choice
[   11.140014] hub 4-0:1.0: USB hub found
[   11.140025] hub 4-0:1.0: 2 ports detected
[   11.243355] Initializing USB Mass Storage driver...
[   11.243434] usbcore: registered new interface driver usb-storage
[   11.243439] USB Mass Storage support registered.
[   11.243512] usbcore: registered new interface driver libusual
[   11.243749] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.276390] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.276400] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.276698] mice: PS/2 mouse device common for all mice
[   11.351398] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.371644] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input6
[   11.422635] cpuidle: using governor ladder
[   12.422718] cpuidle: using governor menu
[   12.422786] sdhci: Secure Digital Host Controller Interface driver
[   12.422792] sdhci: Copyright(c) Pierre Ossman
[   12.422889] sdhci: SDHCI controller found at 0000:02:00.2 [197b:2381] (rev 0)
[   12.422937] ACPI: PCI Interrupt 0000:02:00.2[A] -> GSI 16 (level, low) -> IRQ 17
[   12.422971] PCI: Setting latency timer of device 0000:02:00.2 to 64
[   12.423141] mmc0: SDHCI at 0xf0100400 irq 17 DMA
[   12.426515] ACPI: PCI Interrupt 0000:02:00.3[A] -> GSI 16 (level, low) -> IRQ 17
[   12.426529] PCI: Setting latency timer of device 0000:02:00.3 to 64
[   12.426930] usbcore: registered new interface driver hiddev
[   12.427012] usbcore: registered new interface driver usbhid
[   12.427019] /root/src/hardy-netbook/debian/build/custom-source-lpia/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   12.427191] NET: Registered protocol family 1
[   12.427637] NET: Registered protocol family 10
[   12.427961] lo: Disabled Privacy Extensions
[   12.428516] NET: Registered protocol family 17
[   12.428554] Using IPI No-Shortcut mode
[   12.428771]   Magic number: 5:809:605
[   12.428845]   hash matches device ptyd9
[   12.428857]   hash matches device ptyac
[   12.429107] Freeing unused kernel memory: 296k freed
[   12.817404] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   12.817433] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.817443] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.817652] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   12.821623] ehci_hcd 0000:00:1d.7: debug port 1
[   12.821642] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.821655] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf0544000
[   12.837727] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.838015] usb usb5: configuration #1 chosen from 1 choice
[   12.838111] hub 5-0:1.0: USB hub found
[   12.838126] hub 5-0:1.0: 8 ports detected
[   13.048497] Registering unionfs 1.4
[   13.048502] unionfs: debugging is not enabled
[   13.056594] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   13.142723] fuse init (API version 7.9)
[   14.443872] kjournald starting.  Commit interval 5 seconds
[   14.443881] EXT3-fs: mounted filesystem with ordered data mode.
[   14.887763] Clocksource tsc unstable (delta = -211362743 ns)
[   14.891922] Time: acpi_pm clocksource has been installed.
[   16.679778] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   16.775117] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   16.949234] intel_rng: FWH not detected
[   16.989622] iTCO_vendor_support: vendor-support=0
[   17.010583] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   17.010726] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.010790] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.029123] ieee80211_crypt: registered algorithm 'NULL'
[   17.054780] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.054911] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   17.055045] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   17.056545] eth0: RTL8101e at 0xf8866000, 00:24:e8:91:dd:0f, XID 24a00000 IRQ 220
[   17.150882] ieee80211_crypt: registered algorithm 'TKIP'
[   17.220972] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   17.221402] EXT3 FS on sda2, internal journal
[   18.501737] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   18.501779] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.644816] Linux agpgart interface v0.102
[   18.649583] agpgart: Detected an Intel 945GME Chipset.
[   18.649790] agpgart: Detected 7932K stolen memory.
[   18.667552] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.709443] [drm] Initialized drm 1.1.0 20060810
[   21.183597] drm_psb: exports duplicate symbol drm_order (owned by drm)
[   21.195307] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   21.195340] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   21.197436] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  104.902523] usb 5-8: new high speed USB device using ehci_hcd and address 2
[  105.039646] usb 5-8: configuration #1 chosen from 3 choices
[ 7954.921552] usb 5-8: USB disconnect, address 2
[ 8091.319995] usb 5-8: new high speed USB device using ehci_hcd and address 3
[ 8091.453139] usb 5-8: configuration #1 chosen from 1 choice
[ 8091.454164] scsi2 : SCSI emulation for USB Mass Storage devices
[ 8091.455501] usb-storage: device found at 3
[ 8091.455521] usb-storage: waiting for device to settle before scanning
[ 8095.541772] usb-storage: device scan complete
[ 8095.542372] scsi 2:0:0:0: Direct-Access     USB      Flash Disk       5.00 PQ: 0 ANSI: 2
[ 8095.545203] sd 2:0:0:0: [sdb] 2046976 512-byte hardware sectors (1048 MB)
[ 8095.552788] sd 2:0:0:0: [sdb] Write Protect is off
[ 8095.552801] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 8095.552807] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 8095.554925] sd 2:0:0:0: [sdb] 2046976 512-byte hardware sectors (1048 MB)
[ 8095.555554] sd 2:0:0:0: [sdb] Write Protect is off
[ 8095.555562] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 8095.555567] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 8095.555578]  sdb: sdb1
[ 8095.561575] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 8095.561676] sd 2:0:0:0: Attached scsi generic sg1 type 0
```

---

### Post by khelben1979 on 2009-04-19
> **Windsurfer619 said:**
> It's 
sudo /etc/init.d/NetworkManager restart
on ubuntu.

I will definitely try to remember that. I'm an old Debian user. :)

---

### Post by Windsurfer619 on 2009-04-19
Heh, that's okay.

As for the main problem, it looks like your wireless card is not detected by the system. During my boot process, I get lines like "[   44.317604] ADDRCONF(NETDEV_UP): wlan0: link is not ready" but you don't seem to have any of those, just in regards to your ethernet.
Maybe you bumped into the off switch? If you could paste the output of "lspci" we might be able to figure out if the system knows about your wireless card.

---

### Post by andywhoa on 2009-04-19
> **Windsurfer619 said:**
> Heh, that's okay.

As for the main problem, it looks like your wireless card is not detected by the system. During my boot process, I get lines like "[   44.317604] ADDRCONF(NETDEV_UP): wlan0: link is not ready" but you don't seem to have any of those, just in regards to your ethernet.
Maybe you bumped into the off switch? If you could paste the output of "lspci" we might be able to figure out if the system knows about your wireless card.

I don't think my machine (Dell Mini 9) has a hardware wireless switch... I certainly don't see one and I've tried the fn key

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
```


I appreciate the help

---

### Post by Windsurfer619 on 2009-04-19
Ah. You have a broadcom network card. If you go in Administrator > Hardware Drivers, could you try disabling and re-enabling the driver you see there?

If that doesn't work, you may have to use ndiswrapper...

---

### Post by andywhoa on 2009-04-19
> **Windsurfer619 said:**
> Ah. You have a broadcom network card. If you go in Administrator > Hardware Drivers, could you try disabling and re-enabling the driver you see there?

If that doesn't work, you may have to use ndiswrapper...

Well, we're a step closer...

I opened up Administrator > Hardware Drivers.  There was only one device named "wl" listed there.  It was enabled but not in use.  I unchecked Enabled and then checked it again and the Status changed to "in use."  I then cd'd to my init.d and did *sudo NetworkManager start* and it started!

The problem now is that I cannot connect to either of my wireless routers (one I couldn't connect to before anyway).  I select the wireless network, enter the password when prompted, the icon spins for a couple seconds and then fails.  Any idea about this?

I did notice one thing that seems weird (but maybe it's not).  The wireless network I was connected to before was in my "edit wireless network" prefs.  When I clicked the checkmark to show me the password, it was waaaay off.  It was a really long alphanumeric that, in no way, resembled the password I would type in to connect to it.  I changed it to the correct password, clicked "set password" and exited the prefs.  When it still wouldn't connect, I went back in there again and the password was a really long alphanumeric again.  I can see how this may be normal as some small password may be interpreted into a longer key, but I thought I'd mention it.


Also, when I restart, Network Manager does not show up and wl is "not in use" again in Hardware Drivers

---

