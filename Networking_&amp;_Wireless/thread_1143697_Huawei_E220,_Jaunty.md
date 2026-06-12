---
title: "Huawei E220, Jaunty"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by cocacolaboy on 2009-04-30
Hi! I have recently ungraded an EEE PC to the Jaunty release (9.04). To connect to the Internet I am using the device Huawei E220. Output from lsusb is:

Bus 003 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDAP/HSDPA Modem

I have setup the device with the correct credentials, etc... and can always connect. However, their are problems (hence my post on here!). . .

If I do the following, Internet connectivity is good:

1   Boot into Ubuntu 9.04
2   Connect the device Huawei E220
3   Click System --> Preferences --> Network Proxy
4   Click "Apply System Wide..."
5   Restart the computer

However, if I disconnect the device, or connect the device /once/ Ubuntu has booted, Internet connectivity issues exist. I can still connect using the device, but nothing happens on the connection. 

I am using a Network Proxy (I have to... it is part of the scheme for Computers for Pupils here in UK), and pinging the proxy gives 100% packet loss. 

However, if I follow the above list (1 to 5) everything works fine (0% packet loss when pinging the proxy)

This issue only shows in Jaunty. In other words, in Intrepid there were no such problems, despite the same configuration.

Hopefully, somebody can help :confused:

---

### Post by robinparriath on 2009-05-01
Hey, very similar problem here.  I use a Huawei EG162G USB modem to connect to the internet.  In Intrepid, all I had to do to configure the device was plug it in and select my country and Cellular service provider.

with Jaunty, the connection no longer works.  I even tried replicating the steps mentioned by cocacolaboy.  But even that doesn't work for me.

Well cococolaboy, there seems to be a similar bug reported with a possible solution.  Doesn't work for me, but then again, its for the E220 modem not mine.

[Bug 349560]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/349560")

Try and see if it works for you...

---

### Post by bmdavis on 2009-05-11
Yeah, I'm using the Huawei EG162G as well (0682), to connect to Warid in Uganda using Ubuntu.  Works fine in Mac and XP, no dice in Ubunutu. Here's what WVDIAL gets me:

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.


Any ideas from here?

---

### Post by LequidMetal on 2009-05-11
^ You have not configured your wvdial correctly .....


step 1: Open a terminal , key in ```
lsusb
```  and paste the output here

step 2: key in ```
 ls /dev/ttyU* 
``` and paste the output here


step 3: Finally post your wvdial configuration here ,
key in ```
 sudo gedit /etc/wvdial.conf 
```
 paste it here and dont forget to censure your password and username fields .


@ bmdavis
I went thru your previous posts .... you have def configured your wvdial wrong ..... please provide the requested info so we can help you with your connection :)

---

### Post by pauna on 2009-05-11
> **cocacolaboy said:**
> Hi! I have recently ungraded an EEE PC to the Jaunty release (9.04). To connect to the Internet I am using the device Huawei E220. Output from lsusb is:

Bus 003 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDAP/HSDPA Modem


I have the almost the same configuration: EEE PC 901, Ubuntu 9.04 and Huawei E170. It works flawlessly - Network manager connects automatically to the provider when I insert the stick.

I don't have a proxy in the middle, but that should not be a factor.

I don't have /etc/wvdial.conf anymore, I have let Network Manager take care of all the config details. There's a tab called 'Mobile Broadband' in the NM-applet config GUI.

---

### Post by bmdavis on 2009-05-14
LSUSB - (device 008 is it)

Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 008: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

LS / DEV--

/dev/ttyUSB0

WVDIAL.CONF--
[Dialer Defaults]
Modem=/dev/ttyUSB0
Baud = 460800
Init 1 = AT+CGMM
Init 2 = AT+CMEE=1
Init 3 = ATE0
Init 4 = AT^HS=0,0
Init 5 = AT+CFUN?
Init 6 = AT+CLCK="SC",2
Init 7 = AT+CPIN?
Init 8 = AT+CLCK="SC",2
Modem Type = USB MODEM
Phone=*99#
Username = 
Password = 
Dial Command=ATDT
Stupid Mode=1
ISDN=0


(Thanks)

---

