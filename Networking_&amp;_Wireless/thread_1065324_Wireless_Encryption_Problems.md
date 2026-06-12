---
title: "Wireless Encryption Problems"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by iceman_ch on 2009-02-09
Ok so I've got my wireless working out of the box.  The only problem is if I try and connect to the encrypted network at my school I get a kernel freeze.  I've tried useing ndiswrapper and that didn't help at all.  Also the first time I installed ubuntu the wirelless worked really well but I reinstalled it and now I have to go into term and type the command

sudo iwlist wl0 sacn

Once I do that the wirelless "wakes up"

Here is some more information
chris@chris-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GT [10de:0407] (rev a1)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)



chris@chris-laptop:~$ lsusb
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 006 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 006 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 006 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



chris@chris-laptop:~$ sudo iwlist scan
[sudo] password for chris: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:F6:E9:CB
                    ESSID:"dd-wrt"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-38 dBm  Noise level:-24 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:22:A4:08:5A:61
                    ESSID:"2WIRE336"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-85 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:16:B6:AF:6D:D5
                    ESSID:"linksys"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-61 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

chris@chris-laptop:~$ uname -rm
2.6.27-11-generic i686


chris@chris-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:61:54:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:cf:c8:d8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.2.109 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:3c:82:38:8b:19
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
chris@chris-laptop:~$

---

### Post by pytheas22 on 2009-02-09
There's an alternate driver that might work better for your card (currently it's using the 'wl' driver; the alternate driver is 'b43').  Please post the output of these commands so we can see if b43 would work (you will need to have an Internet connection for the first two commands here):
```

sudo apt-get update
sudo apt-get install b43-fwcutter
sudo rmmod wl
sudo rmmod b43
sudo modprobe b43
iwconfig
dmesg | tail -50
```

At this point, your card should be up under the 'b43' driver and you can try connecting.  Does it work better?  If so, we will make these changes permanent (for the time being, rebooting your machine will erase these modifications).

---

### Post by iceman_ch on 2009-02-11
I tried it.  Same results.  Everything went through smooth when I did the iwconfig it listed Wl0 and Wl10.

I have to use the command 

sudo iwlist wl scan 

to get the wireless turned on then I do the following.

sudo rmmod wl
sudo rmmod b43
sudo modprobe b43

The light stays off until I run the iwlist command again.

---

### Post by pytheas22 on 2009-02-11
I'm not sure why the iwlist command is needed to wake the card up, but there may be some weird issue with your hardware.  As a workaround, you could try writing a boot script that would force the card to scan once during boot time, waking it up.  To do that, first type:
```

sudo gedit /etc/init.d/wifi-fix.sh
```

A blank file will open.  Paste in these lines:
```

#!/bin/bash

ifconfig wlan0 up
iwlist scan
```

Then save and close the file, and run these commands:
```

cd /etc/init.d
sudo chmod +x wifi-fix.sh
sudo update-rc.d wifi-fix.sh defaults
```

Then reboot.  Does the card work automatically now?  If not, it would still be useful to see the output of this command:
```

dmesg
```

---

### Post by iceman_ch on 2009-02-12
I tried the script and it still won't start up on boot.  Should I change it so that it say

iwlsit wl scan

