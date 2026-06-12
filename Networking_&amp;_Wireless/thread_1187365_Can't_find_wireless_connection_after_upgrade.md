---
title: "Can't find wireless connection after upgrade"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by ryy705 on 2009-06-14
Hello,

I upgraded my Dell Inpiron 1501 to Kubuntu 9.04 just a few days ago.
The laptop can't find a wireless connection since then.
If I am reading the output of lshw command correctly(doubtful) my wireless is disabled.  Could someone kindly tell me how to enable it?
And no I do not have a physical button/switch on the laptop to turn off wireless.

Many thanks in advance for your help.

Output of lshw -C network:
```
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8f:e8:dd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.46 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:1c:26:3a:6f:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 42:bf:f0:4c:b8:a7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Output of nm-tool:
```
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8f:e8:dd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.46 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:1c:26:3a:6f:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 42:bf:f0:4c:b8:a7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by ryy705 on 2009-06-14
*bump*

---

### Post by t0mppa on 2009-06-15
Try running **sudo ifconfig eth1 up** from a terminal, that should enable it. However, the interface shouldn't be named eth1 under b43 drivers, so were you using them or the newer STA (wl) under 8.10?

---

### Post by ryy705 on 2009-06-15
doing sudo ifconfig eth1 up gave me "SIOCSIFFLAGS: device not found".  

I really do not know which version of driver I was using before.
Sorry I am not that technical.  Is a good book you could recommend for problems like these?

---

### Post by ryy705 on 2009-06-16
Under such circumstances in windows I would uninstall and reinstall the wireless driver. 
Can I do that in this situation?

---

### Post by ryy705 on 2009-06-16
Would buying a wireless adapter solve the problem?

---

### Post by t0mppa on 2009-06-17
[QUOTE=ryy705]doing sudo ifconfig eth1 up gave me "SIOCSIFFLAGS: device not found".

I really do not know which version of driver I was using before.
Sorry I am not that technical. Is a good book you could recommend for problems like these? [/QUOTE]

Ok, there's probably some conflict in that case. Don't know of any books about this, most of the info is available through a Google search on the internet though - there's just a lot of mixed info for different cards, so sorting through the results requires some work.

[QUOTE=ryy705]Under such circumstances in windows I would uninstall and reinstall the wireless driver. 
Can I do that in this situation?[/QUOTE]

Sure, the easiest way is just going to System / Administration / Hardware Drivers and enabling the Broadcom STA through there.

If it's already enabled, then it's likely a case of the ssb module hogging the interface before the STA (module named wl) can get associated with it. In which case, you can try the following commands from the terminal:
```
sudo modprobe -r b43 ssb
sudo modprobe wl
```

If neither of the above offer any help, run **dmesg** from the terminal and post back with the output, that should give a clue as to what's going wrong.

[QUOTE=ryy705]Would buying a wireless adapter solve the problem?[/QUOTE]

That's always one way of dodging problems, but your current adapter should be well supported, so that's not really necessary.

---

### Post by ryy705 on 2009-06-18
Thank you for your post.  I was beginning to lose hope.  I could google it learn how to do these things.  But I wouldn't know where to start.  That's why I was thinking about getting a book.  I am pasting the output of the commands below:

sudo modprobe -r b43 ssb
```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ssb is in use.

```

sudo modprobe wl:
```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```


