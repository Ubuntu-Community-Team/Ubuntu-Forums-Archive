---
title: "Can't enable wireless using ndiswrapper."
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by rossmc92 on 2009-01-06
Hi

Just installed xubuntu 8.10 on my Medion MIM2120 laptop, however I'm having a very difficult time with the wireless. About 4 months ago I had a windows wireless driver installed and semi-running on ubuntu 8.04. It was picking up the routers signal, just not connecting.

now I've tried again using the latest ndiswrapper and this driver: [http://www1.medion.de/downloads/index.pl?op=detail&id=3017&type=treiber&lang=uk](http://www1.medion.de/downloads/index.pl?op=detail&id=3017&type=treiber&lang=uk) unfortunately this time it won't even pick up a signal from the router even though its installed.

I'm aware that it's not exactly the most supported wireless around for Linux but it really is important that I somehow get it to work, any helps appreciated.

---

### Post by kevdog on 2009-01-06
Lets back up a step, and lets get acquainted with your troubled hardware.

Can you post the results of:
lshw -C network
lspci -nnm

Thanks

---

### Post by rossmc92 on 2009-01-06
> **kevdog said:**
> Lets back up a step, and lets get acquainted with your troubled hardware.

Can you post the results of:
lshw -C network
lspci -nnm

Thanks

ross@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:7f:56:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.4 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: W89C33D 802.11 a/b/g BB/MAC
       vendor: Winbond Electronics Corp
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=128 maxlatency=32 mingnt=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:10:3a:ba:d4:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ross@ubuntu:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [2590]" -r04 "Mitac [1071]" "Device [8048]"
00:02.0 "VGA compatible controller [0300]" "Intel Corporation [8086]" "Mobile 915GM/GMS/910GML Express Graphics Controller [2592]" -r04 "Mitac [1071]" "Device [8048]"
00:02.1 "Display controller [0380]" "Intel Corporation [8086]" "Mobile 915GM/GMS/910GML Express Graphics Controller [2792]" -r04 "Mitac [1071]" "Device [8048]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [2668]" -r04 "Mitac [1071]" "Device [8048]"
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [2658]" -r04 "Mitac [1071]" "Device [8048]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [2659]" -r04 "Mitac [1071]" "Device [8048]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [265a]" -r04 "Mitac [1071]" "Device [8048]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [265c]" -r04 -p20 "Mitac [1071]" "Device [8048]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -rd4 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801FBM (ICH6M) LPC Interface Bridge [2641]" -r04 "Mitac [1071]" "Device [8048]"
00:1f.2 "IDE interface [0101]" "Intel Corporation [8086]" "82801FBM (ICH6M) SATA Controller [2653]" -r04 -p80 "Mitac [1071]" "Device [8048]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [266a]" -r04 "Mitac [1071]" "Device [8048]"
01:02.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCIxx21/x515 Cardbus Controller [8031]" "Mitac [1071]" "Device [8048]"
01:02.2 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "OHCI Compliant IEEE 1394 Host Controller [8032]" -p10 "Mitac [1071]" "Device [8048]"
01:04.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Mitac [1071]" "Device [8048]"
01:05.0 "Ethernet controller [0200]" "Winbond Electronics Corp [1050]" "W89C33D 802.11 a/b/g BB/MAC [0033]" "Winbond Electronics Corp [1050]" "W89C33D 802.11 a/b/g BB/MAC [0033]"

Thanks for the quick reply.

---

### Post by kevdog on 2009-01-06
Ive been providing wireless assistance now for almost 2 years and this is the first time I've run across a WinBOND chipset -- WOW!  Learn something everyday.

I'm going to assume the only possible way to get this up and running is with ndiswrapper -- however it probably won't work.  But we can try.  Winbond -- I'm not going to say its a piece of junk, but it probably is!!

Ok lets find out about your ndiswrapper install.

modinfo ndiswrapper
ndiswrapper -l
dmesg | grep ndis

---

### Post by rossmc92 on 2009-01-06
> **kevdog said:**
> Ive been providing wireless assistance now for almost 2 years and this is the first time I've run across a WinBOND chipset -- WOW!  Learn something everyday.

I'm going to assume the only possible way to get this up and running is with ndiswrapper -- however it probably won't work.  But we can try.  Winbond -- I'm not going to say its a piece of junk, but it probably is!!

Ok lets find out about your ndiswrapper install.

modinfo ndiswrapper
ndiswrapper -l
dmesg | grep ndis

ross@ubuntu:~$ modinfo ndiswrapper
filename:       /lib/modules/2.6.27-9-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.53
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     ED1F39AAE9904B93C47D2FD
depends:        usbcore
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)
ross@ubuntu:~$ ndiswrapper -l
netw33 : driver installed
	device (1050:0033) present

for some reason the terminal just didn't do anything when it came to 'dmesg | grep ndis', I'll try that agin in a minute.

---

### Post by rossmc92 on 2009-01-06
Yeah, still no result from 'dmesg | grep ndis'

---

### Post by kevdog on 2009-01-06
Did you 

sudo modprobe ndiswrapper


Then check dmesg | less for anything about your wireless interface.

---

### Post by rossmc92 on 2009-01-06
> **kevdog said:**
> Did you 

sudo modprobe ndiswrapper


Then check dmesg | less for anything about your wireless interface.


I've done sudo modprobe ndiswrapper many times, including just now but it just seems to hang and do nothing after I input the password for sudo. Is that supposed to happen?

