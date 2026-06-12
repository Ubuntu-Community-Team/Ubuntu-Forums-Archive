---
title: "3G Connection (Novatel Merlin U530 PCMCIA card)"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by Dumpy Dumpster on 2011-08-03
I have been trying for a couple of months to get a 3g connection with a Novatel Merlin U530 PCMCIA card. 
The laptop is a Dell L400/P3/700MHz/256MB with Lubuntu 10.04 as the OS and works well with both ethernet and PCMCIA wireless card for the internet connections.   
From research, I gather that the driver (HSO) is already is already in the kernel, but the laptop cannot 'see' the modem although it recognizes that a PCMCIA card is inserted/removed from 'syslog'.  In other words, the modem is not assigned a 'tty' port or even appear when 'dmesg' is run.
I have checked that the HSO module is present and that Administer the system, Connect to the Internet using a modem and Use modems are checked under User Privileges.  The driver from the Novatel website (novatel_modem_drivers_config_1.1_6.deb) has also been installed and I have also downloaded  and installed 'ozerocdoff' from peck.org/ozerocdoff.html. 
As Lubuntu is a slimmed down version of Ubuntu, could the problem lie with some missing programme?
Run out of ideas and other things to try - so need help!

---

### Post by alexfish on 2011-08-06
not sure about PCMCIA cards

can try these commands

