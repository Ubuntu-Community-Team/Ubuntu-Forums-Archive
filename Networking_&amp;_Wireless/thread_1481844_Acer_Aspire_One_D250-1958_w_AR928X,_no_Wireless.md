---
title: "Acer Aspire One D250-1958 w/ AR928X, no Wireless"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by Capt. Easy on 2010-05-13
I started a thread with problem in the Absolute Beginners section, [<HERE>](http://ubuntuforums.org/showthread.php?t=1468982), but haven't gotten anywhere.

I have a new Acer Aspire One, model D250-1958.  It uses the Atheros AR928X.  I've tried Ubuntu Netbook Remix 9.10 and Ubuntu Netbook Edition 10.04, as well as the conventional Ubuntu.  Everything works beautifully, except no wireless.  The netbook picks up the signal, but when I provide the Key it fails to connect, and eventually prompts me for the key again.

I've tried to research this on my own, but haven't found a solution.  In particular, the solution reported by **narnie** for his Acer Aspire One D250-1584, [<HERE>](http://ubuntuforums.org/showthread.php?t=1309605&highlight=Atheros+AR928X&page=4), didn't work for me.



I'd really like to get this working.  The netbook will be much less useful if it can't make use of our wireless router.

Any help will be much appreciated.

---

### Post by Capt. Easy on 2010-05-16
Well, I _seem_ to be making progress, but no real success so far.

I did a clean install of Ubuntu Netbook Edition 10.04.  I updated with a wired connection to my router, uninstalled Network Manager and installed WICD.  I followed the steps [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros"), to install **madwifi** and **ath_pci**, including creating the file **/etc/modprobe.d/options** to  include the line "options ath_pci rfkill=0"

I then disconnected the wired connection and tried to connect to our home wireless network.  It uses WEP 64 encryption -- I entered the key, but no luck.  It seemed to be stuck on obtaining the IP address.  So, I manually entered the IP address and tried again.

Bingo!  Almost. :evil:


The connection **appears** to have been made.  The connection info is:

SSID:  (My Network's Name)
Speed:  54 Mb/s
IP:  (My Router's IP)
Strength:  (varies between 88% and 90%)
RX:  0.0 Kb/s
TX:  0.0 Kb/s


Just to check I tried connecting with Firefox -- no luck.

So, I opened a terminal window and tried

sudo apt-get update

That failed as well.



So-ooo, has anyone got any ideas?


EDIT:  BTW, the Acer Aspire One has an LED indicator to show when a wireless network is available.  In the past it was always "on" but I could never connect.  This time around the netbook insists it's connected, but the LED is "off."

---

### Post by NUboon2Age on 2010-05-16
Good info, but let's get all the background info from [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681")

---

### Post by Capt. Easy on 2010-05-17
This reply deleted -- forgot to turn off smilies, and it was not very readable.

The next reply should contain the full text and be more intelligible.

---

### Post by Capt. Easy on 2010-05-17
Thanks for the reply!

1 ) Machine Brand and Model (PC/Laptop):  Acer Aspire One AOD250 netbook, model  D250-1958

2 ) Wireless Brand, Model and Wireless Chipset:

[FONT=monospace]_From lspci_
  
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless  Network Adapter (PCI-Express) (rev. 01)
  
  [U]From lsusb
    
  [/U]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/FONT][FONT=monospace]Bus 004 Device 001: ID  1d6b:0001  Linux Foundation 1.1 root hub[/FONT]
[FONT=monospace]Bus 003 Device 001: ID 1d6b:0001  Linux Foundation 1.1 root hub[/FONT]
[FONT=monospace]Bus 002 Device 001: ID 1d6b:0001  Linux Foundation 1.1 root hub[/FONT]
[FONT=monospace]Bus 001 Device 002: ID 04f2:b084  [/FONT]Chicony Electronics Co., Ltd.
[FONT=monospace]Bus 001 Device 001: ID 1d6b:0002  Linux Foundation 2.0 root hub[/FONT]


3 ) check interface:[B]
  
ifconfig
  
[/B]wifi0

Link encap:UNSPEC  HWaddr  0C-EE=E6-85-F5-45-30-30-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:10768 errors:0 dropped:0 overruns:0 frame:561
TX packets:287 errors:2 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:280
RX bytes:1206634 (1.2 MB)  TX bytes:16417 (16.4 KB)


**iwconfig**

lo      no wireless extensions.

eth0  no wireless extensions.
 
wifi0  no wireless extensions.
 
ath0  IEEE 802.11g  ESSID: "(*our network)*"
        Mode:Managed  Frequency:2.462 GHz  Access Point:  00:1F:90:ED:CD:7E
        Bit Rate:54 Mb/s   Tx-Power:13 dBm   Sensitivity=1/1
        Retry:off   RTS thr:off   Fragment thr:off
        Power Management:off
        Link Quality=68/70   Signal level=-27 dBm   Noise level=-95 dBm
        Rx invalid nwid:7442   Rx invalid crypt:0   Rx invalid frag:0
        Tx excessive retries:0   Invalid misc:0   Missed beacon:0


**4 ) Check for modules:**

Module           Size    Used by

wlan_wep       5141   1
...
ath_pci       193197   0
wlan           222892   5   wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal       398604   3  ath_rate_sample,ath_pci
...


**5 ) Kernel boot messages**

