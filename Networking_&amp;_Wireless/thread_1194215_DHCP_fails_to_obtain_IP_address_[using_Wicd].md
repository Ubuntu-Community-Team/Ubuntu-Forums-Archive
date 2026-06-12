---
title: "DHCP fails to obtain IP address [using Wicd]"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by keyshawn on 2009-06-22
Hello, 

I'm using wicd [1.5.9] to connect to my router for a wireless internet network. My network has a WEP passphrase. 

When I connect to the network, I am authorized but wicd hangs when 'obtaining an IP address.' 15-20 seconds later, I am no longer connected to the network. 


I found the DHCP workaround in a stickied thread - [http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441) - followed its directions and I still have the same symptoms. 

I am a bit lost now what I should troubleshoot next so I can get my wireless internet working again. 

thanks,
keyshawn


Here is my syslog:
```
Jun 22 12:04:45 gizang kernel: [  151.820013] eth1: no IPv6 routers present
Jun 22 12:04:47 gizang dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jun 22 12:04:47 gizang dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jun 22 12:04:47 gizang dhclient: All rights reserved.
Jun 22 12:04:47 gizang dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun 22 12:04:47 gizang dhclient: 
Jun 22 12:04:48 gizang dhclient: Listening on LPF/eth1/00:22:69:0a:ef:69
Jun 22 12:04:48 gizang dhclient: Sending on   LPF/eth1/00:22:69:0a:ef:69
Jun 22 12:04:48 gizang dhclient: Sending on   Socket/fallback
Jun 22 12:04:48 gizang dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jun 22 12:04:52 gizang dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jun 22 12:04:58 gizang dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jun 22 12:05:07 gizang dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Jun 22 12:05:20 gizang dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Jun 22 12:05:36 gizang dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Jun 22 12:05:50 gizang dhclient: No DHCPOFFERS received.
Jun 22 12:05:50 gizang dhclient: No working leases in persistent database - sleeping.
Jun 22 12:05:50 gizang avahi-autoipd(eth1)[4322]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Jun 22 12:05:50 gizang avahi-autoipd(eth1)[4322]: Successfully called chroot().
Jun 22 12:05:50 gizang avahi-autoipd(eth1)[4322]: Successfully dropped root privileges.
Jun 22 12:05:50 gizang avahi-autoipd(eth1)[4322]: Starting with address 169.254.6.220
Jun 22 12:05:55 gizang avahi-autoipd(eth1)[4322]: Callout BIND, address 169.254.6.220 on interface eth1
Jun 22 12:05:55 gizang avahi-daemon[3398]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.6.220.
Jun 22 12:05:55 gizang avahi-daemon[3398]: New relevant interface eth1.IPv4 for mDNS.
Jun 22 12:05:55 gizang avahi-daemon[3398]: Registering new address record for 169.254.6.220 on eth1.IPv4.
Jun 22 12:05:59 gizang avahi-autoipd(eth1)[4322]: Successfully claimed IP address 169.254.6.220
```

Here is my /etc/dhcp3/dhclient.conf
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

# option rfc3442-classless-static-routes code 121 = array of unsigned 
# integer 8; Commented out 2009.06.22

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    ntp-servers;
# rfc3442-classless-static-routes, commented this was in req list- 2009.06.22
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

lspci -v | less
spits out: 
```

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
        Subsystem: Foxconn International, Inc. Device e003
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f8000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl


```

---

### Post by keyshawn on 2009-06-23
Just an FYI: I had just moved a few days ago and my wireless was working properly at my old place. The only difference (As far as I can tell) between the two wireless networks was that my old network was protected by WPA2 (IIRC) and this current network is protected by WEP; and the cable internet company is different. 

Also,
Here is some more information that I forgot to post earlier: 

thanks for any help.

regards,
keyshawn

**iwconfig eth1: **
```

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:219  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```**ifconfig eth1:**
```
eth1      Link encap:Ethernet  HWaddr 00:22:69:0a:ef:69  
          inet6 addr: fe80::222:69ff:fe0a:ef69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:5
          TX packets:0 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

```**sudo lshw -C network: **
```

       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:c5:76:ad
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:22:69:0a:ef:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

```[B]
iwlist scan: [/B]
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.


```**uname -r**
2.6.28-11-generic
[B]
Dmesg:[/B]
```