I checked in the system administration hardwaredrivers and found that the broadcom driver had been unchecked.  So I rechecked it.  Here is the infromatioin from dmesg.  It's alot of information 

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe72000 (usable)
[    0.000000]  BIOS-e820: 00000000dfe72000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xdfe72 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781c000 - 37fef804
[    0.000000] ACPI: RSDP 000FBC80, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT DFE73A00, 0064 (r1 DELL    M08     27D80313 ASL        61)
[    0.000000] ACPI: FACP DFE7389C, 00F4 (r4 DELL    M08     27D80313 ASL        61)
[    0.000000] ACPI: DSDT DFE74000, 4BD7 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS DFE82800, 0040
[    0.000000] ACPI: HPET DFE73B00, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC DFE73C00, 0068 (r1 DELL    M08     27D80313 ASL        47)
[    0.000000] ACPI: MCFG DFE73BC0, 003E (r16 DELL    M08     27D80313 ASL        61)
[    0.000000] ACPI: SLIC DFE73C9C, 0176 (r1 DELL    M08     27D80313 ASL        61)
[    0.000000] ACPI: OSFR DFE73200, 002C (r1 DELL    M08     27D80313 ASL        61)
[    0.000000] ACPI: BOOT DFE737C0, 0028 (r1 DELL    M08     27D80313 ASL        61)
[    0.000000] ACPI: SSDT DFE7217E, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] 2686MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781c000 - 0037fef804]          RAMDISK ==> [003781c000 - 0037fef804]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000dfe72
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dfe72
[    0.000000] On node 0 totalpages: 917009
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 681685 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e2000000 (gap: e0000000:14000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 908948
[    0.000000] Kernel command line: root=UUID=1247b7f5-5370-47d0-b545-fa2da83601e2 ro quiet splash i8042.nomux=1
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2393.989 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3620916k/3668424k available (2576k kernel code, 46132k reserved, 1165k data, 424k init, 2750920k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.97 BogoMIPS (lpj=9575956)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017668] ACPI: Core revision 20080609
[    0.019265] ACPI: Checking initramfs for custom DSDT
[    0.303498] ENABLING IO-APIC IRQs
[    0.303683] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.343829] CPU0: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.344021] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4787.94 BogoMIPS (lpj=9575890)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.428549] CPU1: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.428564] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.432044] Brought up 2 CPUs
[    0.432046] Total of 2 processors activated (9575.92 BogoMIPS).
[    0.432065] CPU0 attaching sched-domain:
[    0.432068]  domain 0: span 0-1 level MC
[    0.432070]   groups: 0 1
[    0.432075] CPU1 attaching sched-domain:
[    0.432076]  domain 0: span 0-1 level MC
[    0.432078]   groups: 1 0
[    0.432143] net_namespace: 840 bytes
[    0.432143] Booting paravirtualized kernel on bare hardware
[    0.432250] Time: 10:04:02  Date: 02/12/09
[    0.432277] NET: Registered protocol family 16
[    0.432292] EISA bus registered
[    0.432292] ACPI: bus type pci registered
[    0.432292] PCI: MCFG configuration 0: base f4000000 segment 0 buses 0 - 63
[    0.432292] PCI: MCFG area at f4000000 reserved in E820
[    0.432292] PCI: Using MMCONFIG for extended config space
[    0.432292] PCI: Using configuration type 1 for base access
[    0.432672] ACPI: EC: Look up EC in DSDT
[    0.432847] ACPI: BIOS _OSI(Linux) query ignored
[    0.432849] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    0.455765] ACPI: Interpreter enabled
[    0.455768] ACPI: (supports S0 S3 S4 S5)
[    0.455779] ACPI: Using IOAPIC for interrupt routing
[    0.498082] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.498082] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.498082] pci 0000:00:01.0: PME# disabled
[    0.498082] PCI: 0000:00:1a.0 reg 20 io port: [6f20, 6f3f]
[    0.498082] PCI: 0000:00:1a.1 reg 20 io port: [6f00, 6f1f]
[    0.500093] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fed1c400, fed1c7ff]
[    0.500150] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.500155] pci 0000:00:1a.7: PME# disabled
[    0.500200] PCI: 0000:00:1b.0 reg 10 64bit mmio: [febfc000, febfffff]
[    0.500253] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.500257] pci 0000:00:1b.0: PME# disabled
[    0.500327] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.500331] pci 0000:00:1c.0: PME# disabled
[    0.500400] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.500405] pci 0000:00:1c.1: PME# disabled
[    0.500479] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.500484] pci 0000:00:1c.4: PME# disabled
[    0.500532] PCI: 0000:00:1d.0 reg 20 io port: [6f80, 6f9f]
[    0.500593] PCI: 0000:00:1d.1 reg 20 io port: [6f60, 6f7f]
[    0.500655] PCI: 0000:00:1d.2 reg 20 io port: [6f40, 6f5f]
[    0.500722] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fed1c000, fed1c3ff]
[    0.500777] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.500783] pci 0000:00:1d.7: PME# disabled
[    0.500939] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.500943] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.500971] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
[    0.500979] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
[    0.500986] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
[    0.500994] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
[    0.501001] PCI: 0000:00:1f.1 reg 20 io port: [6fa0, 6faf]
[    0.501072] PCI: 0000:00:1f.2 reg 10 io port: [6eb0, 6eb7]
[    0.501080] PCI: 0000:00:1f.2 reg 14 io port: [6eb8, 6ebb]
[    0.501087] PCI: 0000:00:1f.2 reg 18 io port: [6ec0, 6ec7]
[    0.501095] PCI: 0000:00:1f.2 reg 1c io port: [6ec8, 6ecb]
[    0.501102] PCI: 0000:00:1f.2 reg 20 io port: [6ee0, 6eff]
[    0.501110] PCI: 0000:00:1f.2 reg 24 32bit mmio: [febfb800, febfbfff]
[    0.501142] pci 0000:00:1f.2: PME# supported from D3hot
[    0.501146] pci 0000:00:1f.2: PME# disabled
[    0.501166] PCI: 0000:00:1f.3 reg 10 32bit mmio: [febfb700, febfb7ff]
[    0.501192] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
[    0.501264] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.501279] PCI: 0000:01:00.0 reg 14 64bit mmio: [e0000000, efffffff]
[    0.501295] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.501304] PCI: 0000:01:00.0 reg 24 io port: [ef00, ef7f]
[    0.501312] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.501387] PCI: bridge 0000:00:01.0 io port: [e000, efff]
[    0.501390] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, feafffff]
[    0.501394] PCI: bridge 0000:00:01.0 64bit mmio pref: [e0000000, efffffff]
[    0.501471] PCI: 0000:09:00.0 reg 10 64bit mmio: [f9ffc000, f9ffffff]
[    0.501482] PCI: 0000:09:00.0 reg 18 io port: [de00, deff]
[    0.501555] pci 0000:09:00.0: supports D1
[    0.501556] pci 0000:09:00.0: supports D2
[    0.501558] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.501564] pci 0000:09:00.0: PME# disabled
[    0.501615] PCI: bridge 0000:00:1c.0 io port: [d000, dfff]
[    0.501620] PCI: bridge 0000:00:1c.0 32bit mmio: [f9f00000, f9ffffff]
[    0.501829] PCI: 0000:0b:00.0 reg 10 64bit mmio: [f9efc000, f9efffff]
[    0.502006] pci 0000:0b:00.0: supports D1
[    0.502007] pci 0000:0b:00.0: supports D2
[    0.502008] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
[    0.502020] pci 0000:0b:00.0: PME# disabled
[    0.502074] PCI: bridge 0000:00:1c.1 32bit mmio: [f9e00000, f9efffff]
[    0.502140] PCI: bridge 0000:00:1c.4 io port: [c000, cfff]
[    0.502144] PCI: bridge 0000:00:1c.4 32bit mmio: [f9c00000, f9dfffff]
[    0.502152] PCI: bridge 0000:00:1c.4 64bit mmio pref: [f0000000, f01fffff]
[    0.502210] PCI: 0000:03:09.0 reg 10 32bit mmio: [f9bff800, f9bfffff]
[    0.502264] pci 0000:03:09.0: supports D1
[    0.502266] pci 0000:03:09.0: supports D2
[    0.502267] pci 0000:03:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.502272] pci 0000:03:09.0: PME# disabled
[    0.502308] PCI: 0000:03:09.1 reg 10 32bit mmio: [f9bff400, f9bff4ff]
[    0.502363] pci 0000:03:09.1: supports D1
[    0.502364] pci 0000:03:09.1: supports D2
[    0.502366] pci 0000:03:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.502370] pci 0000:03:09.1: PME# disabled
[    0.502407] PCI: 0000:03:09.2 reg 10 32bit mmio: [f9bff500, f9bff5ff]
[    0.502460] pci 0000:03:09.2: supports D1
[    0.502462] pci 0000:03:09.2: supports D2
[    0.502463] pci 0000:03:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.502468] pci 0000:03:09.2: PME# disabled
[    0.502506] PCI: 0000:03:09.3 reg 10 32bit mmio: [f9bff600, f9bff6ff]
[    0.502559] pci 0000:03:09.3: supports D1
[    0.502560] pci 0000:03:09.3: supports D2
[    0.502561] pci 0000:03:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.502566] pci 0000:03:09.3: PME# disabled
[    0.502602] PCI: 0000:03:09.4 reg 10 32bit mmio: [f9bff700, f9bff7ff]
[    0.502656] pci 0000:03:09.4: supports D1
[    0.502657] pci 0000:03:09.4: supports D2
[    0.502659] pci 0000:03:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.502664] pci 0000:03:09.4: PME# disabled
[    0.502711] pci 0000:00:1e.0: transparent bridge
[    0.502719] PCI: bridge 0000:00:1e.0 32bit mmio: [f9b00000, f9bfffff]
[    0.502754] bus 00 -> node 0
[    0.502759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.503173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.503314] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.503407] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.503527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.503644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.512553] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.512553] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.512553] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    0.512553] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    0.512609] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.512730] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.512850] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.512956] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.513020] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.513020] pnp: PnP ACPI init
[    0.513020] ACPI: bus type pnp registered
[    0.532301] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.532304] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.532342] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.532342] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.532342] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.554345] pnp: PnP ACPI: found 13 devices
[    0.554345] ACPI: ACPI bus type pnp unregistered
[    0.554345] PnPBIOS: Disabled by ACPI PNP
[    0.554345] PCI: Using ACPI for IRQ routing
[    0.560039] NET: Registered protocol family 8
[    0.560041] NET: Registered protocol family 20
[    0.560054] NetLabel: Initializing
[    0.560054] NetLabel:  domain hash size = 128
[    0.560054] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.560059] NetLabel:  unlabeled traffic allowed by default
[    0.560066] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.560070] hpet0: 3 64-bit timers, 14318180 Hz
[    0.561456] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.561459]    actual entries 65620
[    0.561527] AppArmor: AppArmor Filesystem Enabled
[    0.561551] ACPI: RTC can wake from S4
[    0.564037] Switched to high resolution mode on CPU 0
[    0.564583] Switched to high resolution mode on CPU 1
[    0.568021] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    0.568024] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    0.568031] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    0.568037] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.568042] system 00:0a: ioport range 0x900-0x97f has been reserved
[    0.568044] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.568049] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.568052] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.568054] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    0.568056] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.568061] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.568064] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.568066] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.568069] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.568071] system 00:0c: iomem range 0x100000-0xdfe71fff could not be reserved
[    0.568073] system 00:0c: iomem range 0xdfe72000-0xdfefffff could not be reserved
[    0.568076] system 00:0c: iomem range 0xdff00000-0xdfffffff could not be reserved
[    0.568079] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.568081] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.568083] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.568086] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.568088] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.568091] system 00:0c: iomem range 0xfeda0000-0xfeda3fff could not be reserved
[    0.568094] system 00:0c: iomem range 0xfeda4000-0xfeda4fff could not be reserved
[    0.568096] system 00:0c: iomem range 0xfeda5000-0xfeda5fff could not be reserved
[    0.568099] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.568101] system 00:0c: iomem range 0xfed18000-0xfed1bfff could not be reserved
[    0.568103] system 00:0c: iomem range 0xf4000000-0xf7ffffff could not be reserved
[    0.603076] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.603079] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.603083] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfeafffff
[    0.603086] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.603090] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.603094] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.603100] pci 0000:00:1c.0:   MEM window: 0xf9f00000-0xf9ffffff
[    0.603104] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.603112] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0b
[    0.603113] pci 0000:00:1c.1:   IO window: disabled
[    0.603119] pci 0000:00:1c.1:   MEM window: 0xf9e00000-0xf9efffff
[    0.603123] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.603131] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0c
[    0.603134] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.603140] pci 0000:00:1c.4:   MEM window: 0xf9c00000-0xf9dfffff
[    0.603145] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.603153] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.603154] pci 0000:00:1e.0:   IO window: disabled
[    0.603160] pci 0000:00:1e.0:   MEM window: 0xf9b00000-0xf9bfffff
[    0.603164] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.603178] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.603182] pci 0000:00:01.0: setting latency timer to 64
[    0.603189] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.603194] pci 0000:00:1c.0: setting latency timer to 64
[    0.603203] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.603208] pci 0000:00:1c.1: setting latency timer to 64
[    0.603217] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.603221] pci 0000:00:1c.4: setting latency timer to 64
[    0.603229] pci 0000:00:1e.0: setting latency timer to 64
[    0.603233] bus: 00 index 0 io port: [0, ffff]
[    0.603235] bus: 00 index 1 mmio: [0, ffffffff]
[    0.603236] bus: 01 index 0 io port: [e000, efff]
[    0.603238] bus: 01 index 1 mmio: [fa000000, feafffff]
[    0.603240] bus: 01 index 2 mmio: [e0000000, efffffff]
[    0.603242] bus: 01 index 3 mmio: [0, 0]
[    0.603243] bus: 09 index 0 io port: [d000, dfff]
[    0.603245] bus: 09 index 1 mmio: [f9f00000, f9ffffff]
[    0.603247] bus: 09 index 2 mmio: [0, 0]
[    0.603248] bus: 09 index 3 mmio: [0, 0]
[    0.603250] bus: 0b index 0 mmio: [0, 0]
[    0.603251] bus: 0b index 1 mmio: [f9e00000, f9efffff]
[    0.603253] bus: 0b index 2 mmio: [0, 0]
[    0.603254] bus: 0b index 3 mmio: [0, 0]
[    0.603256] bus: 0c index 0 io port: [c000, cfff]
[    0.603258] bus: 0c index 1 mmio: [f9c00000, f9dfffff]
[    0.603260] bus: 0c index 2 mmio: [f0000000, f01fffff]
[    0.603261] bus: 0c index 3 mmio: [0, 0]
[    0.603263] bus: 03 index 0 mmio: [0, 0]
[    0.603265] bus: 03 index 1 mmio: [f9b00000, f9bfffff]
[    0.603266] bus: 03 index 2 mmio: [0, 0]
[    0.603268] bus: 03 index 3 io port: [0, ffff]
[    0.603270] bus: 03 index 4 mmio: [0, ffffffff]
[    0.603276] NET: Registered protocol family 2
[    0.616039] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.616221] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.616506] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.616651] TCP: Hash tables configured (established 131072 bind 65536)
[    0.616654] TCP reno registered
[    0.620051] NET: Registered protocol family 1
[    0.620133] checking if image is initramfs... it is
[    1.194717] Freeing initrd memory: 8014k freed
[    1.194875] Simple Boot Flag at 0x79 set to 0x1
[    1.195643] audit: initializing netlink socket (disabled)
[    1.195664] type=2000 audit(1234433042.192:1): initialized
[    1.200741] highmem bounce pool size: 64 pages
[    1.200746] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.202565] VFS: Disk quotas dquot_6.5.1
[    1.202629] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.202711] msgmni has been set to 1716
[    1.202805] io scheduler noop registered
[    1.202807] io scheduler anticipatory registered
[    1.202809] io scheduler deadline registered
[    1.202818] io scheduler cfq registered (default)
[    1.202977] pci 0000:01:00.0: Boot video device
[    1.203075] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.203107] pcieport-driver 0000:00:01.0: found MSI capability
[    1.203135] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.203166] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.203196] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.203274] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.203321] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.203367] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.203398] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.203429] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.203528] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.203576] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.203622] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.203651] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.203681] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.203781] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.203829] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.203875] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.203906] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.203937] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.204217] isapnp: Scanning for PnP cards...
[    1.558183] isapnp: No Plug & Play device found
[    1.583518] hpet_resources: 0xfed00000 is busy
[    1.583601] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.585245] brd: module loaded
[    1.585300] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.585391] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.597780] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.597785] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.600086] mice: PS/2 mouse device common for all mice
[    1.600183] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.600213] rtc0: alarms up to one month, y3k, hpet irqs
[    1.600311] EISA: Probing bus 0 at eisa.0
[    1.600319] Cannot allocate resource for EISA slot 1
[    1.600347] EISA: Detected 0 cards.
[    1.600350] cpuidle: using governor ladder
[    1.600352] cpuidle: using governor menu
[    1.600753] TCP cubic registered
[    1.600775] Using IPI No-Shortcut mode
[    1.600911] registered taskstats version 1
[    1.601021]   Magic number: 13:447:72
[    1.601099] rtc_cmos 00:04: setting system clock to 2009-02-12 10:04:03 UTC (1234433043)
[    1.601102] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.601103] EDD information not available.
[    1.601310] Freeing unused kernel memory: 424k freed
[    1.601341] Write protecting the kernel text: 2580k
[    1.601362] Write protecting the kernel read-only data: 940k
[    1.633900] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.765075] fuse init (API version 7.9)
[    1.961376] ACPI: SSDT DFE72CB4, 02C8 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.961673] ACPI: SSDT DFE7264A, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.961963] Monitor-Mwait will be used to enter C-1 state
[    1.961966] Monitor-Mwait will be used to enter C-2 state
[    1.961968] Monitor-Mwait will be used to enter C-3 state
[    1.962114] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.962160] processor ACPI0007:00: registered as cooling_device0
[    1.962164] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.962445] ACPI: SSDT DFE72F7C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.962697] ACPI: SSDT DFE72C2F, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.963098] Marking TSC unstable due to TSC halts in idle
[    1.963213] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.963249] processor ACPI0007:01: registered as cooling_device1
[    1.963251] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.965456] thermal LNXTHERM:01: registered as thermal_zone0
[    1.965637] ACPI: Thermal Zone [THM] (53 C)
[    2.215054] usbcore: registered new interface driver usbfs
[    2.215072] usbcore: registered new interface driver hub
[    2.215100] usbcore: registered new device driver usb
[    2.230330] USB Universal Host Controller Interface driver v3.0
[    2.230377] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.230390] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.230397] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.230431] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.230480] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    2.230610] usb usb1: configuration #1 chosen from 1 choice
[    2.230632] hub 1-0:1.0: USB hub found
[    2.230638] hub 1-0:1.0: 2 ports detected
[    2.328492] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.410445] No dock devices found.
[    2.430854] SCSI subsystem initialized
[    2.444617] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.444626] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.444630] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.444653] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.444694] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    2.444772] usb usb2: configuration #1 chosen from 1 choice
[    2.444793] hub 2-0:1.0: USB hub found
[    2.444798] hub 2-0:1.0: 2 ports detected
[    2.453267] libata version 3.00 loaded.
[    2.548312] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.548329] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.548333] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.548353] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.552265] ehci_hcd 0000:00:1a.7: debug port 1
[    2.552272] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.552283] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.557027] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    2.568034] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.568159] usb usb3: configuration #1 chosen from 1 choice
[    2.568181] hub 3-0:1.0: USB hub found
[    2.568187] hub 3-0:1.0: 4 ports detected
[    2.625091] hub 1-0:1.0: unable to enumerate USB device on port 1
[    2.776247] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.776257] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.776261] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.776281] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.776311] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    2.776386] usb usb4: configuration #1 chosen from 1 choice
[    2.776411] hub 4-0:1.0: USB hub found
[    2.776417] hub 4-0:1.0: 2 ports detected
[    2.880455] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.880464] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.880468] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.880489] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    2.880516] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    2.880593] usb usb5: configuration #1 chosen from 1 choice
[    2.880614] hub 5-0:1.0: USB hub found
[    2.880619] hub 5-0:1.0: 2 ports detected
[    2.888243] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    3.000240] Clocksource tsc unstable (delta = -105755049 ns)
[    3.026456] usb 3-1: configuration #1 chosen from 1 choice
[    3.088628] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.088634] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.088638] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.088665] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    3.088690] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    3.088760] usb usb6: configuration #1 chosen from 1 choice
[    3.088781] hub 6-0:1.0: USB hub found
[    3.088786] hub 6-0:1.0: 2 ports detected
[    3.248245] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    3.296557] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.296571] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.296575] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.296597] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.300491] ehci_hcd 0000:00:1d.7: debug port 1
[    3.300497] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.300502] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    3.372235] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.372331] usb usb7: configuration #1 chosen from 1 choice
[    3.372354] hub 7-0:1.0: USB hub found
[    3.372359] hub 7-0:1.0: 6 ports detected
[    3.581498] ahci 0000:00:1f.2: version 3.0
[    3.581513] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.581616] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    3.581619] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    3.581624] ahci 0000:00:1f.2: setting latency timer to 64
[    3.581761] ohci1394 0000:03:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.585043] scsi0 : ahci
[    3.585117] scsi1 : ahci
[    3.585164] scsi2 : ahci
[    3.585400] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 219
[    3.585403] ata2: DUMMY
[    3.585405] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 219
[    3.593055] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.593063] sky2 0000:09:00.0: setting latency timer to 64
[    3.593084] sky2 0000:09:00.0: v1.22 addr 0xf9ffc000 irq 16 Yukon-2 FE+ rev 0
[    3.593474] sky2 eth0: addr 00:1d:09:61:54:1d
[    3.634455] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f9bff800-f9bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.768238] usb 5-1: device not accepting address 2, error -71
[    3.825266] hub 5-0:1.0: unable to enumerate USB device on port 1
[    3.904257] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.986466] ata1.00: ATA-8: TOSHIBA MK3252GSX, LV011D, max UDMA/100
[    3.986471] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    3.987486] ata1.00: configured for UDMA/100
[    4.064243] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    4.236829] usb 1-2: configuration #1 chosen from 1 choice
[    4.320254] ata3: SATA link down (SStatus 0 SControl 300)
[    4.336347] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    4.339878] ata_piix 0000:00:1f.1: version 2.12
[    4.339889] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.339926] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.340012] scsi3 : ata_piix
[    4.340069] scsi4 : ata_piix
[    4.340694] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    4.340696] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    4.347376] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.356955] Driver 'sd' needs updating - please use bus_type methods
[    4.357346] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    4.357359] sd 0:0:0:0: [sda] Write Protect is off
[    4.357361] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.357455] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.357512] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    4.357524] sd 0:0:0:0: [sda] Write Protect is off
[    4.357525] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.357545] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.357548]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    4.476289] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.480262] usb 7-3: new high speed USB device using ehci_hcd and address 2
[    4.501673] ata4.00: ATAPI: MATSHITA DVD+/-RW UJ-875S, D200, max UDMA/33
[    4.516585] ata4.00: configured for UDMA/33
[    4.516686] ata5: port disabled. ignoring.
[    4.518711] scsi 3:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-875S  D200 PQ: 0 ANSI: 5
[    4.518845] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    4.539183] Driver 'sr' needs updating - please use bus_type methods
[    4.545989] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    4.545995] Uniform CD-ROM driver Revision: 3.20
[    4.546083] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.613218] usb 7-3: configuration #1 chosen from 1 choice
[    4.724320] usbcore: registered new interface driver libusual
[    4.729092] Initializing USB Mass Storage driver...
[    4.729679] scsi5 : SCSI emulation for USB Mass Storage devices
[    4.729757] usbcore: registered new interface driver usb-storage
[    4.729759] USB Mass Storage support registered.
[    4.729975] usb-storage: device found at 2
[    4.729977] usb-storage: waiting for device to settle before scanning
[    4.899763] PM: Starting manual resume from disk
[    4.899766] PM: Resume from partition 8:6
[    4.899768] PM: Checking hibernation image.
[    4.899917] PM: Resume from disk failed.
[    4.909099] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc000329cb5c1]
[    4.936901] kjournald starting.  Commit interval 5 seconds
[    4.936914] EXT3-fs: mounted filesystem with ordered data mode.
[    5.104063] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    5.276891] usb 6-2: configuration #1 chosen from 1 choice
[    5.278809] hub 6-2:1.0: USB hub found
[    5.280775] hub 6-2:1.0: 3 ports detected
[    5.569770] usb 6-2.1: new full speed USB device using uhci_hcd and address 3
[    5.693859] usb 6-2.1: configuration #1 chosen from 1 choice
[    5.769772] usb 6-2.2: new full speed USB device using uhci_hcd and address 4
[    5.900877] usb 6-2.2: configuration #1 chosen from 1 choice
[    5.977760] usb 6-2.3: new full speed USB device using uhci_hcd and address 5
[    6.107889] usb 6-2.3: configuration #1 chosen from 1 choice
[    9.728337] usb-storage: device scan complete
[    9.728829] scsi 5:0:0:0: Direct-Access     WD       5000BEV External 1.75 PQ: 0 ANSI: 4
[    9.729728] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    9.730269] sd 5:0:0:0: [sdb] Write Protect is off
[    9.730274] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    9.730278] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    9.730956] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    9.731458] sd 5:0:0:0: [sdb] Write Protect is off
[    9.731462] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    9.731465] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    9.731471]  sdb: sdb1
[   10.074589] sd 5:0:0:0: [sdb] Attached SCSI disk
[   10.074677] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   11.549536] udevd version 124 started
[   12.027040] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.045734] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.109104] iTCO_vendor_support: vendor-support=0
[   12.118857] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.118930] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   12.119027] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.173127] Linux agpgart interface v0.103
[   12.252048] ACPI: AC Adapter [AC] (on-line)
[   12.305535] ACPI: Battery Slot [BAT0] (battery present)
[   12.306160] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   12.452855] ACPI: Lid Switch [LID]
[   12.485422] sdhci: Secure Digital Host Controller Interface driver
[   12.485425] sdhci: Copyright(c) Pierre Ossman
[   12.532447] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.560050] ACPI: Power Button (CM) [PBTN]
[   12.560123] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   12.588016] ACPI: Sleep Button (CM) [SBTN]
[   12.588131] ACPI: WMI: Mapper loaded
[   12.629260] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.629263] ricoh-mmc: Copyright(c) Philip Langdale
[   12.630026] ricoh-mmc: Ricoh MMC controller found at 0000:03:09.2 [1180:0843] (rev 12)
[   12.630045] ricoh-mmc: Controller is now disabled.
[   12.637736] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 22)
[   12.637757] sdhci-pci 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   12.640821] mmc0: SDHCI controller on PCI [0000:03:09.1] using DMA
[   12.712762] acpi device:32: registered as cooling_device2
[   12.713335] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input5
[   12.735708] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   13.207803] nvidia: module license 'NVIDIA' taints kernel.
[   13.477849] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.477859] nvidia 0000:01:00.0: setting latency timer to 64
[   13.477988] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   13.541267] Bluetooth: Core ver 2.13
[   13.542630] NET: Registered protocol family 31
[   13.542633] Bluetooth: HCI device and connection manager initialized
[   13.542636] Bluetooth: HCI socket layer initialized
[   13.565343] usbcore: registered new interface driver hiddev
[   13.568928] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.2/6-2.2:1.0/input/input6
[   13.589046] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.651595] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   13.665182] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2
[   13.670024] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.3/6-2.3:1.0/input/input8
[   13.684763] Linux video capture interface: v2.00
[   13.743822] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   13.748827] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   13.749442] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb3/3-1/3-1:1.0/input/input9
[   13.773225] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3
[   13.773451] usbcore: registered new interface driver usbhid
[   13.773452] usbcore: registered new interface driver btusb
[   13.773550] usbhid: v2.6:USB HID core driver
[   13.796084] usbcore: registered new interface driver uvcvideo
[   13.796089] USB Video Class driver (v0.1.0)
[   14.049780] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[   14.099336] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.099360] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.134107] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   14.175945] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.527292] lp: driver loaded but no devices found
[   15.709101] Adding 4875688k swap on /dev/sda6.  Priority:-1 extents:1 across:4875688k
[   16.304672] EXT3 FS on sda7, internal journal
[   17.380312] type=1505 audit(1234451059.011:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4432
[   17.510398] type=1505 audit(1234451059.143:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4437
[   17.510582] type=1505 audit(1234451059.143:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4437
[   17.722764] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.246065] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.299423] apm: BIOS not found.
[   19.448347] ppdev: user-space parallel port driver
[   24.071849] Bluetooth: L2CAP ver 2.11
[   24.071859] Bluetooth: L2CAP socket layer initialized
[   24.111430] Bluetooth: SCO (Voice Link) ver 0.6
[   24.111442] Bluetooth: SCO socket layer initialized
[   24.154912] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.154922] Bluetooth: BNEP filters: protocol multicast
[   24.192552] Bluetooth: RFCOMM socket layer initialized
[   24.192578] Bluetooth: RFCOMM TTY layer initialized
[   24.192583] Bluetooth: RFCOMM ver 1.10
[   24.213927] Bridge firewalling registered
[   28.376844] sky2 eth0: enabling interface
[   31.094113] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   31.259327] NET: Registered protocol family 17
[   42.869624] NET: Registered protocol family 10
[   42.872177] lo: Disabled Privacy Extensions
[   53.396152] eth0: no IPv6 routers present
[   85.268324] CPU0 attaching NULL sched-domain.
[   85.268332] CPU1 attaching NULL sched-domain.
[   85.288084] CPU0 attaching sched-domain:
[   85.288089]  domain 0: span 0-1 level MC
[   85.288092]   groups: 0 1
[   85.288097] CPU1 attaching sched-domain:
[   85.288099]  domain 0: span 0-1 level MC
[   85.288100]   groups: 1 0
[   85.630913] CPU0 attaching NULL sched-domain.
[   85.630920] CPU1 attaching NULL sched-domain.
[   85.648138] CPU0 attaching sched-domain:
[   85.648144]  domain 0: span 0-1 level MC
[   85.648146]   groups: 0 1
[   85.648152] CPU1 attaching sched-domain:
[   85.648153]  domain 0: span 0-1 level MC
[   85.648155]   groups: 1 0
[   97.455490] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   97.455872] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.1/6-2.1:1.0/bluetooth/hci0/hci0:11/input12
[  168.299206] ieee80211_crypt: registered algorithm 'NULL'
[  168.311084] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  168.311111] wl 0000:0b:00.0: setting latency timer to 64
[  168.545435] ieee80211_crypt: registered algorithm 'TKIP'
[  168.545612] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12
[  178.720145] eth1: no IPv6 routers present
[  277.912164] usb 6-2: USB disconnect, address 2
[  277.912177] usb 6-2.1: USB disconnect, address 3
[  277.912972] btusb_intr_complete: hci0 urb f5c18480 failed to resubmit (19)
[  277.912993] btusb_bulk_complete: hci0 urb f3f71d00 failed to resubmit (19)
[  277.913974] btusb_bulk_complete: hci0 urb f3f71f00 failed to resubmit (19)
[  277.914668] btusb_send_frame: hci0 urb f48d1800 submission failed
[  277.914683] __set_isoc_interface: hci0 setting interface failed (19)
[  278.176527] usb 6-2.2: USB disconnect, address 4
[  278.201828] usb 6-2.3: USB disconnect, address 5
[  282.216060] usb 6-2: new full speed USB device using uhci_hcd and address 6
[  282.391168] usb 6-2: configuration #1 chosen from 1 choice
[  282.394599] hub 6-2:1.0: USB hub found
[  282.396235] hub 6-2:1.0: 3 ports detected
[  282.694241] usb 6-2.1: new full speed USB device using uhci_hcd and address 7
[  282.820288] usb 6-2.1: configuration #1 chosen from 1 choice
[  282.937191] usb 6-2.2: new full speed USB device using uhci_hcd and address 8
[  283.071708] usb 6-2.2: configuration #1 chosen from 1 choice
[  283.091431] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.2/6-2.2:1.0/input/input13
[  283.141146] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2
[  283.223222] usb 6-2.3: new full speed USB device using uhci_hcd and address 9
[  283.355660] usb 6-2.3: configuration #1 chosen from 1 choice
[  283.368497] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.3/6-2.3:1.0/input/input14
[  283.409199] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3
[  292.306714] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.1/6-2.1:1.0/bluetooth/hci0/hci0:11/input15
[  297.320055] eth1: no IPv6 routers present
[  336.860134] CE: hpet increasing min_delta_ns to 15000 nsec

