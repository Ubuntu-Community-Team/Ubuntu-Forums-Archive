---
title: "Broadcom 4306 rev3 and 8.10"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Evil Overlord on 2009-01-26
Gateway 7422GX, with Broadcom 4306 rev 03; Ubuntu 8.10 with latest updates

1. I earlier installed Ubuntu, tried lots of things to get wireless to work, and then somehow, suddenly, it did.  I recall one thing I did was to edit a file that said something specific about b43... - I claim no credit.  To be accurate, it SOMEtimes worked - no rhyme or reason to when.  I can't find the post with instructions anymore.  Then, unfortunately, I had to re-install.

2. What I've tried this time (with restarts at each step):
 i) installed cafuego Intrepid files by downloading and running b43-firmware_1.1-0cafuego1_all.deb
 ii) activated the b43 driver Ubuntu itself offered under Hardware Drivers.  No difference whether this was activated or not.
 iii) edited /etc/modprobe.d/blacklist.  I tried unblacklisting bcm43xx (adding a # comment), and then blacklisting b43.  The only difference was that when b43 was blacklisted, clicking on the network icon in the system panel no longer showed wireless options.
 iv) I reversed the blacklist changes.  After this, b43 no longer shows up as activated in the Hardware Drivers.  Activating it says it's suspended but still active.
 iv) installing ndiswrapper via Applications Add/remove.  I pointed it at bcmwl5.inf.  I tried to use the network configuration button, but it said it couldn't find a network configuration tool.
 vi) tried sudo modprobe b43.  No reaction.
 vii) tried apt-get install bcm43xx-fwcutter
	E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
	E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
      and sudo apt-get install bcm43xx-fwcutter
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	E: Couldn't find package bcm43xx-fwcutter
 ix) after, unfortunately, getting all the data below, I tried:
     ben@Gateway:~$ sudo aptitude install b43-fwcutter
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	Initializing package states... Done
	Writing extended state information... Done
	The following packages will be REMOVED:
	  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} 
	0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
	Need to get 0B of archives. After unpacking 52.0MB will be freed.
	Do you want to continue? [Y/n/?] y
	Writing extended state information... Done
	(Reading database ... 115835 files and directories currently installed.)
	Removing linux-headers-2.6.27-7-generic ...
	Removing linux-headers-2.6.27-7 ...
	Reading package lists... Done             
	Building dependency tree       
	Reading state information... Done
	Reading extended state information      
	Initializing package states... Done
	Writing extended state information... Done
  I haven't rerun all the below data commands, because to be honest I have no idea what this command did.
 x) and also all the instructions at [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)
     neither has had any effect that I can see.

I'm lost.  I'm new to Linux, and find wireless networks to be more voodoo than science, so I'm eager for any advice.  Below is information that often is requested in other fora.

ben@Gateway:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:13.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

ben@Gateway:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ben@Gateway:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:14:93:2f  
          inet addr:192.168.0.131  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe14:932f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1716426 (1.7 MB)  TX bytes:163182 (163.1 KB)
          Interrupt:23 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:c5:aa:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-C5-AA-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ben@Gateway:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