[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6df000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6df000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xbf6d0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf6d0000 (usable)
[    0.000000]  modified: 00000000bf6d0000 - 00000000bf6df000 (ACPI NVS)
[    0.000000]  modified: 00000000bf6df000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378c0000 - 37fef990
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb0990
[    0.000000] Move RAMDISK from 00000000378c0000 - 0000000037fef98f to 00881000 - 00fb098f
[    0.000000] ACPI: RSDP 000F7BF0, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BF6D0A71, 009C (r1 ACRSYS ACRPRDCT  6040000 INNA        0)
[    0.000000] ACPI: FACP BF6DBBD7, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT BF6D2BBA, 8FA9 (r2 INTEL  CRESTLNE  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS BF6DEFC0, 0040
[    0.000000] ACPI: HPET BF6DBCCB, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BF6DBD03, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA BF6DBD3F, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: TMOR BF6DBD71, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC BF6DBD97, 0176 (r1 ACRSYS ACRPRDCT  6040000 ANNI        1)
[    0.000000] ACPI: ASF! BF6DBF0D, 0063 (r32 OEMID  OEMTBL    6040000 PTL         1)
[    0.000000] ACPI: APIC BF6DBF70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BF6DBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT BF6D256B, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D1ED9, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D1D0E, 01CB (r1 BrtRef  DD01BRT     1000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D10C9, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D1023, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D0B0D, 0516 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2178MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb0990]      NEW RAMDISK ==> [0000881000 - 0000fb0990]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f7d60] 000f7d60
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bf6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf6d0
[    0.000000] On node 0 totalpages: 783967
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4358 pages used for memmap
[    0.000000]   HighMem zone: 553420 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777841
[    0.000000] Kernel command line: root=UUID=7d610450-ef9d-469a-9fa7-47d043154614 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1861.966 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15681280 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3079120k/3136320k available (4126k kernel code, 55844k reserved, 2208k data, 532k init, 2231112k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3723.93 BogoMIPS (lpj=7447864)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018549] ACPI: Core revision 20080926
[    0.022358] ACPI: Checking initramfs for custom DSDT
[    0.348455] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.388151] CPU0: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz stepping 0d
[    0.392001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3723.94 BogoMIPS (lpj=7447893)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.476404] CPU1: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz stepping 0d
[    0.476421] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.480043] Brought up 2 CPUs
[    0.480046] Total of 2 processors activated (7447.87 BogoMIPS).
[    0.480106] CPU0 attaching sched-domain:
[    0.480109]  domain 0: span 0-1 level MC
[    0.480111]   groups: 0 1
[    0.480118] CPU1 attaching sched-domain:
[    0.480120]  domain 0: span 0-1 level MC
[    0.480122]   groups: 1 0
[    0.480196] net_namespace: 776 bytes
[    0.480196] Booting paravirtualized kernel on bare hardware
[    0.480349] Time: 12:24:54  Date: 06/23/09
[    0.480349] regulator: core version 0.5
[    0.480349] NET: Registered protocol family 16
[    0.480349] EISA bus registered
[    0.480349] ACPI: bus type pci registered
[    0.480349] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.480349] PCI: MCFG area at e0000000 reserved in E820
[    0.480349] PCI: Using MMCONFIG for extended config space
[    0.480349] PCI: Using configuration type 1 for base access
[    0.481224] ACPI: EC: Look up EC in DSDT
[    0.487728] ACPI: BIOS _OSI(Linux) query ignored
[    0.488021] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.500104] ACPI: Interpreter enabled
[    0.500110] ACPI: (supports S0 S3 S4 S5)
[    0.500130] ACPI: Using IOAPIC for interrupt routing
[    0.916477] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.916479] ACPI: EC: driver started in interrupt mode
[    0.916674] ACPI: No dock devices found.
[    0.916684] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.916787] pci 0000:00:02.0: reg 10 64bit mmio: [0xfc000000-0xfc0fffff]
[    0.916796] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.916802] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.916844] pci 0000:00:02.1: reg 10 64bit mmio: [0xfc100000-0xfc1fffff]
[    0.916972] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.917045] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.917125] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc504000-0xfc5043ff]
[    0.917180] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.917186] pci 0000:00:1a.7: PME# disabled
[    0.917249] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc300000-0xfc303fff]
[    0.917296] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.917301] pci 0000:00:1b.0: PME# disabled
[    0.917378] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.917383] pci 0000:00:1c.0: PME# disabled
[    0.917464] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.917469] pci 0000:00:1c.1: PME# disabled
[    0.917549] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.917555] pci 0000:00:1c.2: PME# disabled
[    0.917630] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.917702] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.917775] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.917855] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc504400-0xfc5047ff]
[    0.917910] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.917916] pci 0000:00:1d.7: PME# disabled
[    0.918096] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.918101] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.918142] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.918151] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.918160] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.918169] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.918177] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.918240] pci 0000:00:1f.2: reg 10 io port: [0x1c00-0x1c07]
[    0.918249] pci 0000:00:1f.2: reg 14 io port: [0x18f4-0x18f7]
[    0.918258] pci 0000:00:1f.2: reg 18 io port: [0x18f8-0x18ff]
[    0.918267] pci 0000:00:1f.2: reg 1c io port: [0x18f0-0x18f3]
[    0.918276] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ef]
[    0.918285] pci 0000:00:1f.2: reg 24 io port: [0x18d0-0x18df]
[    0.918306] pci 0000:00:1f.2: PME# supported from D3hot
[    0.918312] pci 0000:00:1f.2: PME# disabled
[    0.918342] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.918371] pci 0000:00:1f.3: reg 20 io port: [0x1c20-0x1c3f]
[    0.918535] pci 0000:02:00.0: reg 10 64bit mmio: [0xf6000000-0xf600ffff]
[    0.918599] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.918605] pci 0000:02:00.0: PME# disabled
[    0.918684] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.918690] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
[    0.918699] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.919067] pci 0000:04:00.0: reg 10 64bit mmio: [0xf8000000-0xf8003fff]
[    0.919201] pci 0000:04:00.0: supports D1 D2
[    0.919203] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.919215] pci 0000:04:00.0: PME# disabled
[    0.919345] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.919351] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.919360] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
[    0.919431] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.919437] pci 0000:00:1c.2: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.919446] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
[    0.919514] pci 0000:0f:06.0: reg 10 32bit mmio: [0xfc204000-0xfc204fff]
[    0.919529] pci 0000:0f:06.0: supports D1 D2
[    0.919531] pci 0000:0f:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.919537] pci 0000:0f:06.0: PME# disabled
[    0.919593] pci 0000:0f:06.1: reg 10 32bit mmio: [0xfc206000-0xfc2067ff]
[    0.919604] pci 0000:0f:06.1: reg 14 32bit mmio: [0xfc200000-0xfc203fff]
[    0.919661] pci 0000:0f:06.1: supports D1 D2
[    0.919663] pci 0000:0f:06.1: PME# supported from D0 D1 D2 D3hot
[    0.919669] pci 0000:0f:06.1: PME# disabled
[    0.919723] pci 0000:0f:06.2: reg 10 32bit mmio: [0xfc205000-0xfc205fff]
[    0.919783] pci 0000:0f:06.2: supports D1 D2
[    0.919785] pci 0000:0f:06.2: PME# supported from D0 D1 D2 D3hot
[    0.919791] pci 0000:0f:06.2: PME# disabled
[    0.919845] pci 0000:0f:06.3: reg 10 32bit mmio: [0xfc206800-0xfc2068ff]
[    0.919906] pci 0000:0f:06.3: supports D1 D2
[    0.919908] pci 0000:0f:06.3: PME# supported from D0 D1 D2 D3hot
[    0.919913] pci 0000:0f:06.3: PME# disabled
[    0.919982] pci 0000:00:1e.0: transparent bridge
[    0.919991] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc200000-0xfc2fffff]
[    0.920066] bus 00 -> node 0
[    0.920075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.920446] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.920602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.920757] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.920932] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    4.720422] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    4.720555] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[    4.720685] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    4.720813] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[    4.720942] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
[    4.721070] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 *11)
[    4.721199] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[    4.721327] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    4.721825] ACPI: WMI: Mapper loaded
[    4.721865] SCSI subsystem initialized
[    4.721865] libata version 3.00 loaded.
[    4.721865] usbcore: registered new interface driver usbfs
[    4.721865] usbcore: registered new interface driver hub
[    4.721865] usbcore: registered new device driver usb
[    4.721865] PCI: Using ACPI for IRQ routing
[    4.724021] Bluetooth: Core ver 2.13
[    4.724026] NET: Registered protocol family 31
[    4.724026] Bluetooth: HCI device and connection manager initialized
[    4.724026] Bluetooth: HCI socket layer initialized
[    4.724028] NET: Registered protocol family 8
[    4.724030] NET: Registered protocol family 20
[    4.724042] NetLabel: Initializing
[    4.724044] NetLabel:  domain hash size = 128
[    4.724045] NetLabel:  protocols = UNLABELED CIPSOv4
[    4.724060] NetLabel:  unlabeled traffic allowed by default
[    4.724076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    4.724081] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    4.728089] AppArmor: AppArmor Filesystem Enabled
[    4.732017] Switched to high resolution mode on CPU 0
[    4.732469] Switched to high resolution mode on CPU 1
[    4.732479] pnp: PnP ACPI init
[    4.732491] ACPI: bus type pnp registered
[    4.940064] pnp: PnP ACPI: found 11 devices
[    4.940067] ACPI: ACPI bus type pnp unregistered
[    4.940072] PnPBIOS: Disabled by ACPI PNP
[    4.940083] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    4.940086] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    4.940089] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    4.940092] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    4.940095] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    4.940098] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    4.940101] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    4.940109] system 00:06: iomem range 0xfed00000-0xfed003ff has been reserved
[    4.940117] system 00:08: ioport range 0x800-0x80f has been reserved
[    4.940120] system 00:08: ioport range 0x1000-0x107f has been reserved
[    4.940122] system 00:08: ioport range 0x1180-0x11bf has been reserved
[    4.940125] system 00:08: ioport range 0xfe00-0xfe00 has been reserved
[    4.940128] system 00:08: iomem range 0xff800000-0xff800fff has been reserved
[    4.974878] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    4.974882] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    4.974890] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    4.974895] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    4.974904] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    4.974908] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    4.974916] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    4.974921] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    4.974930] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    4.974934] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    4.974941] pci 0000:00:1c.2:   MEM window: 0xfa000000-0xfbffffff
[    4.974947] pci 0000:00:1c.2:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    4.974958] pci 0000:0f:06.0: CardBus bridge, secondary bus 0000:10
[    4.974960] pci 0000:0f:06.0:   IO window: 0x005000-0x0050ff
[    4.974966] pci 0000:0f:06.0:   IO window: 0x005400-0x0054ff
[    4.974972] pci 0000:0f:06.0:   PREFETCH window: 0xc4000000-0xc7ffffff
[    4.974977] pci 0000:0f:06.0:   MEM window: 0xc8000000-0xcbffffff
[    4.974984] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0f
[    4.974988] pci 0000:00:1e.0:   IO window: 0x5000-0x5fff
[    4.974995] pci 0000:00:1e.0:   MEM window: 0xfc200000-0xfc2fffff
[    4.975001] pci 0000:00:1e.0:   PREFETCH window: 0x000000c4000000-0x000000c7ffffff
[    4.975021] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.975028] pci 0000:00:1c.0: setting latency timer to 64
[    4.975039] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.975045] pci 0000:00:1c.1: setting latency timer to 64
[    4.975057] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.975062] pci 0000:00:1c.2: setting latency timer to 64
[    4.975072] pci 0000:00:1e.0: setting latency timer to 64
[    4.975084] pci 0000:0f:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.975092] bus: 00 index 0 io port: [0x00-0xffff]
[    4.975094] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    4.975096] bus: 02 index 0 io port: [0x2000-0x2fff]
[    4.975098] bus: 02 index 1 mmio: [0xf6000000-0xf7ffffff]
[    4.975101] bus: 02 index 2 mmio: [0xf0000000-0xf1ffffff]
[    4.975103] bus: 02 index 3 mmio: [0x0-0x0]
[    4.975105] bus: 04 index 0 io port: [0x3000-0x3fff]
[    4.975107] bus: 04 index 1 mmio: [0xf8000000-0xf9ffffff]
[    4.975109] bus: 04 index 2 mmio: [0xf2000000-0xf3ffffff]
[    4.975111] bus: 04 index 3 mmio: [0x0-0x0]
[    4.975113] bus: 06 index 0 io port: [0x4000-0x4fff]
[    4.975115] bus: 06 index 1 mmio: [0xfa000000-0xfbffffff]
[    4.975118] bus: 06 index 2 mmio: [0xf4000000-0xf5ffffff]
[    4.975120] bus: 06 index 3 mmio: [0x0-0x0]
[    4.975122] bus: 0f index 0 io port: [0x5000-0x5fff]
[    4.975124] bus: 0f index 1 mmio: [0xfc200000-0xfc2fffff]
[    4.975126] bus: 0f index 2 mmio: [0xc4000000-0xc7ffffff]
[    4.975128] bus: 0f index 3 io port: [0x00-0xffff]
[    4.975130] bus: 0f index 4 mmio: [0x000000-0xffffffff]
[    4.975133] bus: 10 index 0 io port: [0x5000-0x50ff]
[    4.975135] bus: 10 index 1 io port: [0x5400-0x54ff]
[    4.975137] bus: 10 index 2 mmio: [0xc4000000-0xc7ffffff]
[    4.975139] bus: 10 index 3 mmio: [0xc8000000-0xcbffffff]
[    4.975149] NET: Registered protocol family 2
[    4.988055] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    4.988329] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    4.988811] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    4.989165] TCP: Hash tables configured (established 131072 bind 65536)
[    4.989168] TCP reno registered
[    4.996118] NET: Registered protocol family 1
[    4.996252] checking if image is initramfs... it is
[    5.643178] Freeing initrd memory: 7358k freed
[    5.643223] Simple Boot Flag at 0x36 set to 0x1
[    5.643406] cpufreq: No nForce2 chipset.
[    5.643554] audit: initializing netlink socket (disabled)
[    5.643573] type=2000 audit(1245759898.640:1): initialized
[    5.651144] highmem bounce pool size: 64 pages
[    5.651152] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    5.652522] VFS: Disk quotas dquot_6.5.1
[    5.652584] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.653222] fuse init (API version 7.10)
[    5.653313] msgmni has been set to 1672
[    5.653493] alg: No test for stdrng (krng)
[    5.653507] io scheduler noop registered
[    5.653509] io scheduler anticipatory registered
[    5.653512] io scheduler deadline registered
[    5.653528] io scheduler cfq registered (default)
[    5.653541] pci 0000:00:02.0: Boot video device
[    6.064160] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    6.064219] pcieport-driver 0000:00:1c.0: found MSI capability
[    6.064260] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    6.064278] pci_express 0000:00:1c.0:pcie00: allocate port service
[    6.064294] pci_express 0000:00:1c.0:pcie02: allocate port service
[    6.064307] pci_express 0000:00:1c.0:pcie03: allocate port service
[    6.064391] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    6.064447] pcieport-driver 0000:00:1c.1: found MSI capability
[    6.064484] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    6.064503] pci_express 0000:00:1c.1:pcie00: allocate port service
[    6.064515] pci_express 0000:00:1c.1:pcie02: allocate port service
[    6.064532] pci_express 0000:00:1c.1:pcie03: allocate port service
[    6.064615] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    6.064672] pcieport-driver 0000:00:1c.2: found MSI capability
[    6.064710] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    6.064728] pci_express 0000:00:1c.2:pcie00: allocate port service
[    6.064740] pci_express 0000:00:1c.2:pcie02: allocate port service
[    6.064753] pci_express 0000:00:1c.2:pcie03: allocate port service
[    6.064843] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    6.065141] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    6.067137] ACPI: AC Adapter [ADP1] (on-line)
[    6.288436] ACPI: Battery Slot [BAT0] (battery present)
[    6.288513] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    6.288516] ACPI: Power Button (FF) [PWRF]
[    6.288559] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    6.291364] ACPI: Lid Switch [LID0]
[    6.291410] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    6.291416] ACPI: Sleep Button (CM) [SLPB]
[    6.291631] ACPI: Extensa 5220 detected - disabling mwait for CPU C-states
[    6.294257] ACPI: SSDT BF6D19CC, 027A (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    6.294732] ACPI: SSDT BF6D1328, 061F (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    6.298842] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    6.298870] processor ACPI_CPU:00: registered as cooling_device0
[    6.298874] ACPI: Processor [CPU0] (supports 8 throttling states)
[    6.302494] ACPI: SSDT BF6D1C46, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    6.302923] ACPI: SSDT BF6D1947, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    6.312997] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    6.313023] processor ACPI_CPU:01: registered as cooling_device1
[    6.313027] ACPI: Processor [CPU1] (supports 8 throttling states)
[    6.543546] thermal LNXTHERM:01: registered as thermal_zone0
[    6.559269] ACPI: Thermal Zone [TZS0] (35 C)
[    6.568292] thermal LNXTHERM:02: registered as thermal_zone1
[    6.573363] ACPI: Thermal Zone [TZS1] (36 C)
[    6.573424] isapnp: Scanning for PnP cards...
[    6.928208] isapnp: No Plug & Play device found
[    6.940281] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    6.941389] brd: module loaded
[    6.941709] loop: module loaded
[    6.941783] Fixed MDIO Bus: probed
[    6.941788] PPP generic driver version 2.4.2
[    6.941851] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    6.941883] Driver 'sd' needs updating - please use bus_type methods
[    6.941893] Driver 'sr' needs updating - please use bus_type methods
[    6.941975] ata_piix 0000:00:1f.1: version 2.12
[    6.941992] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.942035] ata_piix 0000:00:1f.1: setting latency timer to 64
[    6.942135] scsi0 : ata_piix
[    6.942236] scsi1 : ata_piix
[    6.942942] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    6.942945] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    7.104457] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JP01, max UDMA/33
[    7.120393] ata1.00: configured for UDMA/33
[    7.290829] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JP01 PQ: 0 ANSI: 5
[    7.302020] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.302023] Uniform CD-ROM driver Revision: 3.20
[    7.302133] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    7.302180] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    7.302208] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    7.302213] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    7.456033] ata_piix 0000:00:1f.2: setting latency timer to 64
[    7.456097] scsi2 : ata_piix
[    7.456156] scsi3 : ata_piix
[    7.457453] ata3: SATA max UDMA/133 cmd 0x1c00 ctl 0x18f4 bmdma 0x18e0 irq 19
[    7.457460] ata4: SATA max UDMA/133 cmd 0x18f8 ctl 0x18f0 bmdma 0x18e8 irq 19
[    8.252087] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.252106] ata3.01: SATA link down (SStatus 0 SControl 300)
[    8.260521] ata3.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC31P, max UDMA/133
[    8.260523] ata3.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    8.276545] ata3.00: configured for UDMA/133
[    8.927220] ata4.00: SATA link down (SStatus 0 SControl 300)
[    8.927234] ata4.01: SATA link down (SStatus 0 SControl 0)
[    8.927317] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BBCO PQ: 0 ANSI: 5
[    8.927413] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    8.927429] sd 2:0:0:0: [sda] Write Protect is off
[    8.927431] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.927457] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.927518] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    8.927533] sd 2:0:0:0: [sda] Write Protect is off
[    8.927536] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.927561] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.927564]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    8.999221] sd 2:0:0:0: [sda] Attached SCSI disk
[    8.999268] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    8.999986] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    9.000012] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    9.000042] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    9.000046] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    9.000106] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    9.004018] ehci_hcd 0000:00:1a.7: debug port 1
[    9.004025] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    9.004042] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfc504000
[    9.016009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    9.016078] usb usb1: configuration #1 chosen from 1 choice
[    9.016108] hub 1-0:1.0: USB hub found
[    9.016115] hub 1-0:1.0: 4 ports detected
[    9.016224] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    9.016236] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    9.016240] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    9.016290] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    9.020192] ehci_hcd 0000:00:1d.7: debug port 1
[    9.020199] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    9.020215] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504400
[    9.032009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    9.032068] usb usb2: configuration #1 chosen from 1 choice
[    9.032093] hub 2-0:1.0: USB hub found
[    9.032100] hub 2-0:1.0: 6 ports detected
[    9.032200] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    9.032221] uhci_hcd: USB Universal Host Controller Interface driver
[    9.032256] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    9.032264] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    9.032267] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    9.032318] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    9.032346] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001820
[    9.032426] usb usb3: configuration #1 chosen from 1 choice
[    9.032454] hub 3-0:1.0: USB hub found
[    9.032461] hub 3-0:1.0: 2 ports detected
[    9.032552] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    9.032559] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    9.032563] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    9.032605] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    9.032643] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    9.032720] usb usb4: configuration #1 chosen from 1 choice
[    9.032746] hub 4-0:1.0: USB hub found
[    9.032752] hub 4-0:1.0: 2 ports detected
[    9.032841] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    9.032848] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    9.032852] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    9.032902] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    9.032930] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    9.033012] usb usb5: configuration #1 chosen from 1 choice
[    9.033040] hub 5-0:1.0: USB hub found
[    9.033046] hub 5-0:1.0: 2 ports detected
[    9.033138] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.033145] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    9.033149] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    9.033190] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    9.033227] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001880
[    9.033305] usb usb6: configuration #1 chosen from 1 choice
[    9.033330] hub 6-0:1.0: USB hub found
[    9.033337] hub 6-0:1.0: 2 ports detected
[    9.033425] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    9.033432] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    9.033436] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    9.033481] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    9.033518] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    9.033595] usb usb7: configuration #1 chosen from 1 choice
[    9.033621] hub 7-0:1.0: USB hub found
[    9.033628] hub 7-0:1.0: 2 ports detected
[    9.033760] usbcore: registered new interface driver libusual
[    9.033797] usbcore: registered new interface driver usbserial
[    9.033807] USB Serial support registered for generic
[    9.033824] usbcore: registered new interface driver usbserial_generic
[    9.033826] usbserial: USB Serial Driver core
[    9.033880] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.044030] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.050234] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.050240] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.050243] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.050246] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.050248] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.052044] mice: PS/2 mouse device common for all mice
[    9.064076] rtc_cmos 00:09: RTC can wake from S4
[    9.064114] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    9.064150] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    9.064219] device-mapper: uevent: version 1.0.3
[    9.064321] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    9.064394] device-mapper: multipath: version 1.0.5 loaded
[    9.064397] device-mapper: multipath round-robin: version 1.0.0 loaded
[    9.064479] EISA: Probing bus 0 at eisa.0
[    9.064486] Cannot allocate resource for EISA slot 1
[    9.064489] Cannot allocate resource for EISA slot 2
[    9.064491] Cannot allocate resource for EISA slot 3
[    9.064494] Cannot allocate resource for EISA slot 4
[    9.064496] Cannot allocate resource for EISA slot 5
[    9.064511] EISA: Detected 0 cards.
[    9.064629] cpuidle: using governor ladder
[    9.064751] cpuidle: using governor menu
[    9.065285] TCP cubic registered
[    9.065389] NET: Registered protocol family 10
[    9.065837] lo: Disabled Privacy Extensions
[    9.066186] NET: Registered protocol family 17
[    9.066204] Bluetooth: L2CAP ver 2.11
[    9.066206] Bluetooth: L2CAP socket layer initialized
[    9.066209] Bluetooth: SCO (Voice Link) ver 0.6
[    9.066211] Bluetooth: SCO socket layer initialized
[    9.066249] Bluetooth: RFCOMM socket layer initialized
[    9.066257] Bluetooth: RFCOMM TTY layer initialized
[    9.066259] Bluetooth: RFCOMM ver 1.10
[    9.066309] Marking TSC unstable due to TSC halts in idle
[    9.067060] Using IPI No-Shortcut mode
[    9.067145] registered taskstats version 1
[    9.067285]   Magic number: 13:374:431
[    9.067387] rtc_cmos 00:09: setting system clock to 2009-06-23 12:25:03 UTC (1245759903)
[    9.067390] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.067392] EDD information not available.
[    9.067707] Freeing unused kernel memory: 532k freed
[    9.067870] Write protecting the kernel text: 4128k
[    9.067932] Write protecting the kernel read-only data: 1532k
[    9.084762] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    9.361029] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    9.561429] usb 1-1: configuration #1 chosen from 1 choice
[    9.575935] tg3.c:v3.94 (August 14, 2008)
[    9.575995] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.576008] tg3 0000:02:00.0: setting latency timer to 64
[    9.595510] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1d:72:c5:76:ad
[    9.595515] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    9.595517] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    9.683732] ohci1394 0000:0f:06.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.733556] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fc206000-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   10.135667] PM: Starting manual resume from disk
[   10.135671] PM: Resume from partition 8:6
[   10.135673] PM: Checking hibernation image.
[   10.135978] PM: Resume from disk failed.
[   10.179741] kjournald starting.  Commit interval 5 seconds
[   10.179758] EXT3-fs: mounted filesystem with ordered data mode.
[   11.012171] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001d72ffffc576ad]
[   18.883959] udev: starting version 141
[   19.778891] iTCO_vendor_support: vendor-support=0
[   19.891588] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   19.891929] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   19.892023] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.001796] acpi device:05: registered as cooling_device2
[   20.002315] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input5
[   20.005154] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   20.477961] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   20.487521] Linux agpgart interface v0.103
[   20.716955] ieee80211_crypt: registered algorithm 'NULL'
[   20.739616] sdhci: Secure Digital Host Controller Interface driver
[   20.739619] sdhci: Copyright(c) Pierre Ossman
[   20.765914] Linux video capture interface: v2.00
[   20.809126] yenta_cardbus 0000:0f:06.0: CardBus bridge found [1025:011f]
[   20.809152] yenta_cardbus 0000:0f:06.0: Using CSCINT to route CSC interrupts to PCI
[   20.809155] yenta_cardbus 0000:0f:06.0: Routing CardBus interrupts to PCI
[   20.809162] yenta_cardbus 0000:0f:06.0: TI: mfunc 0x01aa1b22, devctl 0x64
[   20.878113] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   20.878553] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   20.882059] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   20.908979] irda_init()
[   20.908992] NET: Registered protocol family 23
[   21.012141] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   21.041394] yenta_cardbus 0000:0f:06.0: ISA IRQ mask 0x0cf8, PCI irq 22
[   21.041398] yenta_cardbus 0000:0f:06.0: Socket status: 30000006
[   21.041402] pci_bus 0000:0f: Raising subordinate bus# of parent bus (#0f) from #10 to #13
[   21.041410] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   21.041413] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.
[   21.041681] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   21.041684] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge Memory window: 0xc4000000 - 0xc7ffffff
[   21.045793] acer-wmi: Acer Laptop ACPI-WMI Extras
[   21.050967] acer-wmi: Brightness must be controlled by generic video driver
[   21.051287] acer-wmi: software RFKILL enabled
[   21.051777] wl: module license '' taints kernel.
[   21.054208] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.054225] wl 0000:04:00.0: setting latency timer to 64
[   21.061731] sdhci-pci 0000:0f:06.3: SDHCI controller found [104c:803c] (rev 0)
[   21.062130] sdhci-pci 0000:0f:06.3: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.062525] mmc0: SDHCI controller on PCI [0000:0f:06.3] using PIO
[   21.113760] tifm_7xx1 0000:0f:06.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.124872] nsc-ircc 00:0a: activated
[   21.124877] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   21.124919] nsc-ircc, chip->init
[   21.124934] nsc-ircc, Found chip at base=0x02e
[   21.125556] nsc-ircc, driver loaded (Dag Brattli)
[   21.126457] IrDA: Registered device irda0
[   21.126524] nsc-ircc, Found dongle: Supports SIR Mode only
[   21.126681] nsc-ircc, chip->init
[   21.126695] nsc-ircc, Found chip at base=0x02e
[   21.126738] nsc-ircc, driver loaded (Dag Brattli)
[   21.126743] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.166099] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.206790] ieee80211_crypt: registered algorithm 'TKIP'
[   21.207164] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.79.10
[   21.263471] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (064e:a103)
[   21.265072] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input7
[   21.268152] usbcore: registered new interface driver uvcvideo
[   21.268178] USB Video Class driver (v0.1.0)
[   21.370551] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   21.370771] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   21.370774] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   21.370776] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   21.690157] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   21.690314] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.707811] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   21.709983] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.710897] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   21.711642] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   21.712598] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   21.723475] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   21.941060] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa04711/0xa04000
[   21.992580] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
[   22.064235] lp: driver loaded but no devices found
[   22.270427] Adding 5719100k swap on /dev/sda6.  Priority:-1 extents:1 across:5719100k
[   22.812926] EXT3 FS on sda5, internal journal
[   24.024462] type=1505 audit(1245774318.456:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2215
[   24.073731] type=1505 audit(1245774318.505:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2219
[   24.073878] type=1505 audit(1245774318.505:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2219
[   24.073929] type=1505 audit(1245774318.505:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2219
[   24.073969] type=1505 audit(1245774318.505:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2219
[   24.211982] type=1505 audit(1245774318.641:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2224
[   24.212224] type=1505 audit(1245774318.641:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2224
[   24.254825] type=1505 audit(1245774318.684:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2228
[   24.300423] type=1505 audit(1245774318.732:10): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=2232
[   28.000083] Clocksource tsc unstable (delta = -116979607 ns)
[   48.799464] tg3 0000:02:00.0: irq 2300 for MSI/MSI-X
[   48.875771] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.986255] ppdev: user-space parallel port driver
[   52.038256] [drm] Initialized drm 1.1.0 20060810
[   52.092861] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   52.092867] pci 0000:00:02.0: setting latency timer to 64
[   52.093000] pci 0000:00:02.0: irq 2299 for MSI/MSI-X
[   52.093101] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   52.095106] [drm:i915_setparam] *ERROR* unknown parameter 4
[   58.576072] eth1: no IPv6 routers present
[  394.060057] eth1: no IPv6 routers present
[  443.548026] eth1: no IPv6 routers present
[  611.958462] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  611.958466] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  611.958469] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.

```

---

### Post by MaindotC on 2009-06-23
For testing purposes, remove the WEP passphrase from your access point and leave it open.  Make sure eth1 is up by using:
```

sudo ifconfig eth1 up

```
Give it 15 seconds, then do
```

iwlist eth1 scan

```
and see if it provides any output.  If it does, then you should be able to connect to the unprotected network.  If you can, THEN try putting the WEP passphrase back on the AP and try connecting that way.

I'm not familiar with WiCD other than it's just a nice little gui for what can easily be accomplished via the command prompt so I'm not sure if it does anything to the dhclient.conf file.  All that file seems to be doing is asking the dhcp server for information and if the dhcp server doesn't have it then I doubt your network connection will refuse to work.

Your hardware output describes that your wireless device is using a Broadcom chip and you are using the wl0 driver.  Please verify that this is the proper chipset in your device and that the proper driver is being used.  If not, we can attack that issue but since you said your device was working properly before with WPA2 I doubt that is the issue.

---

### Post by keyshawn on 2009-06-24
strAlan, Thank you for the response ! 

I followed your directions, removing any security from the WIFI access point. 
Then I did the ifconfig and then the iwlist, and its output was:
iwlist eth1 scan:
eth1      Interface doesn't support scanning.


However, 
I successfully connected to my unprotected wifi network ! Is this result still a problem ? 
I have not tried to reenable the security on the network. I'll reconfigure the network to be WPA and see if that security works. 

Regards, 
keyshawn

---

### Post by MaindotC on 2009-06-24
While you are connected, may I see the output of ifconfig please.  I thought eth1 was your wireless interface but perhaps I was mistaken.

---

### Post by keyshawn on 2009-06-28
here's my ifconfig, after being connected continuously for about 3-4 days:  

```
eth0      Link encap:Ethernet  HWaddr 00:1d:72:c5:76:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:22:69:0a:ef:69  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe0a:ef69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5317720 errors:0 dropped:0 overruns:0 frame:758448
          TX packets:5213351 errors:373 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1411106324 (1.4 GB)  TX bytes:3973039111 (3.9 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54145 (54.1 KB)  TX bytes:54145 (54.1 KB)


```

---

### Post by keyshawn on 2009-07-06
I realized that I was not able to get the interface because I was not using root, so here is the correct output 

(I edited the address of my network)

```
 sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: XX:XX:BF:XX:XX:X9
                    ESSID:"thisiskeyshawnsnetworkname"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-60 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:18:F8:68:DA:BC
                    ESSID:"@HomeDABC"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:23:51:77:79:59
                    ESSID:"2WIRE214"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:22:A4:8D:78:01
                    ESSID:"2WIRE734"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

---

### Post by MaindotC on 2009-07-08
Well, you have an IP address and you're wireless card is correctly scanning for networks.  Is there still a problem?

---