---

### Post by iceman_ch on 2009-02-12
I opened up the blacklist and noticed that the Bcm43xx driver was blacklisted.  Is this correct.  This dmesg is after I "woke up" the wireless.  I also noticed that if I go to the modprobe.d folder there is a file there called blacklist-bcm43 with the following in it.

blacklist bcm43xx
blacklist b43
blacklist b43_legacy
blacklist ssb

---

### Post by pytheas22 on 2009-02-12
The script might not be working because it doesn't know the name of the interface.  Try opening it up by typing:
```

sudo gedit /etc/init.d/wifi-fix.sh
```

and change it to this:
```

#!/bin/bash

ifconfig eth1 up
iwlist eth1 scan
```

Then save and close the file.

The 'iwlist scan' command can take the name of the interface as an argument.  Your interface is named 'eth1', so specifying that might help (although it shouldn't be necessary).  'wl' is the name of the driver, but not the interface.

Whenever you type 'sudo wl scan', you should just get an error message saying that the interface doesn't exist.  Is that not the case?

---

### Post by iceman_ch on 2009-02-12
I'll try it with the eth1 in there.  When I type

iwlist wl scan 

It say that the interface dosn't support scanning.  I'm guessing this is equivelent to it dosn't exist.  It seems like if I type anything other then wl it won't work.  I have to tell it to scan wl to wake up the card.  I'll try on the next boot and see what happens.  Also if I scan eth1 it tells me all of the hubs around me.

---

### Post by pytheas22 on 2009-02-12
That makes sense.  If scanning 'eth1' doesn't work, you could try changing the script to scan 'wl' if you're positive that that's what it takes to get the card up, but really I can't think of any reason that that would sense...not that Linux always makes to me.

---

### Post by iceman_ch on 2009-02-12
I just tested.  The card won't wake up inless I type wl.  I tried eth1, eth0, wl1, w, and the only one that worked was wl.  I think that would mean I have something named wrong somewhere what do you think?  

These popped up in the log as soon as I typed the comand.

Messages
Feb 12 11:58:14 chris-laptop kernel: [  161.300796] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 12 11:58:15 chris-laptop kernel: [  161.539828] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12

kern.log

Feb 12 11:58:14 chris-laptop kernel: [  161.289037] ieee80211_crypt: registered algorithm 'NULL'
Feb 12 11:58:14 chris-laptop kernel: [  161.300796] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 12 11:58:14 chris-laptop kernel: [  161.300829] wl 0000:0b:00.0: setting latency timer to 64
Feb 12 11:58:15 chris-laptop kernel: [  161.539276] ieee80211_crypt: registered algorithm 'TKIP'
Feb 12 11:58:15 chris-laptop kernel: [  161.539828] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12
Feb 12 11:58:26 chris-laptop kernel: [  172.484120] eth1: no IPv6 routers present

syslog

Feb 12 11:58:03 chris-laptop avahi-daemon[5061]: Received non-local response on interface 'eth0.0'.
Feb 12 11:58:04 chris-laptop last message repeated 3 times
Feb 12 11:58:14 chris-laptop kernel: [  161.289037] ieee80211_crypt: registered algorithm 'NULL'
Feb 12 11:58:14 chris-laptop kernel: [  161.300796] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 12 11:58:14 chris-laptop kernel: [  161.300829] wl 0000:0b:00.0: setting latency timer to 64
Feb 12 11:58:15 chris-laptop kernel: [  161.539276] ieee80211_crypt: registered algorithm 'TKIP'
Feb 12 11:58:15 chris-laptop kernel: [  161.539828] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12
Feb 12 11:58:15 chris-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_16_44_cf_c8_d8, iface: eth1): not well known
Feb 12 11:58:15 chris-laptop NetworkManager: <info>  eth1: driver is 'wl'. 
Feb 12 11:58:15 chris-laptop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Feb 12 11:58:15 chris-laptop NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'. 
Feb 12 11:58:15 chris-laptop NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_16_44_cf_c8_d8 
Feb 12 11:58:17 chris-laptop avahi-daemon[5061]: Registering new address record for fe80::216:44ff:fecf:c8d8 on eth1.*.
Feb 12 11:58:19 chris-laptop NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Feb 12 11:58:19 chris-laptop NetworkManager: <info>  (eth1): preparing device. 
Feb 12 11:58:19 chris-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Feb 12 11:58:19 chris-laptop NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Feb 12 11:58:19 chris-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Feb 12 11:58:19 chris-laptop NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Feb 12 11:58:26 chris-laptop kernel: [  172.484120] eth1: no IPv6 routers present