```


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc  version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28  13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000  (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000  (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f576000 (usable)
[    0.000000]  BIOS-e820: 000000003f576000 - 000000003f5bf000  (reserved)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f66d000 (usable)
[    0.000000]  BIOS-e820: 000000003f66d000 - 000000003f6bf000 (ACPI  NVS)
[    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f6ee000 (usable)
[    0.000000]  BIOS-e820: 000000003f6ee000 - 000000003f6ff000 (ACPI  data)
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000  (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000  (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000  (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000  (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000  (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000  (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000  (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
[    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
[    0.000000]   2 base 000000000 mask 0E0000000 write-back
[    0.000000]   3 base 020000000 mask 0E0000000 write-back
[    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new  0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000  (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f576000 (usable)
[    0.000000]  modified: 000000003f576000 - 000000003f5bf000 (reserved)
[    0.000000]  modified: 000000003f5bf000 - 000000003f66d000 (usable)
[    0.000000]  modified: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  modified: 000000003f6bf000 - 000000003f6ee000 (usable)
[    0.000000]  modified: 000000003f6ee000 - 000000003f6ff000 (ACPI  data)
[    0.000000]  modified: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2f0c1000 - 2f8578b5
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACRSYS ACRPRDCT  00000001      01000013)
[    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001  1025 01000013)
[    0.000000] ACPI: DSDT 3f6f0000 070CA (v01 ACRSYS ACRPRDCT 00000001  1025 01000013)
[    0.000000] ACPI: FACS 3f688000 00040
[    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000  INTL 20051117)
[    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACRSYS ACRPRDCT 00000001  1025 01000013)
[    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACRSYS ACRPRDCT 00000001  1025 01000013)
[    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACRSYS ACRPRDCT 00000001  1025 01000013)
[    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001  1025 01000013)
[    0.000000] ACPI: SLIC 3f6ef000 00176 (v01 ACRSYS ACRPRDCT 00000001  1025 01000013)
[    0.000000] ACPI: BOOT 3f6ee000 00028 (v01 ACRSYS ACRPRDCT 00000001  1025 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 -  00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==>  [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==>  [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==>  [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==>  [0000100000 - 00008d9e98]
[    0.000000]   #4 [002f0c1000 - 002f8578b5]          RAMDISK ==>  [002f0c1000 - 002f8578b5]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==>  [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd178]              BRK ==>  [00008da000 - 00008dd178]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==>  [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==>  [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f576
[    0.000000]     0: 0x0003f5bf -> 0x0003f66d
[    0.000000]     0: 0x0003f6bf -> 0x0003f6ee
[    0.000000]     0: 0x0003f6ff -> 0x0003f700
[    0.000000] On node 0 totalpages: 259567
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map  c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32087 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI  0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high  level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 -  0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 -  00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 -  00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 -  0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap:  40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320  u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.   Total pages: 257536
[    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic  root=UUID=1ef305ce-f58c-4525-827f-00edb065a533 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288  bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144  bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5196800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't  want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f700)
[    0.000000] Memory: 1007768k/1039360k available (4673k kernel code,  29988k reserved, 2121k data, 656k init, 129368k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in  supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0,  CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for  per-cpu timer
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches HPET. 1 loops
[    0.000000] Detected 1595.978 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using  timer frequency.. 3191.95 BogoMIPS (lpj=6383912)
[    0.004048] Security Framework initialized
[    0.004092] AppArmor: AppArmor initialized
[    0.004109] Mount-cache hash table entries: 512
[    0.004351] Initializing cgroup subsys ns
[    0.004360] Initializing cgroup subsys cpuacct
[    0.004370] Initializing cgroup subsys memory
[    0.004385] Initializing cgroup subsys devices
[    0.004391] Initializing cgroup subsys freezer
[    0.004396] Initializing cgroup subsys net_cls
[    0.004437] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004444] CPU: L2 cache: 512K
[    0.004449] CPU: Physical Processor ID: 0
[    0.004454] CPU: Processor Core ID: 0
[    0.004462] mce: CPU supports 5 MCE banks
[    0.004481] CPU0: Thermal monitoring enabled (TM2)
[    0.004489] using mwait in idle threads.
[    0.004501] Performance Events: Atom events, Intel PMU driver.
[    0.004518] ... version:                3
[    0.004522] ... bit width:              40
[    0.004527] ... generic registers:      2
[    0.004532] ... value mask:             000000ffffffffff
[    0.004537] ... max period:             000000007fffffff
[    0.004542] ... fixed-purpose events:   3
[    0.004547] ... event mask:             0000000700000003
[    0.004556] Checking 'hlt' instruction... OK.
[    0.020009] Disabling 4MB page tables to avoid TLB bug
[    0.024418] ACPI: Core revision 20090903
[    0.044018] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044029] ftrace: allocating 21771 entries in 43 pages
[    0.048112] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048519] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.089028] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.092001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.176056] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.176085] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.180034] Brought up 2 CPUs
[    0.180041] Total of 2 processors activated (6383.88 BogoMIPS).
[    0.180288] CPU0 attaching sched-domain:
[    0.180297]  domain 0: span 0-1 level SIBLING
[    0.180303]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.180316]   domain 1: span 0-1 level MC
[    0.180321]    groups: 0-1 (cpu_power = 1178)
[    0.180334] CPU1 attaching sched-domain:
[    0.180339]  domain 0: span 0-1 level SIBLING
[    0.180344]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.180356]   domain 1: span 0-1 level MC
[    0.180362]    groups: 0-1 (cpu_power = 1178)
[    0.180593] devtmpfs: initialized
[    0.180593] regulator: core version 0.5
[    0.180593] Time:  4:52:03  Date: 05/17/10
[    0.180593] NET: Registered protocol family 16
[    0.180593] Trying to unpack rootfs image as initramfs...
[    0.180593] EISA bus registered
[    0.180610] ACPI: bus type pci registered
[    0.180780] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0  - 255
[    0.180789] PCI: MCFG area at e0000000 reserved in E820
[    0.180795] PCI: Using MMCONFIG for extended config space
[    0.180802] PCI: Using configuration type 1 for base access
[    0.186040] bio: create slab <bio-0> at 0
[    0.189183] ACPI: EC: Look up EC in DSDT
[    0.225928] ACPI: Executed 1 blocks of module-level executable AML  code
[    0.231335] ACPI: BIOS _OSI(Linux) query ignored
[    0.231861] ACPI: BIOS _OSI(Linux) query ignored
[    0.233388] ACPI: Interpreter enabled
[    0.233406] ACPI: (supports S0 S3 S4 S5)
[    0.233486] ACPI: Using IOAPIC for interrupt routing
[    0.375746] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data =  0x62
[    0.376030] ACPI: Power Resource [FN00] (on)
[    0.376718] ACPI: No dock devices found.
[    0.378484] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.378506] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.378531] ACPI: Marking method _OSC as Serialized because of  AE_ALREADY_EXISTS error
[    0.378613] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.378819] pci 0000:00:02.0: reg 10 32bit mmio:  [0x58280000-0x582fffff]
[    0.378833] pci 0000:00:02.0: reg 14 io port: [0x60f0-0x60f7]
[    0.378845] pci 0000:00:02.0: reg 18 32bit mmio pref:  [0x40000000-0x4fffffff]
[    0.378858] pci 0000:00:02.0: reg 1c 32bit mmio:  [0x58300000-0x5833ffff]
[    0.378927] pci 0000:00:02.1: reg 10 32bit mmio:  [0x58200000-0x5827ffff]
[    0.379092] pci 0000:00:1b.0: reg 10 64bit mmio:  [0x58340000-0x58343fff]
[    0.379176] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.379189] pci 0000:00:1b.0: PME# disabled
[    0.379328] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.379342] pci 0000:00:1c.0: PME# disabled
[    0.379481] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.379492] pci 0000:00:1c.1: PME# disabled
[    0.379624] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.379634] pci 0000:00:1c.2: PME# disabled
[    0.379764] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.379775] pci 0000:00:1c.3: PME# disabled
[    0.379868] pci 0000:00:1d.0: reg 20 io port: [0x60a0-0x60bf]
[    0.379961] pci 0000:00:1d.1: reg 20 io port: [0x6080-0x609f]
[    0.380086] pci 0000:00:1d.2: reg 20 io port: [0x6060-0x607f]
[    0.380189] pci 0000:00:1d.3: reg 20 io port: [0x6040-0x605f]
[    0.380288] pci 0000:00:1d.7: reg 10 32bit mmio:  [0x58344400-0x583447ff]
[    0.380373] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.380385] pci 0000:00:1d.7: PME# disabled
[    0.380620] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6  ACPI/GPIO/TCO
[    0.380632] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6  GPIO
[    0.380646] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at  ff2c (mask 0003)
[    0.380657] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at  0068 (mask 0007)
[    0.380769] pci 0000:00:1f.2: reg 10 io port: [0x60d8-0x60df]
[    0.380786] pci 0000:00:1f.2: reg 14 io port: [0x60fc-0x60ff]
[    0.380802] pci 0000:00:1f.2: reg 18 io port: [0x60d0-0x60d7]
[    0.380817] pci 0000:00:1f.2: reg 1c io port: [0x60f8-0x60fb]
[    0.380832] pci 0000:00:1f.2: reg 20 io port: [0x6020-0x602f]
[    0.380848] pci 0000:00:1f.2: reg 24 32bit mmio:  [0x58344000-0x583443ff]
[    0.380902] pci 0000:00:1f.2: PME# supported from D3hot
[    0.380912] pci 0000:00:1f.2: PME# disabled
[    0.381000] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    0.381143] pci 0000:01:00.0: reg 10 64bit mmio:  [0x57100000-0x5710ffff]
[    0.381256] pci 0000:01:00.0: supports D1
[    0.381263] pci 0000:01:00.0: PME# supported from D0 D1 D3hot
[    0.381275] pci 0000:01:00.0: PME# disabled
[    0.381384] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    0.381395] pci 0000:00:1c.0: bridge 32bit mmio:  [0x57100000-0x581fffff]
[    0.381411] pci 0000:00:1c.0: bridge 64bit mmio pref:  [0x50000000-0x50ffffff]
[    0.381503] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.381516] pci 0000:00:1c.1: bridge 32bit mmio:  [0x56100000-0x570fffff]
[    0.381533] pci 0000:00:1c.1: bridge 64bit mmio pref:  [0x51000000-0x51ffffff]
[    0.381642] pci 0000:03:00.0: reg 10 64bit mmio:  [0x55000000-0x5503ffff]
[    0.381664] pci 0000:03:00.0: reg 18 io port: [0x2000-0x207f]
[    0.381771] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot  D3cold
[    0.381783] pci 0000:03:00.0: PME# disabled
[    0.381886] pci 0000:00:1c.2: bridge io port: [0x2000-0x3fff]
[    0.381898] pci 0000:00:1c.2: bridge 32bit mmio:  [0x55000000-0x560fffff]
[    0.381914] pci 0000:00:1c.2: bridge 64bit mmio pref:  [0x52000000-0x52ffffff]
[    0.382000] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
[    0.382012] pci 0000:00:1c.3: bridge 32bit mmio:  [0x54000000-0x54ffffff]
[    0.382027] pci 0000:00:1c.3: bridge 64bit mmio pref:  [0x53000000-0x53ffffff]
[    0.382117] pci 0000:00:1e.0: transparent bridge
[    0.382176] pci_bus 0000:00: on NUMA node 0
[    0.382198] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.382781] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.383126] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.383400] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.383659] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.384224] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.384245] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.402102] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11  12)
[    0.402452] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11  12)
[    0.402803] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11  12)
[    0.403140] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11  12)
[    0.403480] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12)  *0, disabled.
[    0.403825] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12)  *0, disabled.
[    0.404216] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12)  *0, disabled.
[    0.404563] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12)  *0, disabled.
[    0.404937] vgaarb: device added:  PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.404972] vgaarb: loaded
[    0.405318] SCSI subsystem initialized
[    0.405568] libata version 3.00 loaded.
[    0.405850] usbcore: registered new interface driver usbfs
[    0.405900] usbcore: registered new interface driver hub
[    0.406010] usbcore: registered new device driver usb
[    0.406684] ACPI: WMI: Mapper loaded
[    0.406691] PCI: Using ACPI for IRQ routing
[    0.407126] NetLabel: Initializing
[    0.407133] NetLabel:  domain hash size = 128
[    0.407138] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.407172] NetLabel:  unlabeled traffic allowed by default
[    0.407294] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.407311] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.412094] Switching to clocksource tsc
[    0.416945] AppArmor: AppArmor Filesystem Enabled
[    0.416986] pnp: PnP ACPI init
[    0.417026] ACPI: bus type pnp registered
[    0.480103] pnp 00:01: io resource (0x164e-0x164f) overlaps  0000:00:1c.3 BAR 13 (0x1000-0x1fff), disabling
[    0.482745] pnp: PnP ACPI: found 9 devices
[    0.482756] ACPI: ACPI bus type pnp unregistered
[    0.482766] PnPBIOS: Disabled by ACPI PNP
[    0.482801] system 00:01: ioport range 0x200-0x20f has been reserved
[    0.482812] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.482822] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.482832] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.482842] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.482864] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.482877] system 00:01: ioport range 0xff2c-0xff2f has been  reserved
[    0.482890] system 00:01: iomem range 0xe0000000-0xefffffff has been  reserved
[    0.482901] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been  reserved
[    0.482912] system 00:01: iomem range 0xfed14000-0xfed17fff has been  reserved
[    0.482922] system 00:01: iomem range 0xfed18000-0xfed18fff has been  reserved
[    0.482933] system 00:01: iomem range 0xfed19000-0xfed19fff has been  reserved
[    0.482946] system 00:01: iomem range 0xfec00000-0xfec00fff could not  be reserved
[    0.482991] system 00:01: iomem range 0xfee00000-0xfee00fff has been  reserved
[    0.518224] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.518237] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.518251] pci 0000:00:1c.0:   MEM window: 0x57100000-0x581fffff
[    0.518263] pci 0000:00:1c.0:   PREFETCH window:  0x00000050000000-0x00000050ffffff
[    0.518278] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.518288] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.518300] pci 0000:00:1c.1:   MEM window: 0x56100000-0x570fffff
[    0.518312] pci 0000:00:1c.1:   PREFETCH window:  0x00000051000000-0x00000051ffffff
[    0.518328] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.518337] pci 0000:00:1c.2:   IO window: 0x2000-0x3fff
[    0.518350] pci 0000:00:1c.2:   MEM window: 0x55000000-0x560fffff
[    0.518361] pci 0000:00:1c.2:   PREFETCH window:  0x00000052000000-0x00000052ffffff
[    0.518377] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.518386] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    0.518399] pci 0000:00:1c.3:   MEM window: 0x54000000-0x54ffffff
[    0.518410] pci 0000:00:1c.3:   PREFETCH window:  0x00000053000000-0x00000053ffffff
[    0.518426] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.518433] pci 0000:00:1e.0:   IO window: disabled
[    0.518444] pci 0000:00:1e.0:   MEM window: disabled
[    0.518453] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.518498]   alloc irq_desc for 16 on node -1
[    0.518506]   alloc kstat_irqs on node -1
[    0.518524] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[    0.518537] pci 0000:00:1c.0: setting latency timer to 64
[    0.518557] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.518568]   alloc irq_desc for 17 on node -1
[    0.518574]   alloc kstat_irqs on node -1
[    0.518586] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low)  -> IRQ 17
[    0.518599] pci 0000:00:1c.1: setting latency timer to 64
[    0.518619]   alloc irq_desc for 18 on node -1
[    0.518625]   alloc kstat_irqs on node -1
[    0.518636] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low)  -> IRQ 18
[    0.518647] pci 0000:00:1c.2: setting latency timer to 64
[    0.518666] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.518675]   alloc irq_desc for 19 on node -1
[    0.518681]   alloc kstat_irqs on node -1
[    0.518692] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low)  -> IRQ 19
[    0.518706] pci 0000:00:1c.3: setting latency timer to 64
[    0.518722] pci 0000:00:1e.0: setting latency timer to 64
[    0.518735] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.518744] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.518753] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.518762] pci_bus 0000:01: resource 1 mem: [0x57100000-0x581fffff]
[    0.518771] pci_bus 0000:01: resource 2 pref mem  [0x50000000-0x50ffffff]
[    0.518779] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.518788] pci_bus 0000:02: resource 1 mem: [0x56100000-0x570fffff]
[    0.518797] pci_bus 0000:02: resource 2 pref mem  [0x51000000-0x51ffffff]
[    0.518807] pci_bus 0000:03: resource 0 io:  [0x2000-0x3fff]
[    0.518816] pci_bus 0000:03: resource 1 mem: [0x55000000-0x560fffff]
[    0.518824] pci_bus 0000:03: resource 2 pref mem  [0x52000000-0x52ffffff]
[    0.518832] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
[    0.518841] pci_bus 0000:04: resource 1 mem: [0x54000000-0x54ffffff]
[    0.518851] pci_bus 0000:04: resource 2 pref mem  [0x53000000-0x53ffffff]
[    0.518861] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.518870] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.519005] NET: Registered protocol family 2
[    0.519286] IP route cache hash table entries: 32768 (order: 5,  131072 bytes)
[    0.520219] TCP established hash table entries: 131072 (order: 8,  1048576 bytes)
[    0.521427] TCP bind hash table entries: 65536 (order: 7, 524288  bytes)
[    0.521983] TCP: Hash tables configured (established 131072 bind  65536)
[    0.521992] TCP reno registered
[    0.522342] NET: Registered protocol family 1
[    0.522407] pci 0000:00:02.0: Boot video device
[    0.522730] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.522737] Simple Boot Flag at 0x44 set to 0x1
[    0.523296] cpufreq-nforce2: No nForce2 chipset.
[    0.523385] Scanning for low memory corruption every 60 seconds
[    0.523719] audit: initializing netlink socket (disabled)
[    0.523747] type=2000 audit(1274071922.522:1): initialized
[    0.545257] highmem bounce pool size: 64 pages
[    0.545273] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.550537] VFS: Disk quotas dquot_6.5.2
[    0.550731] Dquot-cache hash table entries: 1024 (order 0, 4096  bytes)
[    0.552795] fuse init (API version 7.13)
[    0.553079] msgmni has been set to 1716
[    0.553768] alg: No test for stdrng (krng)
[    0.553975] Block layer SCSI generic (bsg) driver version 0.4 loaded  (major 253)
[    0.553986] io scheduler noop registered
[    0.553992] io scheduler anticipatory registered
[    0.553998] io scheduler deadline registered
[    0.554138] io scheduler cfq registered (default)
[    0.554489]   alloc irq_desc for 24 on node -1
[    0.554497]   alloc kstat_irqs on node -1
[    0.554520] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.554539] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.554830]   alloc irq_desc for 25 on node -1
[    0.554838]   alloc kstat_irqs on node -1
[    0.554856] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.554874] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.555181]   alloc irq_desc for 26 on node -1
[    0.555188]   alloc kstat_irqs on node -1
[    0.555213] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.555231] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.555514]   alloc irq_desc for 27 on node -1
[    0.555521]   alloc kstat_irqs on node -1
[    0.555541] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.555560] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.555853] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.556148] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.556169] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.556544] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.556565] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.556932] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.556951] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.557293] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.557312] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.557735] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.557755] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.558098] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.558117] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.558466] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.558486] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.558829] ACPI Error (dsfield-0143): [CAPB] Namespace lookup  failure, AE_ALREADY_EXISTS
[    0.558848] ACPI Error (psparse-0537): Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.559069] pciehp: PCI Express Hot Plug Controller Driver version:  0.4
[    0.598170] Freeing initrd memory: 7770k freed
[    0.623207] ACPI: AC Adapter [AC] (off-line)
[    0.623429] input: Power Button as  /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.623438] ACPI: Power Button [PWRB]
[    0.623544] input: Lid Switch as  /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.623642] ACPI: Lid Switch [LID0]
[    0.623751] input: Sleep Button as  /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.623759] ACPI: Sleep Button [SLPB]
[    0.623887] input: Power Button as  /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.623893] ACPI: Power Button [PWRF]
[    0.624200] fan PNP0C0B:00: registered as cooling_device0
[    0.624214] ACPI: Fan [FAN] (on)
[    0.625644] ACPI: SSDT 3f5b7c90 00239 (v02  PmRef  Cpu0Ist 00003000  INTL 20051117)
[    0.626491] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001  INTL 20051117)
[    0.628232] Marking TSC unstable due to TSC halts in idle
[    0.628385] Switching to clocksource hpet
[    0.628587] processor LNXCPU:00: registered as cooling_device1
[    0.629383] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000  INTL 20051117)
[    0.630149] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000  INTL 20051117)
[    0.632077] processor LNXCPU:01: registered as cooling_device2
[    0.699958] thermal LNXTHERM:01: registered as thermal_zone0
[    0.699978] ACPI: Thermal Zone [THRM] (27 C)
[    0.700364] isapnp: Scanning for PnP cards...
[    0.704911] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.708682] brd: module loaded
[    0.710129] loop: module loaded
[    0.710380] input: Macintosh mouse button emulation as  /devices/virtual/input/input4
[    0.711650] Fixed MDIO Bus: probed
[    0.711772] PPP generic driver version 2.4.2
[    0.711882] tun: Universal TUN/TAP device driver, 1.6
[    0.711889] tun: (C) 1999-2004 Max Krasnyansky  <maxk@qualcomm.com>
[    0.712167] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI)  Driver
[    0.712221] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level,  low) -> IRQ 16
[    0.712258] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.712267] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.712374] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned  bus number 1
[    0.712424] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.712444] ehci_hcd 0000:00:1d.7: debug port 1
[    0.716326] ehci_hcd 0000:00:1d.7: cache line size of 32 is not  supported
[    0.716362] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58344400
[    0.732038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.732287] usb usb1: configuration #1 chosen from 1 choice
[    0.732370] hub 1-0:1.0: USB hub found
[    0.732392] hub 1-0:1.0: 8 ports detected
[    0.732555] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732598] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732671] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level,  low) -> IRQ 16
[    0.732688] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.732699] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.732800] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned  bus number 2
[    0.732847] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
[    0.733091] usb usb2: configuration #1 chosen from 1 choice
[    0.733173] hub 2-0:1.0: USB hub found
[    0.733193] hub 2-0:1.0: 2 ports detected
[    0.733308] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level,  low) -> IRQ 17
[    0.733324] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.733332] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.733429] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned  bus number 3
[    0.733489] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
[    0.733734] usb usb3: configuration #1 chosen from 1 choice
[    0.733813] hub 3-0:1.0: USB hub found
[    0.733832] hub 3-0:1.0: 2 ports detected
[    0.733947] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level,  low) -> IRQ 18
[    0.733962] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.733971] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.734060] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned  bus number 4
[    0.734116] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
[    0.734373] usb usb4: configuration #1 chosen from 1 choice
[    0.734451] hub 4-0:1.0: USB hub found
[    0.734470] hub 4-0:1.0: 2 ports detected
[    0.734585] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level,  low) -> IRQ 19
[    0.734599] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.734608] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.734701] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned  bus number 5
[    0.734757] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
[    0.735021] usb usb5: configuration #1 chosen from 1 choice
[    0.735100] hub 5-0:1.0: USB hub found
[    0.735120] hub 5-0:1.0: 2 ports detected
[    0.735358] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at  0x60,0x64 irq 1,12
[    0.759953] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.759973] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.760372] mice: PS/2 mouse device common for all mice
[    0.760807] rtc_cmos 00:03: RTC can wake from S4
[    0.760919] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.760970] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.761299] device-mapper: uevent: version 1.0.3
[    0.761625] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01)  initialised: dm-devel@redhat.com
[    0.761837] device-mapper: multipath: version 1.1.0 loaded
[    0.761845] device-mapper: multipath round-robin: version 1.0.0  loaded
[    0.762185] EISA: Probing bus 0 at eisa.0
[    0.762201] Cannot allocate resource for EISA slot 1
[    0.762207] Cannot allocate resource for EISA slot 2
[    0.762213] Cannot allocate resource for EISA slot 3
[    0.762220] Cannot allocate resource for EISA slot 4
[    0.762226] Cannot allocate resource for EISA slot 5
[    0.762233] Cannot allocate resource for EISA slot 6
[    0.762251] EISA: Detected 0 cards.
[    0.762681] cpuidle: using governor ladder
[    0.763023] cpuidle: using governor menu
[    0.764341] TCP cubic registered
[    0.764845] NET: Registered protocol family 10
[    0.766139] lo: Disabled Privacy Extensions
[    0.767057] NET: Registered protocol family 17
[    0.769175] Using IPI No-Shortcut mode
[    0.769419] PM: Resume from disk failed.
[    0.769459] registered taskstats version 1
[    0.770113]   Magic number: 10:32:869
[    0.770266] rtc_cmos 00:03: setting system clock to 2010-05-17  04:52:03 UTC (1274071923)
[    0.770275] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.770280] EDD information not available.
[    0.781049] input: AT Translated Set 2 keyboard as  /devices/platform/i8042/serio0/input/input5
[    1.055629] isapnp: No Plug & Play device found
[    1.055699] Freeing unused kernel memory: 656k freed
[    1.056361] Write protecting the kernel text: 4676k
[    1.056438] Write protecting the kernel read-only data: 1840k
[    1.080096] usb 1-2: new high speed USB device using ehci_hcd and  address 2
[    1.095349] udev: starting version 151
[    1.352366] ACPI: Battery Slot [BAT0] (battery present)
[    1.386531] usb 1-2: configuration #1 chosen from 1 choice
[    2.245949] ahci 0000:00:1f.2: version 3.0
[    2.245989] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low)  -> IRQ 17
[    2.246063]   alloc irq_desc for 28 on node -1
[    2.246071]   alloc kstat_irqs on node -1
[    2.246097] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    2.246183] ahci: SSS flag set, parallel bus scan disabled
[    2.246246] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5  Gbps 0x5 impl SATA mode
[    2.246259] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo  pio slum part 
[    2.246272] ahci 0000:00:1f.2: setting latency timer to 64
[    2.246759] scsi0 : ahci
[    2.247111] scsi1 : ahci
[    2.247331] scsi2 : ahci
[    2.247542] scsi3 : ahci
[    2.248286] ata1: SATA max UDMA/133 abar m1024@0x58344000 port  0x58344100 irq 28
[    2.248295] ata2: DUMMY
[    2.248304] ata3: SATA max UDMA/133 abar m1024@0x58344000 port  0x58344200 irq 28
[    2.248312] ata4: DUMMY
[    2.564192] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.565496] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES)  filtered out
[    2.602984] ata1.00: ATA-8: WDC WD1200BEVT-00A23T0, 01.01A01, max  UDMA/133
[    2.603000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth  31/32), AA
[    2.604750] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by  device (Stat=0x51 Err=0x04)
[    2.605170] ata1.00: configured for UDMA/133
[    2.620509] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVT-0  01.0 PQ: 0 ANSI: 5
[    2.620849] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.621165] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120  GB/111 GiB)
[    2.621309] sd 0:0:0:0: [sda] Write Protect is off
[    2.621316] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.621391] sd 0:0:0:0: [sda] Write cache: enabled, read cache:  enabled, doesn't support DPO or FUA
[    2.621767]  sda: sda1 sda2 < sda5 >
[    2.658412] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.940170] ata3: SATA link down (SStatus 0 SControl 300)
[    3.306988] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   11.307690] udev: starting version 151
[   11.368585] Adding 2974712k swap on /dev/sda5.  Priority:-1 extents:1  across:2974712k 
[   11.492675] lp: driver loaded but no devices found
[   11.584478] ath_pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[   11.584505] ath_pci 0000:01:00.0: setting latency timer to 64
[   11.715368] acpi device:24: registered as cooling_device3
[   11.715767] input: Video Bus as  /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   11.715890] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes   post: no)
[   12.194862] Linux agpgart interface v0.103
[   12.569836] [drm] Initialized drm 1.1.0 20060810
[   12.597807] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low)  -> IRQ 18
[   12.597833] atl1c 0000:03:00.0: setting latency timer to 64
[   12.609173] MadWifi: ath_attach: Switching rfkill capability off.
[   12.691543] intel_rng: FWH not detected
[   12.691791] Linux video capture interface: v2.00
[   12.696629] type=1505 audit(1274071935.425:2):   operation="profile_load" pid=600 name="/sbin/dhclient3"
[   12.697473] type=1505 audit(1274071935.425:3):   operation="profile_load" pid=600  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.697933] type=1505 audit(1274071935.425:4):   operation="profile_load" pid=600  name="/usr/lib/connman/scripts/dhclient-script"
[   12.716841] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   12.717222] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   12.720286] agpgart-intel 0000:00:00.0: AGP aperture is 256M @  0x40000000
[   12.727202] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
[   12.750546] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.754094] uvcvideo: Found UVC 1.00 device Webcam (04f2:b084)
[   12.764869] wifi0: Atheros AR9280 chip found (MAC 128.2, PHY 5133  13.0, Radio 12.0)
[   12.768039] input: Webcam as  /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
[   12.768237] usbcore: registered new interface driver uvcvideo
[   12.768250] USB Video Class driver (v0.1.0)
[   12.908683] acer-wmi: Unable to detect available WMID devices
[   12.932395] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low)  -> IRQ 16
[   12.932412] i915 0000:00:02.0: setting latency timer to 64
[   12.948167] ath_pci: wifi0: Atheros 9280: mem=0x57100000, irq=16
[   13.013238] [drm] set up 7M of stolen space
[   13.134614] [drm] initialized overlay support
[   13.418388] type=1505 audit(1274071936.145:5):   operation="profile_replace" pid=725 name="/sbin/dhclient3"
[   13.419226] type=1505 audit(1274071936.145:6):   operation="profile_replace" pid=725  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.419705] type=1505 audit(1274071936.145:7):   operation="profile_replace" pid=725  name="/usr/lib/connman/scripts/dhclient-script"
[   13.428217] type=1505 audit(1274071936.157:8):   operation="profile_load" pid=726 name="/usr/bin/evince"
[   13.438537] type=1505 audit(1274071936.165:9):   operation="profile_load" pid=726 name="/usr/bin/evince-previewer"
[   13.444914] type=1505 audit(1274071936.173:10):   operation="profile_load" pid=726 name="/usr/bin/evince-thumbnailer"
[   13.517569] type=1505 audit(1274071936.245:11):   operation="profile_load" pid=728 name="/usr/lib/cups/backend/cups-pdf"
[   13.562187] fb0: inteldrmfb frame buffer device
[   13.562195] registered panic notifier
[   13.562211] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on  minor 0
[   13.562303] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level,  low) -> IRQ 16
[   13.562356] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.569443] vga16fb: initializing
[   13.569457] vga16fb: mapped to 0xc00a0000
[   13.569469] vga16fb: not registering due to another framebuffer  present
[   13.698857] hda_codec: ALC272: BIOS auto-probing.
[   13.700671] input: HDA Digital PCBeep as  /devices/pci0000:00/0000:00:1b.0/input/input8
[   13.751470] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps:  0xd04771/0xa40000
[   13.836646] input: SynPS/2 Synaptics TouchPad as  /devices/platform/i8042/serio1/input/input9
[   13.909961] Console: switching to colour frame buffer device 128x37
[   15.206775] ppdev: user-space parallel port driver
[   15.904837] CPU0 attaching NULL sched-domain.
[   15.904849] CPU1 attaching NULL sched-domain.
[   15.939896] CPU0 attaching sched-domain:
[   15.939904]  domain 0: span 0-1 level SIBLING
[   15.939911]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   15.939924]   domain 1: span 0-1 level MC
[   15.939929]    groups: 0-1 (cpu_power = 1178)
[   15.939942] CPU1 attaching sched-domain:
[   15.939947]  domain 0: span 0-1 level SIBLING
[   15.939952]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   15.939964]   domain 1: span 0-1 level MC
[   15.939969]    groups: 0-1 (cpu_power = 1178)
[   20.258687] CPU0 attaching NULL sched-domain.
[   20.258703] CPU1 attaching NULL sched-domain.
[   20.280187] CPU0 attaching sched-domain:
[   20.280199]  domain 0: span 0-1 level SIBLING
[   20.280208]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   20.280228]   domain 1: span 0-1 level MC
[   20.280236]    groups: 0-1 (cpu_power = 1178)
[   20.280254] CPU1 attaching sched-domain:
[   20.280262]  domain 0: span 0-1 level SIBLING
[   20.280270]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   20.280287]   domain 1: span 0-1 level MC
[   20.280295]    groups: 0-1 (cpu_power = 1178)
[   21.322232]   alloc irq_desc for 29 on node -1
[   21.322240]   alloc kstat_irqs on node -1
[   21.322266] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[   21.323037] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.954310] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[   24.955296] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.389324] ath0: unknown SIOCSIWAUTH flag 12
[   27.769382] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   29.524757] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   30.124771] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   30.579038] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   30.819438] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   31.069926] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   31.660411] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   32.356440] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   33.745354] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   34.127098] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   34.441865] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   34.970181] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[   35.124111] ath0: no IPv6 routers present
[   37.005528] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  102.761169] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  102.765125] wifi0: FAILED verification of AR5K_PHY_AGCSIZE_DESIRED  default value [found=0xc4 (-60) expected=0xde (-34)].
[  102.765125]               (unknown):0x9850:0x6de000e2:.11.11.1  111..... ........ 111...1.:unknown
[  103.019359] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  104.452773] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  105.240442] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  177.761152] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  177.765108] wifi0: FAILED verification of AR5K_PHY_AGCSIZE_DESIRED  default value [found=0xc4 (-60) expected=0xde (-34)].
[  177.765108]               (unknown):0x9850:0x6de000e2:.11.11.1  111..... ........ 111...1.:unknown
[  177.795978] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  178.485829] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  179.100136] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  180.296493] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  244.706442] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  253.645155] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  254.464365] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  323.654450] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  329.623724] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  330.033813] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  345.130042] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  404.475924] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  478.816327] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  479.020809] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  479.430500] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  552.760644] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  554.077685] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  628.622941] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  628.827412] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  629.237208] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  629.442209] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  650.647519] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  688.187410] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  697.915109] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  705.113131] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  706.540182] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  738.770221] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  738.911004] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  739.131682] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  739.442873] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  739.884420] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  741.471806] ath0: unknown SIOCSIWAUTH flag 12
[  751.878262] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  808.021965] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  809.045832] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  809.455483] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  810.070142] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  831.952591] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  883.693242] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  884.307691] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  884.489771] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  885.127157] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  891.648689] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  891.798175] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  892.412398] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  894.219886] ath0: unknown SIOCSIWAUTH flag 12
[  924.727035] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  958.648635] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  958.854168] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  959.058006] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  959.262103] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  959.468785] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  979.916011] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[  993.944354] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1009.715408] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1011.555390] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1012.423778] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1012.643691] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1012.864963] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1013.963889] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1014.231836] ath0: unknown SIOCSIWAUTH flag 12
[ 1020.569501] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1077.787942] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1078.531776] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1078.964091] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1152.760840] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1153.611787] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1182.250853] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1182.612308] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1184.692248] ath0: unknown SIOCSIWAUTH flag 12
[ 1258.875252] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1259.284905] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1259.489510] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1269.800119] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1270.563694] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1272.241164] ath0: unknown SIOCSIWAUTH flag 12
[ 1291.309846] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1291.977653] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1292.199704] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1292.420400] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1293.080632] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1294.007783] ath0: unknown SIOCSIWAUTH flag 12
[ 1339.431189] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1362.788112] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1363.628331] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1364.036803] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1364.651040] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1384.586929] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1384.955846] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1385.483814] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1386.143913] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1387.293059] ath0: unknown SIOCSIWAUTH flag 12
[ 1399.332117] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1399.674556] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1401.875840] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1402.143836] ath0: unknown SIOCSIWAUTH flag 12
[ 1467.787677] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1468.686253] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1468.891025] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1469.505430] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1509.921827] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1544.255033] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1617.760458] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1618.083647] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1618.470020] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1652.050498] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1735.812488] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1767.991910] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1768.401782] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1804.004179] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1804.668131] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1804.888718] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1806.443801] ath0: unknown SIOCSIWAUTH flag 12
[ 1850.288685] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1865.444726] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1873.870394] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1874.461820] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1874.691698] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1875.099008] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1947.760763] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1948.415066] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1948.824593] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1963.744515] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2005.829385] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2008.286904] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2023.677543] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2023.881506] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2024.473118] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2098.016777] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2098.631224] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2098.835962] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2099.450920] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2134.315859] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2172.787825] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2173.688106] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2174.302396] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2174.508149] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2248.642433] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2248.847075] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2273.904084] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2324.495670] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 2340.904202] usb 1-3: new high speed USB device using ehci_hcd and  address 3
[ 2341.040094] usb 1-3: configuration #1 chosen from 1 choice
[ 2341.363190] Initializing USB Mass Storage driver...
[ 2341.363539] scsi4 : SCSI emulation for USB Mass Storage devices
[ 2341.364127] usbcore: registered new interface driver usb-storage
[ 2341.364140] USB Mass Storage support registered.
[ 2341.367026] usb-storage: device found at 3
[ 2341.367034] usb-storage: waiting for device to settle before scanning
[ 2346.367521] usb-storage: device scan complete
[ 2346.369132] scsi 4:0:0:0: Direct-Access     LEXAR    JUMPDRIVE SPORT   3000 PQ: 0 ANSI: 0 CCS
[ 2346.380741] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 2346.383615] sd 4:0:0:0: [sdb] 252928 512-byte logical blocks: (129  MB/123 MiB)
[ 2346.384573] sd 4:0:0:0: [sdb] Write Protect is off
[ 2346.384587] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 2346.384596] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2346.388160] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2346.388178]  sdb: sdb1
[ 2346.526220] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2346.526249] sd 4:0:0:0: [sdb] Attached SCSI removable disk



```**6 ) Network configuration**      