ben@Gateway:~$ dmesg 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fefb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fefb000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3fef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781e000 - 37fefd15
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000F85E0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3FEF6B1F, 0030 (r1 Arima  161Fh     6040000  LTP        0)
[    0.000000] ACPI: FACP 3FEFAE66, 0074 (r1 Arima  161Fh     6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 3FEF6B4F, 4317 (r1  Arima 161Fh     6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEFBFC0, 0040
[    0.000000] ACPI: SSDT 3FEFAEDA, 00D6 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 3FEFAFB0, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003781e000 - 0037fefd15]          RAMDISK ==> [003781e000 - 0037fefd15]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f8550] 000f8550
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003fef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fef0
[    0.000000] On node 0 totalpages: 261775
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32210 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bffe0000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259473
[    0.000000] Kernel command line: root=UUID=e0ece8a7-53a7-40f2-befb-f9763a827018 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2204.971 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1023732k/1047488k available (2572k kernel code, 22984k reserved, 1160k data, 424k init, 129984k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 4409.94 BogoMIPS (lpj=8819884)
[    0.004036] Security Framework initialized
[    0.004046] SELinux:  Disabled at boot.
[    0.004076] AppArmor: AppArmor initialized
[    0.004084] Mount-cache hash table entries: 512
[    0.004262] Initializing cgroup subsys ns
[    0.004266] Initializing cgroup subsys cpuacct
[    0.004269] Initializing cgroup subsys memory
[    0.004284] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004287] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004303] Checking 'hlt' instruction... OK.
[    0.020427] SMP alternatives: switching to UP code
[    0.025339] Freeing SMP alternatives: 11k freed
[    0.025343] ACPI: Core revision 20080609
[    0.026929] ACPI: Checking initramfs for custom DSDT
[    0.332610] ENABLING IO-APIC IRQs
[    0.332917] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[    0.374046] CPU0: AMD Mobile AMD Athlon(tm) 64 Processor 3400+ stepping 0a
[    0.376023] Brought up 1 CPUs
[    0.376023] Total of 1 processors activated (4409.94 BogoMIPS).
[    0.376023] CPU0 attaching sched-domain:
[    0.376023]  domain 0: span 0 level CPU
[    0.376023]   groups: 0
[    0.376023] net_namespace: 840 bytes
[    0.376023] Booting paravirtualized kernel on bare hardware
[    0.376023] Time: 13:47:59  Date: 01/26/09
[    0.376023] NET: Registered protocol family 16
[    0.376023] EISA bus registered
[    0.376023] ACPI: bus type pci registered
[    0.386548] PCI: PCI BIOS revision 2.10 entry at 0xfd8cc, last bus=1
[    0.386551] PCI: Using configuration type 1 for base access
[    0.387637] ACPI: EC: Look up EC in DSDT
[    0.391390] ACPI: Interpreter enabled
[    0.391393] ACPI: (supports S0 S3 S4 S5)
[    0.391404] ACPI: Using IOAPIC for interrupt routing
[    0.393807] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.409341] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[    0.409343] ACPI: EC: driver started in interrupt mode
[    0.409381] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.409452] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, efffffff]
[    0.409510] pci 0000:00:01.0: supports D1
[    0.409539] PCI: 0000:00:0a.0 reg 10 32bit mmio: [ffe7f000, ffe7ffff]
[    0.409551] pci 0000:00:0a.0: supports D1
[    0.409552] pci 0000:00:0a.0: supports D2
[    0.409555] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.409559] pci 0000:00:0a.0: PME# disabled
[    0.409573] PCI: 0000:00:0c.0 reg 10 32bit mmio: [d0000000, d0001fff]
[    0.409632] PCI: 0000:00:10.0 reg 20 io port: [1c80, 1c9f]
[    0.409649] pci 0000:00:10.0: supports D1
[    0.409650] pci 0000:00:10.0: supports D2
[    0.409652] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.409656] pci 0000:00:10.0: PME# disabled
[    0.409689] PCI: 0000:00:10.1 reg 20 io port: [1ca0, 1cbf]
[    0.409706] pci 0000:00:10.1: supports D1
[    0.409707] pci 0000:00:10.1: supports D2
[    0.409709] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.409713] pci 0000:00:10.1: PME# disabled
[    0.409746] PCI: 0000:00:10.2 reg 20 io port: [1cc0, 1cdf]
[    0.409763] pci 0000:00:10.2: supports D1
[    0.409765] pci 0000:00:10.2: supports D2
[    0.409767] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.409770] pci 0000:00:10.2: PME# disabled
[    0.409791] PCI: 0000:00:10.3 reg 10 32bit mmio: [d0002800, d00028ff]
[    0.409820] pci 0000:00:10.3: supports D1
[    0.409822] pci 0000:00:10.3: supports D2
[    0.409824] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.409828] pci 0000:00:10.3: PME# disabled
[    0.409878] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.409884] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
[    0.409887] pci 0000:00:11.0: quirk: region 8100-810f claimed by vt8235 SMB
[    0.409926] PCI: 0000:00:11.1 reg 20 io port: [1ce0, 1cef]
[    0.409969] PCI: 0000:00:11.5 reg 10 io port: [1000, 10ff]
[    0.410001] pci 0000:00:11.5: supports D1
[    0.410002] pci 0000:00:11.5: supports D2
[    0.410023] PCI: 0000:00:11.6 reg 10 io port: [1400, 14ff]
[    0.412061] PCI: 0000:00:12.0 reg 10 io port: [1800, 18ff]
[    0.412067] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0002c00, d0002cff]
[    0.412094] pci 0000:00:12.0: supports D1
[    0.412096] pci 0000:00:12.0: supports D2
[    0.412098] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.412101] pci 0000:00:12.0: PME# disabled
[    0.412122] PCI: 0000:00:13.0 reg 10 32bit mmio: [d0002000, d00027ff]
[    0.412128] PCI: 0000:00:13.0 reg 14 io port: [1c00, 1c7f]
[    0.412156] pci 0000:00:13.0: supports D2
[    0.412158] pci 0000:00:13.0: PME# supported from D2 D3hot D3cold
[    0.412161] pci 0000:00:13.0: PME# disabled
[    0.412231] PCI: 0000:01:00.0 reg 10 32bit mmio: [d8000000, dfffffff]
[    0.412235] PCI: 0000:01:00.0 reg 14 io port: [2000, 20ff]
[    0.412240] PCI: 0000:01:00.0 reg 18 32bit mmio: [d0100000, d010ffff]
[    0.412249] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.412259] pci 0000:01:00.0: supports D1
[    0.412260] pci 0000:01:00.0: supports D2
[    0.412280] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.412284] PCI: bridge 0000:00:01.0 32bit mmio: [d0100000, d01fffff]
[    0.412288] PCI: bridge 0000:00:01.0 32bit mmio pref: [d8000000, dfffffff]
[    0.412305] bus 00 -> node 0
[    0.412311] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.418950] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[    0.419039] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11, disabled.
[    0.419124] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *10, disabled.
[    0.419208] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *10, disabled.
[    0.419325] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 12 14 15)
[    0.419441] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.419557] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 11 12 14 15) *10
[    0.419675] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.419817] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.419850] pnp: PnP ACPI init
[    0.419856] ACPI: bus type pnp registered
[    0.421848] pnp: PnP ACPI: found 9 devices
[    0.421848] ACPI: ACPI bus type pnp unregistered
[    0.421848] PnPBIOS: Disabled by ACPI PNP
[    0.421848] PCI: Using ACPI for IRQ routing
[    0.421848] NET: Registered protocol family 8