---

### Post by pytheas22 on 2009-02-12
hmmm, I don't mean to doubt you, but are you sure you're not typing:
```

sudo modprobe wl
```

rather than:
```

sudo iwlist scan wl
```

Because the modprobe command would make sense--it inserts the 'wl' module, which is consistent with the output you see in the logs after running that command.

If modprobing wl is doing the trick, then it should be sufficient to run this command once so that the system will load it automatically at boot:
```

echo wl | sudo tee -a /etc/modules
```

If that doesn't help, try editing the script to say this:
```

#!/bin/bash

modprobe wl
ifconfig eth1 up
```

If that still doesn't work, let me know and I'll take a deeper look at your log output.

---

### Post by iceman_ch on 2009-02-12
No worries.  Here is my auth.log output.

Feb 12 11:57:57 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/iwlist eth0 scan
Feb 12 11:58:00 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/iwlist eth1 scan
Feb 12 11:58:08 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/iwlist wl1 scan
Feb 12 11:58:14 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/iwlist wl scan

I wonder if for some reason iwlist is making modprope run.  I don't know a ton about linux so I'm just guessing.  I know that if I use the modprobe command it will also "wake up" the card.  Would it be a better idea to take the iwlist command out of the script and instead put in modprope b43 into it since b43 is the driver that should be running?  Also how to I go about changing the script?  Do I just edit in sudo and save?