sudo dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e70000 (usable)
[    0.000000]  BIOS-e820: 0000000037e70000 - 0000000037e80000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e80000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 894MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8530
[    0.000000] Entering add_active_range(0, 0, 228976) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   228976
[    0.000000]   HighMem    228976 ->   228976
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   228976
[    0.000000] On node 0 totalpages: 228976
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1756 pages used for memmap
[    0.000000]   Normal zone: 223124 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8500 checksum 0
[    0.000000] ACPI: RSDP 000F8500, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 37E79522, 003C (r1 DELL    M08      6040000  LTP        0)
[    0.000000] ACPI: FACP 37E7FB4E, 0074 (r1 ATI    Bowfin    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 37E7955E, 65F0 (r1    ATI    SB600  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 37E90FC0, 0040
[    0.000000] ACPI: TCPA 37E7FBC2, 0032 (r2 AMD              6040000 PTEC        0)
[    0.000000] ACPI: SSDT 37E7FBF4, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 37E7FDFA, 0054 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 37E7FE4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SLIC 37E7FE8A, 0176 (r1 DELL    M08      6040000  LTP        0)
[    0.000000] ACPI: DMI detected: Dell
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227188
[    0.000000] Kernel command line: root=UUID=4cf17e41-44c3-407d-a347-8342cc8132e3 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.053 MHz processor.
[   21.356779] Console: colour VGA+ 80x25
[   21.356782] console [tty0] enabled
[   21.357091] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.357448] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.371375] Memory: 895484k/915904k available (2177k kernel code, 19884k reserved, 1005k data, 368k init, 0k highmem)
[   21.371383] virtual kernel memory layout:
[   21.371384]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   21.371385]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.371386]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.371387]     lowmem  : 0xc0000000 - 0xf7e70000   ( 894 MB)
[   21.371388]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   21.371389]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
[   21.371390]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
[   21.371393] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.371423] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.451406] Calibrating delay using timer specific routine.. 3993.91 BogoMIPS (lpj=7987820)
[   21.451427] Security Framework initialized
[   21.451431] SELinux:  Disabled at boot.
[   21.451444] AppArmor: AppArmor initialized
[   21.451447] Failure registering capabilities with primary security module.
[   21.451454] Mount-cache hash table entries: 512
[   21.451548] Initializing cgroup subsys ns
[   21.451551] Initializing cgroup subsys cpuacct
[   21.451559] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   21.451567] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.451569] CPU: L2 Cache: 512K (64 bytes/line)
[   21.451572] CPU 0(2) -> Core 0
[   21.451573] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   21.451581] Compat vDSO mapped to ffffe000.
[   21.451591] Checking 'hlt' instruction... OK.
[   21.467644] SMP alternatives: switching to UP code
[   21.468750] Early unpacking initramfs... done
[   21.785417] ACPI: Core revision 20070126
[   21.785489] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.821634] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 01
[   22.821650] SMP alternatives: switching to SMP code
[   22.822112] Booting processor 1/1 eip 3000
[   22.830992] Initializing CPU#1
[   22.909558] Calibrating delay using timer specific routine.. 3990.27 BogoMIPS (lpj=7980541)
[   22.909565] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   22.909571] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.909573] CPU: L2 Cache: 512K (64 bytes/line)
[   22.909575] CPU 1(2) -> Core 1
[   22.909577] AMD C1E detected late. 	Force timer broadcast.
[   22.909578] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   22.910875] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 01
[   22.910889] Total of 2 processors activated (7984.18 BogoMIPS).
[   22.911050] ENABLING IO-APIC IRQs
[   22.911222] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   22.950927] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   22.950967] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   22.950969] ...trying to set up timer as Virtual Wire IRQ... works.
[   22.990797] Brought up 2 CPUs
[   22.990822] CPU0 attaching sched-domain:
[   22.990825]  domain 0: span 03
[   22.990827]   groups: 01 02
[   22.990830] CPU1 attaching sched-domain:
[   22.990831]  domain 0: span 03
[   22.990833]   groups: 02 01
[   22.991020] net_namespace: 64 bytes
[   22.991027] Booting paravirtualized kernel on bare hardware
[   22.991451] Time:  9:11:19  Date: 06/18/09
[   22.991476] NET: Registered protocol family 16
[   22.991646] EISA bus registered
[   22.991651] ACPI: bus type pci registered
[   23.006964] PCI: BIOS BUG #81[49435000] found
[   23.007000] PCI: Using configuration type 1
[   23.007006] Setting up standard PCI resources
[   23.008669] ACPI: EC: Look up EC in DSDT
[   23.010641] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   23.010889] ACPI: Interpreter enabled
[   23.010892] ACPI: (supports S0 S3 S4 S5)
[   23.010902] ACPI: Using IOAPIC for interrupt routing
[   23.024630] ACPI: EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[   23.024632] ACPI: EC: driver started in poll mode
[   23.024667] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.024854] pci 0000:00:12.0: set SATA to AHCI mode
[   23.026126] PCI: Transparent bridge - 0000:00:14.4
[   23.026154] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.026308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   23.026408] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   23.026518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   23.026607] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   23.029357] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   23.029464] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   23.029567] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   23.029669] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   23.029770] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   23.029875] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   23.029977] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   23.030078] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   23.030179] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   23.030288] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.030315] pnp: PnP ACPI init
[   23.030321] ACPI: bus type pnp registered
[   23.033124] pnp: PnP ACPI: found 10 devices
[   23.033126] ACPI: ACPI bus type pnp unregistered
[   23.033129] PnPBIOS: Disabled by ACPI PNP
[   23.033317] PCI: Using ACPI for IRQ routing
[   23.033320] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.033326] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   23.033328] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   23.032652] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   23.050728] NET: Registered protocol family 8
[   23.050731] NET: Registered protocol family 20
[   23.050790] AppArmor: AppArmor Filesystem Enabled
[   23.066699] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   23.066702] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   23.066705] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   23.066713] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   23.066715] system 00:08: ioport range 0x220-0x22f has been reserved
[   23.066718] system 00:08: ioport range 0x40b-0x40b has been reserved
[   23.066721] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   23.066723] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   23.066725] system 00:08: ioport range 0x530-0x537 has been reserved
[   23.066728] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   23.066731] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   23.066733] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   23.066736] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   23.066738] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   23.066741] system 00:08: ioport range 0xcd0-0xcd3 has been reserved
[   23.066743] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   23.066746] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   23.066748] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   23.066751] system 00:08: ioport range 0x8000-0x805f has been reserved
[   23.066754] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   23.066756] system 00:08: ioport range 0x87f-0x87f has been reserved
[   23.066762] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   23.066765] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   23.066768] system 00:09: iomem range 0xc0004800-0xc0004bff has been reserved
[   23.066771] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[   23.066774] system 00:09: iomem range 0x0-0xfff could not be reserved
[   23.097118] PCI: Bridge: 0000:00:01.0
[   23.097120]   IO window: 9000-9fff
[   23.097123]   MEM window: c0100000-c01fffff
[   23.097126]   PREFETCH window: c8000000-cfffffff
[   23.097128] PCI: Bridge: 0000:00:05.0
[   23.097130]   IO window: disabled.
[   23.097132]   MEM window: disabled.
[   23.097134]   PREFETCH window: disabled.
[   23.097136] PCI: Bridge: 0000:00:06.0
[   23.097138]   IO window: disabled.
[   23.097140]   MEM window: c0200000-c02fffff
[   23.097142]   PREFETCH window: disabled.
[   23.097145] PCI: Bridge: 0000:00:14.4
[   23.097146]   IO window: disabled.
[   23.097152]   MEM window: c0300000-c03fffff
[   23.097156]   PREFETCH window: disabled.
[   23.097175] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   23.097182] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   23.097199] NET: Registered protocol family 2
[   23.098650] Time: acpi_pm clocksource has been installed.
[   23.098655] Clockevents: could not switch to one-shot mode:<6>Clockevents: could not switch to one-shot mode: lapic is not functional.
[   23.097522] Could not switch to high resolution mode on CPU 1
[   23.098665]  lapic is not functional.
[   23.098667] Could not switch to high resolution mode on CPU 0
[   23.146700] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.146973] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.147687] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.148016] TCP: Hash tables configured (established 131072 bind 65536)
[   23.148019] TCP reno registered
[   23.162757] checking if image is initramfs... it is
[   23.778758] Freeing initrd memory: 7742k freed
[   23.778360] audit: initializing netlink socket (disabled)
[   23.778374] audit(1245316278.352:1): initialized
[   23.780281] VFS: Disk quotas dquot_6.5.1
[   23.780347] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.780464] io scheduler noop registered
[   23.780466] io scheduler anticipatory registered
[   23.780467] io scheduler deadline registered
[   23.780480] io scheduler cfq registered (default)
[   23.780486] PCI: MSI quirk detected. MSI deactivated.
[   23.780550] Boot video device is 0000:01:05.0
[   23.780661] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   23.780682] assign_interrupt_mode Found MSI capability
[   23.780684] Allocate Port Service[0000:00:05.0:pcie00]
[   23.780723] Allocate Port Service[0000:00:05.0:pcie02]
[   23.780780] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   23.780799] assign_interrupt_mode Found MSI capability
[   23.780802] Allocate Port Service[0000:00:06.0:pcie00]
[   23.780837] Allocate Port Service[0000:00:06.0:pcie02]
[   23.781052] isapnp: Scanning for PnP cards...
[   24.134761] isapnp: No Plug & Play device found
[   24.165223] Real Time Clock Driver v1.12ac
[   24.165325] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.166502] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.166566] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   24.166656] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   24.170117] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.170123] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.189029] mice: PS/2 mouse device common for all mice
[   24.189149] EISA: Probing bus 0 at eisa.0
[   24.189157] Cannot allocate resource for EISA slot 1
[   24.189184] Cannot allocate resource for EISA slot 8
[   24.189186] EISA: Detected 0 cards.
[   24.189189] cpuidle: using governor ladder
[   24.189191] cpuidle: using governor menu
[   24.189275] NET: Registered protocol family 1
[   24.189299] Using IPI No-Shortcut mode
[   24.189331] registered taskstats version 1
[   24.189460]   Magic number: 13:919:171
[   24.189611] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   24.189613] EDD information not available.
[   24.189866] Freeing unused kernel memory: 368k freed
[   24.189891] Write protecting the kernel read-only data: 801k
[   24.234111] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   25.417582] fuse init (API version 7.9)
[   25.497200] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.523904] ACPI: Thermal Zone [THRM] (35 C)
[   25.885282] usbcore: registered new interface driver usbfs
[   25.885306] usbcore: registered new interface driver hub
[   25.897725] SCSI subsystem initialized
[   25.903679] usbcore: registered new device driver usb
[   25.926166] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[   25.926180] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   25.945183] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   25.945194] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   25.945201] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   25.945208] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   25.945527] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.961189] libata version 3.00 loaded.
[   25.985201] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[   25.985237] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 17
[   25.985251] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   25.985521] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   25.985540] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0005000
[   26.041257] usb usb1: configuration #1 chosen from 1 choice
[   26.041282] hub 1-0:1.0: USB hub found
[   26.041291] hub 1-0:1.0: 2 ports detected
[   26.145158] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 18
[   26.145175] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   26.145201] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   26.145220] ohci_hcd 0000:00:13.1: irq 18, io mem 0xc0006000
[   26.201161] usb usb2: configuration #1 chosen from 1 choice
[   26.201184] hub 2-0:1.0: USB hub found
[   26.201193] hub 2-0:1.0: 2 ports detected
[   26.308008] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 16
[   26.308024] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   26.308048] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   26.308067] ohci_hcd 0000:00:13.2: irq 16, io mem 0xc0007000
[   26.364069] usb usb3: configuration #1 chosen from 1 choice
[   26.364093] hub 3-0:1.0: USB hub found
[   26.364102] hub 3-0:1.0: 2 ports detected
[   26.467924] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 18
[   26.467941] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   26.467963] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   26.467978] ohci_hcd 0000:00:13.3: irq 18, io mem 0xc0008000
[   26.523907] usb usb4: configuration #1 chosen from 1 choice
[   26.523928] hub 4-0:1.0: USB hub found
[   26.523936] hub 4-0:1.0: 2 ports detected
[   26.627819] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 16
[   26.627832] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   26.627851] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   26.627864] ohci_hcd 0000:00:13.4: irq 16, io mem 0xc0009000
[   26.683831] usb usb5: configuration #1 chosen from 1 choice
[   26.683853] hub 5-0:1.0: USB hub found
[   26.683861] hub 5-0:1.0: 2 ports detected
[   26.788828] ahci 0000:00:12.0: version 3.0
[   26.788861] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 19
[   26.788879] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   26.788881] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   27.792274] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   27.792278] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   27.792642] scsi0 : ahci
[   27.792702] scsi1 : ahci
[   27.792736] scsi2 : ahci
[   27.792775] scsi3 : ahci
[   27.792845] ata1: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004100 irq 19
[   27.792848] ata2: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004180 irq 19
[   27.792852] ata3: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004200 irq 19
[   27.792856] ata4: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004280 irq 19
[   28.268006] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.267867] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7KP, max UDMA/100
[   28.267872] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   28.268948] ata1.00: configured for UDMA/100
[   28.579849] ata2: SATA link down (SStatus 0 SControl 300)
[   28.891694] ata3: SATA link down (SStatus 0 SControl 300)
[   29.203539] ata4: SATA link down (SStatus 0 SControl 300)
[   29.203642] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[   29.203042] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 20
[   29.203060] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   29.203095] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   29.203137] ehci_hcd 0000:00:13.5: debug port 1
[   29.203152] ehci_hcd 0000:00:13.5: irq 20, io mem 0xc0004400
[   29.209820] Driver 'sd' needs updating - please use bus_type methods
[   29.214462] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.214575] usb usb6: configuration #1 chosen from 1 choice
[   29.214597] hub 6-0:1.0: USB hub found
[   29.214602] hub 6-0:1.0: 10 ports detected
[   29.219583] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   29.219596] sd 0:0:0:0: [sda] Write Protect is off
[   29.219598] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.219614] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.219658] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   29.219666] sd 0:0:0:0: [sda] Write Protect is off
[   29.219668] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.219681] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.219684]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   29.272087] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.277234] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.319650] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   29.339493] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   29.339503] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   29.339511] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   29.379494] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[   29.379522] b44.c:v2.0
[   29.399763] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:8f:e8:dd
[   29.400350] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   29.400395] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   29.400408] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   29.401963] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   29.402965] scsi4 : pata_atiixp
[   29.403613] scsi5 : pata_atiixp
[   29.404173] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[   29.404176] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[   29.739753] ata5.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D200, max UDMA/33
[   29.927620] ata5.00: configured for UDMA/33
[   30.085510] scsi 4:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D200 PQ: 0 ANSI: 5
[   30.085588] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   30.090924] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.090930] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.100521] Driver 'sr' needs updating - please use bus_type methods
[   30.118962] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   30.118967] Uniform CD-ROM driver Revision: 3.20
[   30.119013] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   30.203868] Attempting manual resume
[   30.203872] swsusp: Resume From Partition 8:5
[   30.203873] PM: Checking swsusp image.
[   30.204002] PM: Resume from disk failed.
[   30.235470] kjournald starting.  Commit interval 5 seconds
[   30.234416] EXT3-fs: mounted filesystem with ordered data mode.
[   41.307477] udev: starting version 141
[   42.096540] ACPI: AC Adapter [ACAD] (off-line)
[   42.153466] input: Power Button (FF) as /devices/virtual/input/input2
[   42.172020] ACPI: Power Button (FF) [PWRF]
[   42.172107] input: Power Button (CM) as /devices/virtual/input/input3
[   42.188017] ACPI: Power Button (CM) [PWRB]
[   42.188114] input: Sleep Button (CM) as /devices/virtual/input/input4
[   42.204001] ACPI: Sleep Button (CM) [SLPB]
[   42.204080] input: Lid Switch as /devices/virtual/input/input5
[   42.205052] ACPI: Lid Switch [LID]
[   42.293425] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input6
[   42.311962] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   42.404657] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   42.482294] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.585435] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.657568] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   42.715867] ACPI: Battery Slot [BAT1] (battery present)
[   42.745487] ricoh-mmc: Ricoh MMC Controller disabling driver
[   42.745489] ricoh-mmc: Copyright(c) Philip Langdale
[   42.745531] ricoh-mmc: Ricoh MMC controller found at 0000:08:01.1 [1180:0843] (rev 1)
[   42.745537] ricoh-mmc: Main firewire function not found. Cannot disable controller.
[   42.895488] ACPI: WMI-Acer: Mapper loaded
[   42.939134] Linux agpgart interface v0.102
[   43.025089] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   43.049302] [fglrx] Maximum main memory to use for locked dma buffers: 802 MBytes.
[   43.049333] [fglrx] ASYNCIO init succeed!
[   43.049650] [fglrx] PAT is enabled successfully!
[   43.049673] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   43.079375] sdhci: Secure Digital Host Controller Interface driver
[   43.079379] sdhci: Copyright(c) Pierre Ossman
[   43.079422] sdhci: SDHCI controller found at 0000:08:01.0 [1180:0822] (rev 19)
[   43.079449] ACPI: PCI Interrupt 0000:08:01.0[B] -> GSI 20 (level, low) -> IRQ 22
[   43.079467] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   43.079519] mmc0: SDHCI at 0xc0302800 irq 22 DMA
[   43.126505] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   43.453134] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   43.490309] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   43.490919] b43-phy0: Broadcom 4311 WLAN found
[   43.531361] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   43.531382] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   43.556392] phy0: Selected rate control algorithm 'simple'
[   43.674646] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   43.677427] udev: renamed network interface wlan0 to eth1
[   43.933640] lp: driver loaded but no devices found
[   44.030873] Adding 2024148k swap on /dev/sda5.  Priority:-1 extents:1 across:2024148k
[   44.047530] EXT3 FS on sda3, internal journal
[   44.222892] device-mapper: uevent: version 1.0.3
[   44.222928] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   44.830028] audit(1245316299.414:2): type=1505 operation="profile_load" info="unsupported interface version" pid=4457
[   44.999291] audit(1245316299.586:3): type=1505 operation="profile_load" info="unsupported interface version" pid=4464
[   45.098287] audit(1245316299.682:4): type=1505 operation="profile_load" info="unsupported interface version" pid=4472
[   45.130625] audit(1245316299.718:5): type=1505 operation="profile_load" info="unsupported interface version" pid=4478
[   45.553574] No dock devices found.
[   47.792558] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[   47.792566] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[   47.802376] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[   47.802380] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[   52.720234] Bluetooth: Core ver 2.11
[   52.720821] NET: Registered protocol family 31
[   52.720825] Bluetooth: HCI device and connection manager initialized
[   52.720829] Bluetooth: HCI socket layer initialized
[   52.766615] Bluetooth: L2CAP ver 2.9
[   52.766620] Bluetooth: L2CAP socket layer initialized
[   52.780682] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[   52.780687] Bluetooth: BNEP filters: protocol multicast
[   52.808710] Bridge firewalling registered
[   52.808087] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   52.815798] Bluetooth: SCO (Voice Link) ver 0.6
[   52.815806] Bluetooth: SCO socket layer initialized
[   53.039779] Bluetooth: RFCOMM socket layer initialized
[   53.039796] Bluetooth: RFCOMM TTY layer initialized
[   53.039798] Bluetooth: RFCOMM ver 1.8
[   54.523213] ppdev: user-space parallel port driver
[   55.568375] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 18
[   57.121027] NET: Registered protocol family 10
[   57.121303] lo: Disabled Privacy Extensions
[   58.409351] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   58.477026] input: b43-phy0 as /devices/virtual/input/input9
[   58.887257] b43-phy0 ERROR: YOUR FIRMWARE IS TOO NEW. Please downgrade your firmware.
[   58.887265] b43-phy0 ERROR: Use this firmware tarball: http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
[   58.887271] b43-phy0 ERROR: Use this b43-fwcutter tarball: http://bu3sch.de/b43/fwcutter/b43-fwcutter-009.tar.bz2
[   58.887274] b43-phy0 ERROR: Read, understand and _do_ what this message says, please.
[   59.088664] input: b43-phy0 as /devices/virtual/input/input10
[   59.244059] b43-phy0 ERROR: Microcode not responding
[   59.244069] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   59.264615] NET: Registered protocol family 17
[   87.283992] CPU0 attaching NULL sched-domain.
[   87.283998] CPU1 attaching NULL sched-domain.
[   87.302941] CPU0 attaching sched-domain:
[   87.302946]  domain 0: span 03
[   87.302948]   groups: 01 02
[   87.302951] CPU1 attaching sched-domain:
[   87.302953]  domain 0: span 03
[   87.302955]   groups: 02 01
[  118.429214] hda-intel: Invalid position buffer, using LPIB read method instead.
[  248.161581] b44: eth0: Link is up at 100 Mbps, full duplex.
[  248.161588] b44: eth0: Flow control is off for TX and off for RX.
[  248.162817] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  258.401053] eth0: no IPv6 routers present
[ 6607.760777] APIC error on CPU0: 00(40)
[ 6607.763281] APIC error on CPU1: 00(40)
[ 6696.319647] BUG: unable to handle kernel paging request at virtual address f89950d0
[ 6696.319655] printing eip: f89950d0 *pde = 361b1067 *pte = 00000000 
[ 6696.319661] Oops: 0000 [#1] SMP 
[ 6696.319664] Modules linked in: af_packet rfkill_input ipv6 binfmt_misc ppdev rfcomm sco bridge bnep l2cap bluetooth sbs container dock sbshc dm_crypt dm_mod lp parport snd_hda_intel arc4 ecb blkcipher joydev snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi rfkill snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw ati_agp i2c_piix4 sdhci fglrx(P) snd agpgart wmi_acer psmouse i2c_core ricoh_mmc mmc_core pcspkr k8temp shpchp pci_hotplug dcdbas evdev battery video output button soundcore ac ext3 jbd mbcache sr_mod cdrom atiixp ide_core pata_atiixp pata_acpi sg sd_mod b44 mii ata_generic ahci ehci_hcd ohci_hcd ssb libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 6696.319712] 
[ 6696.319715] Pid: 6012, comm: ipolldevd Tainted: P        (2.6.24-21-generic #1)
[ 6696.319718] EIP: 0060:[<f89950d0>] EFLAGS: 00010247 CPU: 1
[ 6696.319722] EIP is at 0xf89950d0
[ 6696.319724] EAX: f7112374 EBX: f7112374 ECX: f7112378 EDX: f66c1484
[ 6696.319726] ESI: f66c1480 EDI: f66c1480 EBP: f89950d0 ESP: f73e5f84
[ 6696.319728]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[ 6696.319731] Process ipolldevd (pid: 6012, ti=f73e4000 task=f795d140 task.ti=f73e4000)
[ 6696.319733] Stack: c013cdaf 00000000 000000ff 00000000 00000000 f66c1484 f66c148c f66c1480 
[ 6696.319739]        c013d850 f66c1484 c013d8d4 00000000 f795d140 c0140b60 f73e5fbc f73e5fbc 
[ 6696.319744]        fffffffc f66c1480 c013d850 00000000 c01408a2 c0140860 00000000 00000000 
[ 6696.319749] Call Trace:
[ 6696.319751]  [<c013cdaf>] run_workqueue+0xbf/0x160
[ 6696.319761]  [<c013d850>] worker_thread+0x0/0xe0
[ 6696.319766]  [<c013d8d4>] worker_thread+0x84/0xe0
[ 6696.319771]  [<c0140b60>] autoremove_wake_function+0x0/0x40
[ 6696.319777]  [<c013d850>] worker_thread+0x0/0xe0
[ 6696.319781]  [<c01408a2>] kthread+0x42/0x70
[ 6696.319784]  [<c0140860>] kthread+0x0/0x70
[ 6696.319788]  [<c0105667>] kernel_thread_helper+0x7/0x10
[ 6696.319794]  =======================
[ 6696.319795] Code:  Bad EIP value.
[ 6696.319799] EIP: [<f89950d0>] 0xf89950d0 SS:ESP 0068:f73e5f84
[ 6696.319804] ---[ end trace 3bb517facaaf3fe5 ]---
[ 6832.889430] APIC error on CPU0: 40(40)
[ 6832.892605] APIC error on CPU1: 40(40)
[ 6912.524020] ieee80211_crypt: registered algorithm 'NULL'
[ 6927.091907] APIC error on CPU0: 40(40)
[ 6927.095309] APIC error on CPU1: 40(40)

```

---

### Post by t0mppa on 2009-06-18
Ok, looks like you have b43 active and then also some remnants of NDISWrapper around. And you really didn't have to run the modprobes (unloading the b43 & ssb modules from the kernel and loading up the wl module), unless you had the STA marked as active in the Hardware Drivers.

Personally, I prefer going as native with Linux as possible and that means avoiding things like ndiswrapper (that simply wraps Windows drivers to work with Linux) unless there's no other choice. And having more than one driver for any interface is bound to lead to trouble.

So, first you should make sure you're starting from a clean plate. Run **lsmod | grep ndiswrapper** from a terminal and if that shows any output, then it means it is active and you should remove it. [Here]("http://ubuntuforums.org/showthread.php?t=507378")'s a thread about how to do that. If no output is given, then it's not active and you can just remove /etc/modprobe.d/ndiswrapper, since like modprobe tells you, it's a deprecated format and might end up causing trouble in the long run.

Once that's done, then you have two choices for a driver: the b43 and STA (wl). A lot of people prefer the latter and installing that should be as simple as enabling it from the Hardware Drivers. It doesn't support my card though, so I haven't personally used it and am not that familiar with issues related to it. You will need to blacklist b43 in order for that to work though and since your wired interface uses b44, that's a bit of a hassle, as the ssb module is used by that one also, like the modprobe output you pasted was saying.

The simplest thing would be just giving the b43 a try, as that's already being the driver that's trying to get associated with the interface. Just make sure the STA is not active on the Hardware Drivers page, if you do this, since having both of them around will create conflicts and neither will likely work. Like dmesg says, you'll just need to install the correct version of firmware for it:

[QUOTE=ryy705][   58.887257] b43-phy0 ERROR: YOUR FIRMWARE IS TOO NEW. Please downgrade your firmware.
[   58.887265] b43-phy0 ERROR: Use this firmware tarball: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
[   58.887271] b43-phy0 ERROR: Use this b43-fwcutter tarball: [http://bu3sch.de/b43/fwcutter/b43-fwcutter-009.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-009.tar.bz2)
[   58.887274] b43-phy0 ERROR: Read, understand and _do_ what this message says, please.
[   59.088664] input: b43-phy0 as /devices/virtual/input/input10
[   59.244059] b43-phy0 ERROR: Microcode not responding
[   59.244069] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).[/QUOTE]

That's fairly self-explanatory. The page at linuxwireless.org has pretty good instructions what you need to do to install firmware. Jaunty uses Linux-2.6.28 kernel, so the 4.150.10.5 is the correct version of firmware for your case.

Anyhow, I'm heading out of town for 3 days for midsummer celebrations and won't be having internet access, so can't be instantly there to help you out, if some trouble arises. Broadcom chips are fairly commont though, so there are a lot of people familiar with them on the forum, so you should be able to find someone else to assist, if there's further trouble. Or if not, I'll check back on your progress on monday.

---

### Post by matashi on 2009-06-19
Just want to say thanks for this thread. It got my wireless connection up and running!

---

### Post by ryy705 on 2009-06-19
I am glad that you got everything working.
Would you mind sharing with me what you did?
**lsmod | grep ndiswrapper** did not return anything so I went ahead and did **sudo rm /etc/modprobe.d/ndiswrapper**

Then I went to **system>hardware drivers>** and saw that b43 driver is active and sta driver is inactive.  

However, I my laptop still can't find wireless connection.
What can I do next?:(

---

### Post by ryy705 on 2009-06-21
*bump*

---

### Post by t0mppa on 2009-06-21
> **ryy705 said:**
> I am glad that you got everything working.
Would you mind sharing with me what you did?
**lsmod | grep ndiswrapper** did not return anything so I went ahead and did **sudo rm /etc/modprobe.d/ndiswrapper**

Then I went to **system>hardware drivers>** and saw that b43 driver is active and sta driver is inactive.  

However, I my laptop still can't find wireless connection.
What can I do next?:(

Ok, back in town. Merely enabling the b43 in the hardware drivers will not get it up and running, since it also needs the firmware (piece of code that's uploaded to the card to tell it what to do) on top of the driver software.

And like I quoted your dmesg in the earlier post, the version of firmware you currently have is too new and you need to install an older version for it to work with your wireless card. Those lines even show what you should do to fix the problem, so did you visit the page and follow the instructions?

---

### Post by ryy705 on 2009-06-28
Sorry about the delayed response.  I was trying get settled in a new office.

I went with the wrapper solution.  My laptop has Vista installed on another partition and every time I turn on Vista it will upgrade the firmware.

So, I think the wrapper solution is the best solution for me.

Many thanks for your help.

Now I'll have get Mysql to work.  That got messed up after the upgrade as well.  But I guess that will have be another thread.

---

### Post by t0mppa on 2009-06-29
No problem, main point is that you got it working.

---