```


  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 0c:ee:e6:85:f5:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical  ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.1  latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:16 memory:57100000-5710ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:5c:e2:ce
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:29 memory:55000000-5503ffff ioport:2000(size=128)


```[B]7 ) Scan for networks:
  
[/B]```


ath0      Scan completed :
          Cell 01 - Address: 00:1F:90:ED:CD:7E
                    ESSID:"CARO2"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-36 dBm  Noise level=-95  dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                     Extra:wme_ie=dd180050f2020101020003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:1F:90:E2:83:FA
                    ESSID:"RFZ30"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95  dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                     Extra:wme_ie=dd180050f2020101020003a4000027a4000042435e0062322f00
          Cell 03 - Address: 00:18:01:EA:CD:73
                    ESSID:"KT9T1"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=13/70  Signal level=-82 dBm  Noise level=-95  dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                     Extra:wme_ie=dd180050f2020101020003a4000027a4000042435e0062322f00
          Cell 04 - Address: 00:21:29:96:36:94
                    ESSID:"DumpoNet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-78 dBm  Noise level=-95  dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                     Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00


```[B]8 ) Ubuntu Version: 
[/B]
Description:   Ubuntu 10.04 LTS



[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
  
[/B]2.6.32-22-generic i686


[B]10 ) Restarting the network:
  