Ok, figure this one out.  If I inload wl using modprobe and instead load b43 the card won't wake up until I type iwlist wl scan.  I can shut the card off and on by unloading and loading el using modprobe.  Seems wierd to me. If I'm reading the logs right when the b43 driver is loaded it dosn't associate with anything wheres the wl driver does.

Auto.log
Feb 12 13:02:15 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/modprobe -r wl
Feb 12 13:02:58 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/modprobe b43
Feb 12 13:03:20 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/ifconfig eth1 up
Feb 12 13:03:41 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/ifconfig wl1 up
Feb 12 13:03:44 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/ifconfig wlo1 up
Feb 12 13:03:48 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/ifconfig wl01 up
Feb 12 13:04:26 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/iwlist wl scan
Feb 12 13:04:47 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/modprobe -r wl
Feb 12 13:04:48 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/modprobe -r wl
Feb 12 13:04:53 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/modprobe -r b43
Feb 12 13:05:04 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/modprobe wl

kern.log

Feb 12 13:02:15 chris-laptop kernel: [ 4002.341376] wl 0000:0b:00.0: PCI INT A disabled
Feb 12 13:02:59 chris-laptop kernel: [ 4045.562155] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
Feb 12 13:04:26 chris-laptop kernel: [ 4133.220534] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 12 13:04:26 chris-laptop kernel: [ 4133.220569] wl 0000:0b:00.0: setting latency timer to 64
Feb 12 13:04:26 chris-laptop kernel: [ 4133.240341] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12
Feb 12 13:04:37 chris-laptop kernel: [ 4143.829067] eth1: no IPv6 routers present
Feb 12 13:04:47 chris-laptop kernel: [ 4153.599058] wl 0000:0b:00.0: PCI INT A disabled
Feb 12 13:05:04 chris-laptop kernel: [ 4170.678701] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 12 13:05:04 chris-laptop kernel: [ 4170.678736] wl 0000:0b:00.0: setting latency timer to 64
Feb 12 13:05:04 chris-laptop kernel: [ 4170.697660] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12
Feb 12 13:05:15 chris-laptop kernel: [ 4181.769058] eth1: no IPv6 routers present