[    0.421848] NET: Registered protocol family 20
[    0.421848] NetLabel: Initializing
[    0.421848] NetLabel:  domain hash size = 128
[    0.421848] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.421848] NetLabel:  unlabeled traffic allowed by default
[    0.421848] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.421848]    actual entries 65620
[    0.421848] AppArmor: AppArmor Filesystem Enabled
[    0.421848] ACPI: RTC can wake from S4
[    0.421848] system 00:05: iomem range 0x0-0x9ffff could not be reserved
[    0.421848] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
[    0.421848] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.421848] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved
[    0.421848] system 00:05: iomem range 0xfee00400-0xfee013ff has been reserved
[    0.421848] system 00:05: iomem range 0xffe00000-0xffe7ffff could not be reserved
[    0.421848] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.421848] system 00:06: ioport range 0xf510-0xf511 has been reserved
[    0.421848] system 00:06: ioport range 0xf500-0xf500 has been reserved
[    0.421848] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.421848] system 00:06: ioport range 0x8100-0x811f could not be reserved
[    0.421848] system 00:06: ioport range 0x200-0x20f has been reserved
[    0.421848] system 00:06: ioport range 0x300-0x301 has been reserved
[    0.458330] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.458333] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.458338] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
[    0.458342] pci 0000:00:01.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
[    0.458347] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.458350] pci 0000:00:0a.0:   IO window: 0x003000-0x0030ff
[    0.458353] pci 0000:00:0a.0:   IO window: 0x003400-0x0034ff
[    0.458357] pci 0000:00:0a.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.458361] pci 0000:00:0a.0:   MEM window: 0x54000000-0x57ffffff
[    0.458374] pci 0000:00:01.0: setting latency timer to 64
[    0.458414] pci 0000:00:0a.0: power state changed by ACPI to D0
[    0.458422] pci 0000:00:0a.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.458431] bus: 00 index 0 io port: [0, ffff]
[    0.458433] bus: 00 index 1 mmio: [0, ffffffff]
[    0.458435] bus: 01 index 0 io port: [2000, 2fff]
[    0.458437] bus: 01 index 1 mmio: [d0100000, d01fffff]
[    0.458439] bus: 01 index 2 mmio: [d8000000, dfffffff]
[    0.458441] bus: 01 index 3 mmio: [0, 0]
[    0.458443] bus: 02 index 0 io port: [3000, 30ff]
[    0.458445] bus: 02 index 1 io port: [3400, 34ff]
[    0.458447] bus: 02 index 2 mmio: [50000000, 53ffffff]
[    0.458449] bus: 02 index 3 mmio: [54000000, 57ffffff]
[    0.458458] NET: Registered protocol family 2
[    0.458570] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.458886] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.460048] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.460622] TCP: Hash tables configured (established 131072 bind 65536)
[    0.460625] TCP reno registered
[    0.460744] NET: Registered protocol family 1
[    0.460882] checking if image is initramfs... it is
[    0.960076] Switched to high resolution mode on CPU 0
[    1.105711] Freeing initrd memory: 8007k freed
[    1.106478] audit: initializing netlink socket (disabled)
[    1.106496] type=2000 audit(1232977679.104:1): initialized
[    1.111986] highmem bounce pool size: 64 pages
[    1.111993] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.114101] VFS: Disk quotas dquot_6.5.1
[    1.114185] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.114285] msgmni has been set to 1762
[    1.114394] io scheduler noop registered
[    1.114397] io scheduler anticipatory registered
[    1.114399] io scheduler deadline registered
[    1.114409] io scheduler cfq registered (default)
[    1.114419] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.114485] pci 0000:01:00.0: Boot video device
[    1.114784] isapnp: Scanning for PnP cards...
[    1.468409] isapnp: No Plug & Play device found
[    1.500619] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.502608] brd: module loaded
[    1.502678] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.502775] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.505100] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.505106] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.505439] mice: PS/2 mouse device common for all mice
[    1.505556] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.505587] rtc0: alarms up to one year, y3k
[    1.505685] EISA: Probing bus 0 at eisa.0
[    1.505693] Cannot allocate resource for EISA slot 1
[    1.505696] Cannot allocate resource for EISA slot 2
[    1.505698] Cannot allocate resource for EISA slot 3
[    1.505700] Cannot allocate resource for EISA slot 4
[    1.505717] EISA: Detected 0 cards.
[    1.505720] cpuidle: using governor ladder
[    1.505723] cpuidle: using governor menu
[    1.506164] TCP cubic registered
[    1.506190] Using IPI No-Shortcut mode
[    1.506362] registered taskstats version 1
[    1.506468]   Magic number: 9:536:787
[    1.506584] tty ptyq9: hash matches
[    1.506658] rtc_cmos 00:02: setting system clock to 2009-01-26 13:48:00 UTC (1232977680)
[    1.506661] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.506663] EDD information not available.
[    1.507202] Freeing unused kernel memory: 424k freed
[    1.507256] Write protecting the kernel text: 2576k
[    1.507289] Write protecting the kernel read-only data: 936k
[    1.533573] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.728461] fuse init (API version 7.9)
[    2.009728] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.009781] processor ACPI0007:00: registered as cooling_device0
[    2.537500] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.540832] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0c.0
[    2.600627] usbcore: registered new interface driver usbfs
[    2.600653] usbcore: registered new interface driver hub
[    2.600697] usbcore: registered new device driver usb
[    2.602523] USB Universal Host Controller Interface driver v3.0
[    2.602677] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
[    2.602741] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
[    2.602744] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
[    2.602753] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    2.602763] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.602818] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    2.602852] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001c80
[    2.603042] usb usb1: configuration #1 chosen from 1 choice
[    2.603069] hub 1-0:1.0: USB hub found
[    2.603079] hub 1-0:1.0: 2 ports detected
[    2.631415] No dock devices found.
[    2.687921] SCSI subsystem initialized
[    2.744390] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.763120] libata version 3.00 loaded.
[    2.808285] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    2.808297] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.808319] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    2.808342] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001ca0
[    2.808438] usb usb2: configuration #1 chosen from 1 choice
[    2.808463] hub 2-0:1.0: USB hub found
[    2.808474] hub 2-0:1.0: 2 ports detected
[    3.016301] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    3.016314] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.016336] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.016362] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001cc0
[    3.016465] usb usb3: configuration #1 chosen from 1 choice
[    3.016496] hub 3-0:1.0: USB hub found
[    3.016507] hub 3-0:1.0: 2 ports detected
[    3.195382] Marking TSC unstable due to TSC halts in idle
[    3.224425] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    3.224443] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    3.224466] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    3.224503] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd0002800
[    3.236014] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.236098] usb usb4: configuration #1 chosen from 1 choice
[    3.236124] hub 4-0:1.0: USB hub found
[    3.236133] hub 4-0:1.0: 6 ports detected
[    3.355461] via-rhine 0000:00:12.0: power state changed by ACPI to D0
[    3.355540] ACPI: PCI Interrupt Link [ALKB] disabled and referenced, BIOS bug
[    3.355601] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 23
[    3.355604] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[    3.355611] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKB] -> GSI 23 (level, low) -> IRQ 23
[    3.360744] eth0: VIA Rhine II at 0xd0002c00, 00:03:25:14:93:2f, IRQ 23.
[    3.361451] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[    3.362962] ohci1394 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.415691] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[d0002000-d00027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.426669] pata_via 0000:00:11.1: version 0.3.3
[    3.426741] pata_via 0000:00:11.1: power state changed by ACPI to D0
[    3.426821] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[    3.426885] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 22
[    3.426888] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 22
[    3.426896] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 22 (level, low) -> IRQ 22
[    3.427272] scsi0 : pata_via
[    3.427973] scsi1 : pata_via
[    3.428768] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1ce0 irq 14
[    3.428771] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1ce8 irq 15
[    3.592621] ata1.00: ATA-6: FUJITSU MHT2080AT, 0022, max UDMA/100
[    3.592626] ata1.00: 156301488 sectors, multi 16: LBA 
[    3.608459] ata1.00: configured for UDMA/100
[    3.772349] ata2.00: ATAPI: HL-DT-ST DVD-RW GCA-4080N, 0G32, max UDMA/33
[    3.788224] ata2.00: configured for UDMA/33
[    3.788335] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2080A 0022 PQ: 0 ANSI: 5
[    3.792262] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GCA-4080N 0G32 PQ: 0 ANSI: 5
[    3.806413] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.806448] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    3.828542] Driver 'sd' needs updating - please use bus_type methods
[    3.830219] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.830241] sd 0:0:0:0: [sda] Write Protect is off
[    3.830244] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.830277] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.830349] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.830367] sd 0:0:0:0: [sda] Write Protect is off
[    3.830369] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.830400] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.830405]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    3.892805]  sda1 sda2 < sda5 >
[    3.924666] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.938418] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.938424] Uniform CD-ROM driver Revision: 3.20
[    3.938523] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.242327] PM: Starting manual resume from disk
[    4.242332] PM: Resume from partition 8:5
[    4.242333] PM: Checking hibernation image.
[    4.242520] PM: Resume from disk failed.
[    4.312082] kjournald starting.  Commit interval 5 seconds
[    4.312096] EXT3-fs: mounted filesystem with ordered data mode.
[    4.692155] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00032521290165b5]
[   11.985940] udevd version 124 started
[   12.315556] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.665302] Linux agpgart interface v0.103
[   12.832095] Yenta: CardBus bridge found at 0000:00:0a.0 [161f:2032]
[   12.832113] Yenta: Using CSCINT to route CSC interrupts to PCI
[   12.832116] Yenta: Routing CardBus interrupts to PCI
[   12.832120] Yenta TI: socket 0000:00:0a.0, mfunc 0x01001002, devctl 0x44
[   13.064844] Yenta: ISA IRQ mask 0x0890, PCI irq 17
[   13.064848] Socket status: 30000006
[   13.113176] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
[   13.123331] usbcore: registered new interface driver ndiswrapper
[   13.123503] agpgart-amd64 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   13.143673] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.164518] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.279516] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.288031] ACPI: Power Button (FF) [PWRF]
[   13.288169] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   13.304058] ACPI: Power Button (CM) [PWRB]
[   13.304202] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.316037] ACPI: Sleep Button (CM) [SLPB]
[   13.316177] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   13.316579] ACPI: Lid Switch [LID]
[   13.506699] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.782424] irda_init()
[   13.782443] NET: Registered protocol family 23
[   13.915338] ACPI: AC Adapter [AC] (on-line)
[   14.223410] ACPI: Battery Slot [BAT0] (battery present)
[   14.459745] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   14.500614] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   14.604885] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/input/input8
[   14.608074] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.692876] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
[   14.692947] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[   14.693009] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   14.693012] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   14.693017] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   14.697746] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   15.028895] b43-phy0: Broadcom 4306 WLAN found
[   15.078367] phy0: Selected rate control algorithm 'pid'
[   15.304131] MC'97 1 converters and GPIO not ready (0xff00)
[   15.369755] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   15.369767] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   15.369900] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   15.370079] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   16.348876] cs: IO port probe 0x100-0x3af: clean.
[   16.350745] cs: IO port probe 0x3e0-0x4ff: clean.
[   16.351556] cs: IO port probe 0x820-0x8ff: clean.
[   16.352263] cs: IO port probe 0xc00-0xcf7: clean.
[   16.353094] cs: IO port probe 0xa00-0xaff: clean.
[   16.993234] lp: driver loaded but no devices found
[   17.190559] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k
[   17.941912] EXT3 FS on sda1, internal journal
[   19.005666] type=1505 audit(1232977698.155:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3976
[   19.205730] type=1505 audit(1232977698.355:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3981
[   19.206022] type=1505 audit(1232977698.355:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3981
[   19.380986] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.031669] ACPI: WMI: Mapper loaded
[   20.327887] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[   20.327930] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   20.327933] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x12
[   20.327935] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18
[   21.084219] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.175645] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   21.175654] apm: overridden by ACPI.
[   21.365015] ppdev: user-space parallel port driver
[   22.456031] Clocksource tsc unstable (delta = -129720352 ns)
[   22.965197] Bluetooth: Core ver 2.13
[   22.968312] NET: Registered protocol family 31
[   22.968320] Bluetooth: HCI device and connection manager initialized
[   22.968326] Bluetooth: HCI socket layer initialized
[   23.000767] Bluetooth: L2CAP ver 2.11
[   23.000775] Bluetooth: L2CAP socket layer initialized
[   23.023785] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.023793] Bluetooth: BNEP filters: protocol multicast
[   23.078382] Bridge firewalling registered
[   23.079474] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   23.105473] Bluetooth: SCO (Voice Link) ver 0.6
[   23.105482] Bluetooth: SCO socket layer initialized
[   23.137875] Bluetooth: RFCOMM socket layer initialized
[   23.138186] Bluetooth: RFCOMM TTY layer initialized
[   23.138193] Bluetooth: RFCOMM ver 1.10
[   25.360220] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.794605] [drm] Initialized drm 1.1.0 20060810
[   25.837983] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   26.005708] agpgart-amd64 0000:00:00.0: AGP 3.5 bridge
[   26.005753] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   26.005839] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   26.319439] [drm] Setting GART location based on new memory map
[   26.319461] [drm] Loading R300 Microcode
[   26.319527] [drm] Num pipes: 1
[   26.319539] [drm] writeback test succeeded in 1 usecs
[   27.285144] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   27.363876] input: b43-phy0 as /devices/virtual/input/input9
[   27.432050] firmware: requesting b43/ucode5.fw
[   27.531688] firmware: requesting b43/pcm5.fw
[   27.567282] firmware: requesting b43/b0g0initvals5.fw
[   27.594669] firmware: requesting b43/b0g0bsinitvals5.fw
[   27.840052] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   28.000299] Registered led device: b43-phy0::tx
[   28.001179] Registered led device: b43-phy0::rx
[   28.001822] Registered led device: b43-phy0::radio
[   28.286002] NET: Registered protocol family 17
[   34.007970] NET: Registered protocol family 10
[   34.011745] lo: Disabled Privacy Extensions
[   34.022617] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.904027] eth0: no IPv6 routers present