see if device is listing in the dev/*
post results
```
ls -al /dev/serial/by-id
```
or
```
ls -al /dev/ttyHS*
```
if reply is "does not exist"
```
sudo modprobe hso
```

then repeat
```
ls -al /dev/serial/by-id
```
```
ls -al /dev/ttyHS*
```
if reply still  "does not exist"

need to see if a file new_id exists
post results of
```
ls -R /sys/module/hso/drivers/usb:hso
```

need to find device on system + the device id's for entering in the new_id
post results of
```
lspci -nn
```


also have you checked this site
[http://www.pharscape.org/](http://www.pharscape.org/)

alexfish

---

### Post by Dumpy Dumpster on 2011-08-07
Thank you, alexfish, for your reply.  So here goes....

[HTML]michael@michael-laptop:~$ ls -al /dev/serial/by-id
ls: cannot access /dev/serial/by-id: No such file or directory
michael@michael-laptop:~$ ls -al /dev/ttyHS*
ls: cannot access /dev/ttyHS*: No such file or directory
michael@michael-laptop:~$ sudo modprobe hso
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
michael@michael-laptop:~$ ls -al /dev/serial/by-id
ls: cannot access /dev/serial/by-id: No such file or directory
michael@michael-laptop:~$ ls -al /dev/ttyHS*
ls: cannot access /dev/ttyHS*: No such file or directory
michael@michael-laptop:~$ ls -R /sys/module/hso/drivers/usb:hso
/sys/module/hso/drivers/usb:hso:
bind  module  new_id  uevent  unbind
michael@michael-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 Multimedia audio controller [0401]: Cirrus Logic Crystal CS4281 PCI Audio [1013:6005] (rev 01)
00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
00:0d.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
00:10.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0448] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility P/M AGP 2x [1002:4c4d] (rev 64)
michael@michael-laptop:~$ 
[/HTML]

I had already found Pharscape's excellent site. Following Pharscape's page on the use of Network Manager, I tested for the installation of the H2O and it seems to be present...

[HTMLmichael@michael-laptop:~$ find /lib/modules/`uname -r` -name 'hso.ko'
/lib/modules/2.6.32-32-generic/kernel/drivers/net/usb/hso.ko
/lib/modules/2.6.32-32-generic/updates/dkms/hso.ko][/HTML]

I have also downloaded 'ozerocdoff' from [http://peck.org/ozerocdoff.html]("http://peck.org/ozerocdoff.html")
I think I installed it correctly but it makes no difference.  
But when I came to checking if the ports had been created...

[HTML]michael@michael-laptop:~$ ls dev/ttyHS*
ls: cannot access dev/ttyHS*: No such file or directory
[/HTML]

So it seems that the laptop cannot 'see' the modem.

I notice that there is now a mention above of the winmodem that is built into the laptop.  It would be possible to disconnect the power supply to it if you think it would perhaps resolve a conflict.

Thanks again for your time.

---

### Post by alexfish on 2011-08-07
hi

may need to use alternate command to see if the card details can be found

the standard command used to be "cardctl " on my ubuntu 11.04 the only command I can find is "pccardctl"

can suggest trying man pages for both commands . need to find the Vendor and Product numbers for the device.

as mentioned in previous posts. the udev seems to be hot plugging "noted from comment "in the syslog". so can assume the cardctl or pccardctl is activating the udev , but not insmod or modprobing the device. can post details of the log: 

from the novatel info , looks like the most probable driver = OPTION 

but this can be resolved later.

Added: ozerocdoff may not contain your card ids: but will only be required if it has windows drivers built in : if it has then usb_modeswitch would be the best option: but lets find the device and the ID's first

regards

alexfish

---

### Post by Dumpy Dumpster on 2011-08-07
Good Afternoon, alexfish,

I installed 'pcmciautils' after a prompt from the 'pccardctl' command, and here are some of the results...

[HTML]michael@michael-laptop:~$ pccardctl
pcmciautils 014
Copyright (C) 2004-2005 Dominik Brodowski, (C) 1999 David A. Hinds
Report errors and bugs to <linux-pcmcia@lists.infradead.org>, please.
invalid or unknown argument
Usage: pccardctl COMMAND
Supported commands are:
	ls
	insert
	eject
	suspend
	resume
	reset
	info
	status
	config
	ident
michael@michael-laptop:~$ pccardctl ident
Socket 0:
  product info: "Novatel Wireless", "Merlin UMTS Modem", "NRM6831", ""
  manfid: 0x00a4, 0x1aaf
  function: 2 (serial)
michael@michael-laptop:~$ pccardctl info
PRODID_1="Novatel Wireless"
PRODID_2="Merlin UMTS Modem"
PRODID_3="NRM6831"
PRODID_4=""
MANFID=00a4,1aaf
FUNCID=2
michael@michael-laptop:~$ pccardctl status
Socket 0:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "serial_cs"
  Subdevice 1 (function 1) [unbound]
michael@michael-laptop:~$ pccardctl config
Socket 0:
command 'config' not yet handled by pccardctl
[/HTML]

The driver I installed from Novatel website [http://www.novatelwireless.com/index.php?option=com_content&view=article&id=82&Itemid=164]("http://www.novatelwireless.com/index.php?option=com_content&view=article&id=82&Itemid=164") was Debian Modem Driver Config_1.1_6

I think you wanted the syslog output again...


[HTML]michael@michael-laptop:~$ tail -f /var/log/syslog
Aug  7 12:50:52 michael-laptop ntpd[927]: frequency initialized 36.316 PPM from /var/lib/ntp/ntp.drift
Aug  7 12:50:53 michael-laptop init: plymouth-stop pre-start process (946) terminated with status 1
Aug  7 12:50:57 michael-laptop kernel: [   30.872071] eth1: no IPv6 routers present
Aug  7 12:50:59 michael-laptop polkitd[1083]: started daemon version 0.96 using authority implementation `local' version `0.96'
Aug  7 12:51:01 michael-laptop anacron[1127]: Anacron 2.3 started on 2011-08-07
Aug  7 12:51:01 michael-laptop anacron[1127]: Normal exit (0 jobs run)
Aug  7 12:55:13 michael-laptop ntpd[927]: synchronized to 91.189.94.4, stratum 2
Aug  7 12:55:13 michael-laptop ntpd[927]: time reset -0.271232 s
Aug  7 12:55:13 michael-laptop ntpd[927]: kernel time sync status change 2001
Aug  7 13:01:58 michael-laptop ntpd[927]: synchronized to 91.189.94.4, stratum 2
[/HTML]

You might need also the results from 'dmesg'...


[HTML]michael@michael-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-33-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #71-Ubuntu SMP Wed Jul 20 17:30:40 UTC 2011 (Ubuntu 2.6.32-33.71-generic 2.6.32.41+drm33.18)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ea000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffea000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ea000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  modified: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  modified: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  modified: 00000000fffea000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000000fff0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 000fc00000 page 2M
[    0.000000]  000fc00000 - 000fff0000 page 4k
[    0.000000] kernel direct mapping tables up to fff0000 @ 7000-c000
[    0.000000] RAMDISK: 0b35c000 - 0c03323e
[    0.000000] ACPI: RSDP 000f6f60 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 0fffc4c4 0002C (v01 DELL   ATLAS II 20010709  LTP 00000000)
[    0.000000] ACPI: FACP 0ffffb65 00074 (v01 DELL   Atlas II 20010709 PTL  000F4240)
[    0.000000] ACPI: DSDT 0fffc4f0 03675 (v01    PTL    BX-TJ 20010709 MSFT 01000007)
[    0.000000] ACPI: FACS 0fffffc0 00040
[    0.000000] ACPI: BOOT 0ffffbd9 00027 (v01 PTLTD  $SBFTBL$ 20010709  LTP 00000001)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 0 - 0fff0000
[    0.000000]   node 0 low ram: 00000000 - 0fff0000
[    0.000000]   node 0 bootmap 00008000 - 0000a000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e0ef8]    TEXT DATA BSS ==> [0000100000 - 00008e0ef8]
[    0.000000]   #4 [000b35c000 - 000c03323e]          RAMDISK ==> [000b35c000 - 000c03323e]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008e1000 - 00008e4280]              BRK ==> [00008e1000 - 00008e4280]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000a000]          BOOTMAP ==> [0000008000 - 000000a000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65419
[    0.000000] free_area_init_node: node 0, pgdat c079a7c0, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60944 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ea000
[    0.000000] PM: Registered nosave memory: 00000000000ea000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 10000000:effea000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36312 r0 d21032 u4194304
[    0.000000] pcpu-alloc: s36312 r0 d21032 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64907
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=5bbaaf21-6e06-43f1-8458-b792d588d33b ro quiet splash
[    0.000000] PID hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1310400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 236472k/262080k available (4675k kernel code, 24868k reserved, 2127k data, 668k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd07f0000 - 0xff7fe000   ( 752 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084c000   ( 668 kB)
[    0.000000]       .data : 0xc0590dc7 - 0xc07a4d88   (2127 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590dc7   (4675 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 497.878 MHz processor.
[    0.008014] Calibrating delay loop (skipped), value calculated using timer frequency.. 995.75 BogoMIPS (lpj=1991512)
[    0.008091] Security Framework initialized
[    0.008196] AppArmor: AppArmor initialized
[    0.008232] Mount-cache hash table entries: 512
[    0.008728] Initializing cgroup subsys ns
[    0.008746] Initializing cgroup subsys cpuacct
[    0.008767] Initializing cgroup subsys memory
[    0.008807] Initializing cgroup subsys devices
[    0.008821] Initializing cgroup subsys freezer
[    0.008833] Initializing cgroup subsys net_cls
[    0.008921] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.008937] CPU: L2 cache: 256K
[    0.008958] mce: CPU supports 5 MCE banks
[    0.009011] Performance Events: 
[    0.009023] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.009036] no hardware sampling interrupt available.
[    0.009047] p6 PMU driver.
[    0.009134] ... version:                0
[    0.009144] ... bit width:              32
[    0.009155] ... generic registers:      2
[    0.009166] ... value mask:             00000000ffffffff
[    0.009178] ... max period:             000000007fffffff
[    0.009189] ... fixed-purpose events:   0
[    0.009200] ... event mask:             0000000000000003
[    0.009218] Checking 'hlt' instruction... OK.
[    0.026105] SMP alternatives: switching to UP code
[    0.049626] Freeing SMP alternatives: 19k freed
[    0.049701] ACPI: Core revision 20090903
[    0.063948] ACPI: setting ELCR to 0200 (from 0c08)
[    0.064029] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.064065] ftrace: allocating 21725 entries in 43 pages
[    0.068369] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.068390] weird, boot CPU (#0) not listed by the BIOS.
[    0.068401] SMP motherboard not detected.
[    0.068412] Local APIC not detected. Using dummy APIC emulation.
[    0.068423] SMP disabled
[    0.069324] Brought up 1 CPUs
[    0.069343] Total of 1 processors activated (995.75 BogoMIPS).
[    0.069416] CPU0 attaching NULL sched-domain.
[    0.072129] devtmpfs: initialized
[    0.074027] regulator: core version 0.5
[    0.074084] Time: 10:50:26  Date: 08/07/11
[    0.074329] NET: Registered protocol family 16
[    0.074883] EISA bus registered
[    0.074934] ACPI: bus type pci registered
[    0.078029] PCI: PCI BIOS revision 2.10 entry at 0xfd9c5, last bus=1
[    0.078041] PCI: Using configuration type 1 for base access
[    0.082941] bio: create slab <bio-0> at 0
[    0.085211] ACPI: EC: Look up EC in DSDT
[    0.112720] ACPI: Interpreter enabled
[    0.112744] ACPI: (supports S0 S3 S4 S5)
[    0.112827] ACPI: Using PIC for interrupt routing
[    0.272490] ACPI: EC: GPE = 0x0, I/O: command/status = 0x66, data = 0x62
[    0.272733] ACPI: Power Resource [PFN0] (off)
[    0.272733] ACPI: Power Resource [PFN1] (off)
[    0.272772] ACPI: No dock devices found.
[    0.276220] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.276388] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xf8000000-0xfbffffff]
[    0.276660] pci 0000:00:07.1: reg 20 io port: [0xfcd0-0xfcdf]
[    0.276760] pci 0000:00:07.2: reg 20 io port: [0xfce0-0xfcff]
[    0.276881] pci 0000:00:07.3: quirk: region 8000-803f claimed by PIIX4 ACPI
[    0.276899] pci 0000:00:07.3: quirk: region 2180-218f claimed by PIIX4 SMB
[    0.276920] pci 0000:00:07.3: PIIX4 devres I PIO at 0398-0399
[    0.277007] pci 0000:00:08.0: reg 10 32bit mmio: [0xfedef000-0xfedeffff]
[    0.277028] pci 0000:00:08.0: reg 14 32bit mmio: [0xfedf0000-0xfedfffff]
[    0.277094] pci 0000:00:08.0: supports D1 D2
[    0.277107] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot
[    0.277122] pci 0000:00:08.0: PME# disabled
[    0.277189] pci 0000:00:0a.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.277227] pci 0000:00:0a.0: supports D1 D2
[    0.277239] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.277254] pci 0000:00:0a.0: PME# disabled
[    0.277321] pci 0000:00:0d.0: reg 10 io port: [0xfc00-0xfc7f]
[    0.277342] pci 0000:00:0d.0: reg 14 32bit mmio: [0xfededc00-0xfededc7f]
[    0.277385] pci 0000:00:0d.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.277421] pci 0000:00:0d.0: supports D1 D2
[    0.277433] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.277448] pci 0000:00:0d.0: PME# disabled
[    0.277516] pci 0000:00:10.0: reg 10 32bit mmio: [0xfeded800-0xfeded8ff]
[    0.277537] pci 0000:00:10.0: reg 14 io port: [0xfcc8-0xfccf]
[    0.277557] pci 0000:00:10.0: reg 18 io port: [0xf800-0xf8ff]
[    0.277615] pci 0000:00:10.0: supports D2
[    0.277627] pci 0000:00:10.0: PME# supported from D2 D3hot D3cold
[    0.277642] pci 0000:00:10.0: PME# disabled
[    0.277756] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.277778] pci 0000:01:00.0: reg 14 io port: [0xe800-0xe8ff]
[    0.277798] pci 0000:01:00.0: reg 18 32bit mmio: [0xfecfe000-0xfecfefff]
[    0.277835] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.277879] pci 0000:01:00.0: supports D1 D2
[    0.277954] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.277970] pci 0000:00:01.0: bridge 32bit mmio: [0xfd000000-0xfecfffff]
[    0.278024] pci_bus 0000:00: on NUMA node 0
[    0.278045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.278236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.283517] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    0.283977] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    0.284464] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 14 15)
[    0.284898] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    0.285387] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.285403] vgaarb: loaded
[    0.285978] SCSI subsystem initialized
[    0.286284] libata version 3.00 loaded.
[    0.286644] usbcore: registered new interface driver usbfs
[    0.286711] usbcore: registered new interface driver hub
[    0.286860] usbcore: registered new device driver usb
[    0.287519] ACPI: WMI: Mapper loaded
[    0.287529] PCI: Using ACPI for IRQ routing
[    0.288074] NetLabel: Initializing
[    0.288085] NetLabel:  domain hash size = 128
[    0.288094] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.288152] NetLabel:  unlabeled traffic allowed by default
[    0.288338] Switching to clocksource tsc
[    0.297060] AppArmor: AppArmor Filesystem Enabled
[    0.297146] pnp: PnP ACPI init
[    0.297219] ACPI: bus type pnp registered
[    0.381607] pnp: PnP ACPI: found 12 devices
[    0.381621] ACPI: ACPI bus type pnp unregistered
[    0.381639] PnPBIOS: Disabled by ACPI PNP
[    0.381699] system 00:05: iomem range 0x0-0x9fbff could not be reserved
[    0.381718] system 00:05: iomem range 0xe8000-0xfffff could not be reserved
[    0.381735] system 00:05: iomem range 0xdc000-0xdffff has been reserved
[    0.381751] system 00:05: iomem range 0x100000-0xffffff could not be reserved
[    0.381769] system 00:05: iomem range 0xfff80000-0xfffdffff has been reserved
[    0.381803] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.381820] system 00:06: ioport range 0x8000-0x803f has been reserved
[    0.381836] system 00:06: ioport range 0x2180-0x218f has been reserved
[    0.381852] system 00:06: ioport range 0x398-0x399 has been reserved
[    0.417339] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.417356] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.417373] pci 0000:00:01.0:   MEM window: 0xfd000000-0xfecfffff
[    0.417389] pci 0000:00:01.0:   PREFETCH window: 0x18000000-0x180fffff
[    0.417410] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.417423] pci 0000:00:0a.0:   IO window: 0x001000-0x0010ff
[    0.417438] pci 0000:00:0a.0:   IO window: 0x001400-0x0014ff
[    0.417454] pci 0000:00:0a.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.417471] pci 0000:00:0a.0:   MEM window: 0x14000000-0x17ffffff
[    0.418272] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    0.418287] PCI: setting IRQ 10 as level-triggered
[    0.418305] pci 0000:00:0a.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    0.418330] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.418344] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.418358] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.418372] pci_bus 0000:01: resource 1 mem: [0xfd000000-0xfecfffff]
[    0.418387] pci_bus 0000:01: resource 2 pref mem [0x18000000-0x180fffff]
[    0.418402] pci_bus 0000:02: resource 0 io:  [0x1000-0x10ff]
[    0.418415] pci_bus 0000:02: resource 1 io:  [0x1400-0x14ff]
[    0.418429] pci_bus 0000:02: resource 2 pref mem [0x10000000-0x13ffffff]
[    0.418444] pci_bus 0000:02: resource 3 mem: [0x14000000-0x17ffffff]
[    0.418611] NET: Registered protocol family 2
[    0.419090] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.420633] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.420848] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.421047] TCP: Hash tables configured (established 8192 bind 8192)
[    0.421059] TCP reno registered
[    0.421412] NET: Registered protocol family 1
[    0.421488] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.421577] pci 0000:01:00.0: Boot video device
[    0.421881] Simple Boot Flag at 0x63 set to 0x1
[    0.422195] cpufreq-nforce2: No nForce2 chipset.
[    0.422304] Scanning for low memory corruption every 60 seconds
[    0.422951] audit: initializing netlink socket (disabled)
[    0.422998] type=2000 audit(1312714226.419:1): initialized
[    0.466231] Trying to unpack rootfs image as initramfs...
[    0.513190] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.532154] VFS: Disk quotas dquot_6.5.2
[    0.532582] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.536177] fuse init (API version 7.13)
[    0.536655] msgmni has been set to 462
[    0.545091] alg: No test for stdrng (krng)
[    0.545354] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.545371] io scheduler noop registered
[    0.545381] io scheduler anticipatory registered
[    0.545392] io scheduler deadline registered
[    0.545644] io scheduler cfq registered (default)
[    0.546074] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.546207] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.548463] ACPI: AC Adapter [ACAD] (on-line)
[    0.548870] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.551643] ACPI: Lid Switch [LID]
[    0.551866] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.551883] ACPI: Sleep Button [SBTN]
[    0.552113] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.552129] ACPI: Power Button [PWRF]
[    0.558799] fan PNP0C0B:00: registered as cooling_device0
[    0.558840] ACPI: Fan [FAN0] (off)
[    0.559137] fan PNP0C0B:01: registered as cooling_device1
[    0.559168] ACPI: Fan [FAN1] (off)
[    0.559792] Marking TSC unstable due to TSC halts in idle
[    0.560117] processor LNXCPU:00: registered as cooling_device2
[    0.568580] Switching to clocksource acpi_pm
[    0.645068] thermal LNXTHERM:01: registered as thermal_zone0
[    0.645118] ACPI: Thermal Zone [THRM] (50 C)
[    0.660195] isapnp: Scanning for PnP cards...
[    0.668146] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.668367] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.669712] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.677275] ACPI: Battery Slot [BAT1] (battery absent)
[    0.727590] brd: module loaded
[    0.736170] loop: module loaded
[    0.736651] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.737129] ata_piix 0000:00:07.1: version 2.13
[    0.737221] ata_piix 0000:00:07.1: power state changed by ACPI to D0
[    0.737254] ata_piix 0000:00:07.1: power state changed by ACPI to D0
[    0.737761] scsi0 : ata_piix
[    0.740233] scsi1 : ata_piix
[    0.743202] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xfcd0 irq 14
[    0.743219] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xfcd8 irq 15
[    0.745375] Fixed MDIO Bus: probed
[    0.745558] PPP generic driver version 2.4.2
[    0.745847] tun: Universal TUN/TAP device driver, 1.6
[    0.745859] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.746288] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.746388] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.746455] uhci_hcd: USB Universal Host Controller Interface driver
[    0.747364] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.747379] PCI: setting IRQ 11 as level-triggered
[    0.747397] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.747430] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    0.747645] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    0.747713] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000fce0
[    0.753873] usb usb1: configuration #1 chosen from 1 choice
[    0.754037] hub 1-0:1.0: USB hub found
[    0.754100] hub 1-0:1.0: 2 ports detected
[    0.754549] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    0.760683] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.760732] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.761455] mice: PS/2 mouse device common for all mice
[    0.764491] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.764545] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.765137] device-mapper: uevent: version 1.0.3
[    0.769701] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.770092] device-mapper: multipath: version 1.1.0 loaded
[    0.770106] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.770797] EISA: Probing bus 0 at eisa.0
[    0.770819] Cannot allocate resource for EISA slot 1
[    0.770859] Cannot allocate resource for EISA slot 8
[    0.770870] EISA: Detected 0 cards.
[    0.773439] cpuidle: using governor ladder
[    0.773658] cpuidle: using governor menu
[    0.776117] TCP cubic registered
[    0.777003] NET: Registered protocol family 10
[    0.786475] NET: Registered protocol family 17
[    0.786728] Using IPI No-Shortcut mode
[    0.787176] PM: Resume from disk failed.
[    0.787247] registered taskstats version 1
[    0.787805]   Magic number: 7:384:830
[    0.788007] rtc_cmos 00:02: setting system clock to 2011-08-07 10:50:27 UTC (1312714227)
[    0.788098] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.788109] EDD information not available.
[    0.799956] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.941703] ata1.00: ATA-5: IC25N020ATCS04-0, CA2OA72A, max UDMA/100
[    0.941722] ata1.00: 39070080 sectors, multi 16: LBA 
[    0.959777] ata1.00: configured for UDMA/33
[    1.108375] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    1.372287] isapnp: No Plug & Play device found
[    1.372916] scsi 0:0:0:0: Direct-Access     ATA      IC25N020ATCS04-0 CA2O PQ: 0 ANSI: 5
[    1.373582] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.374001] sd 0:0:0:0: [sda] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.374265] sd 0:0:0:0: [sda] Write Protect is off
[    1.374281] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.374419] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.375125]  sda:
[    1.393459] usb 1-1: configuration #1 chosen from 1 choice
[    1.395640]  sda1 sda2 <
[    1.396280] hub 1-0:1.0: over-current change on port 2
[    1.426354]  sda5 >
[    1.427909] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.560594] Freeing initrd memory: 13148k freed
[    2.635290] Freeing unused kernel memory: 668k freed
[    2.639499] Write protecting the kernel text: 4676k
[    2.639679] Write protecting the kernel read-only data: 1848k
[    2.736443] udev: starting version 151
[    3.639987] Linux agpgart interface v0.103
[    3.693672] Floppy drive(s): fd0 is 1.44M
[    3.731853] FDC 0 is a National Semiconductor PC87306
[    3.732320] vga16fb: initializing
[    3.732349] vga16fb: mapped to 0xc00a0000
[    3.735760] fb0: VGA16 VGA frame buffer device
[    3.780237] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[    3.787688] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    3.819126] 3c59x 0000:00:0d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    3.819170] 3c59x: Donald Becker and others.
[    3.819196] 0000:00:0d.0: 3Com PCI 3c905C Tornado at d0810c00.
[    3.862065] usbcore: registered new interface driver hiddev
[    3.882121] input: HID compliant-mouse HID compliant-mouse as /devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0/input/input5
[    3.883151] generic-usb 0003:1D57:2400.0001: input,hidraw0: USB HID v1.10 Mouse [HID compliant-mouse HID compliant-mouse] on usb-0000:00:07.2-1/input0
[    3.883320] usbcore: registered new interface driver usbhid
[    3.883853] usbhid: v2.6:USB HID core driver
[    4.031068] Console: switching to colour frame buffer device 80x30
[    4.960922] xor: automatically using best checksumming function: pIII_sse
[    4.980041]    pIII_sse  :  1009.000 MB/sec
[    4.980053] xor: using function: pIII_sse (1009.000 MB/sec)
[    5.037554] device-mapper: dm-raid45: initialized v0.2594b
[    5.434371] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    8.863056] Adding 732152k swap on /dev/sda5.  Priority:-1 extents:1 across:732152k 
[   10.409715] udev: starting version 151
[   11.280481] udev: renamed network interface eth0 to eth1
[   12.976252] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.087222] piix4_smbus 0000:00:07.3: SMBus Host Controller at 0x2180, revision 0
[   13.183463] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.255974] lp: driver loaded but no devices found
[   13.315885] parport_pc 00:07: reported by Plug and Play ACPI
[   13.315977] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   13.376597] dell-wmi: No known WMI GUID found
[   13.420146] lp0: using parport0 (interrupt-driven).
[   13.514274] ppdev: user-space parallel port driver
[   13.833127] yenta_cardbus 0000:00:0a.0: CardBus bridge found [1028:00dc]
[   13.833170] yenta_cardbus 0000:00:0a.0: Enabling burst memory read transactions
[   13.833188] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
[   13.833201] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
[   13.833219] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01201272, devctl 0x64
[   14.064428] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 10
[   14.064446] yenta_cardbus 0000:00:0a.0: Socket status: 30000010
[   14.191993] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x8848a1, caps: 0x0/0x0/0x0
[   14.229525] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   14.337070] type=1505 audit(1312714241.048:2):  operation="profile_load" pid=447 name="/sbin/dhclient3"
[   14.339351] type=1505 audit(1312714241.048:3):  operation="profile_load" pid=447 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.342118] type=1505 audit(1312714241.052:4):  operation="profile_replace" pid=448 name="/sbin/dhclient3"
[   14.346532] type=1505 audit(1312714241.056:5):  operation="profile_replace" pid=448 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.347879] type=1505 audit(1312714241.056:6):  operation="profile_load" pid=448 name="/usr/lib/connman/scripts/dhclient-script"
[   14.350321] type=1505 audit(1312714241.060:7):  operation="profile_replace" pid=447 name="/usr/lib/connman/scripts/dhclient-script"
[   14.636797] type=1505 audit(1312714241.348:8):  operation="profile_load" pid=553 name="/usr/sbin/ntpd"
[   14.640013] type=1505 audit(1312714241.348:9):  operation="profile_replace" pid=554 name="/usr/sbin/ntpd"
[   17.144126] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   17.701001] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   17.702033] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   17.702576] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.703067] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.705715] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   17.706289] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   17.721131] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   17.723098] pcmcia 0.1: pcmcia: registering new device pcmcia0.1
[   17.810264] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   17.810288] CS4281 0000:00:08.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   17.966009] type=1505 audit(1312714244.676:10):  operation="profile_replace" pid=648 name="/sbin/dhclient3"
[   17.969280] type=1505 audit(1312714244.680:11):  operation="profile_replace" pid=648 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.347958] 0.0: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.566743] gameport: CS4281 Gameport is pci0000:00:08.0/gameport0, speed 2294kHz
[   20.489488] eth1:  setting full-duplex.
[   30.872071] eth1: no IPv6 routers present
[/HTML]

By and large, it is all double-dutch to me!   Hope you can glean something out of all this!

---

### Post by alexfish on 2011-08-07
look like the device ID's are
> 0x00a4:0x1aaffrom the initial driver
> Subdevice 0 (function 0) bound to driver "serial_cs"looking up
[http://pcmcia-cs.sourceforge.net/man/serial_cs.4.html](http://pcmcia-cs.sourceforge.net/man/serial_cs.4.html)
need to find if this serial driver is binding as dev/modem and if ttyS* is listing
although not sure if this be the correct driver to communicate with this device ,
can try these commands
```
ls -al /dev/ttyS*
``````
ls -al /dev/cua*
``````
ls -al /dev/modem
```will then look further

Note:
have look through the info about the drivers , mainly udev rules (which will eject the cd part of a device: yours is not listed : and hal info (again no id  ). also has a script file to init the process for device product id 0x1410 , (so will not work)

Added
also need to check if  registering as usb device

can post results of

```
lsusb
```

regards
alexfish

---

### Post by Dumpy Dumpster on 2011-08-07
!

---

### Post by Dumpy Dumpster on 2011-08-07
Here we go again...


[HTML]michael@michael-laptop:~$ ls -al /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2011-08-07 15:25 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2011-08-07 15:25 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2011-08-07 15:20 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2011-08-07 15:20 /dev/ttyS3
michael@michael-laptop:~$ ls -al /dev/cua*
ls: cannot access /dev/cua*: No such file or directory
michael@michael-laptop:~$ ls -al /dev/modem
ls: cannot access /dev/modem: No such file or directory
[/HTML]

and...

[HTML]michael@michael-laptop:~$ lsusb
Bus 001 Device 002: ID 1d57:2400  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/HTML]

I have noticed that quite a few devices do not work with Network Manager - they require wvdial.  So I have installed it.

Here are some outputs that may be of use...

[HTML]michael@michael-laptop:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- OK
ttyS1<*1>: ATQ0 V1 E1 Z -- OK
ttyS1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- ERROR
ttyS1<*1>: Modem Identifier: ATI -- Manufacturer: Novatel Wireless Incorporated
ttyS1<*1>: Speed 4800: AT -- OK
ttyS1<*1>: Speed 9600: AT -- OK
ttyS1<*1>: Speed 19200: AT -- OK
ttyS1<*1>: Speed 38400: AT -- OK
ttyS1<*1>: Speed 57600: AT -- OK
ttyS1<*1>: Speed 115200: AT -- OK
ttyS1<*1>: Max speed is 115200; that should be safe.
ttyS1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
Modem Port Scan<*1>: S3   

Found a modem on /dev/ttyS1.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp1341': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyS1<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2"
[/HTML]

I note the magic words 'Found a modem on ..' so we must be progressing?
I am not surprised you did not find all the information about the modem on the Novatel site - like me, my laptop and our cat, we are all rather old!

---

### Post by alexfish on 2011-08-08
Almost there
Looks as if wvdial will communicate with the device but is halting at ttyS1

 the device has a total of  4 ports (need to check if can communicate AT commands on each port , so worth trying to find what the specs are for the device and what each port can do).

the driver is looking good for speeds up-to 115200 (this is the normal setting for 3g connection) but will have to monitor this when the actual connection is made (need to monitor any errors when in use).

will need info to configure the device, if device definitely 3g then require the APN , user name and password if required

sometimes  possible to get this info by probing the modem using AT commands

can try this by using 2 terminals , going to try port ttyS1 . open up first terminal and enter this command
```
tr -s "\n" < /dev/ttyS1
``` this will monitor the outputs from terminal 2
open up second terminal and enter the following codes
see if the modem responds to AT command
```
echo -e "AT\r" > /dev/ttyS1
``` if responce is OK then assume the modem is responding
to show the APN's
```
echo -e "AT+CGDCONT?\r" > /dev/ttyS1 
```
Find ISP or Operator
```
echo -e "AT+COPS?\r" > /dev/ttyS1
```
to find the mmc and mnc numbers
set the code to access this part of the device
```
echo -e "AT+COPS=0,2\r" > /dev/ttyS1
```
to retrieve the mmc and mnc numbers
```
echo -e "AT+COPS?\r" > /dev/ttyS1
``` , from this it may be possible to find the APN,user name and password from the service providers data base.
copy and paste this into the browser
```
file:///usr/share/mobile-broadband-provider-info/serviceproviders.xml
```
here is an example of my modem reponse
> +COPS: 0,2,"23430",2
the mcc and mnc number is taken from "23430" and splits into
mcc =234 (first 3 digits)
mnc =30 (remainder)
if got the correct response the look up the data in the sevice providers data base

see what happens. will then look at configuring wvdial. 

if fail to retrieve the info will have to look further by using different ttyS* as listed by the "ls -al /dev/ttyS*" command. also check for AT command response on every port , as said the modem may have several functions.

Note if info can't be found then will have to get the info from your service provder

regards
alexfish

---

### Post by Dumpy Dumpster on 2011-08-08
Here is first command after the second was put in a seperate terminal.....

[HTML]michael@michael-laptop:~$ tr -s "\n" < /dev/ttyS1
AT
OK
AT
OK[/HTML]
  
There were lots more 'AT's and 'OK's.

The other commands produced nothing.

[HTML]michael@michael-laptop:~$ echo -e "AT+CGDCONT?\r" > /dev/ttyS1
michael@michael-laptop:~$ echo -e "AT+COPS?\r" > /dev/ttyS1
michael@michael-laptop:~$ echo -e "AT+COPS=0,2\r" > /dev/ttyS1
michael@michael-laptop:~$ echo -e "AT+COPS?\r" > /dev/ttyS1
michael@michael-laptop:~$ file:///usr/share/mobile-broadband-provider-info/serviceproviders.xml
[/HTML]

I have altered and saved the /etc/wvdial.conf to reflect the APN,user and password that I have found on the website you mentioned.   

[Dialer Defaults]
Phone = general.t-mobile.uk
Username = user
Password = mms 
New PPPD = yes

But the light on the modem remains stubbornly red and nothing else happens.   Does wvdial start automatically?

---

### Post by alexfish on 2011-08-08
the details of my provider where put as an example of how to find apn etc if the modem had responder to the AT commands, your providers apn may be different,

going to try default dialing commands for wvdial

from the terminal
```
sudo gedit /etc/wvdial.conf
```edit the file to look like
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS1
ISDN = 0
Phone = *99#
Password = *
Username = *
```save the file and exit

then from the terminal call wvdial
```
sudo wvdial
```note if wvdial not connecting on ttyS1 then try each of the ports listed ttyS0 , ttyS2 , ttyS3

see what happens

---

### Post by Dumpy Dumpster on 2011-08-08
I have found this site: [http://linux.die.net/man/5/wvdial.conf]("http://linux.die.net/man/5/wvdial.conf")
and my wvdial.conf file does not look theirs - I seem to be missing a large chunk - especially the first part:

[Dialer Defaults]
Modem = /dev/ttyS2
Baud = 57600
Init = ATZ
Init2 = AT S11=50
Phone = 555-4242
Username = apenwarr
Password = my-password
[Dialer phone2]
Phone = 555-4243

[Dialer shh]
Init3 = ATM0

[Dialer pulse]
Dial Command = ATDP

Thanks alexfish - our replies literally crossed - will action yours...

---

### Post by Dumpy Dumpster on 2011-08-08
wvdial changed as requested.  Here is output from sudo wvdial:


[HTML]michael@michael-laptop:~$ sudo wvdial
[sudo] password for michael: 
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.
michael@michael:~$ 
[/HTML]

I assume that ttyS1 is not working - so here are outputs with the Modem = /dev/ttyS set to 0,2 and 3....

[HTML] michael@michael-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
michael@michael-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyS2: Input/output error
--> Cannot open /dev/ttyS2: Input/output error
--> Cannot open /dev/ttyS2: Input/output error
michael@michael-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyS3: Input/output error
--> Cannot open /dev/ttyS3: Input/output error
--> Cannot open /dev/ttyS3: Input/output error
michael@michael-laptop:~$ 
[/HTML]

Hope this helps. I also tried changing the Phone,Password and Username to those for T-Mobile.uk..... 


[HTML]michael@michael-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.
michael@michael-laptop:~$ 
[/HTML]

I have now changed wvdial.conf back to your original spec.

---

### Post by alexfish on 2011-08-09
Appols , did not check previous wv log the device will not accept FCLASS=0
can change the /etc/wvdial.conf to

```
[Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 
Modem Type = Analog Modem 
Baud = 115200 
New PPPD = yes 
Modem = /dev/ttyS1 
ISDN = 0 
Phone = *99# 
Password = * 
Username = *
```if met with failure try deleting the line at Init2
see what happens
alexfish

---

### Post by Dumpy Dumpster on 2011-08-09
Good Afternoon again, alexfish.
I amended wvdial.conf as you suggested and tried it with and without the Init2 line and nothing happened.
Rummaging around the internet, I came across [http://mybroadband.co.za/vb/showthread.php/21726-Linux-HOWTO-(With-Stats)]("http://mybroadband.co.za/vb/showthread.php/21726-Linux-HOWTO-(With-Stats)") 
It is for a different Novatel card but you may get something out of...
 
[HTML]michael@michael-laptop:~$ modprobe usbserial vendor=0x00a4 product=0x1aaf
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting usbserial (/lib/modules/2.6.32-33-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted
michael@michael-laptop:~$ find /dev/ | grep ttyS
/dev/ttyS1
/dev/.udev/db/tty:ttyS1
/dev/.udev/db/tty:ttyS0
/dev/.udev/db/tty:ttyS2
/dev/.udev/db/tty:ttyS3
/dev/ttyS0
/dev/ttyS3
/dev/ttyS2
michael@michael-laptop:~$ 
[/HTML]

also...

[HTML]michael@michael-laptop:~$ wvdial novatel intenet 3gonly 394k
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer novatel] does not exist in wvdial.conf.
--> Warning: section [Dialer intenet] does not exist in wvdial.conf.
--> Warning: section [Dialer 3gonly] does not exist in wvdial.conf.
--> Warning: section [Dialer 394k] does not exist in wvdial.conf.
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue Aug  9 14:51:04 2011
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 1245
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533; H&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; H&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; H&#65533;&#65533; 
[/HTML]

It went back and repeated some of the above steps again.
Does this indicate anything to you?

---

### Post by alexfish on 2011-08-09
hi need to run wvdial as root (default call is)
```
sudo wvdial
```see what happens

added double check with your service provider to see if user name and password required

regards
alexfish

---

### Post by Dumpy Dumpster on 2011-08-11
Here is the sudo wvdial you requested...

[HTML]michael@michael-laptop:~$ sudo wvdial
[sudo] password for michael: 
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Aug 10 16:34:35 2011
--> Pid of pppd: 1313
--> Using interface ppp0
--> pppd: `8&#65533; &#65533;>&#65533; 
--> pppd: `8&#65533; &#65533;>&#65533; 
--> pppd: `8&#65533; &#65533;>&#65533; 
--> pppd: `8&#65533; &#65533;>&#65533; [/HTML]


I found a previous explanation of how to set up mobile broadband, albeit with a different dongle:   [http://ubuntuforums.org/showthread/php?p=5601261]("http://ubuntuforums.org/showthread/php?p=5601261")

In post #5, there is an explantion for the use of GnomePPP, which is already installed.  So I gave it a try.  I cannot switch off wireless (item 5), but as wireless uses an PCMCIA card, I assumed it was already off.  It all went as predicted but failed to connect. I attach a screenshot of the log.  I was expecting to get DNS of 10.11.12.13.and 14 as per item 16 as I am in France and the SIM card is for a UK ISP.  That does not matter to me as I would like the system to be ready on my next UK visit where I will not have any other internet acess other than this mobile broadband - so I will be limited in my fiddling with it to set it up.  The modem light remains steady red, whereas I'd hoped to see flashing green indicating service is available but not connected.

I thought the interesting points from the attached log were:
	'Cannot set information for serial port', and
	'Bad init string'

Is this where the problem lies?

I have also read somewhere that on some cards, it is necessary to 'activate' them first on a Windows installation with the provided CD.  I have got and adapter coming fron Hong Kong so that I can attach the Novatel to a desktop. 

I cannot see any reference to the mcc and mnc numbers - they were shown in your modem response in post #9 - mine appear to be the same as yours.

I am sure we are almost there and that a tweak of a config file will do the trick!

---

### Post by Dumpy Dumpster on 2011-08-11
Well - something has happened, but I don't know if is significant!

I was playing with GnomePPP and various settings. I noticed that the Init string was still set at you 'old' one i.e. with 'FCLASS=0' at the end.  So I deleted that part and changed the user name/password to user/mms and it seemed to connect. I attach a picture below. The light on the modem remained steady red but maybe I will have to wait until in UK and T-Mobile coverage for that to change.  

Here is wvdial as it is now....
 
[HTML][sudo] password for michael: 
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Aug 11 16:28:15 2011
--> Pid of pppd: 1455
--> Using interface ppp0
--> pppd: `hf[08]&#65533;nf[08]
--> pppd: `hf[08]&#65533;nf[08]
--> pppd: `hf[08]&#65533;nf[08]
--> pppd: `hf[08]&#65533;nf[08]
[/HTML]

What do you think?

---

### Post by Dumpy Dumpster on 2011-08-13
I think that is about as far as I can go at present.  I did modify the wvdial.conf by adding 'stupid mode=0' so that wvdial now no longer waits for a prompt.

I will try the card in a Windows desktop when the adapter arrives and post back any information.  I will also post back how it connects up in the UK.

All that remains is for me to offer a BIG thank you, alexfish, for your work and patience in sorting this out. The aim was to get the card 'seen' and to connect and that has been achieved.

---

### Post by alexfish on 2011-08-13
> **Dumpy Dumpster said:**
> I think that is about as far as I can go at present.  I did modify the wvdial.conf by adding 'stupid mode=0' so that wvdial now no longer waits for a prompt.

I will try the card in a Windows desktop when the adapter arrives and post back any information.  I will also post back how it connects up in the UK.

All that remains is for me to offer a BIG thank you, alexfish, for your work and patience in sorting this out. The aim was to get the card 'seen' and to connect and that has been achieved.

thanks

also noted that the sim card is for UK so may seen obvious the device will not connect abroad.

look forward to see if it connects in the UK. 

can send PM if a problem

also a site worth reading

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

regards

alexfish

---