messages.log
Feb 12 13:02:15 chris-laptop kernel: [ 4002.341376] wl 0000:0b:00.0: PCI INT A disabled
Feb 12 13:02:59 chris-laptop kernel: [ 4045.562155] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
Feb 12 13:04:26 chris-laptop kernel: [ 4133.220534] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 12 13:04:26 chris-laptop kernel: [ 4133.240341] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12
Feb 12 13:04:47 chris-laptop kernel: [ 4153.599058] wl 0000:0b:00.0: PCI INT A disabled
Feb 12 13:05:04 chris-laptop kernel: [ 4170.678701] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 12 13:05:04 chris-laptop kernel: [ 4170.697660] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12

---

### Post by pytheas22 on 2009-02-12
> Would it be a better idea to take the iwlist command out of the script and instead put in modprope b43 into it since b43 is the driver that should be running?

b43 seems not to allow you actually to connect, so I think you should stick with 'wl'.  Try modifying the script so that it says 'sudo modprobe wl'.  You can put in a 'sudo iwlist wl scan' too if you want; it won't hurt anything.
> 
Also how to I go about changing the script? Do I just edit in sudo and save?

Yes, just type 'sudo gedit /etc/init.d/wifi-fix.sh' and the file will pop open.  Make your changes, then save and close.