### Post by Abbas_Anjum on 2009-05-18
Aslam o Alaikum
I m a new ubuntu jaunty user and i want to connect to internet via Huawei ETS 2552(simple usb i.e usb is on both end) but i m failed to configure huawei ETS 2552 modem. plz help me my dmesg files are given below.
plz help me. i shall be thankful to you...
 
 
[SIZE=2][ 0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] NSC Geode by NSC
[ 0.000000] Cyrix CyrixInstead
[ 0.000000] Centaur CentaurHauls
[ 0.000000] Transmeta GenuineTMx86
[ 0.000000] Transmeta TransmetaCPU
[ 0.000000] UMC UMC UMC UMC
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 0000000027740000 (usable)
[ 0.000000] BIOS-e820: 0000000027740000 - 0000000027750000 (ACPI data)
[ 0.000000] BIOS-e820: 0000000027750000 - 0000000027800000 (ACPI NVS)
[ 0.000000] DMI 2.3 present.
[ 0.000000] last_pfn = 0x27740 max_arch_pfn = 0x100000
[ 0.000000] Scanning 2 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000002000 (usable)
[ 0.000000] modified: 0000000000002000 - 0000000000006000 (reserved)
[ 0.000000] modified: 0000000000006000 - 0000000000007000 (usable)
[ 0.000000] modified: 0000000000007000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 0000000000092c00 (usable)
[ 0.000000] modified: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000e0000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 0000000027740000 (usable)
[ 0.000000] modified: 0000000027740000 - 0000000027750000 (ACPI data)
[ 0.000000] modified: 0000000027750000 - 0000000027800000 (ACPI NVS)
[ 0.000000] kernel direct mapping tables up to 27740000 @ 10000-16000
[ 0.000000] RAMDISK: 26ffc000 - 2772f2d4
[ 0.000000] ACPI: RSDP 000F6F20, 0014 (r0 ACPIAM)
[ 0.000000] ACPI: RSDT 27740000, 002C (r1 INTEL D845GVFN 20040907 MSFT 97)
[ 0.000000] ACPI: FACP 27740200, 0074 (r1 INTEL D845GVFN 20040907 MSFT 97)
[ 0.000000] ACPI: DSDT 27740370, 3FBF (r1 INTEL D845GVFN 10A MSFT 100000D)
[ 0.000000] ACPI: FACS 27750000, 0040
[ 0.000000] ACPI: APIC 27740300, 0068 (r1 INTEL D845GVFN 20040907 MSFT 97)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 631MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 27740000
[ 0.000000] low ram: 00000000 - 27740000
[ 0.000000] bootmap 00012000 - 00016ee8
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 0027740000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 000087c52c] TEXT DATA BSS ==> [0000100000 - 000087c52c]
[ 0.000000] #4 [0026ffc000 - 002772f2d4] RAMDISK ==> [0026ffc000 - 002772f2d4]
[ 0.000000] #5 [000087d000 - 0000881000] INIT_PG_TABLE ==> [000087d000 - 0000881000]
[ 0.000000] #6 [000009fc00 - 0000100000] BIOS reserved ==> [000009fc00 - 0000100000]
[ 0.000000] #7 [0000010000 - 0000012000] PGTABLE ==> [0000010000 - 0000012000]
[ 0.000000] #8 [0000012000 - 0000017000] BOOTMAP ==> [0000012000 - 0000017000]
[ 0.000000] found SMP MP-table at [c00ff780] 000ff780
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000000 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x00027740
[ 0.000000] HighMem 0x00027740 -> 0x00027740
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[4] active PFN ranges
[ 0.000000] 0: 0x00000000 -> 0x00000002
[ 0.000000] 0: 0x00000006 -> 0x00000007
[ 0.000000] 0: 0x00000010 -> 0x00000092
[ 0.000000] 0: 0x00000100 -> 0x00027740
[ 0.000000] On node 0 totalpages: 161477
[ 0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3941 pages, LIFO batch:0
[ 0.000000] Normal zone: 1231 pages used for memmap
[ 0.000000] Normal zone: 156273 pages, LIFO batch:31
[ 0.000000] HighMem zone: 0 pages used for memmap
[ 0.000000] Movable zone: 0 pages used for memmap
[ 0.000000] ACPI: PM-Timer IO Port: 0x408
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[ 0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[ 0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[ 0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[ 0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 30000000 (gap: 27800000:d8800000)
[ 0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[ 0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 160214
[ 0.000000] Kernel command line: root=UUID=88c6bb1f-d22c-4ec5-8236-c54e0224b6e2 ro quiet splash 
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 2266.470 MHz processor.
[ 0.004000] Console: colour VGA+ 80x25
[ 0.004000] console [tty0] enabled
[ 0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.004000] allocated 3232000 bytes of page_cgroup
[ 0.004000] please try cgroup_disable=memory option if you don't want
[ 0.004000] Scanning for low memory corruption every 60 seconds
[ 0.004000] Memory: 621416k/646400k available (4126k kernel code, 24208k reserved, 2208k data, 532k init, 0k highmem)
[ 0.004000] virtual kernel memory layout:
[ 0.004000] fixmap : 0xffc77000 - 0xfffff000 (3616 kB)
[ 0.004000] pkmap : 0xff400000 - 0xff800000 (4096 kB)
[ 0.004000] vmalloc : 0xe7f40000 - 0xff3fe000 ( 372 MB)
[ 0.004000] lowmem : 0xc0000000 - 0xe7740000 ( 631 MB)
[ 0.004000] .init : 0xc0737000 - 0xc07bc000 ( 532 kB)
[ 0.004000] .data : 0xc0507a6f - 0xc072fe60 (2208 kB)
[ 0.004000] .text : 0xc0100000 - 0xc0507a6f (4126 kB)
[ 0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[ 0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 4532.94 BogoMIPS (lpj=9065880)
[ 0.004045] Security Framework initialized
[ 0.004054] SELinux: Disabled at boot.
[ 0.004080] AppArmor: AppArmor initialized
[ 0.004096] Mount-cache hash table entries: 512
[ 0.004315] Initializing cgroup subsys ns
[ 0.004324] Initializing cgroup subsys cpuacct
[ 0.004328] Initializing cgroup subsys memory
[ 0.004334] Initializing cgroup subsys freezer
[ 0.004361] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 0.004367] CPU: L2 cache: 256K
[ 0.004371] CPU: Hyper-Threading is disabled
[ 0.004378] using mwait in idle threads.
[ 0.004398] Checking 'hlt' instruction... OK.
[ 0.021138] SMP alternatives: switching to UP code
[ 0.192045] ACPI: Core revision 20080926
[ 0.196837] ACPI: Checking initramfs for custom DSDT
[ 0.578267] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.617964] CPU0: Intel(R) Celeron(R) CPU 2.26GHz stepping 01
[ 0.620002] Brought up 1 CPUs
[ 0.620002] Total of 1 processors activated (4532.94 BogoMIPS).
[ 0.620002] CPU0 attaching NULL sched-domain.
[ 0.620002] net_namespace: 776 bytes
[ 0.620002] Booting paravirtualized kernel on bare hardware
[ 0.620002] Time: 20:12:59 Date: 05/18/09
[ 0.620002] regulator: core version 0.5
[ 0.620002] NET: Registered protocol family 16
[ 0.620002] EISA bus registered
[ 0.620002] ACPI: bus type pci registered
[ 0.620002] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[ 0.620002] PCI: Using configuration type 1 for base access
[ 0.621007] ACPI: EC: Look up EC in DSDT
[ 0.630080] ACPI: Interpreter enabled
[ 0.630091] ACPI: (supports S0 S1 S4 S5)
[ 0.630122] ACPI: Using IOAPIC for interrupt routing
[ 0.639349] ACPI: No dock devices found.
[ 0.639372] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.639451] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[ 0.639529] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[ 0.639538] pci 0000:00:02.0: reg 14 32bit mmio: [0xffa80000-0xffafffff]
[ 0.639656] pci 0000:00:1d.0: reg 20 io port: [0xe800-0xe81f]
[ 0.639716] pci 0000:00:1d.1: reg 20 io port: [0xe880-0xe89f]
[ 0.639776] pci 0000:00:1d.2: reg 20 io port: [0xec00-0xec1f]
[ 0.639846] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa7fc00-0xffa7ffff]
[ 0.639897] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.639903] pci 0000:00:1d.7: PME# disabled
[ 0.639964] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[ 0.639965] * this clock source is slow. If you are sure your timer does not have
[ 0.639967] * this bug, please use "acpi_pm_good" to disable the workaround
[ 0.640043] HPET not enabled in BIOS. You might try hpet=force boot option
[ 0.640053] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[ 0.640058] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[ 0.640084] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[ 0.640092] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[ 0.640100] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[ 0.640109] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[ 0.640117] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[ 0.640126] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[ 0.640184] pci 0000:00:1f.3: reg 20 io port: [0xe000-0xe01f]
[ 0.640234] pci 0000:00:1f.5: reg 10 io port: [0xe400-0xe4ff]
[ 0.640242] pci 0000:00:1f.5: reg 14 io port: [0xe080-0xe0bf]
[ 0.640250] pci 0000:00:1f.5: reg 18 32bit mmio: [0xffa7f800-0xffa7f9ff]
[ 0.640258] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xffa7f400-0xffa7f4ff]
[ 0.640285] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[ 0.640291] pci 0000:00:1f.5: PME# disabled
[ 0.640352] pci 0000:00:1e.0: transparent bridge
[ 0.640358] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[ 0.640364] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff8fffff]
[ 0.640371] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xcea00000-0xceafffff]
[ 0.640382] bus 00 -> node 0
[ 0.640395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.640636] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[ 0.642582] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[ 0.642838] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[ 0.643089] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[ 0.643337] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[ 0.643584] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 0.643835] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 0.644125] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 0.644378] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[ 0.644570] ACPI: Power Resource [URP1] (off)
[ 0.644629] ACPI: Power Resource [FDDP] (off)
[ 0.644688] ACPI: Power Resource [LPTP] (off)
[ 0.644831] ACPI: WMI: Mapper loaded
[ 0.645208] SCSI subsystem initialized
[ 0.645298] libata version 3.00 loaded.
[ 0.645390] usbcore: registered new interface driver usbfs
[ 0.645430] usbcore: registered new interface driver hub
[ 0.645490] usbcore: registered new device driver usb
[ 0.645708] PCI: Using ACPI for IRQ routing
[ 0.645851] Bluetooth: Core ver 2.13
[ 0.645851] NET: Registered protocol family 31
[ 0.645851] Bluetooth: HCI device and connection manager initialized
[ 0.645851] Bluetooth: HCI socket layer initialized
[ 0.645851] NET: Registered protocol family 8
[ 0.645851] NET: Registered protocol family 20
[ 0.645851] NetLabel: Initializing
[ 0.645851] NetLabel: domain hash size = 128
[ 0.645851] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.645851] NetLabel: unlabeled traffic allowed by default
[ 0.645851] AppArmor: AppArmor Filesystem Enabled
[ 0.645851] pnp: PnP ACPI init
[ 0.645851] ACPI: bus type pnp registered
[ 0.652293] pnp: PnP ACPI: found 14 devices
[ 0.652299] ACPI: ACPI bus type pnp unregistered
[ 0.652306] PnPBIOS: Disabled by ACPI PNP
[ 0.652332] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[ 0.652346] system 00:0c: ioport range 0x400-0x47f has been reserved
[ 0.652350] system 00:0c: ioport range 0x680-0x6ff has been reserved
[ 0.652353] system 00:0c: ioport range 0x480-0x4bf has been reserved
[ 0.652359] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[ 0.652363] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[ 0.652372] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[ 0.652376] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[ 0.652379] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[ 0.652383] system 00:0d: iomem range 0x100000-0x277fffff could not be reserved
[ 0.687239] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[ 0.687245] pci 0000:00:1e.0: IO window: 0xd000-0xdfff
[ 0.687252] pci 0000:00:1e.0: MEM window: 0xff800000-0xff8fffff
[ 0.687258] pci 0000:00:1e.0: PREFETCH window: 0x000000cea00000-0x000000ceafffff
[ 0.687278] pci 0000:00:1e.0: setting latency timer to 64
[ 0.687284] bus: 00 index 0 io port: [0x00-0xffff]
[ 0.687287] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[ 0.687290] bus: 01 index 0 io port: [0xd000-0xdfff]
[ 0.687293] bus: 01 index 1 mmio: [0xff800000-0xff8fffff]
[ 0.687296] bus: 01 index 2 mmio: [0xcea00000-0xceafffff]
[ 0.687299] bus: 01 index 3 io port: [0x00-0xffff]
[ 0.687302] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[ 0.687320] NET: Registered protocol family 2
[ 0.687553] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.688106] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.689763] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.690692] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.690702] TCP reno registered
[ 0.691014] NET: Registered protocol family 1
[ 0.691242] checking if image is initramfs... it is
[ 1.188079] Switched to high resolution mode on CPU 0
[ 1.485943] Freeing initrd memory: 7372k freed
[ 1.486158] cpufreq: No nForce2 chipset.
[ 1.486391] audit: initializing netlink socket (disabled)
[ 1.486426] type=2000 audit(1242677579.484:1): initialized
[ 1.497208] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 1.498948] VFS: Disk quotas dquot_6.5.1
[ 1.499059] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1.500134] fuse init (API version 7.10)
[ 1.500294] msgmni has been set to 1228
[ 1.500649] alg: No test for stdrng (krng)
[ 1.500682] io scheduler noop registered
[ 1.500686] io scheduler anticipatory registered
[ 1.500688] io scheduler deadline registered
[ 1.500737] io scheduler cfq registered (default)
[ 1.500762] pci 0000:00:02.0: Boot video device
[ 1.504892] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1.504909] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 1.505112] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[ 1.505117] ACPI: Power Button (FF) [PWRF]
[ 1.505205] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[ 1.505215] ACPI: Sleep Button (CM) [SLPB]
[ 1.505485] processor ACPI_CPU:00: registered as cooling_device0
[ 1.505492] ACPI: Processor [CPU1] (supports 8 throttling states)
[ 1.507988] isapnp: Scanning for PnP cards...
[ 1.859781] isapnp: No Plug & Play device found
[ 1.861969] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[ 1.862092] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.862633] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.863955] brd: module loaded
[ 1.864582] loop: module loaded
[ 1.864774] Fixed MDIO Bus: probed
[ 1.864784] PPP generic driver version 2.4.2
[ 1.864888] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[ 1.864952] Driver 'sd' needs updating - please use bus_type methods
[ 1.864970] Driver 'sr' needs updating - please use bus_type methods
[ 1.865091] ata_piix 0000:00:1f.1: version 2.12
[ 1.865113] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[ 1.865132] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1.865207] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 1.865401] scsi0 : ata_piix
[ 1.865600] scsi1 : ata_piix
[ 1.867464] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[ 1.867469] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[ 2.084501] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
[ 2.084505] ata1.00: 156301488 sectors, multi 16: LBA48 
[ 2.084544] ata1.00: limited to UDMA/33 due to 40-wire cable
[ 2.100488] ata1.00: configured for UDMA/33
[ 2.264311] ata2.00: ATAPI: ASUS CD-S520/A5, 1.22, max UDMA/33
[ 2.280270] ata2.00: configured for UDMA/33
[ 2.280691] scsi 0:0:0:0: Direct-Access ATA ST380011A 8.01 PQ: 0 ANSI: 5
[ 2.280908] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2.280940] sd 0:0:0:0: [sda] Write Protect is off
[ 2.280944] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2.280989] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.281125] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2.281154] sd 0:0:0:0: [sda] Write Protect is off
[ 2.281158] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2.281202] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.281210] sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
[ 2.385013] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2.385121] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 2.385500] scsi 1:0:0:0: CD-ROM ASUS CD-S520/A5 1.22 PQ: 0 ANSI: 5
[ 2.388449] sr0: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
[ 2.388456] Uniform CD-ROM driver Revision: 3.20
[ 2.388655] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 2.388752] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 2.389628] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 2.389679] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[ 2.389721] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2.389727] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 2.389868] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 2.393793] ehci_hcd 0000:00:1d.7: debug port 1
[ 2.393802] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[ 2.393826] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa7fc00
[ 2.408014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 2.408137] usb usb1: configuration #1 chosen from 1 choice
[ 2.408182] hub 1-0:1.0: USB hub found
[ 2.408201] hub 1-0:1.0: 6 ports detected
[ 2.408404] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 2.408442] uhci_hcd: USB Universal Host Controller Interface driver
[ 2.408519] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2.408532] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2.408537] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 2.408634] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 2.408674] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[ 2.408820] usb usb2: configuration #1 chosen from 1 choice
[ 2.408863] hub 2-0:1.0: USB hub found
[ 2.408879] hub 2-0:1.0: 2 ports detected
[ 2.409026] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2.409039] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2.409043] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 2.409141] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 2.409179] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
[ 2.409308] usb usb3: configuration #1 chosen from 1 choice
[ 2.409350] hub 3-0:1.0: USB hub found
[ 2.409364] hub 3-0:1.0: 2 ports detected
[ 2.409508] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2.409519] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2.409524] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 2.409603] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 2.409644] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[ 2.409775] usb usb4: configuration #1 chosen from 1 choice
[ 2.409833] hub 4-0:1.0: USB hub found
[ 2.409849] hub 4-0:1.0: 2 ports detected
[ 2.410050] usbcore: registered new interface driver libusual
[ 2.410116] usbcore: registered new interface driver usbserial
[ 2.410143] USB Serial support registered for generic
[ 2.410167] usbcore: registered new interface driver usbserial_generic
[ 2.410171] usbserial: USB Serial Driver core
[ 2.410252] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[ 2.413138] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2.413149] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 2.413390] mice: PS/2 mouse device common for all mice
[ 2.413622] rtc_cmos 00:02: RTC can wake from S4
[ 2.413695] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[ 2.413726] rtc0: alarms up to one month, 114 bytes nvram
[ 2.413862] device-mapper: uevent: version 1.0.3
[ 2.414119] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[ 2.414238] device-mapper: multipath: version 1.0.5 loaded
[ 2.414244] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 2.414433] EISA: Probing bus 0 at eisa.0
[ 2.414478] EISA: Detected 0 cards.
[ 2.414544] cpuidle: using governor ladder
[ 2.414549] cpuidle: using governor menu
[ 2.415324] TCP cubic registered
[ 2.415452] NET: Registered protocol family 10
[ 2.416124] lo: Disabled Privacy Extensions
[ 2.416609] NET: Registered protocol family 17
[ 2.416655] Bluetooth: L2CAP ver 2.11
[ 2.416658] Bluetooth: L2CAP socket layer initialized
[ 2.416662] Bluetooth: SCO (Voice Link) ver 0.6
[ 2.416664] Bluetooth: SCO socket layer initialized
[ 2.416772] Bluetooth: RFCOMM socket layer initialized
[ 2.416795] Bluetooth: RFCOMM TTY layer initialized
[ 2.416798] Bluetooth: RFCOMM ver 1.10
[ 2.416903] Using IPI No-Shortcut mode
[ 2.417081] registered taskstats version 1
[ 2.417212] Magic number: 9:635:245
[ 2.417318] rtc_cmos 00:02: setting system clock to 2009-05-18 20:13:01 UTC (1242677581)
[ 2.417323] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 2.417326] EDD information not available.
[ 2.418261] Freeing unused kernel memory: 532k freed
[ 2.418433] Write protecting the kernel text: 4128k
[ 2.418486] Write protecting the kernel read-only data: 1532k
[ 2.454803] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[ 3.093886] Floppy drive(s): fd0 is 1.44M
[ 3.111819] FDC 0 is a post-1991 82077
[ 4.687949] PM: Starting manual resume from disk
[ 4.687956] PM: Resume from partition 8:11
[ 4.687959] PM: Checking hibernation image.
[ 4.688350] PM: Resume from disk failed.
[ 4.711685] kjournald starting. Commit interval 5 seconds
[ 4.711712] EXT3-fs: mounted filesystem with ordered data mode.
[ 10.277768] udev: starting version 141
[ 10.528044] parport_pc 00:09: reported by Plug and Play ACPI
[ 10.528078] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[ 10.573655] Linux agpgart interface v0.103
[ 10.583153] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[ 10.583422] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[ 10.585722] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[ 10.615705] intel_rng: Firmware space is locked read-only. If you can't or
[ 10.615708] intel_rng: don't want to disable this in firmware setup, and if
[ 10.615710] intel_rng: you are certain that your system has a functional
[ 10.615712] intel_rng: RNG, try using the 'no_fwh_detect' option.
[ 10.891505] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 10.899780] iTCO_vendor_support: vendor-support=0
[ 10.903443] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[ 10.903714] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[ 10.903883] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 10.940924] input: PC Speaker as /devices/platform/pcspkr/input/input4
[ 11.072143] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 11.518863] psmouse serio1: ID: 10 00 64<6>ppdev: user-space parallel port driver
[ 12.030434] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 12.030677] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 12.035904] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[ 12.352023] intel8x0_measure_ac97_clock: measured 55021 usecs
[ 12.352029] intel8x0: clocking to 48000
[ 12.595266] lp0: using parport0 (interrupt-driven).
[ 12.763574] Adding 345356k swap on /dev/sda11. Priority:-1 extents:1 across:345356k
[ 13.343966] EXT3 FS on sda10, internal journal
[ 14.680826] type=1505 audit(1242655993.762:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1859
[ 14.760063] type=1505 audit(1242655993.842:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1863
[ 14.760384] type=1505 audit(1242655993.842:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1863
[ 14.760535] type=1505 audit(1242655993.842:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1863
[ 14.760645] type=1505 audit(1242655993.842:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1863
[ 14.976472] type=1505 audit(1242655994.058:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1868
[ 14.976951] type=1505 audit(1242655994.058:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1868
[ 15.026853] type=1505 audit(1242655994.106:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1872
[ 20.006775] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 20.006781] Bluetooth: BNEP filters: protocol multicast
[ 20.048052] Bridge firewalling registered
[ 22.052071] [drm] Initialized drm 1.1.0 20060810
[ 22.080713] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 22.080722] pci 0000:00:02.0: setting latency timer to 64
[ 22.081018] [drm] Initialized i915 1.6.0 20080730 on minor 0
[ 22.250541] [drm:i915_setparam] *ERROR* unknown parameter 4
[ 22.250597] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 22.802669] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 94.908051] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 95.227821] usb 3-2: configuration #1 chosen from 1 choice
[/SIZE]

---

### Post by alan k on 2009-05-20
i recently got the huawei E220 (vodaphone) for my acer netbook....wiped XP and loaded ubuntu 9.04.....the modem installed right away..all i had to do was configure the settings (in GUI mode) also it just came up straight after i plugged te device in...the only issue i have is i cant find any software that will tell me what data allowance i have used and what speeds im getting.....does anyone know if there is anything about?
 
cheers alan.....
 
p.s. i downloaded and installed ubuntu remix for netbooks 9.04 edition and then did an update....obviously will varie according to your machines.

---

### Post by LequidMetal on 2009-05-21
> **bmdavis said:**
> LSUSB - (device 008 is it)

Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 008: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

LS / DEV--

/dev/ttyUSB0

WVDIAL.CONF--
[Dialer Defaults]
Modem=/dev/ttyUSB0
Baud = 460800
Init 1 = AT+CGMM
Init 2 = AT+CMEE=1
Init 3 = ATE0
Init 4 = AT^HS=0,0
Init 5 = AT+CFUN?
Init 6 = AT+CLCK="SC",2
Init 7 = AT+CPIN?
Init 8 = AT+CLCK="SC",2
Modem Type = USB MODEM
Phone=*99#
Username = 
Password = 
Dial Command=ATDT
Stupid Mode=1
ISDN=0


(Thanks)

very sorry havent logged in here for a long time . Hope you managed to get it connected , if not try this 

> 
sudo modprobe usbserial vendor=0x12d1 product=0x1001


---

### Post by LequidMetal on 2009-05-21
(and then)Try this as your Phone parameter 

> 
*99***1#


and please do post the error you get for both your first and second configuration

---

### Post by LequidMetal on 2009-05-21
> **alan k said:**
> the only issue i have is i cant find any software that will tell me what data allowance i have used and what speeds im getting.....does anyone know if there is anything about?
 
cheers alan.....
 


Gnome-ppp in gnome 
or
kppp in kde

---

### Post by bmdavis on 2009-05-28
Still the same error from above.... surely my wvdial.conf must be configured incorrectly.

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

---

### Post by carlleigh@gmail.com on 2009-05-28
Netbook Remix 9.04
I've run into a problem with the resolv.conf file. /etc/resolv.conf.
I can log into my service provider correctly then connection the doesn't work. (No ping!)

If I manually add a new nameserver 208.67.222.222 or 208.67.220.220 as the first line in resolv.conf it then works.
208.67.222.222 by the way is opendns.
Or if I use a different name server from my service provider it will also work. 
The two nameservers provided originally by Network Manager don't.

opendns.com.

Note I'm also having the same problem with Eeebuntu base 3. Any permanent fix?

Provider or 9.04? 

I have two different model Huawai modems same problem. E220 and E960.

---