In the meantime, heres the dmesg | less results;

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000f7df000 (usable)
[    0.000000]  BIOS-e820: 000000000f7e0000 - 000000000f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000000f7fffc0 - 000000000f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xf7df max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to f7df000 @ 7000-d000
[    0.000000] RAMDISK: 0f000000 - 0f7cef45
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 INSYDE)
[    0.000000] ACPI: RSDT 0F7FB1A4, 0038 (r1 INSYDE RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 0F7FFA80, 0074 (r1 INSYDE FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 0F7FB3C0, 46BC (r1 INSYDE SONOMA          1 INTL  2002:

---

### Post by kevdog on 2009-01-06
Do the modprobe statement and then post both just dmesg and lshw -C network and iwlist scan

---

### Post by rossmc92 on 2009-01-06
dmesg: ross@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000f7df000 (usable)
[    0.000000]  BIOS-e820: 000000000f7e0000 - 000000000f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000000f7fffc0 - 000000000f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xf7df max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to f7df000 @ 7000-d000
[    0.000000] RAMDISK: 0f000000 - 0f7cef45
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 INSYDE)
[    0.000000] ACPI: RSDT 0F7FB1A4, 0038 (r1 INSYDE RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 0F7FFA80, 0074 (r1 INSYDE FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 0F7FB3C0, 46BC (r1 INSYDE SONOMA          1 INTL  2002036)
[    0.000000] ACPI: FACS 0F7FFFC0, 0040
[    0.000000] ACPI: APIC 0F7FFB10, 0068 (r1 STUPID MAPIC_00 30307830 ABCD    10200)
[    0.000000] ACPI: HPET 0F7FFB80, 0038 (r1 INSYDE HPET_000 30303030 0000 30303030)
[    0.000000] ACPI: MCFG 0F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 0F7FB1DC, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 247MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0f7df000
[    0.000000]   low ram: 00000000 - 0f7df000
[    0.000000]   bootmap 00002000 - 00003efc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000f7df000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [000f000000 - 000f7cef45]          RAMDISK ==> [000f000000 - 000f7cef45]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000f7df
[    0.000000]   HighMem  0x0000f7df -> 0x0000f7df
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000f7df
[    0.000000] On node 0 totalpages: 63358
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 58837 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0 is invalid
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: f800000:f0700000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 62800
[    0.000000] Kernel command line: root=UUID=d8158e20-2755-4790-898f-073a5fce9400 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1296.743 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 237892k/253820k available (2572k kernel code, 15440k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0000000 - 0xff3fe000   ( 755 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcf7df000   ( 247 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 2593.48 BogoMIPS (lpj=5186972)
[    0.004041] Security Framework initialized
[    0.004052] SELinux:  Disabled at boot.
[    0.004082] AppArmor: AppArmor initialized
[    0.004093] Mount-cache hash table entries: 512
[    0.004327] Initializing cgroup subsys ns
[    0.004334] Initializing cgroup subsys cpuacct
[    0.004338] Initializing cgroup subsys memory
[    0.004360] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004365] CPU: L2 cache: 1024K
[    0.004378] Checking 'hlt' instruction... OK.
[    0.020686] SMP alternatives: switching to UP code
[    0.028008] ACPI: Core revision 20080609
[    0.030381] ACPI: Checking initramfs for custom DSDT
[    0.552283] ENABLING IO-APIC IRQs
[    0.552495] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.592188] CPU0: Intel(R) Celeron(R) M processor         1.30GHz stepping 08
[    0.596031] Brought up 1 CPUs
[    0.596031] Total of 1 processors activated (2593.48 BogoMIPS).
[    0.596031] CPU0 attaching sched-domain:
[    0.596031]  domain 0: span 0 level CPU
[    0.596031]   groups: 0
[    0.596031] net_namespace: 840 bytes
[    0.596031] Booting paravirtualized kernel on bare hardware
[    0.596031] Time:  1:13:25  Date: 01/07/09
[    0.596031] NET: Registered protocol family 16
[    0.596031] EISA bus registered
[    0.596031] ACPI: bus type pci registered
[    0.596031] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.596031] PCI: Not using MMCONFIG.
[    0.596031] PCI: PCI BIOS revision 2.10 entry at 0xea304, last bus=1
[    0.596031] PCI: Using configuration type 1 for base access
[    0.596031] ACPI: EC: Look up EC in DSDT
[    0.599231] ACPI: Interpreter enabled
[    0.599236] ACPI: (supports S0 S3 S4 S5)
[    0.599260] ACPI: Using IOAPIC for interrupt routing
[    0.599327] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.599415] ACPI Error (evregion-0315): No handler for Region [ERAM] (cec25028) [EmbeddedControl] [20080609]
[    0.599423] ACPI Error (exfldio-0291): Region EmbeddedControl(3) has no handler [20080609]
[    0.599432] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.BAT0._STA] (Node cec23528), AE_NOT_EXIST
[    0.599476] ACPI Error (uteval-0232): Method execution failed [\_SB_.BAT0._STA] (Node cec23528), AE_NOT_EXIST
[    0.600365] ACPI Error (evregion-0315): No handler for Region [ERAM] (cec25028) [EmbeddedControl] [20080609]
[    0.600373] ACPI Error (exfldio-0291): Region EmbeddedControl(3) has no handler [20080609]
[    0.600381] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.BAT0._STA] (Node cec23528), AE_NOT_EXIST
[    0.600424] ACPI Error (uteval-0232): Method execution failed [\_SB_.BAT0._STA] (Node cec23528), AE_NOT_EXIST
[    0.600449] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.600453] PCI: Using MMCONFIG for extended config space
[    0.601322] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.624657] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.624662] ACPI: EC: driver started in interrupt mode
[    0.624740] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.624879] PCI: 0000:00:02.0 reg 10 32bit mmio: [d0000000, d007ffff]
[    0.624886] PCI: 0000:00:02.0 reg 14 io port: [e000, e007]
[    0.624893] PCI: 0000:00:02.0 reg 18 32bit mmio: [a0000000, afffffff]
[    0.624899] PCI: 0000:00:02.0 reg 1c 32bit mmio: [d0080000, d00bffff]
[    0.624936] PCI: 0000:00:02.1 reg 10 32bit mmio: [d0100000, d017ffff]
[    0.625058] PCI: 0000:00:1b.0 reg 10 64bit mmio: [d0180000, d0183fff]
[    0.625114] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.625123] pci 0000:00:1b.0: PME# disabled
[    0.625171] PCI: 0000:00:1d.0 reg 20 io port: [1200, 121f]
[    0.625239] PCI: 0000:00:1d.1 reg 20 io port: [1220, 123f]
[    0.625305] PCI: 0000:00:1d.2 reg 20 io port: [1240, 125f]
[    0.625377] PCI: 0000:00:1d.7 reg 10 32bit mmio: [0, 3ff]
[    0.625437] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.625444] pci 0000:00:1d.7: PME# disabled
[    0.625589] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.625598] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.625605] pci 0000:00:1f.0: quirk: region 1300-133f claimed by ICH6 GPIO
[    0.625645] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[    0.625655] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[    0.625664] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[    0.625673] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[    0.625683] PCI: 0000:00:1f.2 reg 20 io port: [1100, 110f]
[    0.625717] pci 0000:00:1f.2: PME# supported from D3hot
[    0.625723] pci 0000:00:1f.2: PME# disabled
[    0.625783] PCI: 0000:00:1f.3 reg 20 io port: [1400, 141f]
[    0.625870] PCI: 0000:01:02.0 reg 10 32bit mmio: [0, fff]
[    0.625893] pci 0000:01:02.0: supports D1
[    0.625896] pci 0000:01:02.0: supports D2
[    0.625899] pci 0000:01:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.625907] pci 0000:01:02.0: PME# disabled
[    0.625953] PCI: 0000:01:02.2 reg 10 32bit mmio: [fedff800, fedfffff]
[    0.625964] PCI: 0000:01:02.2 reg 14 32bit mmio: [cc00c000, cc00ffff]
[    0.626028] pci 0000:01:02.2: supports D1
[    0.626031] pci 0000:01:02.2: supports D2
[    0.626034] pci 0000:01:02.2: PME# supported from D0 D1 D2 D3hot
[    0.626041] pci 0000:01:02.2: PME# disabled
[    0.626096] PCI: 0000:01:04.0 reg 10 io port: [c200, c2ff]
[    0.626108] PCI: 0000:01:04.0 reg 14 32bit mmio: [cc000200, cc0002ff]
[    0.626167] pci 0000:01:04.0: supports D1
[    0.626170] pci 0000:01:04.0: supports D2
[    0.626173] pci 0000:01:04.0: PME# supported from D1 D2 D3hot D3cold
[    0.626180] pci 0000:01:04.0: PME# disabled
[    0.626225] PCI: 0000:01:05.0 reg 10 io port: [c000, c0ff]
[    0.626236] PCI: 0000:01:05.0 reg 14 io port: [c100, c17f]
[    0.626247] PCI: 0000:01:05.0 reg 18 32bit mmio: [cc000000, cc0001ff]
[    0.626299] pci 0000:01:05.0: supports D1
[    0.626302] pci 0000:01:05.0: PME# supported from D1 D3hot
[    0.626309] pci 0000:01:05.0: PME# disabled
[    0.626362] pci 0000:00:1e.0: transparent bridge
[    0.626368] PCI: bridge 0000:00:1e.0 io port: [c000, dfff]
[    0.626375] PCI: bridge 0000:00:1e.0 32bit mmio: [cc000000, cfffffff]
[    0.626384] PCI: bridge 0000:00:1e.0 64bit mmio pref: [9c000000, 9fffffff]
[    0.626422] bus 00 -> node 0
[    0.626433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.627053] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.633565] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.633733] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.633895] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.634057] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.634220] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.634382] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.634548] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.634711] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.634986] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.635040] pnp: PnP ACPI init
[    0.635051] ACPI: bus type pnp registered
[    0.638600] pnp: PnP ACPI: found 9 devices
[    0.638604] ACPI: ACPI bus type pnp unregistered
[    0.638610] PnPBIOS: Disabled by ACPI PNP
[    0.639117] PCI: Using ACPI for IRQ routing
[    0.639283] NET: Registered protocol family 8
[    0.639283] NET: Registered protocol family 20
[    0.639283] NetLabel: Initializing
[    0.639283] NetLabel:  domain hash size = 128
[    0.639283] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.639283] NetLabel:  unlabeled traffic allowed by default
[    0.639283] hpet clockevent registered
[    0.639283] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.639283] hpet0: 3 64-bit timers, 14318180 Hz
[    0.640766] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.640771]    actual entries 65620
[    0.640920] AppArmor: AppArmor Filesystem Enabled
[    0.640967] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.640967] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.640967] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.640967] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.640967] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.640967] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.640967] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.640967] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.640967] system 00:05: ioport range 0x3e0-0x3e1 has been reserved
[    0.640967] system 00:05: ioport range 0x3f8-0x3ff has been reserved
[    0.640967] system 00:05: ioport range 0x600-0x60f has been reserved
[    0.640967] system 00:05: ioport range 0x680-0x6ff has been reserved
[    0.640967] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.640967] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.640967] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.640967] system 00:05: ioport range 0x1640-0x164f has been reserved
[    0.640967] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[    0.640967] system 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.640967] system 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.640967] system 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.640967] system 00:05: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.677353] pci 0000:01:02.0: CardBus bridge, secondary bus 0000:02
[    0.677357] pci 0000:01:02.0:   IO window: 0x00c400-0x00c4ff
[    0.677364] pci 0000:01:02.0:   IO window: 0x00c800-0x00c8ff
[    0.677372] pci 0000:01:02.0:   PREFETCH window: 0x9c000000-0x9fffffff
[    0.677380] pci 0000:01:02.0:   MEM window: 0x14000000-0x17ffffff
[    0.677387] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.677392] pci 0000:00:1e.0:   IO window: 0xc000-0xdfff
[    0.677400] pci 0000:00:1e.0:   MEM window: 0xcc000000-0xcfffffff
[    0.677407] pci 0000:00:1e.0:   PREFETCH window: 0x0000009c000000-0x0000009fffffff
[    0.677428] pci 0000:00:1e.0: setting latency timer to 64
[    0.678580] pci 0000:01:02.0: power state changed by ACPI to D0
[    0.678597] pci 0000:01:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.678606] bus: 00 index 0 io port: [0, ffff]
[    0.678609] bus: 00 index 1 mmio: [0, ffffffff]
[    0.678613] bus: 01 index 0 io port: [c000, dfff]
[    0.678616] bus: 01 index 1 mmio: [cc000000, cfffffff]
[    0.678620] bus: 01 index 2 mmio: [9c000000, 9fffffff]
[    0.678623] bus: 01 index 3 io port: [0, ffff]
[    0.678626] bus: 01 index 4 mmio: [0, ffffffff]
[    0.678630] bus: 02 index 0 io port: [c400, c4ff]
[    0.678633] bus: 02 index 1 io port: [c800, c8ff]
[    0.678636] bus: 02 index 2 mmio: [9c000000, 9fffffff]
[    0.678640] bus: 02 index 3 mmio: [14000000, 17ffffff]
[    0.678655] NET: Registered protocol family 2
[    0.678849] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.679141] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.679199] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.679261] TCP: Hash tables configured (established 8192 bind 8192)
[    0.679266] TCP reno registered
[    0.679374] NET: Registered protocol family 1
[    0.679535] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.187196]  it is
[    1.736452] Freeing initrd memory: 7995k freed
[    1.737531] audit: initializing netlink socket (disabled)
[    1.737558] type=2000 audit(1231290805.736:1): initialized
[    1.747066] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.750561] VFS: Disk quotas dquot_6.5.1
[    1.750699] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.750871] msgmni has been set to 480
[    1.751065] io scheduler noop registered
[    1.751070] io scheduler anticipatory registered
[    1.751074] io scheduler deadline registered
[    1.751092] io scheduler cfq registered (default)
[    1.751115] pci 0000:00:02.0: Boot video device
[    1.751676] isapnp: Scanning for PnP cards...
[    2.105685] isapnp: No Plug & Play device found
[    2.160295] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.163606] brd: module loaded
[    2.163729] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.163925] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.170778] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.174166] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.174175] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.174179] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.174183] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.174187] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.174871] mice: PS/2 mouse device common for all mice
[    2.175096] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.175131] rtc0: alarms up to one month, y3k, hpet irqs
[    2.175304] EISA: Probing bus 0 at eisa.0
[    2.175314] Cannot allocate resource for EISA slot 1
[    2.175348] EISA: Detected 0 cards.
[    2.175353] cpuidle: using governor ladder
[    2.175356] cpuidle: using governor menu
[    2.176118] TCP cubic registered
[    2.176163] Using IPI No-Shortcut mode
[    2.176480] registered taskstats version 1
[    2.176657]   Magic number: 9:762:204
[    2.176722] tty ttyt2: hash matches
[    2.176892] rtc_cmos 00:06: setting system clock to 2009-01-07 01:13:26 UTC (1231290806)
[    2.176897] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.176900] EDD information not available.
[    2.177199] Freeing unused kernel memory: 424k freed
[    2.177272] Write protecting the kernel text: 2576k
[    2.177315] Write protecting the kernel read-only data: 936k
[    2.181596] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.475108] fuse init (API version 7.9)
[    2.728198] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.728287] processor ACPI0007:00: registered as cooling_device0
[    2.728293] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.519042] usbcore: registered new interface driver usbfs
[    3.519081] usbcore: registered new interface driver hub
[    3.528828] usbcore: registered new device driver usb
[    3.542214] No dock devices found.
[    3.546445] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    3.546461] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.546480] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.546485] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.546568] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.550471] ehci_hcd 0000:00:1d.7: debug port 1
[    3.550480] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.550499] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x10000000
[    3.558204] USB Universal Host Controller Interface driver v3.0
[    3.582028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.582277] usb usb1: configuration #1 chosen from 1 choice
[    3.582330] hub 1-0:1.0: USB hub found
[    3.582344] hub 1-0:1.0: 6 ports detected
[    3.634547] SCSI subsystem initialized
[    3.671154] 8139too Fast Ethernet driver 0.9.28
[    3.699613] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.699628] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.699633] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.699669] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.699705] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001200
[    3.699860] usb usb2: configuration #1 chosen from 1 choice
[    3.699900] hub 2-0:1.0: USB hub found
[    3.699912] hub 2-0:1.0: 2 ports detected
[    3.795435] libata version 3.00 loaded.
[    3.801028] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.801043] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.801049] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.801093] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.801137] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001220
[    3.801285] usb usb3: configuration #1 chosen from 1 choice
[    3.801325] hub 3-0:1.0: USB hub found
[    3.801336] hub 3-0:1.0: 2 ports detected
[    3.904430] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.904446] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.904452] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.904489] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.904532] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001240
[    3.904680] usb usb4: configuration #1 chosen from 1 choice
[    3.904728] hub 4-0:1.0: USB hub found
[    3.904740] hub 4-0:1.0: 2 ports detected
[    4.008633] 8139too 0000:01:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.009673] eth0: RealTek RTL8139 at 0xc200, 00:40:d0:7f:56:20, IRQ 20
[    4.009677] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.014411] ohci1394 0000:01:02.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    4.064195] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fedff800-fedfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.065373] ata_piix 0000:00:1f.2: version 2.12
[    4.065395] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.065401] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.065688] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.220048] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.221097] scsi0 : ata_piix
[    4.221263] scsi1 : ata_piix
[    4.222826] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    4.222831] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    4.384327] ata1.00: ATA-6: WDC WD400UE-22HCT0, 09.07D09, max UDMA/100
[    4.384333] ata1.00: 78140160 sectors, multi 16: LBA 
[    4.384337] ata1.00: applying bridge limits
[    4.392407] ata1.00: configured for UDMA/100
[    4.470311] Marking TSC unstable due to TSC halts in idle
[    4.556483] ata2.00: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CL02, max UDMA/33
[    4.572424] ata2.00: configured for UDMA/33
[    4.572595] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400UE-22HC 09.0 PQ: 0 ANSI: 5
[    4.576406] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CL02 PQ: 0 ANSI: 5
[    4.613342] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.613397] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.641869] Driver 'sd' needs updating - please use bus_type methods
[    4.644886] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.644926] sd 0:0:0:0: [sda] Write Protect is off
[    4.644930] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.644991] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.645113] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.645144] sd 0:0:0:0: [sda] Write Protect is off
[    4.645148] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.645205] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.645211]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.922255]  sda1 sda2 < sda5 >
[    4.955081] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.969465] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.969473] Uniform CD-ROM driver Revision: 3.20
[    4.969608] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.294822] PM: Starting manual resume from disk
[    5.294828] PM: Resume from partition 8:5
[    5.294831] PM: Checking hibernation image.
[    5.295067] PM: Resume from disk failed.
[    5.325278] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.325285] EXT3-fs: write access will be enabled during recovery.
[    5.340220] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d00100337786]
[   10.296020] kjournald starting.  Commit interval 5 seconds
[   10.296042] EXT3-fs: recovery complete.
[   10.323315] EXT3-fs: mounted filesystem with ordered data mode.
[   18.984465] udevd version 124 started
[   20.715519] iTCO_vendor_support: vendor-support=0
[   20.776934] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   20.777105] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   20.777308] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.882204] Linux agpgart interface v0.103
[   21.055474] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   21.108707] intel_rng: Firmware space is locked read-only. If you can't or
[   21.108710] intel_rng: don't want to disable this in firmware setup, and if
[   21.108712] intel_rng: you are certain that your system has a functional
[   21.108714] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   21.179233] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   21.179510] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   21.201094] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[   21.297486] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   21.308072] ACPI: Power Button (FF) [PWRF]
[   21.308239] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   21.320042] ACPI: Sleep Button (CM) [SBTN]
[   21.320218] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   21.322113] ACPI: Lid Switch [LID]
[   21.362377] ACPI: AC Adapter [AC] (on-line)
[   21.449721] ACPI: Battery Slot [BAT0] (battery present)
[   21.713924] Yenta: CardBus bridge found at 0000:01:02.0 [1071:8048]
[   21.713954] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.713958] Yenta: Routing CardBus interrupts to PCI
[   21.713965] Yenta TI: socket 0000:01:02.0, mfunc 0x01ac1b22, devctl 0x64
[   21.944843] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   21.944850] Socket status: 30000006
[   21.944855] Yenta: Raising subordinate bus# of parent bus (#01) from #02 to #05
[   21.944865] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xdfff
[   21.944869] cs: IO port probe 0xc000-0xdfff: clean.
[   21.945520] pcmcia: parent PCI bridge Memory window: 0xcc000000 - 0xcfffffff
[   21.945524] pcmcia: parent PCI bridge Memory window: 0x9c000000 - 0x9fffffff
[   22.415772] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   22.458832] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input6
[   23.131759] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7
[   23.140051] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.289969] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.290009] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.394956] cs: IO port probe 0x100-0x3af: clean.
[   26.396752] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   26.397465] cs: IO port probe 0x820-0x8ff: clean.
[   26.398088] cs: IO port probe 0xc00-0xcf7: clean.
[   26.398930] cs: IO port probe 0xa00-0xaff: clean.
[   26.685633] loop: module loaded
[   26.781757] lp: driver loaded but no devices found
[   27.135027] Adding 722884k swap on /dev/sda5.  Priority:-1 extents:1 across:722884k
[   27.732357] EXT3 FS on sda1, internal journal
[   29.121281] type=1505 audit(1231290833.543:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3829
[   29.121659] type=1505 audit(1231290833.543:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3829
[   29.601386] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.447333] ACPI: WMI: Mapper loaded
[   31.733106] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   31.835049] apm: BIOS not found.
[   32.064079] ppdev: user-space parallel port driver
[   34.164090] Bluetooth: Core ver 2.13
[   34.166644] NET: Registered protocol family 31
[   34.166653] Bluetooth: HCI device and connection manager initialized
[   34.166658] Bluetooth: HCI socket layer initialized
[   34.205562] Bluetooth: L2CAP ver 2.11
[   34.205573] Bluetooth: L2CAP socket layer initialized
[   34.264183] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.264193] Bluetooth: BNEP filters: protocol multicast
[   34.333355] Bridge firewalling registered
[   34.333833] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   34.397255] Bluetooth: RFCOMM socket layer initialized
[   34.397576] Bluetooth: RFCOMM TTY layer initialized
[   34.397585] Bluetooth: RFCOMM ver 1.10
[   34.398691] Bluetooth: SCO (Voice Link) ver 0.6
[   34.398700] Bluetooth: SCO socket layer initialized
[   38.512425] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   38.852564] [drm] Initialized drm 1.1.0 20060810
[   38.896193] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   38.896208] pci 0000:00:02.0: setting latency timer to 64
[   38.896976] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.200979] NET: Registered protocol family 17
[   46.310560] NET: Registered protocol family 10
[   46.312667] lo: Disabled Privacy Extensions
[   56.716065] eth0: no IPv6 routers present
[ 1085.230478] eth0: link down
[ 1089.903195] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1090.199528] eth0: link down
[ 1090.799171] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1090.967911] eth0: link down
[ 1091.375157] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1091.479076] eth0: link down
[ 1092.015143] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1092.119672] eth0: link down
[ 1092.271135] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1092.375250] eth0: link down
[ 1092.463132] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1092.560524] nm-applet[5169]: segfault at 0 ip 0805624d sp bfea0dd0 error 4 in nm-applet[8048000+42000]
[ 1092.630835] eth0: link down
[ 1092.719121] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1092.951949] eth0: link down
[ 1096.431053] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1096.535021] eth0: link down
[ 1096.879042] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1097.047826] eth0: link down
[ 1097.455036] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1097.558989] eth0: link down
[ 1098.415005] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1099.030224] eth0: link down
[ 1099.630982] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1099.734720] eth0: link down
[ 1100.206969] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1100.317248] eth0: link down
[ 1101.422944] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1101.846551] eth0: link down
[ 1102.574921] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1102.742725] eth0: link down
[ 1104.046887] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1104.215598] eth0: link down
[ 1104.366874] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1104.471179] eth0: link down
[ 1104.558868] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1104.662866] eth0: link down
[ 1104.814865] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1105.046237] eth0: link down
[ 1105.262851] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1105.495145] eth0: link down
[ 1106.158844] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1106.391326] eth0: link down
[ 1106.478833] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1106.774696] eth0: link down
[ 1107.374814] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1107.479186] eth0: link down
[ 1108.014796] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1108.118144] eth0: link down
[ 1108.718781] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1108.886531] eth0: link down
[ 1109.102779] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1109.206005] eth0: link down
[ 1109.742758] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1109.974394] eth0: link down
[ 1110.126760] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1110.229979] eth0: link down
[ 1110.574738] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1110.870567] eth0: link down
[ 1111.150728] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1111.253934] eth0: link down
[ 1111.534725] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1111.638949] eth0: link down
[ 1111.790719] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1111.958430] eth0: link down
[ 1112.046711] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1112.150123] eth0: link down
[ 1112.238700] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1112.471238] eth0: link down
[ 1112.686695] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1112.790715] eth0: link down
[ 1114.714164] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1386.621370] eth0: link down
[ 1388.158595] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1694.252047] eth0: link down
[ 2021.966183] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3045.352052] usb 1-1: new high speed USB device using ehci_hcd and address 2
[ 3045.486616] usb 1-1: configuration #1 chosen from 2 choices
[ 3045.682341] eth0: link down
[ 3047.187335] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3048.183641] usbcore: registered new interface driver libusual
[ 3048.980134] Initializing USB Mass Storage driver...
[ 3048.982431] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3048.987718] usbcore: registered new interface driver usb-storage
[ 3048.988077] USB Mass Storage support registered.
[ 3048.988497] usb-storage: device found at 2
[ 3048.988505] usb-storage: waiting for device to settle before scanning
[ 3053.988401] usb-storage: device scan complete
[ 3053.989637] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3054.003352] sd 2:0:0:0: [sdb] 3999743 512-byte hardware sectors (2048 MB)
[ 3054.004975] sd 2:0:0:0: [sdb] Write Protect is off
[ 3054.004983] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3054.004987] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3054.007595] sd 2:0:0:0: [sdb] 3999743 512-byte hardware sectors (2048 MB)
[ 3054.009100] sd 2:0:0:0: [sdb] Write Protect is off
[ 3054.009108] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3054.009112] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3054.009636]  sdb: sdb1 sdb2
[ 3054.037064] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 3054.037624] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 4741.954193] usb 1-1: USB disconnect, address 2
[ 4743.854726] scsi 2:0:0:0: rejecting I/O to dead device
[ 8134.344660] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 8134.987244] ndiswrapper: driver netw33 (Winbond Electronics Corp.,07/26/2005,1.2.81.1001) loaded
[ 8134.989311] ndiswrapper 0000:01:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 8134.989598] ndiswrapper (NdisMRegisterInterrupt:1942): shared but dynamic interrupt!
[ 8134.989627] ndiswrapper: using IRQ 21
[ 8136.512064] BUG: unable to handle kernel NULL pointer dereference at 00000024
[ 8136.512077] IP: [<c02f046f>] __netif_schedule+0xf/0x60
[ 8136.512089] *pde = 00000000 
[ 8136.512095] Oops: 0002 [#1] SMP 
[ 8136.512100] Modules linked in: ndiswrapper(+) nls_iso8859_1 nls_cp437 vfat fat usb_storage libusual ipv6 af_packet i915 drm sco rfcomm bridge stp bnep l2cap bluetooth ppdev cpufreq_conservative cpufreq_stats cpufreq_ondemand freq_table cpufreq_powersave cpufreq_userspace wmi pci_slot container sbs sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport loop joydev pcmcia snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy evdev snd_seq_oss video snd_seq_midi output snd_rawmidi snd_seq_midi_event snd_seq serio_raw snd_timer snd_seq_device psmouse yenta_socket rsrc_nonstatic pcmcia_core snd battery ac button soundcore intel_agp pcspkr snd_page_alloc agpgart iTCO_wdt iTCO_vendor_support ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg pata_acpi ahci ata_generic 8139cp ata_piix ohci1394 libata 8139too mii ieee1394 scsi_mod uhci_hcd ehci_hcd dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 8136.512214] 
[ 8136.512219] Pid: 7332, comm: ntos_wq Tainted: P          (2.6.27-9-generic #1)
[ 8136.512223] EIP: 0060:[<c02f046f>] EFLAGS: 00010246 CPU: 0
[ 8136.512229] EIP is at __netif_schedule+0xf/0x60
[ 8136.512233] EAX: 00000024 EBX: d0732848 ECX: 00000000 EDX: ffffffff
[ 8136.512237] ESI: d0732848 EDI: d07321a0 EBP: c16b5e90 ESP: c16b5e8c
[ 8136.512241]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[ 8136.512245] Process ntos_wq (pid: 7332, ti=c16b4000 task=c163d7f0 task.ti=c16b4000)
[ 8136.512249] Stack: d0732848 c16b5f04 d0760e58 c02e3931 00000067 00000001 c8936480 cec03900 
[ 8136.512260]        00000028 00000067 c16b5ed0 c02e3a04 c16b5ed0 00000246 00000000 cecb8c00 
[ 8136.512270]        00000067 c16b5ef8 c025d3e0 00000001 c16b5ee8 00000028 00000246 00000042 
[ 8136.512280] Call Trace:
[ 8136.512291]  [<d0760e58>] ? NdisMIndicateStatus+0x298/0x3a0 [ndiswrapper]
[ 8136.512321]  [<c02e3931>] ? raw_pci_read+0x81/0x90
[ 8136.512330]  [<c02e3a04>] ? pci_read+0x34/0x40
[ 8136.512336]  [<c025d3e0>] ? pci_bus_read_config_byte+0x60/0x70
[ 8136.512366]  [<d0767aad>] ? kdpc_worker+0xcd/0x150 [ndiswrapper]
[ 8136.512405]  [<d07679e0>] ? kdpc_worker+0x0/0x150 [ndiswrapper]
[ 8136.512428]  [<c0143645>] ? run_workqueue+0x95/0x160
[ 8136.512451]  [<c0147576>] ? finish_wait+0x16/0x70
[ 8136.512457]  [<c01438e8>] ? worker_thread+0x88/0xf0
[ 8136.512463]  [<c01474b0>] ? autoremove_wake_function+0x0/0x50
[ 8136.512469]  [<c0143860>] ? worker_thread+0x0/0xf0
[ 8136.512475]  [<c0147141>] ? kthread+0x41/0x80
[ 8136.512481]  [<c0147100>] ? kthread+0x0/0x80
[ 8136.512487]  [<c0105297>] ? kernel_thread_helper+0x7/0x10
[ 8136.512494]  =======================
[ 8136.512497] Code: 8d 74 26 00 eb b8 8d b6 00 00 00 00 83 f1 0c 90 8d 74 26 00 eb 99 8d b6 00 00 00 00 55 89 e5 53 e8 37 4e e1 ff 89 c1 8d 40 24 90 <0f> ba 28 01 19 d2 85 d2 75 41 9c 58 90 8d b4 26 00 00 00 00 89 
[ 8136.512552] EIP: [<c02f046f>] __netif_schedule+0xf/0x60 SS:ESP 0068:c16b5e8c
[ 8136.512562] ---[ end trace a64b78ee28c70fbc ]---

ishw -C network: ross@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:7f:56:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.102 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Ethernet controller
       product: W89C33D 802.11 a/b/g BB/MAC
       vendor: Winbond Electronics Corp
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=128 maxlatency=32 mingnt=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:23:f5:a5:c6:de
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

iwlist scan: ross@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

Hope I done that right.

---

### Post by rossmc92 on 2009-01-06
dmesg: ross@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000f7df000 (usable)
[    0.000000]  BIOS-e820: 000000000f7e0000 - 000000000f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000000f7fffc0 - 000000000f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xf7df max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to f7df000 @ 7000-d000
[    0.000000] RAMDISK: 0f000000 - 0f7cef45
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 INSYDE)
[    0.000000] ACPI: RSDT 0F7FB1A4, 0038 (r1 INSYDE RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 0F7FFA80, 0074 (r1 INSYDE FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 0F7FB3C0, 46BC (r1 INSYDE SONOMA          1 INTL  2002036)
[    0.000000] ACPI: FACS 0F7FFFC0, 0040
[    0.000000] ACPI: APIC 0F7FFB10, 0068 (r1 STUPID MAPIC_00 30307830 ABCD    10200)
[    0.000000] ACPI: HPET 0F7FFB80, 0038 (r1 INSYDE HPET_000 30303030 0000 30303030)
[    0.000000] ACPI: MCFG 0F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 0F7FB1DC, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 247MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0f7df000
[    0.000000]   low ram: 00000000 - 0f7df000
[    0.000000]   bootmap 00002000 - 00003efc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000f7df000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [000f000000 - 000f7cef45]          RAMDISK ==> [000f000000 - 000f7cef45]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000f7df
[    0.000000]   HighMem  0x0000f7df -> 0x0000f7df
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000f7df
[    0.000000] On node 0 totalpages: 63358
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 58837 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0 is invalid
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: f800000:f0700000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 62800
[    0.000000] Kernel command line: root=UUID=d8158e20-2755-4790-898f-073a5fce9400 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1296.743 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 237892k/253820k available (2572k kernel code, 15440k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0000000 - 0xff3fe000   ( 755 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcf7df000   ( 247 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 2593.48 BogoMIPS (lpj=5186972)
[    0.004041] Security Framework initialized
[    0.004052] SELinux:  Disabled at boot.
[    0.004082] AppArmor: AppArmor initialized
[    0.004093] Mount-cache hash table entries: 512
[    0.004327] Initializing cgroup subsys ns
[    0.004334] Initializing cgroup subsys cpuacct
[    0.004338] Initializing cgroup subsys memory
[    0.004360] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004365] CPU: L2 cache: 1024K
[    0.004378] Checking 'hlt' instruction... OK.
[    0.020686] SMP alternatives: switching to UP code
[    0.028008] ACPI: Core revision 20080609
[    0.030381] ACPI: Checking initramfs for custom DSDT
[    0.552283] ENABLING IO-APIC IRQs
[    0.552495] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.592188] CPU0: Intel(R) Celeron(R) M processor         1.30GHz stepping 08
[    0.596031] Brought up 1 CPUs
[    0.596031] Total of 1 processors activated (2593.48 BogoMIPS).
[    0.596031] CPU0 attaching sched-domain:
[    0.596031]  domain 0: span 0 level CPU
[    0.596031]   groups: 0
[    0.596031] net_namespace: 840 bytes
[    0.596031] Booting paravirtualized kernel on bare hardware
[    0.596031] Time:  1:13:25  Date: 01/07/09
[    0.596031] NET: Registered protocol family 16
[    0.596031] EISA bus registered
[    0.596031] ACPI: bus type pci registered
[    0.596031] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.596031] PCI: Not using MMCONFIG.
[    0.596031] PCI: PCI BIOS revision 2.10 entry at 0xea304, last bus=1
[    0.596031] PCI: Using configuration type 1 for base access
[    0.596031] ACPI: EC: Look up EC in DSDT
[    0.599231] ACPI: Interpreter enabled
[    0.599236] ACPI: (supports S0 S3 S4 S5)
[    0.599260] ACPI: Using IOAPIC for interrupt routing
[    0.599327] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.599415] ACPI Error (evregion-0315): No handler for Region [ERAM] (cec25028) [EmbeddedControl] [20080609]
[    0.599423] ACPI Error (exfldio-0291): Region EmbeddedControl(3) has no handler [20080609]
[    0.599432] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.BAT0._STA] (Node cec23528), AE_NOT_EXIST
[    0.599476] ACPI Error (uteval-0232): Method execution failed [\_SB_.BAT0._STA] (Node cec23528), AE_NOT_EXIST
[    0.600365] ACPI Error (evregion-0315): No handler for Region [ERAM] (cec25028) [EmbeddedControl] [20080609]
[    0.600373] ACPI Error (exfldio-0291): Region EmbeddedControl(3) has no handler [20080609]
[    0.600381] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.BAT0._STA] (Node cec23528), AE_NOT_EXIST
[    0.600424] ACPI Error (uteval-0232): Method execution failed [\_SB_.BAT0._STA] (Node cec23528), AE_NOT_EXIST
[    0.600449] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.600453] PCI: Using MMCONFIG for extended config space
[    0.601322] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.624657] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.624662] ACPI: EC: driver started in interrupt mode
[    0.624740] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.624879] PCI: 0000:00:02.0 reg 10 32bit mmio: [d0000000, d007ffff]
[    0.624886] PCI: 0000:00:02.0 reg 14 io port: [e000, e007]
[    0.624893] PCI: 0000:00:02.0 reg 18 32bit mmio: [a0000000, afffffff]
[    0.624899] PCI: 0000:00:02.0 reg 1c 32bit mmio: [d0080000, d00bffff]
[    0.624936] PCI: 0000:00:02.1 reg 10 32bit mmio: [d0100000, d017ffff]
[    0.625058] PCI: 0000:00:1b.0 reg 10 64bit mmio: [d0180000, d0183fff]
[    0.625114] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.625123] pci 0000:00:1b.0: PME# disabled
[    0.625171] PCI: 0000:00:1d.0 reg 20 io port: [1200, 121f]
[    0.625239] PCI: 0000:00:1d.1 reg 20 io port: [1220, 123f]
[    0.625305] PCI: 0000:00:1d.2 reg 20 io port: [1240, 125f]
[    0.625377] PCI: 0000:00:1d.7 reg 10 32bit mmio: [0, 3ff]
[    0.625437] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.625444] pci 0000:00:1d.7: PME# disabled
[    0.625589] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.625598] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.625605] pci 0000:00:1f.0: quirk: region 1300-133f claimed by ICH6 GPIO
[    0.625645] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[    0.625655] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[    0.625664] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[    0.625673] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[    0.625683] PCI: 0000:00:1f.2 reg 20 io port: [1100, 110f]
[    0.625717] pci 0000:00:1f.2: PME# supported from D3hot
[    0.625723] pci 0000:00:1f.2: PME# disabled
[    0.625783] PCI: 0000:00:1f.3 reg 20 io port: [1400, 141f]
[    0.625870] PCI: 0000:01:02.0 reg 10 32bit mmio: [0, fff]
[    0.625893] pci 0000:01:02.0: supports D1
[    0.625896] pci 0000:01:02.0: supports D2
[    0.625899] pci 0000:01:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.625907] pci 0000:01:02.0: PME# disabled
[    0.625953] PCI: 0000:01:02.2 reg 10 32bit mmio: [fedff800, fedfffff]
[    0.625964] PCI: 0000:01:02.2 reg 14 32bit mmio: [cc00c000, cc00ffff]
[    0.626028] pci 0000:01:02.2: supports D1
[    0.626031] pci 0000:01:02.2: supports D2
[    0.626034] pci 0000:01:02.2: PME# supported from D0 D1 D2 D3hot
[    0.626041] pci 0000:01:02.2: PME# disabled
[    0.626096] PCI: 0000:01:04.0 reg 10 io port: [c200, c2ff]
[    0.626108] PCI: 0000:01:04.0 reg 14 32bit mmio: [cc000200, cc0002ff]
[    0.626167] pci 0000:01:04.0: supports D1
[    0.626170] pci 0000:01:04.0: supports D2
[    0.626173] pci 0000:01:04.0: PME# supported from D1 D2 D3hot D3cold
[    0.626180] pci 0000:01:04.0: PME# disabled
[    0.626225] PCI: 0000:01:05.0 reg 10 io port: [c000, c0ff]
[    0.626236] PCI: 0000:01:05.0 reg 14 io port: [c100, c17f]
[    0.626247] PCI: 0000:01:05.0 reg 18 32bit mmio: [cc000000, cc0001ff]
[    0.626299] pci 0000:01:05.0: supports D1
[    0.626302] pci 0000:01:05.0: PME# supported from D1 D3hot
[    0.626309] pci 0000:01:05.0: PME# disabled
[    0.626362] pci 0000:00:1e.0: transparent bridge
[    0.626368] PCI: bridge 0000:00:1e.0 io port: [c000, dfff]
[    0.626375] PCI: bridge 0000:00:1e.0 32bit mmio: [cc000000, cfffffff]
[    0.626384] PCI: bridge 0000:00:1e.0 64bit mmio pref: [9c000000, 9fffffff]
[    0.626422] bus 00 -> node 0
[    0.626433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.627053] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.633565] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.633733] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.633895] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.634057] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.634220] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.634382] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.634548] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.634711] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.634986] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.635040] pnp: PnP ACPI init
[    0.635051] ACPI: bus type pnp registered
[    0.638600] pnp: PnP ACPI: found 9 devices
[    0.638604] ACPI: ACPI bus type pnp unregistered
[    0.638610] PnPBIOS: Disabled by ACPI PNP
[    0.639117] PCI: Using ACPI for IRQ routing
[    0.639283] NET: Registered protocol family 8
[    0.639283] NET: Registered protocol family 20
[    0.639283] NetLabel: Initializing
[    0.639283] NetLabel:  domain hash size = 128
[    0.639283] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.639283] NetLabel:  unlabeled traffic allowed by default
[    0.639283] hpet clockevent registered
[    0.639283] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.639283] hpet0: 3 64-bit timers, 14318180 Hz
[    0.640766] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.640771]    actual entries 65620
[    0.640920] AppArmor: AppArmor Filesystem Enabled
[    0.640967] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.640967] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.640967] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.640967] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.640967] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.640967] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.640967] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.640967] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.640967] system 00:05: ioport range 0x3e0-0x3e1 has been reserved
[    0.640967] system 00:05: ioport range 0x3f8-0x3ff has been reserved
[    0.640967] system 00:05: ioport range 0x600-0x60f has been reserved
[    0.640967] system 00:05: ioport range 0x680-0x6ff has been reserved
[    0.640967] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.640967] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.640967] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.640967] system 00:05: ioport range 0x1640-0x164f has been reserved
[    0.640967] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[    0.640967] system 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.640967] system 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.640967] system 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.640967] system 00:05: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.677353] pci 0000:01:02.0: CardBus bridge, secondary bus 0000:02
[    0.677357] pci 0000:01:02.0:   IO window: 0x00c400-0x00c4ff
[    0.677364] pci 0000:01:02.0:   IO window: 0x00c800-0x00c8ff
[    0.677372] pci 0000:01:02.0:   PREFETCH window: 0x9c000000-0x9fffffff
[    0.677380] pci 0000:01:02.0:   MEM window: 0x14000000-0x17ffffff
[    0.677387] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.677392] pci 0000:00:1e.0:   IO window: 0xc000-0xdfff
[    0.677400] pci 0000:00:1e.0:   MEM window: 0xcc000000-0xcfffffff
[    0.677407] pci 0000:00:1e.0:   PREFETCH window: 0x0000009c000000-0x0000009fffffff
[    0.677428] pci 0000:00:1e.0: setting latency timer to 64
[    0.678580] pci 0000:01:02.0: power state changed by ACPI to D0
[    0.678597] pci 0000:01:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.678606] bus: 00 index 0 io port: [0, ffff]
[    0.678609] bus: 00 index 1 mmio: [0, ffffffff]
[    0.678613] bus: 01 index 0 io port: [c000, dfff]
[    0.678616] bus: 01 index 1 mmio: [cc000000, cfffffff]
[    0.678620] bus: 01 index 2 mmio: [9c000000, 9fffffff]
[    0.678623] bus: 01 index 3 io port: [0, ffff]
[    0.678626] bus: 01 index 4 mmio: [0, ffffffff]
[    0.678630] bus: 02 index 0 io port: [c400, c4ff]
[    0.678633] bus: 02 index 1 io port: [c800, c8ff]
[    0.678636] bus: 02 index 2 mmio: [9c000000, 9fffffff]
[    0.678640] bus: 02 index 3 mmio: [14000000, 17ffffff]
[    0.678655] NET: Registered protocol family 2
[    0.678849] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.679141] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.679199] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.679261] TCP: Hash tables configured (established 8192 bind 8192)
[    0.679266] TCP reno registered
[    0.679374] NET: Registered protocol family 1
[    0.679535] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.187196]  it is
[    1.736452] Freeing initrd memory: 7995k freed
[    1.737531] audit: initializing netlink socket (disabled)
[    1.737558] type=2000 audit(1231290805.736:1): initialized
[    1.747066] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.750561] VFS: Disk quotas dquot_6.5.1
[    1.750699] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.750871] msgmni has been set to 480
[    1.751065] io scheduler noop registered
[    1.751070] io scheduler anticipatory registered
[    1.751074] io scheduler deadline registered
[    1.751092] io scheduler cfq registered (default)
[    1.751115] pci 0000:00:02.0: Boot video device
[    1.751676] isapnp: Scanning for PnP cards...
[    2.105685] isapnp: No Plug & Play device found
[    2.160295] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.163606] brd: module loaded
[    2.163729] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.163925] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.170778] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.174166] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.174175] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.174179] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.174183] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.174187] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.174871] mice: PS/2 mouse device common for all mice
[    2.175096] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.175131] rtc0: alarms up to one month, y3k, hpet irqs
[    2.175304] EISA: Probing bus 0 at eisa.0
[    2.175314] Cannot allocate resource for EISA slot 1
[    2.175348] EISA: Detected 0 cards.
[    2.175353] cpuidle: using governor ladder
[    2.175356] cpuidle: using governor menu
[    2.176118] TCP cubic registered
[    2.176163] Using IPI No-Shortcut mode
[    2.176480] registered taskstats version 1
[    2.176657]   Magic number: 9:762:204
[    2.176722] tty ttyt2: hash matches
[    2.176892] rtc_cmos 00:06: setting system clock to 2009-01-07 01:13:26 UTC (1231290806)
[    2.176897] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.176900] EDD information not available.
[    2.177199] Freeing unused kernel memory: 424k freed
[    2.177272] Write protecting the kernel text: 2576k
[    2.177315] Write protecting the kernel read-only data: 936k
[    2.181596] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.475108] fuse init (API version 7.9)
[    2.728198] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.728287] processor ACPI0007:00: registered as cooling_device0
[    2.728293] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.519042] usbcore: registered new interface driver usbfs
[    3.519081] usbcore: registered new interface driver hub
[    3.528828] usbcore: registered new device driver usb
[    3.542214] No dock devices found.
[    3.546445] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    3.546461] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.546480] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.546485] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.546568] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.550471] ehci_hcd 0000:00:1d.7: debug port 1
[    3.550480] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.550499] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x10000000
[    3.558204] USB Universal Host Controller Interface driver v3.0
[    3.582028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.582277] usb usb1: configuration #1 chosen from 1 choice
[    3.582330] hub 1-0:1.0: USB hub found
[    3.582344] hub 1-0:1.0: 6 ports detected
[    3.634547] SCSI subsystem initialized
[    3.671154] 8139too Fast Ethernet driver 0.9.28
[    3.699613] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.699628] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.699633] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.699669] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.699705] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001200
[    3.699860] usb usb2: configuration #1 chosen from 1 choice
[    3.699900] hub 2-0:1.0: USB hub found
[    3.699912] hub 2-0:1.0: 2 ports detected
[    3.795435] libata version 3.00 loaded.
[    3.801028] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.801043] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.801049] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.801093] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.801137] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001220
[    3.801285] usb usb3: configuration #1 chosen from 1 choice
[    3.801325] hub 3-0:1.0: USB hub found
[    3.801336] hub 3-0:1.0: 2 ports detected
[    3.904430] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.904446] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.904452] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.904489] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.904532] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001240
[    3.904680] usb usb4: configuration #1 chosen from 1 choice
[    3.904728] hub 4-0:1.0: USB hub found
[    3.904740] hub 4-0:1.0: 2 ports detected
[    4.008633] 8139too 0000:01:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.009673] eth0: RealTek RTL8139 at 0xc200, 00:40:d0:7f:56:20, IRQ 20
[    4.009677] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.014411] ohci1394 0000:01:02.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    4.064195] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fedff800-fedfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.065373] ata_piix 0000:00:1f.2: version 2.12
[    4.065395] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.065401] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.065688] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.220048] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.221097] scsi0 : ata_piix
[    4.221263] scsi1 : ata_piix
[    4.222826] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    4.222831] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    4.384327] ata1.00: ATA-6: WDC WD400UE-22HCT0, 09.07D09, max UDMA/100
[    4.384333] ata1.00: 78140160 sectors, multi 16: LBA 
[    4.384337] ata1.00: applying bridge limits
[    4.392407] ata1.00: configured for UDMA/100
[    4.470311] Marking TSC unstable due to TSC halts in idle
[    4.556483] ata2.00: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CL02, max UDMA/33
[    4.572424] ata2.00: configured for UDMA/33
[    4.572595] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400UE-22HC 09.0 PQ: 0 ANSI: 5
[    4.576406] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CL02 PQ: 0 ANSI: 5
[    4.613342] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.613397] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.641869] Driver 'sd' needs updating - please use bus_type methods
[    4.644886] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.644926] sd 0:0:0:0: [sda] Write Protect is off
[    4.644930] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.644991] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.645113] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.645144] sd 0:0:0:0: [sda] Write Protect is off
[    4.645148] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.645205] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.645211]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.922255]  sda1 sda2 < sda5 >
[    4.955081] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.969465] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.969473] Uniform CD-ROM driver Revision: 3.20
[    4.969608] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.294822] PM: Starting manual resume from disk
[    5.294828] PM: Resume from partition 8:5
[    5.294831] PM: Checking hibernation image.
[    5.295067] PM: Resume from disk failed.
[    5.325278] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.325285] EXT3-fs: write access will be enabled during recovery.
[    5.340220] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d00100337786]
[   10.296020] kjournald starting.  Commit interval 5 seconds
[   10.296042] EXT3-fs: recovery complete.
[   10.323315] EXT3-fs: mounted filesystem with ordered data mode.
[   18.984465] udevd version 124 started
[   20.715519] iTCO_vendor_support: vendor-support=0
[   20.776934] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   20.777105] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   20.777308] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.882204] Linux agpgart interface v0.103
[   21.055474] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   21.108707] intel_rng: Firmware space is locked read-only. If you can't or
[   21.108710] intel_rng: don't want to disable this in firmware setup, and if
[   21.108712] intel_rng: you are certain that your system has a functional
[   21.108714] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   21.179233] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   21.179510] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   21.201094] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[   21.297486] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   21.308072] ACPI: Power Button (FF) [PWRF]
[   21.308239] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   21.320042] ACPI: Sleep Button (CM) [SBTN]
[   21.320218] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   21.322113] ACPI: Lid Switch [LID]
[   21.362377] ACPI: AC Adapter [AC] (on-line)
[   21.449721] ACPI: Battery Slot [BAT0] (battery present)
[   21.713924] Yenta: CardBus bridge found at 0000:01:02.0 [1071:8048]
[   21.713954] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.713958] Yenta: Routing CardBus interrupts to PCI
[   21.713965] Yenta TI: socket 0000:01:02.0, mfunc 0x01ac1b22, devctl 0x64
[   21.944843] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   21.944850] Socket status: 30000006
[   21.944855] Yenta: Raising subordinate bus# of parent bus (#01) from #02 to #05
[   21.944865] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xdfff
[   21.944869] cs: IO port probe 0xc000-0xdfff: clean.
[   21.945520] pcmcia: parent PCI bridge Memory window: 0xcc000000 - 0xcfffffff
[   21.945524] pcmcia: parent PCI bridge Memory window: 0x9c000000 - 0x9fffffff
[   22.415772] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   22.458832] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input6
[   23.131759] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7
[   23.140051] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.289969] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.290009] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.394956] cs: IO port probe 0x100-0x3af: clean.
[   26.396752] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   26.397465] cs: IO port probe 0x820-0x8ff: clean.
[   26.398088] cs: IO port probe 0xc00-0xcf7: clean.
[   26.398930] cs: IO port probe 0xa00-0xaff: clean.
[   26.685633] loop: module loaded
[   26.781757] lp: driver loaded but no devices found
[   27.135027] Adding 722884k swap on /dev/sda5.  Priority:-1 extents:1 across:722884k
[   27.732357] EXT3 FS on sda1, internal journal
[   29.121281] type=1505 audit(1231290833.543:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3829
[   29.121659] type=1505 audit(1231290833.543:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3829
[   29.601386] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.447333] ACPI: WMI: Mapper loaded
[   31.733106] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   31.835049] apm: BIOS not found.
[   32.064079] ppdev: user-space parallel port driver
[   34.164090] Bluetooth: Core ver 2.13
[   34.166644] NET: Registered protocol family 31
[   34.166653] Bluetooth: HCI device and connection manager initialized
[   34.166658] Bluetooth: HCI socket layer initialized
[   34.205562] Bluetooth: L2CAP ver 2.11
[   34.205573] Bluetooth: L2CAP socket layer initialized
[   34.264183] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.264193] Bluetooth: BNEP filters: protocol multicast
[   34.333355] Bridge firewalling registered
[   34.333833] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   34.397255] Bluetooth: RFCOMM socket layer initialized
[   34.397576] Bluetooth: RFCOMM TTY layer initialized
[   34.397585] Bluetooth: RFCOMM ver 1.10
[   34.398691] Bluetooth: SCO (Voice Link) ver 0.6
[   34.398700] Bluetooth: SCO socket layer initialized
[   38.512425] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   38.852564] [drm] Initialized drm 1.1.0 20060810
[   38.896193] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   38.896208] pci 0000:00:02.0: setting latency timer to 64
[   38.896976] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.200979] NET: Registered protocol family 17
[   46.310560] NET: Registered protocol family 10
[   46.312667] lo: Disabled Privacy Extensions
[   56.716065] eth0: no IPv6 routers present
[ 1085.230478] eth0: link down
[ 1089.903195] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1090.199528] eth0: link down
[ 1090.799171] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1090.967911] eth0: link down
[ 1091.375157] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1091.479076] eth0: link down
[ 1092.015143] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1092.119672] eth0: link down
[ 1092.271135] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1092.375250] eth0: link down
[ 1092.463132] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1092.560524] nm-applet[5169]: segfault at 0 ip 0805624d sp bfea0dd0 error 4 in nm-applet[8048000+42000]
[ 1092.630835] eth0: link down
[ 1092.719121] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1092.951949] eth0: link down
[ 1096.431053] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1096.535021] eth0: link down
[ 1096.879042] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1097.047826] eth0: link down
[ 1097.455036] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1097.558989] eth0: link down
[ 1098.415005] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1099.030224] eth0: link down
[ 1099.630982] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1099.734720] eth0: link down
[ 1100.206969] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1100.317248] eth0: link down
[ 1101.422944] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1101.846551] eth0: link down
[ 1102.574921] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1102.742725] eth0: link down
[ 1104.046887] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1104.215598] eth0: link down
[ 1104.366874] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1104.471179] eth0: link down
[ 1104.558868] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1104.662866] eth0: link down
[ 1104.814865] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1105.046237] eth0: link down
[ 1105.262851] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1105.495145] eth0: link down
[ 1106.158844] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1106.391326] eth0: link down
[ 1106.478833] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1106.774696] eth0: link down
[ 1107.374814] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1107.479186] eth0: link down
[ 1108.014796] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1108.118144] eth0: link down
[ 1108.718781] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1108.886531] eth0: link down
[ 1109.102779] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1109.206005] eth0: link down
[ 1109.742758] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1109.974394] eth0: link down
[ 1110.126760] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1110.229979] eth0: link down
[ 1110.574738] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1110.870567] eth0: link down
[ 1111.150728] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1111.253934] eth0: link down
[ 1111.534725] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1111.638949] eth0: link down
[ 1111.790719] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1111.958430] eth0: link down
[ 1112.046711] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1112.150123] eth0: link down
[ 1112.238700] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1112.471238] eth0: link down
[ 1112.686695] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1112.790715] eth0: link down
[ 1114.714164] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1386.621370] eth0: link down
[ 1388.158595] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1694.252047] eth0: link down
[ 2021.966183] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3045.352052] usb 1-1: new high speed USB device using ehci_hcd and address 2
[ 3045.486616] usb 1-1: configuration #1 chosen from 2 choices
[ 3045.682341] eth0: link down
[ 3047.187335] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3048.183641] usbcore: registered new interface driver libusual
[ 3048.980134] Initializing USB Mass Storage driver...
[ 3048.982431] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3048.987718] usbcore: registered new interface driver usb-storage
[ 3048.988077] USB Mass Storage support registered.
[ 3048.988497] usb-storage: device found at 2
[ 3048.988505] usb-storage: waiting for device to settle before scanning
[ 3053.988401] usb-storage: device scan complete
[ 3053.989637] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3054.003352] sd 2:0:0:0: [sdb] 3999743 512-byte hardware sectors (2048 MB)
[ 3054.004975] sd 2:0:0:0: [sdb] Write Protect is off
[ 3054.004983] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3054.004987] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3054.007595] sd 2:0:0:0: [sdb] 3999743 512-byte hardware sectors (2048 MB)
[ 3054.009100] sd 2:0:0:0: [sdb] Write Protect is off
[ 3054.009108] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3054.009112] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3054.009636]  sdb: sdb1 sdb2
[ 3054.037064] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 3054.037624] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 4741.954193] usb 1-1: USB disconnect, address 2
[ 4743.854726] scsi 2:0:0:0: rejecting I/O to dead device
[ 8134.344660] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 8134.987244] ndiswrapper: driver netw33 (Winbond Electronics Corp.,07/26/2005,1.2.81.1001) loaded
[ 8134.989311] ndiswrapper 0000:01:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 8134.989598] ndiswrapper (NdisMRegisterInterrupt:1942): shared but dynamic interrupt!
[ 8134.989627] ndiswrapper: using IRQ 21
[ 8136.512064] BUG: unable to handle kernel NULL pointer dereference at 00000024
[ 8136.512077] IP: [<c02f046f>] __netif_schedule+0xf/0x60
[ 8136.512089] *pde = 00000000 
[ 8136.512095] Oops: 0002 [#1] SMP 
[ 8136.512100] Modules linked in: ndiswrapper(+) nls_iso8859_1 nls_cp437 vfat fat usb_storage libusual ipv6 af_packet i915 drm sco rfcomm bridge stp bnep l2cap bluetooth ppdev cpufreq_conservative cpufreq_stats cpufreq_ondemand freq_table cpufreq_powersave cpufreq_userspace wmi pci_slot container sbs sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport loop joydev pcmcia snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy evdev snd_seq_oss video snd_seq_midi output snd_rawmidi snd_seq_midi_event snd_seq serio_raw snd_timer snd_seq_device psmouse yenta_socket rsrc_nonstatic pcmcia_core snd battery ac button soundcore intel_agp pcspkr snd_page_alloc agpgart iTCO_wdt iTCO_vendor_support ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg pata_acpi ahci ata_generic 8139cp ata_piix ohci1394 libata 8139too mii ieee1394 scsi_mod uhci_hcd ehci_hcd dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 8136.512214] 
[ 8136.512219] Pid: 7332, comm: ntos_wq Tainted: P          (2.6.27-9-generic #1)
[ 8136.512223] EIP: 0060:[<c02f046f>] EFLAGS: 00010246 CPU: 0
[ 8136.512229] EIP is at __netif_schedule+0xf/0x60
[ 8136.512233] EAX: 00000024 EBX: d0732848 ECX: 00000000 EDX: ffffffff
[ 8136.512237] ESI: d0732848 EDI: d07321a0 EBP: c16b5e90 ESP: c16b5e8c
[ 8136.512241]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[ 8136.512245] Process ntos_wq (pid: 7332, ti=c16b4000 task=c163d7f0 task.ti=c16b4000)
[ 8136.512249] Stack: d0732848 c16b5f04 d0760e58 c02e3931 00000067 00000001 c8936480 cec03900 
[ 8136.512260]        00000028 00000067 c16b5ed0 c02e3a04 c16b5ed0 00000246 00000000 cecb8c00 
[ 8136.512270]        00000067 c16b5ef8 c025d3e0 00000001 c16b5ee8 00000028 00000246 00000042 
[ 8136.512280] Call Trace:
[ 8136.512291]  [<d0760e58>] ? NdisMIndicateStatus+0x298/0x3a0 [ndiswrapper]
[ 8136.512321]  [<c02e3931>] ? raw_pci_read+0x81/0x90
[ 8136.512330]  [<c02e3a04>] ? pci_read+0x34/0x40
[ 8136.512336]  [<c025d3e0>] ? pci_bus_read_config_byte+0x60/0x70
[ 8136.512366]  [<d0767aad>] ? kdpc_worker+0xcd/0x150 [ndiswrapper]
[ 8136.512405]  [<d07679e0>] ? kdpc_worker+0x0/0x150 [ndiswrapper]
[ 8136.512428]  [<c0143645>] ? run_workqueue+0x95/0x160
[ 8136.512451]  [<c0147576>] ? finish_wait+0x16/0x70
[ 8136.512457]  [<c01438e8>] ? worker_thread+0x88/0xf0
[ 8136.512463]  [<c01474b0>] ? autoremove_wake_function+0x0/0x50
[ 8136.512469]  [<c0143860>] ? worker_thread+0x0/0xf0
[ 8136.512475]  [<c0147141>] ? kthread+0x41/0x80
[ 8136.512481]  [<c0147100>] ? kthread+0x0/0x80
[ 8136.512487]  [<c0105297>] ? kernel_thread_helper+0x7/0x10
[ 8136.512494]  =======================
[ 8136.512497] Code: 8d 74 26 00 eb b8 8d b6 00 00 00 00 83 f1 0c 90 8d 74 26 00 eb 99 8d b6 00 00 00 00 55 89 e5 53 e8 37 4e e1 ff 89 c1 8d 40 24 90 <0f> ba 28 01 19 d2 85 d2 75 41 9c 58 90 8d b4 26 00 00 00 00 89 
[ 8136.512552] EIP: [<c02f046f>] __netif_schedule+0xf/0x60 SS:ESP 0068:c16b5e8c
[ 8136.512562] ---[ end trace a64b78ee28c70fbc ]---

ishw -C network: ross@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:7f:56:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.102 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Ethernet controller
       product: W89C33D 802.11 a/b/g BB/MAC
       vendor: Winbond Electronics Corp
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=128 maxlatency=32 mingnt=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:23:f5:a5:c6:de
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

iwlist scan: ross@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

Hope I done that right.

---

### Post by kevdog on 2009-01-06
Unless you can find a specific solution for this very intruiging and rare chipset -- you have a problem.  dmesg gives a stacktrace:

BUG: unable to handle kernel NULL pointer dereference at 00000024
[ 8136.512077] IP: [<c02f046f>] __netif_schedule+0xf/0x60
[ 8136.512089] *pde = 00000000
[ 8136.512095] Oops: 0002 [#1] SMP
[ 8136.512100] Modules linked in: ndiswrapper(+) nls_iso8859_1 nls_cp437 vfat fat usb_storage libusual ipv6 af_packet i915 drm sco rfcomm bridge stp bnep l2cap bluetooth ppdev cpufreq_conservative cpufreq_stats cpufreq_ondemand freq_table cpufreq_powersave cpufreq_userspace wmi pci_slot container sbs sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport loop joydev pcmcia snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy evdev snd_seq_oss video snd_seq_midi output snd_rawmidi snd_seq_midi_event snd_seq serio_raw snd_timer snd_seq_device psmouse yenta_socket rsrc_nonstatic pcmcia_core snd battery ac button soundcore intel_agp pcspkr snd_page_alloc agpgart iTCO_wdt iTCO_vendor_support ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg pata_acpi ahci ata_generic 8139cp ata_piix ohci1394 libata 8139too mii ieee1394 scsi_mod uhci_hcd ehci_hcd dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 8136.512214]
[ 8136.512219] Pid: 7332, comm: ntos_wq Tainted: P (2.6.27-9-generic #1)
[ 8136.512223] EIP: 0060:[<c02f046f>] EFLAGS: 00010246 CPU: 0
[ 8136.512229] EIP is at __netif_schedule+0xf/0x60
[ 8136.512233] EAX: 00000024 EBX: d0732848 ECX: 00000000 EDX: ffffffff
[ 8136.512237] ESI: d0732848 EDI: d07321a0 EBP: c16b5e90 ESP: c16b5e8c
[ 8136.512241] DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[ 8136.512245] Process ntos_wq (pid: 7332, ti=c16b4000 task=c163d7f0 task.ti=c16b4000)
[ 8136.512249] Stack: d0732848 c16b5f04 d0760e58 c02e3931 00000067 00000001 c8936480 cec03900
[ 8136.512260] 00000028 00000067 c16b5ed0 c02e3a04 c16b5ed0 00000246 00000000 cecb8c00
[ 8136.512270] 00000067 c16b5ef8 c025d3e0 00000001 c16b5ee8 00000028 00000246 00000042
[ 8136.512280] Call Trace:
[ 8136.512291] [<d0760e58>] ? NdisMIndicateStatus+0x298/0x3a0 [ndiswrapper]
[ 8136.512321] [<c02e3931>] ? raw_pci_read+0x81/0x90
[ 8136.512330] [<c02e3a04>] ? pci_read+0x34/0x40
[ 8136.512336] [<c025d3e0>] ? pci_bus_read_config_byte+0x60/0x70
[ 8136.512366] [<d0767aad>] ? kdpc_worker+0xcd/0x150 [ndiswrapper]
[ 8136.512405] [<d07679e0>] ? kdpc_worker+0x0/0x150 [ndiswrapper]
[ 8136.512428] [<c0143645>] ? run_workqueue+0x95/0x160
[ 8136.512451] [<c0147576>] ? finish_wait+0x16/0x70
[ 8136.512457] [<c01438e8>] ? worker_thread+0x88/0xf0
[ 8136.512463] [<c01474b0>] ? autoremove_wake_function+0x0/0x50
[ 8136.512469] [<c0143860>] ? worker_thread+0x0/0xf0
[ 8136.512475] [<c0147141>] ? kthread+0x41/0x80
[ 8136.512481] [<c0147100>] ? kthread+0x0/0x80
[ 8136.512487] [<c0105297>] ? kernel_thread_helper+0x7/0x10
[ 8136.512494] =======================
[ 8136.512497] Code: 8d 74 26 00 eb b8 8d b6 00 00 00 00 83 f1 0c 90 8d 74 26 00 eb 99 8d b6 00 00 00 00 55 89 e5 53 e8 37 4e e1 ff 89 c1 8d 40 24 90 <0f> ba 28 01 19 d2 85 d2 75 41 9c 58 90 8d b4 26 00 00 00 00 89
[ 8136.512552] EIP: [<c02f046f>] __netif_schedule+0xf/0x60 SS:ESP 0068:c16b5e8c
[ 8136.512562] ---[ end trace a64b78ee28c70fbc ]---


Basically that driver is not going to work.  Is this the winxp driver?  I would try with both a winxp and win98 driver.  If these don't work you may be SOL -- meaning another wireless adapter with far better supported chipset (ie Atheros) may be in order.

---

### Post by rossmc92 on 2009-01-08
Bump.

---

### Post by rossmc92 on 2009-01-08
Oh, never realised that you'd replied. I'll give the 98 driver a try but if that fails I'm just going to get a new wireless card. Any suggestions on the best?

I'm assuming that It'd have to be specific to my hardware as well?

---