ben@Gateway:~$ lsmod
Module                  Size  Used by
ipv6                  263972  8 
af_packet              25728  4 
rfkill_input           12672  0 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
pci_slot               12552  0 
container              11520  0 
wmi                    14504  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
b43                   131356  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
led_class              12164  1 b43
evdev                  17696  11 
snd_via82xx            32536  3 
input_polldev          11912  1 b43
gameport               19468  1 snd_via82xx
snd_via82xx_modem      19464  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_ac97_codec        111652  2 snd_via82xx,snd_via82xx_modem
video                  25104  0 
ac97_bus                9856  1 snd_ac97_codec
snd_mpu401_uart        15360  1 snd_via82xx
snd_pcm                83204  4 snd_via82xx,snd_via82xx_modem,snd_pcm_oss,snd_ac97_codec
output                 11008  1 video
snd_seq_dummy          10884  0 
battery                18436  0 
serio_raw              13444  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
via_ircc               32020  0 
ac                     12292  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
psmouse                45200  0 
irda                  199612  1 via_ircc
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
crc_ccitt              10112  1 irda
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_viapro             15764  0 
button                 14224  0 
k8temp                 12416  0 
snd                    63268  18 snd_via82xx,snd_via82xx_modem,snd_pcm_oss,snd_mixer_oss,snd_ac97_codec,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              15328  1 snd
i2c_core               31892  1 i2c_viapro
amd64_agp              18184  1 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                42184  2 drm,amd64_agp
ndiswrapper           196380  0 
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
pata_via               16132  2 
ohci1394               37936  0 
ata_generic            12932  0 
ieee1394               96324  2 sbp2,ohci1394
via_rhine              30216  0 
mii                    13440  1 via_rhine
libata                177312  3 pata_acpi,pata_via,ata_generic
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  4 ndiswrapper,ehci_hcd,uhci_hcd
ssb                    40580  1 b43
thermal                23708  0 
processor              42156  3 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