---

### Post by iceman_ch on 2009-02-12
What do you think is holding the b43 driver back?  I need the b43 driver so that I can connect to the encrypted network at school.

---

### Post by pytheas22 on 2009-02-13
Doesn't the 'wl' driver allow you to connect to encrypted networks?  It should.  'wl' and 'b43' do the same thing.  I thought 'wl' was working better for you, but you can use whichever one you want.  Just note these differences:

- with 'b43', your wireless interface is going to be named 'wlan0'
- under 'wl', the interface is named 'eth1'

You can try both drivers by just modifying your script appropriately.

---

### Post by iceman_ch on 2009-02-13
Thats the problem that I'm having.  What ever came with ubuntu by default will not let me connect to the encrypted network.  It causes a kernel panic.  I tried to switch to ndiswrapper and same thing.  I've also tried to used b43 but it dosn't seem to want to work. My wireless will work for unencrypted networks and I know there are peoples on campus who can use the wireless in ubuntu no problem.

---

### Post by pytheas22 on 2009-02-13
Alright, that clarifies things.  I thought 'wl' was working.  You might have better luck using [wicd]("http://wicd.sourceforge.net") instead of Network Manager to connect to WPA-encrypted networks under the b43 driver.

If you want to know which driver you're using, run the command 'lshw -C Network' and the output will show you, for example:
```

*-network
description: Wireless interface
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
logical name: eth1
version: 01
serial: 00:16:44:cf:c8:d8
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.2.109 latency=0 **module=wl** multicast=yes wireless=IEEE 802.11
```

indicates that it's using wl.  If you want to switch to b43, you would type:
```

sudo rmmod wl
sudo modprobe b43
```

To switch from b43 to wl, type:
```

sudo rmmod b43
sudo rmmod ssb
sudo modprobe wl
```

The addition of the 'rmmod ssb' line is necessary because of some module-dependency issues involving b43.

---

### Post by beekr on 2009-02-14
> **pytheas22 said:**
> There's an alternate driver that might work better for your card (currently it's using the 'wl' driver; the alternate driver is 'b43').  Please post the output of these commands so we can see if b43 would work (you will need to have an Internet connection for the first two commands here):
```

sudo apt-get update
sudo apt-get install b43-fwcutter
sudo rmmod wl
sudo rmmod b43
sudo modprobe b43
iwconfig
dmesg | tail -50
```

At this point, your card should be up under the 'b43' driver and you can try connecting.  Does it work better?  If so, we will make these changes permanent (for the time being, rebooting your machine will erase these modifications).

Running the above code seems to have fixed my wireless issue. How do I go about making this a permanent change? Thanks in advance,

Beekr

---

### Post by pytheas22 on 2009-02-14
> Running the above code seems to have fixed my wireless issue. How do I go about making this a permanent change? Thanks in advance,

You would want to blacklist the 'wl' driver by typing:
```

echo 'blacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
```

Then add 'b43' to /etc/modules so that it gets loaded at boot by typing:
```

echo b43 | sudo tee -a /etc/modules
```

And that should do it.  If not, let me know.

---

### Post by iceman_ch on 2009-02-18
Alright so heres the update.  I reinstalled the system.  Now my card turns on automatically when the computer boots.  I installed wicd.  It's nice but, it didn't help.  when ever I connect to the encrypted network at school the kernel panics.  I can still connect to unencrypted networks.  I tried to reinstall fwcutter.  When ever I remove the wl module the wireless light turns off.  When I insert the b43 module the light never comes back on.  here is the dmesg output.

chris@iceman:~$ sudo rmmod wl
chris@iceman:~$ sudo rmmod wl
ERROR: Module wl does not exist in /proc/modules
chris@iceman:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
chris@iceman:~$ sudo modprobe b43
chris@iceman:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

chris@iceman:~$ dmesg | tail -50
[   31.030189] vboxdrv: Successfully done.
[   31.030193] vboxdrv: Found 2 processor cores.
[   31.034314] vboxdrv: fAsync=0 offMin=0x408 offMax=0x1818
[   31.037306] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.037316] vboxdrv: Successfully loaded version 2.1.4 (interface 0x000a0009).
[   34.563923] sky2 eth0: enabling interface
[   35.750360] Bluetooth: L2CAP ver 2.11
[   35.750372] Bluetooth: L2CAP socket layer initialized
[   35.789989] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.790003] Bluetooth: BNEP filters: protocol multicast
[   35.841084] Bridge firewalling registered
[   35.856830] Bluetooth: RFCOMM socket layer initialized
[   35.857192] Bluetooth: RFCOMM TTY layer initialized
[   35.857201] Bluetooth: RFCOMM ver 1.10
[   35.893607] Bluetooth: SCO (Voice Link) ver 0.6
[   35.893617] Bluetooth: SCO socket layer initialized
[   39.698350] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   39.698717] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.1/6-2.1:1.0/bluetooth/hci0/hci0:11/input12
[   91.088971] CPU0 attaching NULL sched-domain.
[   91.088979] CPU1 attaching NULL sched-domain.
[   91.132077] CPU0 attaching sched-domain:
[   91.132083]  domain 0: span 0-1 level MC
[   91.132086]   groups: 0 1
[   91.132091] CPU1 attaching sched-domain:
[   91.132093]  domain 0: span 0-1 level MC
[   91.132095]   groups: 1 0
[  126.880085] CE: hpet increasing min_delta_ns to 15000 nsec
[  164.284778] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[  183.865485] NET: Registered protocol family 10
[  183.867643] lo: Disabled Privacy Extensions
[  194.145050] eth0: no IPv6 routers present
[  194.668124] eth1: no IPv6 routers present
[  237.810536] sky2 eth0: disabling interface
[  238.021198] NET: Registered protocol family 17
[  238.128759] sky2 eth0: enabling interface
[  238.131690] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  240.873164] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[  240.873626] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  251.280056] eth0: no IPv6 routers present
[  257.981686] sky2 eth0: disabling interface
[  258.184473] sky2 eth0: enabling interface
[  258.188483] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  260.922024] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[  260.923976] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  271.665078] eth0: no IPv6 routers present
[  325.744084] CE: hpet increasing min_delta_ns to 22500 nsec
[  579.724034] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x21ef000a
[  611.464303] wl 0000:0b:00.0: PCI INT A disabled
[  622.076644] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[  811.530371] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
chris@iceman:~$