[/B]-- Done ... no change  --




If you need anything else, or if this needs to be refined, please let me  know!

Thanks.

---

### Post by NUboon2Age on 2010-05-17
Does Jockey, the GUI third party driver manager come up with anything when you run it?

System->Administration->Hardware Drivers

**If it comes up with ath5k** and **you enable it** and [B]then you

Changed /etc/modprobe.d/blacklist-ath_pci.conf[/B] from

# other comments, blah, blah, blah
blacklist ath5k

to

#blacklist ath5k
blacklist ath_hal
blacklist ath_pci

If you do all this and it works, you'll have essentially replaced your previous ath_hal and ath_pci drivers with ath5k.  

This worked for this person:
[http://ubuntuforums.org/showthread.php?t=1238766](http://ubuntuforums.org/showthread.php?t=1238766)

---

### Post by Capt. Easy on 2010-05-17
System->Administration->Hardware Drivers only shows Alternate Atheros "madwifi" driver.

it notes:

> 

Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.



---

### Post by Capt. Easy on 2010-05-23
Okay, I'm officially baffled.

I spent quite a bit of time running a couple other distros.  In particular, I spent the weekend with Mandriva.  It was very impressive, but probably better suited to a desktop -- it struck me as a bit unwieldy for a netbook.  But ... my wireless worked right away.

Just for the heck of it I reloaded 10.04 Netbook Edition, downloaded the updates, didn't see anything that really struck me as helpful/hopeful, configured the wireless and gave it one more try.

And logged right in.  :?

Straight off the same CD I've been using all along.  BTSOOM.  (Beats the ... stuffing ... out of me!)



Anyway, I want to try some of the other versions of Ubuntu (although I suppose I really should leave well enough alone) before I decide which one I'm going to use.  And I may try WICD again.  I'll be back if anything breaks!

Thanks for all the help.  I wish I could say what happened.

---