ben@Gateway:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:03:25:14:93:2F

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         192.168.0.131
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            NULL(info.linux.driver)
  State:             disconnected
  Default:           no
  HW Address:        00:90:4B:C5:AA:9F

  Capabilities:
    Supported:       yes

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

ben@Gateway:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:14:93:2f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.131 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:c5:aa:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:25:7e:6c:8d:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

ben@Gateway:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ben@Gateway:~$ uname -a
Linux Gateway 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

ben@Gateway:~$ lsb_release -d
Description:	Ubuntu 8.10

ben@Gateway:~$ uname -mr
2.6.27-9-generic i686

---

### Post by kevdog on 2009-01-26
See this page for your available options:
[http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61](http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61)

---

### Post by Ayuthia on 2009-01-26
Accordig to lsmod, you have ndiswrapper and b43 running.  Because of this, the ndiswrapper module is most likely not running.

The question that I have is which module did you want to try to get working (b43 or ndiswrapper)?

I am not for sure about what guide you used for ndiswrapper.  If you can supply that information, it will help us see what we need to do to activate the module.  If you want to go this route, please let us know the guide along with ndiswrapper -l so that we can verify that it is set up fine.

---

### Post by Evil Overlord on 2009-01-26
> **Ayuthia said:**
> 
The question that I have is which module did you want to try to get working (b43 or ndiswrapper)?