---

### Post by kevdog on 2009-02-18
You only need to install fw-cutter once -- repeating the process doesnt help anything.

It sounds like its the order in which you are loading your drivers.  Some need to be unloaded prior to loading others -- you just cant keep piling new ones ontop of old ones, and expect the driver attached to the device to magically be reassigned by the kernel.

After you modprobe the device, you phyically need to bring the device up (either manually or wicd does this).  The command is sudo ifconfig wlan0/eth1 up

---

### Post by iceman_ch on 2009-02-18
I did a fresh install of ubuntu and then installed fwcutter.  Also the commands that I used were the following

rmmod wl  (to unload the wl)
rmmod wl  (just to make sure)
rmmod b43  (also to make sure)
modprobe b43 (to load the b43 driver)

then when I add in the ifconfig wlan0 up command that you added it still won't turn the card on.  I can only get the card to turn on after I unload the b43 driver and load the wl driver back in.  As soon as I load the wl driver the card imedietly turns on.  It seems like loading the b43 driver isn't attaching it to the device.

---

### Post by pytheas22 on 2009-02-18
> then when I add in the ifconfig wlan0 up command that you added it still won't turn the card on. I can only get the card to turn on after I unload the b43 driver and load the wl driver back in. As soon as I load the wl driver the card imedietly turns on. It seems like loading the b43 driver isn't attaching it to the device.

Yes, from your dmesg output in post #20, it looks like b43 is refusing to claim your card.  I'm not sure why.

It also appears that you're not the only one having issues with the wl driver and WPA-enterprise networks.  Other users report freezes upon trying to connect to university networks; see this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/305907").  Unfortunately, no one has a solution yet.

I'm thinking that perhaps the best thing to do in this situation, now that we understand it better, is to use ndiswrapper.  ndiswrapper is a third driver solution that involves neither b43 nor wl.  To get ndiswrapper set up, please plug your computer into the Internet, then run these commands (which are based on [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")):
```

sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
echo 'blacklist b43' | sudo tee -a /etc/modules
echo 'blacklist wl' | sudo tee -a /etc/modules
wget http://myspamb8.googlepages.com/R174291-pruned.zip
unzip R174291-pruned.zip
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Then reboot.  Does your wireless work now?  If not, what is the output of:
```

lsmod | grep ndis
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

---

### Post by kevdog on 2009-02-18
I take it you have seen this page: 
[http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61](http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61)

Seems like as pytheas suggested, Id give ndiswrapper an honest effort!

---

### Post by iceman_ch on 2009-02-19
Alright so I tried to set up ndiswrapper and everything went well.  When I i insterted ndiswrapper the turned on I tried to connect to the encrypted network and I the system froze.  I wonder if I'm doomed until the initial bug gets fixed.  Here is the output.  I just started poking around and for kicks looked to see if the wl driver is loaded and it is.  I removed it and tryed to load ndiswrapper and now the card won't turn on. grrrrr.

chris@iceman:~$ lsmod | grep ndis
ndiswrapper           196380  0 
usbcore               149360  9 usb_storage,libusual,ndiswrapper,uvcvideo,usbhid,btusb,ehci_hcd,uhci_hcd

chris@iceman:~$ dmesg | grep -e ndis -e wlan
[   15.630918] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   15.658781] usbcore: registered new interface driver ndiswrapper

chris@iceman:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4315) present (alternate driver: wl)


Just for kicks here is the log showing the commands that I used.  In case I screwed it up.

Feb 18 14:41:30 iceman sudo:    chris : TTY=unknown ; PWD=/home/chris ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 39845891 --update-at-startup
Feb 18 14:50:15 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
Feb 18 14:51:05 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/tee -a /etc/modules
Feb 18 14:51:13 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/tee -a /etc/modules
Feb 18 14:52:34 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/sbin/ndiswrapper -i bcmwl5.inf
Feb 18 14:52:54 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/depmod -a
Feb 18 14:53:12 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/rmmod wl
Feb 18 14:53:19 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/rmmod ssb
Feb 18 14:53:22 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/rmmod wl
Feb 18 14:53:24 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/rmmod b43
Feb 18 14:53:33 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/sbin/modprobe ndiswrapper
Feb 18 14:53:59 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/bin/cp /etc/network/interfaces /etc/network/interfaces.orig
Feb 18 14:54:48 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/tee /etc/network/interfaces
Feb 18 14:55:06 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/sbin/ndiswrapper -m
Feb 18 14:55:40 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/tee -a /etc/modules
Feb 18 14:56:18 iceman sudo:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/tee -a /etc/default/wpasupplicant
Feb 18 14:56:31 iceman gdm[5700]: pam_unix(gdm:session): session closed for user chris
Feb 18 14:57:51 iceman gdm[5673]: pam_unix(gdm:session): session opened for user chris by (uid=0)
Feb 18 14:57:51 iceman gdm[5673]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Feb 18 14:57:51 iceman gdm[5673]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Feb 18 14:57:51 iceman gdm[5673]: Autolaunch error: X11 initialization failed.
Feb 18 14:57:51 iceman gdm[5673]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Feb 18 14:57:51 iceman gdm[5673]: Autolaunch error: X11 initialization failed.
Feb 18 14:57:51 iceman gdm[5673]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Feb 18 14:57:51 iceman gdm[5673]: Autolaunch error: X11 initialization failed.
Feb 18 14:57:51 iceman gdm[5673]: )

---

### Post by iceman_ch on 2009-02-19
Sorry, to post twice but I wanted to explain something I found real quick.  After checking to see wich driver was loaded using lshw -C network I found I was still on wl.  So I removed every driver I could think of wl, ssb, b43, and ndiswrapper.  Then I instered ndiswrapper and the card turned back on.  I checked ifconfig and found nothing so I brought the card up using ifconfi wlan0 up and now the card is listed.  The next problem is I can't see any networks....  I'm going to keep digging to find the command so that I can see it.  Then I will try to connect to the encrypted network again.

---

### Post by iceman_ch on 2009-02-19
Alright yay!!!! It worked.  I got ndiswrapper to work and I am now using an encrypted connection.  So even though I had set up ndiswrapper correctly apperently whenever I restart the computer ubuntu loads the wl driver.  If I unload every driver that I can think of and then reload ndis it works.  The other thing that I had to do was switch back to network manager.  WiCd still wouldn't connect but, it wasn't freezing either.  Now that it works what do I need to do so that I don't have to unload and reload everything?

Thanks for all of the help

Alright last post for this thread.  I went into modules and deleted the lines that said blacklist wl and blacklist b43.  I then created a file called blacklist-custom in the modprobe.d directory and add the line blacklist wl to it.  Now when I boot the computer ndiswrapper loads and everything works.  Thanks again for all of the help.  Now it's on to create a custom conky.

---

### Post by pytheas22 on 2009-02-19
Glad everything is finally solved.  Sorry it took so long.

---