I am not for sure about what guide you used for ndiswrapper.  If you can supply that information, it will help us see what we need to do to activate the module.

I'd rather get b43 working, if possible, just because it seems 'cleaner', but a) I find that I really don't understand this stuff well, and b) whatever works!

For ndiswrapper - I saw lots of info on the web that seemed very complicated.  What I did was to use Applications Add/Remove to install ndiswrapper, then point it at a copy of bcmwl5.inf that I had from the first go-round.

Ben

PS sorry about the formatting of the first post.  I thought I had it nice and clean, but I see now that it ended up cramped and mashed together.

---

### Post by Ayuthia on 2009-01-26
You can first try:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe b43
sudo /etc/init.d/network restart
sudo iwlist scan
```
Please let us know if produces any wireless sites.  If it does not, we can try the ndiswrapper version:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d/network restart
sudo iwlist scan
```

---

### Post by Evil Overlord on 2009-01-26
> **Ayuthia said:**
> You can first try:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe b43
sudo /etc/init.d/network restart
sudo iwlist scan
```
Please let us know if produces any wireless sites.  If it does not, we can try the ndiswrapper version:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d/network restart
sudo iwlist scan
```
When trying the first option, at line 3 I got command not found.  So, for good measure I just restarted the system.  No wireless sites (I know there are plenty). Results were either interface doesn't support scanning, or wlan0 no scan results.

With second option, command again not found, naturally.  System restart, and exactly the same - no sites, same scan results. 

Maybe a system restart is not enough?

---

### Post by Ayuthia on 2009-01-26
Just to verify the firmware is happy, can you post the results of:
```
dmesg|grep b43
```Usually a restart is not necessary when you do the modprobe commands for the b43 module.

---

### Post by Evil Overlord on 2009-01-26
ben@Gateway:~$ dmesg|grep b43
[    2.508051] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.906059] b43-phy0: Broadcom 4306 WLAN found
[   27.348000] input: b43-phy0 as /devices/virtual/input/input9
[   27.416051] firmware: requesting b43/ucode5.fw
[   27.512474] firmware: requesting b43/pcm5.fw
[   27.547607] firmware: requesting b43/b0g0initvals5.fw
[   27.570093] firmware: requesting b43/b0g0bsinitvals5.fw
[   27.824053] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   27.984223] Registered led device: b43-phy0::tx
[   27.984751] Registered led device: b43-phy0::rx
[   27.985381] Registered led device: b43-phy0::radio

I figured a full restart wasn't necessary, but when I couldn't get the network restart command to work, I figured it couldn't hurt.  Would disabling and re-enabling wireless work instead?

---

