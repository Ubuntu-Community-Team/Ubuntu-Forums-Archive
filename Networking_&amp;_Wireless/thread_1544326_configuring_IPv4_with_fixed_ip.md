---
title: "configuring IPv4 with fixed ip"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by Hetepeperfan on 2010-08-02
Hi,

Is there anyone experiencing similar problems like me? Our router is pretty old and only capable of giving fixed ip and there is no support for IPv6. Via the gnome networkmanager I try to set a manual IP to 192.168.1.123 and a netmask to 255.255.255.0 and a default gw at 192.168.1.1 . However, this does not work.

If I open a terminal and type:

```
sudo ifconfig eth0 inet 192.168.1.123
sudo route add default gw 192.168.1.1
```Then I get a perfectly valid connection to the internet. 
ifconfig by it self returns:

```
myname@mycomp:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:74:e1:be  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe74:e1be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:8122461 (8.1 MB)  TX bytes:1243808 (1.2 MB)

```The difference between the ifconfig before and after the ```
sudo ifconfig eth0 inet 192.168.1.123
sudo route add default gw 192.168.1.1
```commando is that only after the CLI commando's the inet line is added to the ifconfig output.

ffor me it seems that the gnome network manager doesn't save the information that I gently ask it to.
I hope someone can help me.

I can fix it with the CLI commands, but I would like to know whats going on.

Kind regards,

Maarten

---

### Post by marc.verwerft on 2010-08-02
Look for the network-manager applet/icon on your desktop, right-click on it and select 'Edit connections' or select 'System/Preferences/Network connections'.
Typically your connection should show up as 'auto eth0'. If it doesn't, add it. Make sure that in the IPv4 tab, you have selected 'Manual' as 'Method'.
Fill in your data for the connection as necessary.

Regards,

Marc

---

### Post by Hetepeperfan on 2010-08-02
> **marc.verwerft said:**
> Look for the network-manager applet/icon on your desktop, right-click on it and select 'Edit connections' or select 'System/Preferences/Network connections'.
Typically your connection should show up as 'auto eth0'. If it doesn't, add it. Make sure that in the IPv4 tab, you have selected 'Manual' as 'Method'.
Fill in your data for the connection as necessary.

Regards,

Marc

Hi Marc,

Thanks for your fast reply! But unfortunately this doesnt help me. I did as you told via system/preferences/network-connections. The auto-eth0 never was there I must admit. Thus I added the 'auto-eth0' connection. But I had allready some connections with different names with a manual IPv4 settings. But every time I reboot my computer ifconfig prints an IPv6 adress for eth0 but the inet (IPv4) settings are not there. I suppose for the network-connections it doesn't really matter if I name the connection 'auto eth0' or 'wired connection'. I've got three diiferent connections all have a manual ipv4 setting to manual.

However I really need to do

```
ipconfig eth0 inet 192.168.1.123
```to be able to  ping the router and 

```
route add default gw 192.168.1.1
```to tell my system to comunnicate with the router in order to access internet.

Do you perhaps have any other ideas?

---

### Post by marc.verwerft on 2010-08-02
Are you sure that the ipv6 tab of your connection (under edit connection) is set to 'ignore'?

Can you perhaps send the dmesg output and /var/log/messages?

Regards,

Marc

---

### Post by Hetepeperfan on 2010-08-02
Hi Mark,

Thanks for your attention.

Yes as soon a I start to edit the IPv4 connection the IPv6  is automatically set to ignore on my system, I just double checked it and it is set to ignore. The network-connecitons manager tell me that it has never used one of my connections.

the content  of /var/log/messages/ =

```

Aug  2 11:25:38 mja-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="606" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug  2 11:52:18 mja-desktop kernel: Kernel logging (proc) stopped.
Aug  2 11:52:47 mja-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug  2 11:52:47 mja-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="547" x-info="http://www.rsyslog.com"] (re)start
Aug  2 11:52:47 mja-desktop rsyslogd: rsyslogd's groupid changed to 103
Aug  2 11:52:47 mja-desktop rsyslogd: rsyslogd's userid changed to 102
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] KERNEL supported cpus:
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   Intel GenuineIntel
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   AMD AuthenticAMD
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   NSC Geode by NSC
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   Centaur CentaurHauls
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff72000 (ACPI NVS)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff72000 - 000000001ff93000 (ACPI data)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff93000 - 0000000020000000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] DMI 2.3 present.
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] modified physical RAM map:
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000001ff70000 (usable)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 000000001ff70000 - 000000001ff72000 (ACPI NVS)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 000000001ff72000 - 000000001ff93000 (ACPI data)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 000000001ff93000 - 0000000020000000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] RAMDISK: 1f7d7000 - 1ff5ff90
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: RSDP 000feba0 00014 (v00 DELL  )
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: RSDT 000fd192 00038 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: FACP 000fd1ca 00074 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: DSDT fffd2759 02795 (v01   DELL    dt_ex 00001000 MSFT 0100000D)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: FACS 1ff70000 00040
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: SSDT fffd4eee 000A7 (v01   DELL    st_ex 00001000 MSFT 0100000D)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: APIC 000fd23e 0006C (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: BOOT 000fd2aa 00028 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: ASF! 000fd2d2 00067 (v16 DELL    GX270   00000007 ASL  00000061)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] 511MB LOWMEM available.
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   mapped low ram: 0 - 1ff70000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   low ram: 0 - 1ff70000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 1ff70000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bff0
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ff70000]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #4 [001f7d7000 - 001ff5ff90]          RAMDISK ==> [001f7d7000 - 001ff5ff90]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #6 [00008dc000 - 00008df18c]              BRK ==> [00008dc000 - 00008df18c]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] found SMP MP-table at [c00fe710] fe710
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Zone PFN ranges:
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x0001ff70
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]   HighMem  0x0001ff70 -> 0x0001ff70
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x000000a0
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0001ff70
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Using APIC driver default
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u1048576
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129805
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Kernel command line: root=UUID=baf3a80c-4e26-4d98-83d6-305197df60c3 ro quiet splash 
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Initializing CPU#0
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] allocated 2618560 bytes of page_cgroup
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Memory: 499660k/523712k available (4679k kernel code, 23108k reserved, 2116k data, 660k init, 0k highmem)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] virtual kernel memory layout:
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] console [tty0] enabled
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Aug  2 11:52:47 mja-desktop kernel: [    0.000000] Detected 2793.527 MHz processor.
Aug  2 11:52:47 mja-desktop kernel: [    0.008006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5587.05 BogoMIPS (lpj=11174108)
Aug  2 11:52:47 mja-desktop kernel: [    0.008028] Security Framework initialized
Aug  2 11:52:47 mja-desktop kernel: [    0.008054] AppArmor: AppArmor initialized
Aug  2 11:52:47 mja-desktop kernel: [    0.008064] Mount-cache hash table entries: 512
Aug  2 11:52:47 mja-desktop kernel: [    0.008229] Initializing cgroup subsys ns
Aug  2 11:52:47 mja-desktop kernel: [    0.008236] Initializing cgroup subsys cpuacct
Aug  2 11:52:47 mja-desktop kernel: [    0.008241] Initializing cgroup subsys memory
Aug  2 11:52:47 mja-desktop kernel: [    0.008250] Initializing cgroup subsys devices
Aug  2 11:52:47 mja-desktop kernel: [    0.008254] Initializing cgroup subsys freezer
Aug  2 11:52:47 mja-desktop kernel: [    0.008257] Initializing cgroup subsys net_cls
Aug  2 11:52:47 mja-desktop kernel: [    0.008285] CPU: Trace cache: 12K uops, L1 D cache: 8K
Aug  2 11:52:47 mja-desktop kernel: [    0.008289] CPU: L2 cache: 512K
Aug  2 11:52:47 mja-desktop kernel: [    0.008292] CPU: Hyper-Threading is disabled
Aug  2 11:52:47 mja-desktop kernel: [    0.008297] mce: CPU supports 4 MCE banks
Aug  2 11:52:47 mja-desktop kernel: [    0.008309] CPU0: Thermal monitoring enabled (TM1)
Aug  2 11:52:47 mja-desktop kernel: [    0.008320] Performance Events: no PMU driver, software events only.
Aug  2 11:52:47 mja-desktop kernel: [    0.008328] Checking 'hlt' instruction... OK.
Aug  2 11:52:47 mja-desktop kernel: [    0.024926] SMP alternatives: switching to UP code
Aug  2 11:52:47 mja-desktop kernel: [    0.035920] ACPI: Core revision 20090903
Aug  2 11:52:47 mja-desktop kernel: [    0.073603] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug  2 11:52:47 mja-desktop kernel: [    0.073611] ftrace: allocating 21780 entries in 43 pages
Aug  2 11:52:47 mja-desktop kernel: [    0.076089] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug  2 11:52:47 mja-desktop kernel: [    0.076388] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  2 11:52:47 mja-desktop kernel: [    0.117820] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] Brought up 1 CPUs
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] Total of 1 processors activated (5587.05 BogoMIPS).
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] devtmpfs: initialized
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] regulator: core version 0.5
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] Time:  9:52:36  Date: 08/02/10
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] NET: Registered protocol family 16
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] EISA bus registered
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] ACPI: bus type pci registered
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] PCI: PCI BIOS revision 2.10 entry at 0xfbab0, last bus=2
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] PCI: Using configuration type 1 for base access
Aug  2 11:52:47 mja-desktop kernel: [    0.120001] bio: create slab <bio-0> at 0
Aug  2 11:52:47 mja-desktop kernel: [    0.148108] ACPI: Interpreter enabled
Aug  2 11:52:47 mja-desktop kernel: [    0.148128] ACPI: (supports S0 S1 S3 S4 S5)
Aug  2 11:52:47 mja-desktop kernel: [    0.148156] ACPI: Using IOAPIC for interrupt routing
Aug  2 11:52:47 mja-desktop kernel: [    0.175985] ACPI: No dock devices found.
Aug  2 11:52:47 mja-desktop kernel: [    0.180107] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  2 11:52:47 mja-desktop kernel: [    0.180156] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
Aug  2 11:52:47 mja-desktop kernel: [    0.180658] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug  2 11:52:47 mja-desktop kernel: [    0.180664] pci 0000:00:1d.7: PME# disabled
Aug  2 11:52:47 mja-desktop kernel: [    0.180760] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Aug  2 11:52:47 mja-desktop kernel: [    0.180764] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
Aug  2 11:52:47 mja-desktop kernel: [    0.181043] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Aug  2 11:52:47 mja-desktop kernel: [    0.181048] pci 0000:00:1f.5: PME# disabled
Aug  2 11:52:47 mja-desktop kernel: [    0.181383] pci 0000:02:0c.0: PME# supported from D0 D3hot D3cold
Aug  2 11:52:47 mja-desktop kernel: [    0.181388] pci 0000:02:0c.0: PME# disabled
Aug  2 11:52:47 mja-desktop kernel: [    0.181421] pci 0000:00:1e.0: transparent bridge
Aug  2 11:52:47 mja-desktop kernel: [    0.300372] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Aug  2 11:52:47 mja-desktop kernel: [    0.300687] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
Aug  2 11:52:47 mja-desktop kernel: [    0.300999] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Aug  2 11:52:47 mja-desktop kernel: [    0.301310] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Aug  2 11:52:47 mja-desktop kernel: [    0.301618] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 11:52:47 mja-desktop kernel: [    0.301930] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 11:52:47 mja-desktop kernel: [    0.302238] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 11:52:47 mja-desktop kernel: [    0.302552] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Aug  2 11:52:47 mja-desktop kernel: [    0.302732] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug  2 11:52:47 mja-desktop kernel: [    0.302736] vgaarb: loaded
Aug  2 11:52:47 mja-desktop kernel: [    0.302895] SCSI subsystem initialized
Aug  2 11:52:47 mja-desktop kernel: [    0.303067] usbcore: registered new interface driver usbfs
Aug  2 11:52:47 mja-desktop kernel: [    0.303082] usbcore: registered new interface driver hub
Aug  2 11:52:47 mja-desktop kernel: [    0.303112] usbcore: registered new device driver usb
Aug  2 11:52:47 mja-desktop kernel: [    0.303267] ACPI: WMI: Mapper loaded
Aug  2 11:52:47 mja-desktop kernel: [    0.303270] PCI: Using ACPI for IRQ routing
Aug  2 11:52:47 mja-desktop kernel: [    0.303440] NetLabel: Initializing
Aug  2 11:52:47 mja-desktop kernel: [    0.303443] NetLabel:  domain hash size = 128
Aug  2 11:52:47 mja-desktop kernel: [    0.303444] NetLabel:  protocols = UNLABELED CIPSOv4
Aug  2 11:52:47 mja-desktop kernel: [    0.303460] NetLabel:  unlabeled traffic allowed by default
Aug  2 11:52:47 mja-desktop kernel: [    0.303594] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug  2 11:52:47 mja-desktop kernel: [    0.303600] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug  2 11:52:47 mja-desktop kernel: [    0.303607] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Aug  2 11:52:47 mja-desktop kernel: [    0.308026] Switching to clocksource tsc
Aug  2 11:52:47 mja-desktop kernel: [    0.310246] AppArmor: AppArmor Filesystem Enabled
Aug  2 11:52:47 mja-desktop kernel: [    0.310269] pnp: PnP ACPI init
Aug  2 11:52:47 mja-desktop kernel: [    0.310292] ACPI: bus type pnp registered
Aug  2 11:52:47 mja-desktop kernel: [    0.337926] pnp 00:0a: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Aug  2 11:52:47 mja-desktop kernel: [    0.337932] pnp 00:0a: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Aug  2 11:52:47 mja-desktop kernel: [    0.338625] pnp: PnP ACPI: found 11 devices
Aug  2 11:52:47 mja-desktop kernel: [    0.338628] ACPI: ACPI bus type pnp unregistered
Aug  2 11:52:47 mja-desktop kernel: [    0.338635] PnPBIOS: Disabled by ACPI PNP
Aug  2 11:52:47 mja-desktop kernel: [    0.338648] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338654] system 00:00: iomem range 0x100000-0xffffff could not be reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338658] system 00:00: iomem range 0x1000000-0x1ff6ffff could not be reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338661] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338665] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338669] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338672] system 00:00: iomem range 0xfed20000-0xfed8ffff has been reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338676] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338679] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338683] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.338694] system 00:0a: ioport range 0xc00-0xc7f has been reserved
Aug  2 11:52:47 mja-desktop kernel: [    0.373449] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Aug  2 11:52:47 mja-desktop kernel: [    0.373454] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
Aug  2 11:52:47 mja-desktop kernel: [    0.373460] pci 0000:00:01.0:   MEM window: 0xfe900000-0xfeafffff
Aug  2 11:52:47 mja-desktop kernel: [    0.373466] pci 0000:00:01.0:   PREFETCH window: 0xc8000000-0xefffffff
Aug  2 11:52:47 mja-desktop kernel: [    0.373473] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Aug  2 11:52:47 mja-desktop kernel: [    0.373476] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Aug  2 11:52:47 mja-desktop kernel: [    0.373482] pci 0000:00:1e.0:   MEM window: 0xfe800000-0xfe8fffff
Aug  2 11:52:47 mja-desktop kernel: [    0.373487] pci 0000:00:1e.0:   PREFETCH window: disabled
Aug  2 11:52:47 mja-desktop kernel: [    0.373582] NET: Registered protocol family 2
Aug  2 11:52:47 mja-desktop kernel: [    0.373697] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Aug  2 11:52:47 mja-desktop kernel: [    0.374018] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Aug  2 11:52:47 mja-desktop kernel: [    0.374088] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Aug  2 11:52:47 mja-desktop kernel: [    0.374156] TCP: Hash tables configured (established 16384 bind 16384)
Aug  2 11:52:47 mja-desktop kernel: [    0.374159] TCP reno registered
Aug  2 11:52:47 mja-desktop kernel: [    0.374259] NET: Registered protocol family 1
Aug  2 11:52:47 mja-desktop kernel: [    0.374472] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Aug  2 11:52:47 mja-desktop kernel: [    0.374475] Simple Boot Flag at 0x7a set to 0x1
Aug  2 11:52:47 mja-desktop kernel: [    0.374578] cpufreq-nforce2: No nForce2 chipset.
Aug  2 11:52:47 mja-desktop kernel: [    0.374613] Scanning for low memory corruption every 60 seconds
Aug  2 11:52:47 mja-desktop kernel: [    0.374747] audit: initializing netlink socket (disabled)
Aug  2 11:52:47 mja-desktop kernel: [    0.374760] type=2000 audit(1280742755.371:1): initialized
Aug  2 11:52:47 mja-desktop kernel: [    0.383260] Trying to unpack rootfs image as initramfs...
Aug  2 11:52:47 mja-desktop kernel: [    0.392311] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug  2 11:52:47 mja-desktop kernel: [    0.397842] VFS: Disk quotas dquot_6.5.2
Aug  2 11:52:47 mja-desktop kernel: [    0.397916] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  2 11:52:47 mja-desktop kernel: [    0.398638] fuse init (API version 7.13)
Aug  2 11:52:47 mja-desktop kernel: [    0.398744] msgmni has been set to 976
Aug  2 11:52:47 mja-desktop kernel: [    0.404456] alg: No test for stdrng (krng)
Aug  2 11:52:47 mja-desktop kernel: [    0.404571] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug  2 11:52:47 mja-desktop kernel: [    0.404575] io scheduler noop registered
Aug  2 11:52:47 mja-desktop kernel: [    0.404577] io scheduler anticipatory registered
Aug  2 11:52:47 mja-desktop kernel: [    0.404580] io scheduler deadline registered
Aug  2 11:52:47 mja-desktop kernel: [    0.404636] io scheduler cfq registered (default)
Aug  2 11:52:47 mja-desktop kernel: [    0.404773] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  2 11:52:47 mja-desktop kernel: [    0.404802] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug  2 11:52:47 mja-desktop kernel: [    0.404907] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Aug  2 11:52:47 mja-desktop kernel: [    0.404917] ACPI: Power Button [VBTN]
Aug  2 11:52:47 mja-desktop kernel: [    0.404980] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Aug  2 11:52:47 mja-desktop kernel: [    0.404983] ACPI: Power Button [PWRF]
Aug  2 11:52:47 mja-desktop kernel: [    0.405215] processor LNXCPU:00: registered as cooling_device0
Aug  2 11:52:47 mja-desktop kernel: [    0.442221] isapnp: Scanning for PnP cards...
Aug  2 11:52:47 mja-desktop kernel: [    0.447962] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug  2 11:52:47 mja-desktop kernel: [    0.448063] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  2 11:52:47 mja-desktop kernel: [    0.448477] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  2 11:52:47 mja-desktop kernel: [    0.449707] brd: module loaded
Aug  2 11:52:47 mja-desktop kernel: [    0.450268] loop: module loaded
Aug  2 11:52:47 mja-desktop kernel: [    0.450384] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Aug  2 11:52:47 mja-desktop kernel: [    0.450539] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 11:52:47 mja-desktop kernel: [    0.456112] scsi0 : ata_piix
Aug  2 11:52:47 mja-desktop kernel: [    0.456279] scsi1 : ata_piix
Aug  2 11:52:47 mja-desktop kernel: [    0.456323] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Aug  2 11:52:47 mja-desktop kernel: [    0.456327] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Aug  2 11:52:47 mja-desktop kernel: [    0.456376] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 11:52:47 mja-desktop kernel: [    0.456383] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Aug  2 11:52:47 mja-desktop kernel: [    0.456515] scsi2 : ata_piix
Aug  2 11:52:47 mja-desktop kernel: [    0.504293] scsi3 : ata_piix
Aug  2 11:52:47 mja-desktop kernel: [    0.504370] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 18
Aug  2 11:52:47 mja-desktop kernel: [    0.504374] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 18
Aug  2 11:52:47 mja-desktop kernel: [    0.504809] Fixed MDIO Bus: probed
Aug  2 11:52:47 mja-desktop kernel: [    0.504853] PPP generic driver version 2.4.2
Aug  2 11:52:47 mja-desktop kernel: [    0.504939] tun: Universal TUN/TAP device driver, 1.6
Aug  2 11:52:47 mja-desktop kernel: [    0.504942] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug  2 11:52:47 mja-desktop kernel: [    0.505051] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug  2 11:52:47 mja-desktop kernel: [    0.505092] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Aug  2 11:52:47 mja-desktop kernel: [    0.505117] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug  2 11:52:47 mja-desktop kernel: [    0.505168] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Aug  2 11:52:47 mja-desktop kernel: [    0.505202] ehci_hcd 0000:00:1d.7: debug port 1
Aug  2 11:52:47 mja-desktop kernel: [    0.509430] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
Aug  2 11:52:47 mja-desktop kernel: [    0.528050] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug  2 11:52:47 mja-desktop kernel: [    0.528214] usb usb1: configuration #1 chosen from 1 choice
Aug  2 11:52:47 mja-desktop kernel: [    0.528253] hub 1-0:1.0: USB hub found
Aug  2 11:52:47 mja-desktop kernel: [    0.528266] hub 1-0:1.0: 8 ports detected
Aug  2 11:52:47 mja-desktop kernel: [    0.528355] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug  2 11:52:47 mja-desktop kernel: [    0.528375] uhci_hcd: USB Universal Host Controller Interface driver
Aug  2 11:52:47 mja-desktop kernel: [    0.528444] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 11:52:47 mja-desktop kernel: [    0.528459] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  2 11:52:47 mja-desktop kernel: [    0.528509] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug  2 11:52:47 mja-desktop kernel: [    0.528546] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
Aug  2 11:52:47 mja-desktop kernel: [    0.528655] usb usb2: configuration #1 chosen from 1 choice
Aug  2 11:52:47 mja-desktop kernel: [    0.528688] hub 2-0:1.0: USB hub found
Aug  2 11:52:47 mja-desktop kernel: [    0.528697] hub 2-0:1.0: 2 ports detected
Aug  2 11:52:47 mja-desktop kernel: [    0.528760] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug  2 11:52:47 mja-desktop kernel: [    0.528771] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  2 11:52:47 mja-desktop kernel: [    0.528814] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Aug  2 11:52:47 mja-desktop kernel: [    0.528845] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
Aug  2 11:52:47 mja-desktop kernel: [    0.528950] usb usb3: configuration #1 chosen from 1 choice
Aug  2 11:52:47 mja-desktop kernel: [    0.528984] hub 3-0:1.0: USB hub found
Aug  2 11:52:47 mja-desktop kernel: [    0.528995] hub 3-0:1.0: 2 ports detected
Aug  2 11:52:47 mja-desktop kernel: [    0.529045] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  2 11:52:47 mja-desktop kernel: [    0.529056] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  2 11:52:47 mja-desktop kernel: [    0.529094] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Aug  2 11:52:47 mja-desktop kernel: [    0.529117] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Aug  2 11:52:47 mja-desktop kernel: [    0.529221] usb usb4: configuration #1 chosen from 1 choice
Aug  2 11:52:47 mja-desktop kernel: [    0.529256] hub 4-0:1.0: USB hub found
Aug  2 11:52:47 mja-desktop kernel: [    0.529264] hub 4-0:1.0: 2 ports detected
Aug  2 11:52:47 mja-desktop kernel: [    0.529314] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 11:52:47 mja-desktop kernel: [    0.529324] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug  2 11:52:47 mja-desktop kernel: [    0.529362] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Aug  2 11:52:47 mja-desktop kernel: [    0.529385] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
Aug  2 11:52:47 mja-desktop kernel: [    0.529485] usb usb5: configuration #1 chosen from 1 choice
Aug  2 11:52:47 mja-desktop kernel: [    0.529517] hub 5-0:1.0: USB hub found
Aug  2 11:52:47 mja-desktop kernel: [    0.529526] hub 5-0:1.0: 2 ports detected
Aug  2 11:52:47 mja-desktop kernel: [    0.529631] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
Aug  2 11:52:47 mja-desktop kernel: [    0.529634] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug  2 11:52:47 mja-desktop kernel: [    0.530369] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  2 11:52:47 mja-desktop kernel: [    0.530515] mice: PS/2 mouse device common for all mice
Aug  2 11:52:47 mja-desktop kernel: [    0.530662] rtc_cmos 00:05: RTC can wake from S4
Aug  2 11:52:47 mja-desktop kernel: [    0.530712] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Aug  2 11:52:47 mja-desktop kernel: [    0.530741] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
Aug  2 11:52:47 mja-desktop kernel: [    0.530882] device-mapper: uevent: version 1.0.3
Aug  2 11:52:47 mja-desktop kernel: [    0.534102] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Aug  2 11:52:47 mja-desktop kernel: [    0.536149] device-mapper: multipath: version 1.1.0 loaded
Aug  2 11:52:47 mja-desktop kernel: [    0.536154] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug  2 11:52:47 mja-desktop kernel: [    0.536369] EISA: Probing bus 0 at eisa.0
Aug  2 11:52:47 mja-desktop kernel: [    0.536407] EISA: Detected 0 cards.
Aug  2 11:52:47 mja-desktop kernel: [    0.540122] cpuidle: using governor ladder
Aug  2 11:52:47 mja-desktop kernel: [    0.540127] cpuidle: using governor menu
Aug  2 11:52:47 mja-desktop kernel: [    0.540780] TCP cubic registered
Aug  2 11:52:47 mja-desktop kernel: [    0.540941] NET: Registered protocol family 10
Aug  2 11:52:47 mja-desktop kernel: [    0.541492] lo: Disabled Privacy Extensions
Aug  2 11:52:47 mja-desktop kernel: [    0.541877] NET: Registered protocol family 17
Aug  2 11:52:47 mja-desktop kernel: [    0.541946] Using IPI No-Shortcut mode
Aug  2 11:52:47 mja-desktop kernel: [    0.542081] registered taskstats version 1
Aug  2 11:52:47 mja-desktop kernel: [    0.542354]   Magic number: 6:453:878
Aug  2 11:52:47 mja-desktop kernel: [    0.542438] rtc_cmos 00:05: setting system clock to 2010-08-02 09:52:36 UTC (1280742756)
Aug  2 11:52:47 mja-desktop kernel: [    0.542442] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  2 11:52:47 mja-desktop kernel: [    0.542444] EDD information not available.
Aug  2 11:52:47 mja-desktop kernel: [    0.609729] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Aug  2 11:52:47 mja-desktop kernel: [    0.700810] ata3.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
Aug  2 11:52:47 mja-desktop kernel: [    0.700816] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug  2 11:52:47 mja-desktop kernel: [    0.700922] ata4.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
Aug  2 11:52:47 mja-desktop kernel: [    0.700926] ata4.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug  2 11:52:47 mja-desktop kernel: [    0.701363] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-252S, R901, max UDMA/33
Aug  2 11:52:47 mja-desktop kernel: [    0.701407] ata2.01: ATAPI: HL-DT-STDVDRRW GCA-4164B, H.I0, max UDMA/33
Aug  2 11:52:47 mja-desktop kernel: [    0.708732] ata4.00: configured for UDMA/100
Aug  2 11:52:47 mja-desktop kernel: [    0.708793] ata3.00: configured for UDMA/100
Aug  2 11:52:47 mja-desktop kernel: [    0.716395] ata2.00: configured for UDMA/33
Aug  2 11:52:47 mja-desktop kernel: [    0.732503] ata2.01: configured for UDMA/33
Aug  2 11:52:47 mja-desktop kernel: [    0.892108] Freeing initrd memory: 7715k freed
Aug  2 11:52:47 mja-desktop kernel: [    1.030334] isapnp: No Plug & Play device found
Aug  2 11:52:47 mja-desktop kernel: [    1.031339] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-252S  R901 PQ: 0 ANSI: 5
Aug  2 11:52:47 mja-desktop kernel: [    1.035293] sr0: scsi3-mmc drive: 48x/16x writer cd/rw xa/form2 cdda tray
Aug  2 11:52:47 mja-desktop kernel: [    1.035298] Uniform CD-ROM driver Revision: 3.20
Aug  2 11:52:47 mja-desktop kernel: [    1.035526] sr 1:0:0:0: Attached scsi generic sg0 type 5
Aug  2 11:52:47 mja-desktop kernel: [    1.037021] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRRW GCA-4164B H.I0 PQ: 0 ANSI: 5
Aug  2 11:52:47 mja-desktop kernel: [    1.042132] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Aug  2 11:52:47 mja-desktop kernel: [    1.042300] sr 1:0:1:0: Attached scsi generic sg1 type 5
Aug  2 11:52:47 mja-desktop kernel: [    1.042434] scsi 2:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
Aug  2 11:52:47 mja-desktop kernel: [    1.042579] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug  2 11:52:47 mja-desktop kernel: [    1.042712] scsi 3:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
Aug  2 11:52:47 mja-desktop kernel: [    1.042846] sd 3:0:0:0: Attached scsi generic sg3 type 0
Aug  2 11:52:47 mja-desktop kernel: [    1.042929] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug  2 11:52:47 mja-desktop kernel: [    1.042977] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug  2 11:52:47 mja-desktop kernel: [    1.043045] sd 3:0:0:0: [sdb] Write Protect is off
Aug  2 11:52:47 mja-desktop kernel: [    1.043078] sd 2:0:0:0: [sda] Write Protect is off
Aug  2 11:52:47 mja-desktop kernel: [    1.043111] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 11:52:47 mja-desktop kernel: [    1.043190] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 11:52:47 mja-desktop kernel: [    1.043427]  sda:
Aug  2 11:52:47 mja-desktop kernel: [    1.043521]  sdb: sdb1 sdb2 < sda1
Aug  2 11:52:47 mja-desktop kernel: [    1.064724] sd 2:0:0:0: [sda] Attached SCSI disk
Aug  2 11:52:47 mja-desktop kernel: [    1.085812]  sdb5 >
Aug  2 11:52:47 mja-desktop kernel: [    1.086124] sd 3:0:0:0: [sdb] Attached SCSI disk
Aug  2 11:52:47 mja-desktop kernel: [    1.086143] Freeing unused kernel memory: 660k freed
Aug  2 11:52:47 mja-desktop kernel: [    1.086775] Write protecting the kernel text: 4680k
Aug  2 11:52:47 mja-desktop kernel: [    1.086807] Write protecting the kernel read-only data: 1840k
Aug  2 11:52:47 mja-desktop kernel: [    1.095961] usb 3-2: new low speed USB device using uhci_hcd and address 2
Aug  2 11:52:47 mja-desktop kernel: [    1.111665] udev: starting version 151
Aug  2 11:52:47 mja-desktop kernel: [    1.272809] usb 3-2: configuration #1 chosen from 1 choice
Aug  2 11:52:47 mja-desktop kernel: [    1.356910] Floppy drive(s): fd0 is 1.44M
Aug  2 11:52:47 mja-desktop kernel: [    1.364353] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
Aug  2 11:52:47 mja-desktop kernel: [    1.364359] Copyright (c) 1999-2006 Intel Corporation.
Aug  2 11:52:47 mja-desktop kernel: [    1.364408] e1000 0000:02:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 11:52:47 mja-desktop kernel: [    1.374125] FDC 0 is a post-1991 82077
Aug  2 11:52:47 mja-desktop kernel: [    1.383934] usbcore: registered new interface driver hiddev
Aug  2 11:52:47 mja-desktop kernel: [    1.638852] e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0f:1f:74:e1:be
Aug  2 11:52:47 mja-desktop kernel: [    1.639682] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
Aug  2 11:52:47 mja-desktop kernel: [    1.639960] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
Aug  2 11:52:47 mja-desktop kernel: [    1.640075] usbcore: registered new interface driver usbhid
Aug  2 11:52:47 mja-desktop kernel: [    1.640440] usbhid: v2.6:USB HID core driver
Aug  2 11:52:47 mja-desktop kernel: [    1.677190] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Aug  2 11:52:47 mja-desktop kernel: [    1.848379] kjournald starting.  Commit interval 5 seconds
Aug  2 11:52:47 mja-desktop kernel: [    1.848394] EXT3-fs: mounted filesystem with ordered data mode.
Aug  2 11:52:47 mja-desktop kernel: [   10.396391] Adding 1510068k swap on /dev/sdb5.  Priority:-1 extents:1 across:1510068k 
Aug  2 11:52:47 mja-desktop kernel: [   10.461224] udev: starting version 151
Aug  2 11:52:47 mja-desktop kernel: [   10.524738] EXT3 FS on sda1, internal journal
Aug  2 11:52:47 mja-desktop kernel: [   10.652694] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  2 11:52:47 mja-desktop kernel: [   10.738002] lp: driver loaded but no devices found
Aug  2 11:52:47 mja-desktop kernel: [   10.833155] Linux agpgart interface v0.103
Aug  2 11:52:47 mja-desktop kernel: [   10.871240] intel_rng: FWH not detected
Aug  2 11:52:47 mja-desktop kernel: [   10.916206] parport_pc 00:09: reported by Plug and Play ACPI
Aug  2 11:52:47 mja-desktop kernel: [   10.916258] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Aug  2 11:52:47 mja-desktop kernel: [   10.946305] agpgart-intel 0000:00:00.0: Intel 865 Chipset
Aug  2 11:52:47 mja-desktop kernel: [   10.987175] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Aug  2 11:52:47 mja-desktop kernel: [   11.004069] dell-wmi: No known WMI GUID found
Aug  2 11:52:47 mja-desktop kernel: [   11.030550] lp0: using parport0 (interrupt-driven).
Aug  2 11:52:47 mja-desktop kernel: [   11.104126] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xc0000000
Aug  2 11:52:47 mja-desktop kernel: [   11.158312] ppdev: user-space parallel port driver
Aug  2 11:52:47 mja-desktop kernel: [   11.158880] [drm] Initialized drm 1.1.0 20060810
Aug  2 11:52:47 mja-desktop kernel: [   11.219775] type=1505 audit(1280742767.173:2):  operation="profile_load" pid=495 name="/sbin/dhclient3"
Aug  2 11:52:47 mja-desktop kernel: [   11.220379] type=1505 audit(1280742767.177:3):  operation="profile_load" pid=495 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug  2 11:52:47 mja-desktop kernel: [   11.220675] type=1505 audit(1280742767.177:4):  operation="profile_load" pid=495 name="/usr/lib/connman/scripts/dhclient-script"
Aug  2 11:52:47 mja-desktop kernel: [   11.382671] [drm] radeon defaulting to kernel modesetting.
Aug  2 11:52:47 mja-desktop kernel: [   11.382677] [drm] radeon kernel modesetting enabled.
Aug  2 11:52:47 mja-desktop kernel: [   11.382746] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 11:52:47 mja-desktop kernel: [   11.392533] [drm] radeon: Initializing kernel modesetting.
Aug  2 11:52:47 mja-desktop kernel: [   11.399788] [drm] register mmio base: 0xFE9E0000
Aug  2 11:52:47 mja-desktop kernel: [   11.399792] [drm] register mmio size: 65536
Aug  2 11:52:47 mja-desktop kernel: [   11.400076] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Aug  2 11:52:47 mja-desktop kernel: [   11.400109] [drm] Generation 2 PCI interface, using max accessible memory
Aug  2 11:52:47 mja-desktop kernel: [   11.400120] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Aug  2 11:52:47 mja-desktop kernel: [   11.400140] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Aug  2 11:52:47 mja-desktop kernel: [   11.400178] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
Aug  2 11:52:47 mja-desktop kernel: [   11.400197] [drm] radeon: VRAM 128M
Aug  2 11:52:47 mja-desktop kernel: [   11.400199] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
Aug  2 11:52:47 mja-desktop kernel: [   11.400201] [drm] radeon: GTT 128M
Aug  2 11:52:47 mja-desktop kernel: [   11.400203] [drm] radeon: GTT from 0xC0000000 to 0xC7FFFFFF
Aug  2 11:52:47 mja-desktop kernel: [   11.400226] [drm] radeon: irq initialized.
Aug  2 11:52:47 mja-desktop kernel: [   11.400339] [drm] Detected VRAM RAM=128M, BAR=256M
Aug  2 11:52:47 mja-desktop kernel: [   11.400344] [drm] RAM width 64bits DDR
Aug  2 11:52:47 mja-desktop kernel: [   11.405540] [TTM] Zone  kernel: Available graphics memory: 254288 kiB.
Aug  2 11:52:47 mja-desktop kernel: [   11.405564] [drm] radeon: 128M of VRAM memory ready
Aug  2 11:52:47 mja-desktop kernel: [   11.405567] [drm] radeon: 128M of GTT memory ready.
Aug  2 11:52:47 mja-desktop kernel: [   11.405802] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Aug  2 11:52:47 mja-desktop kernel: [   11.405817] [drm] radeon: cp idle (0x10000C03)
Aug  2 11:52:47 mja-desktop kernel: [   11.405942] [drm] Loading R300 Microcode
Aug  2 11:52:47 mja-desktop kernel: [   11.406304] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
Aug  2 11:52:47 mja-desktop kernel: [   11.435475] [drm] radeon: ring at 0x00000000C0000000
Aug  2 11:52:47 mja-desktop kernel: [   11.435498] [drm] ring test succeeded in 1 usecs
Aug  2 11:52:47 mja-desktop kernel: [   11.444619] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  2 11:52:47 mja-desktop kernel: [   11.448385] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug  2 11:52:47 mja-desktop kernel: [   11.448558] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug  2 11:52:47 mja-desktop kernel: [   11.462018] [drm] radeon: ib pool ready.
Aug  2 11:52:47 mja-desktop kernel: [   11.462112] [drm] ib test succeeded in 0 usecs
Aug  2 11:52:47 mja-desktop kernel: [   11.463403] [drm] Default TV standard: PAL
Aug  2 11:52:47 mja-desktop kernel: [   11.463408] [drm] 27.000000000 MHz TV ref clk
Aug  2 11:52:47 mja-desktop kernel: [   11.463412] [drm] DFP table revision: 3
Aug  2 11:52:47 mja-desktop kernel: [   11.464560] [drm] Default TV standard: PAL
Aug  2 11:52:47 mja-desktop kernel: [   11.464565] [drm] 27.000000000 MHz TV ref clk
Aug  2 11:52:47 mja-desktop kernel: [   11.464726] [drm] Radeon Display Connectors
Aug  2 11:52:47 mja-desktop kernel: [   11.464729] [drm] Connector 0:
Aug  2 11:52:47 mja-desktop kernel: [   11.464732] [drm]   VGA
Aug  2 11:52:47 mja-desktop kernel: [   11.464735] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Aug  2 11:52:47 mja-desktop kernel: [   11.464737] [drm]   Encoders:
Aug  2 11:52:47 mja-desktop kernel: [   11.464739] [drm]     CRT1: INTERNAL_DAC1
Aug  2 11:52:47 mja-desktop kernel: [   11.464741] [drm] Connector 1:
Aug  2 11:52:47 mja-desktop kernel: [   11.464743] [drm]   DVI-I
Aug  2 11:52:47 mja-desktop kernel: [   11.464744] [drm]   HPD1
Aug  2 11:52:47 mja-desktop kernel: [   11.464747] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Aug  2 11:52:47 mja-desktop kernel: [   11.464749] [drm]   Encoders:
Aug  2 11:52:47 mja-desktop kernel: [   11.464751] [drm]     CRT2: INTERNAL_DAC2
Aug  2 11:52:47 mja-desktop kernel: [   11.464753] [drm]     DFP1: INTERNAL_TMDS1
Aug  2 11:52:47 mja-desktop kernel: [   11.464754] [drm] Connector 2:
Aug  2 11:52:47 mja-desktop kernel: [   11.464756] [drm]   S-video
Aug  2 11:52:47 mja-desktop kernel: [   11.464758] [drm]   Encoders:
Aug  2 11:52:47 mja-desktop kernel: [   11.464759] [drm]     TV1: INTERNAL_DAC2
Aug  2 11:52:47 mja-desktop kernel: [   11.650834] type=1505 audit(1280742767.605:5):  operation="profile_load" pid=643 name="/usr/share/gdm/guest-session/Xsession"
Aug  2 11:52:47 mja-desktop kernel: [   11.659067] type=1505 audit(1280742767.613:6):  operation="profile_replace" pid=644 name="/sbin/dhclient3"
Aug  2 11:52:47 mja-desktop kernel: [   11.659648] type=1505 audit(1280742767.613:7):  operation="profile_replace" pid=644 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug  2 11:52:47 mja-desktop kernel: [   11.659956] type=1505 audit(1280742767.613:8):  operation="profile_replace" pid=644 name="/usr/lib/connman/scripts/dhclient-script"
Aug  2 11:52:47 mja-desktop kernel: [   11.718756] type=1505 audit(1280742767.673:9):  operation="profile_load" pid=650 name="/usr/bin/evince"
Aug  2 11:52:47 mja-desktop kernel: [   11.775378] type=1505 audit(1280742767.729:10):  operation="profile_load" pid=650 name="/usr/bin/evince-previewer"
Aug  2 11:52:47 mja-desktop kernel: [   11.835975] type=1505 audit(1280742767.789:11):  operation="profile_load" pid=650 name="/usr/bin/evince-thumbnailer"
Aug  2 11:52:47 mja-desktop kernel: [   11.845253] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  2 11:52:47 mja-desktop kernel: [   12.021100] [drm] fb mappable at 0xE0040000
Aug  2 11:52:47 mja-desktop kernel: [   12.021104] [drm] vram apper at 0xE0000000
Aug  2 11:52:47 mja-desktop kernel: [   12.021107] [drm] size 5242880
Aug  2 11:52:47 mja-desktop kernel: [   12.021109] [drm] fb depth is 24
Aug  2 11:52:47 mja-desktop kernel: [   12.021111] [drm]    pitch is 5120
Aug  2 11:52:47 mja-desktop kernel: [   12.029903] fb0: radeondrmfb frame buffer device
Aug  2 11:52:47 mja-desktop kernel: [   12.029908] registered panic notifier
Aug  2 11:52:47 mja-desktop kernel: [   12.029917] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
Aug  2 11:52:47 mja-desktop kernel: [   12.038383] vga16fb: mapped to 0xc00a0000
Aug  2 11:52:47 mja-desktop kernel: [   12.038389] vga16fb: not registering due to another framebuffer present
Aug  2 11:52:48 mja-desktop kernel: [   12.217322] Console: switching to colour frame buffer device 160x64
Aug  2 11:52:48 mja-desktop kernel: [   12.270141] intel8x0_measure_ac97_clock: measured 55149 usecs (2657 samples)
Aug  2 11:52:48 mja-desktop kernel: [   12.270146] intel8x0: clocking to 48000
Aug  2 11:52:48 mja-desktop kernel: [   12.408791] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug  2 11:52:48 mja-desktop kernel: [   12.408795] apm: overridden by ACPI.
Aug  2 11:52:56 mja-desktop pulseaudio[1096]: ratelimit.c: 2 events suppressed
Aug  2 11:53:15 mja-desktop pulseaudio[1283]: ratelimit.c: 2 events suppressed
Aug  2 11:53:20 mja-desktop pulseaudio[1283]: ratelimit.c: 3 events suppressed
Aug  2 15:06:45 mja-desktop kernel: [ 4809.896242] PM: Syncing filesystems ... done.
Aug  2 15:06:45 mja-desktop kernel: [ 4809.912027] Freezing user space processes ... (elapsed 0.00 seconds) done.
Aug  2 15:06:45 mja-desktop kernel: [ 4809.913762] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Aug  2 15:06:45 mja-desktop kernel: [ 4809.914361] Suspending console(s) (use no_console_suspend to debug)
Aug  2 15:06:45 mja-desktop kernel: [ 4809.932023] sd 3:0:0:0: [sdb] Synchronizing SCSI cache
Aug  2 15:06:45 mja-desktop kernel: [ 4809.932122] sd 3:0:0:0: [sdb] Stopping disk
Aug  2 15:06:45 mja-desktop kernel: [ 4809.932260] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Aug  2 15:06:45 mja-desktop kernel: [ 4809.953369] sd 2:0:0:0: [sda] Stopping disk
Aug  2 15:06:45 mja-desktop kernel: [ 4810.137812] PM: suspend of drv:sd dev:2:0:0:0 complete after 205.551 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4810.704011] PM: suspend of drv:atkbd dev:serio0 complete after 566.150 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4810.704835] parport_pc 00:09: disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4810.705264] serial 00:08: disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4810.754007] e1000 0000:02:0c.0: PCI INT A disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4810.754015] e1000 0000:02:0c.0: PME# enabled
Aug  2 15:06:45 mja-desktop kernel: [ 4810.754028] pci 0000:00:1e.0: wake-up capability enabled by ACPI
Aug  2 15:06:45 mja-desktop kernel: [ 4812.834818] radeon 0000:01:00.0: PCI INT A disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848020] PM: suspend of drv:radeon dev:0000:01:00.0 complete after 2080.000 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848210] Intel ICH 0000:00:1f.5: PCI INT B disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848336] ata_piix 0000:00:1f.2: PCI INT A disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848448] ata_piix 0000:00:1f.1: PCI INT A disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848461] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848468] uhci_hcd 0000:00:1d.3: PCI INT A disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848476] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848483] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848490] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848648] PM: suspend of devices complete after 2934.108 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4812.848652] PM: suspend devices took 2.936 seconds
Aug  2 15:06:45 mja-desktop kernel: [ 4812.864173] PM: late suspend of devices complete after 15.516 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4812.864275] ACPI: Preparing to enter system sleep state S3
Aug  2 15:06:45 mja-desktop kernel: [ 4812.865040] Disabling non-boot CPUs ...
Aug  2 15:06:45 mja-desktop kernel: [ 4812.865062] CPU0: Thermal monitoring enabled (TM1)
Aug  2 15:06:45 mja-desktop kernel: [ 4812.865062] ACPI: Waking up from system sleep state S3
Aug  2 15:06:45 mja-desktop kernel: [ 4812.871691] PM: early resume of devices complete after 0.769 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4812.871912] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 15:06:45 mja-desktop kernel: [ 4812.871938] usb usb2: root hub lost power or was reset
Aug  2 15:06:45 mja-desktop kernel: [ 4812.871955] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug  2 15:06:45 mja-desktop kernel: [ 4812.871980] usb usb3: root hub lost power or was reset
Aug  2 15:06:45 mja-desktop kernel: [ 4812.872019] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  2 15:06:45 mja-desktop kernel: [ 4812.872044] usb usb4: root hub lost power or was reset
Aug  2 15:06:45 mja-desktop kernel: [ 4812.872060] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 15:06:45 mja-desktop kernel: [ 4812.872084] usb usb5: root hub lost power or was reset
Aug  2 15:06:45 mja-desktop kernel: [ 4812.872099] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Aug  2 15:06:45 mja-desktop kernel: [ 4812.872127] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 15:06:45 mja-desktop kernel: [ 4812.872303] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 15:06:45 mja-desktop kernel: [ 4812.872347] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  2 15:06:45 mja-desktop kernel: [ 4812.881891] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 15:06:45 mja-desktop kernel: [ 4812.881899] [drm] AGP mode requested: 8
Aug  2 15:06:45 mja-desktop kernel: [ 4812.881902] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Aug  2 15:06:45 mja-desktop kernel: [ 4812.881919] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Aug  2 15:06:45 mja-desktop kernel: [ 4812.881958] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
Aug  2 15:06:45 mja-desktop kernel: [ 4812.882182] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Aug  2 15:06:45 mja-desktop kernel: [ 4812.986563] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Aug  2 15:06:45 mja-desktop kernel: [ 4812.986568] [drm] radeon: cp idle (0x10000C03)
Aug  2 15:06:45 mja-desktop kernel: [ 4812.986607] [drm] radeon: ring at 0x00000000C0000000
Aug  2 15:06:45 mja-desktop kernel: [ 4812.986633] [drm] ring test succeeded in 1 usecs
Aug  2 15:06:45 mja-desktop kernel: [ 4812.986650] [drm] ib test succeeded in 0 usecs
Aug  2 15:06:45 mja-desktop kernel: [ 4813.042990] PM: resume of drv:radeon dev:0000:01:00.0 complete after 161.103 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4813.043005] e1000 0000:02:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 15:06:45 mja-desktop kernel: [ 4813.043023] pci 0000:00:1e.0: wake-up capability disabled by ACPI
Aug  2 15:06:45 mja-desktop kernel: [ 4813.043028] e1000 0000:02:0c.0: PME# disabled
Aug  2 15:06:45 mja-desktop kernel: [ 4813.077130] serial 00:08: activated
Aug  2 15:06:45 mja-desktop kernel: [ 4813.082341] parport_pc 00:09: activated
Aug  2 15:06:45 mja-desktop kernel: [ 4813.104198] ata2.00: configured for UDMA/33
Aug  2 15:06:45 mja-desktop kernel: [ 4813.120277] ata2.01: configured for UDMA/33
Aug  2 15:06:45 mja-desktop kernel: [ 4813.380011] PM: resume of drv:usb dev:usb3 complete after 247.969 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4813.380293] sd 2:0:0:0: [sda] Starting disk
Aug  2 15:06:45 mja-desktop kernel: [ 4814.728367] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug  2 15:06:45 mja-desktop kernel: [ 4817.156252] ata3.00: configured for UDMA/100
Aug  2 15:06:45 mja-desktop kernel: [ 4817.180272] PM: resume of drv:sd dev:2:0:0:0 complete after 3799.979 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4817.180280] sd 3:0:0:0: [sdb] Starting disk
Aug  2 15:06:45 mja-desktop kernel: [ 4817.252253] ata4.00: configured for UDMA/100
Aug  2 15:06:45 mja-desktop kernel: [ 4817.524013] usb 3-2: reset low speed USB device using uhci_hcd and address 2
Aug  2 15:06:45 mja-desktop kernel: [ 4817.831670] PM: resume of drv:usb dev:3-2 complete after 565.753 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828005] 
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828007] floppy driver state
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828008] -------------------
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828011] now=1130207 last interrupt=4294896181 diff=1201322 last called handler=e07ea2a0
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828014] timeout_message=lock fdc
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828015] last output bytes:
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828018]  8 80 4294892639
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828019]  8 80 4294892639
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828021]  8 80 4294892639
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828023]  8 80 4294892639
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828025] 12 80 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828027]  0 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828029] 13 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828031]  0 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828033] 1a 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828034]  0 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828036]  3 80 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828038] c1 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828040] 10 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828042]  7 80 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828044]  0 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828046]  8 81 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828047]  f 80 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828049]  0 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828051]  1 90 4294896180
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828053]  8 81 4294896181
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828055] last result at 4294896181
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828056] last redo_fd_request at 4294896186
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828058] 20  1 
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828067] status=0
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828069] fdc_busy=1
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828070] do_floppy=e07e55b0
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828072] cont=e07ec290
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828074] current_req=(null)
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828076] command_status=-1
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828077] 
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828080] floppy0: floppy timeout called
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828091] PM: resume of drv:floppy dev:floppy.0 complete after 2996.413 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828140] PM: resume of devices complete after 7956.412 msecs
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828295] PM: resume devices took 7.960 seconds
Aug  2 15:06:45 mja-desktop kernel: [ 4820.828337] Restarting tasks ... done.
Aug  2 16:11:52 mja-desktop kernel: Kernel logging (proc) stopped.
Aug  2 16:11:52 mja-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="547" x-info="http://www.rsyslog.com"] exiting on signal 15.
Aug  2 16:12:27 mja-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug  2 16:12:27 mja-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="583" x-info="http://www.rsyslog.com"] (re)start
Aug  2 16:12:27 mja-desktop rsyslogd: rsyslogd's groupid changed to 103
Aug  2 16:12:27 mja-desktop rsyslogd: rsyslogd's userid changed to 102
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] KERNEL supported cpus:
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   Intel GenuineIntel
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   AMD AuthenticAMD
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   NSC Geode by NSC
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   Centaur CentaurHauls
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff72000 (ACPI NVS)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff72000 - 000000001ff93000 (ACPI data)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff93000 - 0000000020000000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] DMI 2.3 present.
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] modified physical RAM map:
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000001ff70000 (usable)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 000000001ff70000 - 000000001ff72000 (ACPI NVS)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 000000001ff72000 - 000000001ff93000 (ACPI data)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 000000001ff93000 - 0000000020000000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] RAMDISK: 1f7d7000 - 1ff5ff90
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: RSDP 000feba0 00014 (v00 DELL  )
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: RSDT 000fd192 00038 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: FACP 000fd1ca 00074 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: DSDT fffd2759 02795 (v01   DELL    dt_ex 00001000 MSFT 0100000D)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: FACS 1ff70000 00040
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: SSDT fffd4eee 000A7 (v01   DELL    st_ex 00001000 MSFT 0100000D)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: APIC 000fd23e 0006C (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: BOOT 000fd2aa 00028 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: ASF! 000fd2d2 00067 (v16 DELL    GX270   00000007 ASL  00000061)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] 511MB LOWMEM available.
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   mapped low ram: 0 - 1ff70000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   low ram: 0 - 1ff70000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 1ff70000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bff0
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ff70000]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #4 [001f7d7000 - 001ff5ff90]          RAMDISK ==> [001f7d7000 - 001ff5ff90]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #6 [00008dc000 - 00008df18c]              BRK ==> [00008dc000 - 00008df18c]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] found SMP MP-table at [c00fe710] fe710
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Zone PFN ranges:
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x0001ff70
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]   HighMem  0x0001ff70 -> 0x0001ff70
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x000000a0
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0001ff70
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Using APIC driver default
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u1048576
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129805
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Kernel command line: root=UUID=baf3a80c-4e26-4d98-83d6-305197df60c3 ro quiet splash 
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Initializing CPU#0
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] allocated 2618560 bytes of page_cgroup
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Memory: 499660k/523712k available (4679k kernel code, 23108k reserved, 2116k data, 660k init, 0k highmem)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] virtual kernel memory layout:
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] console [tty0] enabled
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Aug  2 16:12:27 mja-desktop kernel: [    0.000000] Detected 2793.479 MHz processor.
Aug  2 16:12:27 mja-desktop kernel: [    0.008006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5586.95 BogoMIPS (lpj=11173916)
Aug  2 16:12:27 mja-desktop kernel: [    0.008028] Security Framework initialized
Aug  2 16:12:27 mja-desktop kernel: [    0.008054] AppArmor: AppArmor initialized
Aug  2 16:12:27 mja-desktop kernel: [    0.008063] Mount-cache hash table entries: 512
Aug  2 16:12:27 mja-desktop kernel: [    0.008229] Initializing cgroup subsys ns
Aug  2 16:12:27 mja-desktop kernel: [    0.008235] Initializing cgroup subsys cpuacct
Aug  2 16:12:27 mja-desktop kernel: [    0.008240] Initializing cgroup subsys memory
Aug  2 16:12:27 mja-desktop kernel: [    0.008250] Initializing cgroup subsys devices
Aug  2 16:12:27 mja-desktop kernel: [    0.008253] Initializing cgroup subsys freezer
Aug  2 16:12:27 mja-desktop kernel: [    0.008256] Initializing cgroup subsys net_cls
Aug  2 16:12:27 mja-desktop kernel: [    0.008284] CPU: Trace cache: 12K uops, L1 D cache: 8K
Aug  2 16:12:27 mja-desktop kernel: [    0.008288] CPU: L2 cache: 512K
Aug  2 16:12:27 mja-desktop kernel: [    0.008291] CPU: Hyper-Threading is disabled
Aug  2 16:12:27 mja-desktop kernel: [    0.008296] mce: CPU supports 4 MCE banks
Aug  2 16:12:27 mja-desktop kernel: [    0.008308] CPU0: Thermal monitoring enabled (TM1)
Aug  2 16:12:27 mja-desktop kernel: [    0.008319] Performance Events: no PMU driver, software events only.
Aug  2 16:12:27 mja-desktop kernel: [    0.008327] Checking 'hlt' instruction... OK.
Aug  2 16:12:27 mja-desktop kernel: [    0.024925] SMP alternatives: switching to UP code
Aug  2 16:12:27 mja-desktop kernel: [    0.035919] ACPI: Core revision 20090903
Aug  2 16:12:27 mja-desktop kernel: [    0.073613] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug  2 16:12:27 mja-desktop kernel: [    0.073621] ftrace: allocating 21780 entries in 43 pages
Aug  2 16:12:27 mja-desktop kernel: [    0.076089] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug  2 16:12:27 mja-desktop kernel: [    0.076387] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  2 16:12:27 mja-desktop kernel: [    0.117829] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] Brought up 1 CPUs
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] Total of 1 processors activated (5586.95 BogoMIPS).
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] devtmpfs: initialized
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] regulator: core version 0.5
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] Time: 14:12:16  Date: 08/02/10
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] NET: Registered protocol family 16
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] EISA bus registered
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] ACPI: bus type pci registered
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] PCI: PCI BIOS revision 2.10 entry at 0xfbab0, last bus=2
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] PCI: Using configuration type 1 for base access
Aug  2 16:12:27 mja-desktop kernel: [    0.120001] bio: create slab <bio-0> at 0
Aug  2 16:12:27 mja-desktop kernel: [    0.148103] ACPI: Interpreter enabled
Aug  2 16:12:27 mja-desktop kernel: [    0.148123] ACPI: (supports S0 S1 S3 S4 S5)
Aug  2 16:12:27 mja-desktop kernel: [    0.148150] ACPI: Using IOAPIC for interrupt routing
Aug  2 16:12:27 mja-desktop kernel: [    0.175980] ACPI: No dock devices found.
Aug  2 16:12:27 mja-desktop kernel: [    0.180107] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  2 16:12:27 mja-desktop kernel: [    0.180155] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
Aug  2 16:12:27 mja-desktop kernel: [    0.180659] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug  2 16:12:27 mja-desktop kernel: [    0.180664] pci 0000:00:1d.7: PME# disabled
Aug  2 16:12:27 mja-desktop kernel: [    0.180761] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Aug  2 16:12:27 mja-desktop kernel: [    0.180765] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
Aug  2 16:12:27 mja-desktop kernel: [    0.181043] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Aug  2 16:12:27 mja-desktop kernel: [    0.181048] pci 0000:00:1f.5: PME# disabled
Aug  2 16:12:27 mja-desktop kernel: [    0.181385] pci 0000:02:0c.0: PME# supported from D0 D3hot D3cold
Aug  2 16:12:27 mja-desktop kernel: [    0.181389] pci 0000:02:0c.0: PME# disabled
Aug  2 16:12:27 mja-desktop kernel: [    0.181423] pci 0000:00:1e.0: transparent bridge
Aug  2 16:12:27 mja-desktop kernel: [    0.300364] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Aug  2 16:12:27 mja-desktop kernel: [    0.300678] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
Aug  2 16:12:27 mja-desktop kernel: [    0.300990] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Aug  2 16:12:27 mja-desktop kernel: [    0.301301] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Aug  2 16:12:27 mja-desktop kernel: [    0.301610] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 16:12:27 mja-desktop kernel: [    0.301921] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 16:12:27 mja-desktop kernel: [    0.302230] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 16:12:27 mja-desktop kernel: [    0.302543] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Aug  2 16:12:27 mja-desktop kernel: [    0.302724] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug  2 16:12:27 mja-desktop kernel: [    0.302728] vgaarb: loaded
Aug  2 16:12:27 mja-desktop kernel: [    0.302886] SCSI subsystem initialized
Aug  2 16:12:27 mja-desktop kernel: [    0.303057] usbcore: registered new interface driver usbfs
Aug  2 16:12:27 mja-desktop kernel: [    0.303073] usbcore: registered new interface driver hub
Aug  2 16:12:27 mja-desktop kernel: [    0.303102] usbcore: registered new device driver usb
Aug  2 16:12:27 mja-desktop kernel: [    0.303257] ACPI: WMI: Mapper loaded
Aug  2 16:12:27 mja-desktop kernel: [    0.303260] PCI: Using ACPI for IRQ routing
Aug  2 16:12:27 mja-desktop kernel: [    0.303431] NetLabel: Initializing
Aug  2 16:12:27 mja-desktop kernel: [    0.303434] NetLabel:  domain hash size = 128
Aug  2 16:12:27 mja-desktop kernel: [    0.303435] NetLabel:  protocols = UNLABELED CIPSOv4
Aug  2 16:12:27 mja-desktop kernel: [    0.303451] NetLabel:  unlabeled traffic allowed by default
Aug  2 16:12:27 mja-desktop kernel: [    0.303587] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug  2 16:12:27 mja-desktop kernel: [    0.303593] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug  2 16:12:27 mja-desktop kernel: [    0.303599] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Aug  2 16:12:27 mja-desktop kernel: [    0.308026] Switching to clocksource tsc
Aug  2 16:12:27 mja-desktop kernel: [    0.310250] AppArmor: AppArmor Filesystem Enabled
Aug  2 16:12:27 mja-desktop kernel: [    0.310273] pnp: PnP ACPI init
Aug  2 16:12:27 mja-desktop kernel: [    0.310296] ACPI: bus type pnp registered
Aug  2 16:12:27 mja-desktop kernel: [    0.337929] pnp 00:0a: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Aug  2 16:12:27 mja-desktop kernel: [    0.337934] pnp 00:0a: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Aug  2 16:12:27 mja-desktop kernel: [    0.338628] pnp: PnP ACPI: found 11 devices
Aug  2 16:12:27 mja-desktop kernel: [    0.338631] ACPI: ACPI bus type pnp unregistered
Aug  2 16:12:27 mja-desktop kernel: [    0.338638] PnPBIOS: Disabled by ACPI PNP
Aug  2 16:12:27 mja-desktop kernel: [    0.338651] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338657] system 00:00: iomem range 0x100000-0xffffff could not be reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338661] system 00:00: iomem range 0x1000000-0x1ff6ffff could not be reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338664] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338668] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338672] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338675] system 00:00: iomem range 0xfed20000-0xfed8ffff has been reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338679] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338682] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338686] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.338698] system 00:0a: ioport range 0xc00-0xc7f has been reserved
Aug  2 16:12:27 mja-desktop kernel: [    0.373450] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Aug  2 16:12:27 mja-desktop kernel: [    0.373454] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
Aug  2 16:12:27 mja-desktop kernel: [    0.373461] pci 0000:00:01.0:   MEM window: 0xfe900000-0xfeafffff
Aug  2 16:12:27 mja-desktop kernel: [    0.373466] pci 0000:00:01.0:   PREFETCH window: 0xc8000000-0xefffffff
Aug  2 16:12:27 mja-desktop kernel: [    0.373473] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Aug  2 16:12:27 mja-desktop kernel: [    0.373477] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Aug  2 16:12:27 mja-desktop kernel: [    0.373482] pci 0000:00:1e.0:   MEM window: 0xfe800000-0xfe8fffff
Aug  2 16:12:27 mja-desktop kernel: [    0.373487] pci 0000:00:1e.0:   PREFETCH window: disabled
Aug  2 16:12:27 mja-desktop kernel: [    0.373582] NET: Registered protocol family 2
Aug  2 16:12:27 mja-desktop kernel: [    0.373697] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Aug  2 16:12:27 mja-desktop kernel: [    0.374030] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Aug  2 16:12:27 mja-desktop kernel: [    0.374101] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Aug  2 16:12:27 mja-desktop kernel: [    0.374170] TCP: Hash tables configured (established 16384 bind 16384)
Aug  2 16:12:27 mja-desktop kernel: [    0.374173] TCP reno registered
Aug  2 16:12:27 mja-desktop kernel: [    0.374273] NET: Registered protocol family 1
Aug  2 16:12:27 mja-desktop kernel: [    0.374484] Simple Boot Flag at 0x7a set to 0x1
Aug  2 16:12:27 mja-desktop kernel: [    0.374586] cpufreq-nforce2: No nForce2 chipset.
Aug  2 16:12:27 mja-desktop kernel: [    0.374622] Scanning for low memory corruption every 60 seconds
Aug  2 16:12:27 mja-desktop kernel: [    0.374756] audit: initializing netlink socket (disabled)
Aug  2 16:12:27 mja-desktop kernel: [    0.374769] type=2000 audit(1280758335.371:1): initialized
Aug  2 16:12:27 mja-desktop kernel: [    0.383250] Trying to unpack rootfs image as initramfs...
Aug  2 16:12:27 mja-desktop kernel: [    0.392292] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug  2 16:12:27 mja-desktop kernel: [    0.397783] VFS: Disk quotas dquot_6.5.2
Aug  2 16:12:27 mja-desktop kernel: [    0.397857] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  2 16:12:27 mja-desktop kernel: [    0.398584] fuse init (API version 7.13)
Aug  2 16:12:27 mja-desktop kernel: [    0.398689] msgmni has been set to 976
Aug  2 16:12:27 mja-desktop kernel: [    0.404348] alg: No test for stdrng (krng)
Aug  2 16:12:27 mja-desktop kernel: [    0.404465] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug  2 16:12:27 mja-desktop kernel: [    0.404469] io scheduler noop registered
Aug  2 16:12:27 mja-desktop kernel: [    0.404471] io scheduler anticipatory registered
Aug  2 16:12:27 mja-desktop kernel: [    0.404473] io scheduler deadline registered
Aug  2 16:12:27 mja-desktop kernel: [    0.404530] io scheduler cfq registered (default)
Aug  2 16:12:27 mja-desktop kernel: [    0.404668] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  2 16:12:27 mja-desktop kernel: [    0.404696] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug  2 16:12:27 mja-desktop kernel: [    0.404800] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Aug  2 16:12:27 mja-desktop kernel: [    0.404810] ACPI: Power Button [VBTN]
Aug  2 16:12:27 mja-desktop kernel: [    0.404873] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Aug  2 16:12:27 mja-desktop kernel: [    0.404876] ACPI: Power Button [PWRF]
Aug  2 16:12:27 mja-desktop kernel: [    0.405107] processor LNXCPU:00: registered as cooling_device0
Aug  2 16:12:27 mja-desktop kernel: [    0.442596] isapnp: Scanning for PnP cards...
Aug  2 16:12:27 mja-desktop kernel: [    0.448342] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug  2 16:12:27 mja-desktop kernel: [    0.448444] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  2 16:12:27 mja-desktop kernel: [    0.448857] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  2 16:12:27 mja-desktop kernel: [    0.450089] brd: module loaded
Aug  2 16:12:27 mja-desktop kernel: [    0.450649] loop: module loaded
Aug  2 16:12:27 mja-desktop kernel: [    0.450763] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Aug  2 16:12:27 mja-desktop kernel: [    0.450918] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 16:12:27 mja-desktop kernel: [    0.456040] scsi0 : ata_piix
Aug  2 16:12:27 mja-desktop kernel: [    0.456209] scsi1 : ata_piix
Aug  2 16:12:27 mja-desktop kernel: [    0.456253] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Aug  2 16:12:27 mja-desktop kernel: [    0.456257] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Aug  2 16:12:27 mja-desktop kernel: [    0.456306] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 16:12:27 mja-desktop kernel: [    0.456313] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Aug  2 16:12:27 mja-desktop kernel: [    0.456447] scsi2 : ata_piix
Aug  2 16:12:27 mja-desktop kernel: [    0.503738] scsi3 : ata_piix
Aug  2 16:12:27 mja-desktop kernel: [    0.503814] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 18
Aug  2 16:12:27 mja-desktop kernel: [    0.503818] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 18
Aug  2 16:12:27 mja-desktop kernel: [    0.504261] Fixed MDIO Bus: probed
Aug  2 16:12:27 mja-desktop kernel: [    0.504307] PPP generic driver version 2.4.2
Aug  2 16:12:27 mja-desktop kernel: [    0.504393] tun: Universal TUN/TAP device driver, 1.6
Aug  2 16:12:27 mja-desktop kernel: [    0.504395] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug  2 16:12:27 mja-desktop kernel: [    0.504505] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug  2 16:12:27 mja-desktop kernel: [    0.504546] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Aug  2 16:12:27 mja-desktop kernel: [    0.504570] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug  2 16:12:27 mja-desktop kernel: [    0.504614] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Aug  2 16:12:27 mja-desktop kernel: [    0.504648] ehci_hcd 0000:00:1d.7: debug port 1
Aug  2 16:12:27 mja-desktop kernel: [    0.508900] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
Aug  2 16:12:27 mja-desktop kernel: [    0.531950] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug  2 16:12:27 mja-desktop kernel: [    0.532115] usb usb1: configuration #1 chosen from 1 choice
Aug  2 16:12:27 mja-desktop kernel: [    0.532154] hub 1-0:1.0: USB hub found
Aug  2 16:12:27 mja-desktop kernel: [    0.532168] hub 1-0:1.0: 8 ports detected
Aug  2 16:12:27 mja-desktop kernel: [    0.532255] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug  2 16:12:27 mja-desktop kernel: [    0.532276] uhci_hcd: USB Universal Host Controller Interface driver
Aug  2 16:12:27 mja-desktop kernel: [    0.532348] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 16:12:27 mja-desktop kernel: [    0.532364] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  2 16:12:27 mja-desktop kernel: [    0.532415] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug  2 16:12:27 mja-desktop kernel: [    0.532452] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
Aug  2 16:12:27 mja-desktop kernel: [    0.532563] usb usb2: configuration #1 chosen from 1 choice
Aug  2 16:12:27 mja-desktop kernel: [    0.532595] hub 2-0:1.0: USB hub found
Aug  2 16:12:27 mja-desktop kernel: [    0.532605] hub 2-0:1.0: 2 ports detected
Aug  2 16:12:27 mja-desktop kernel: [    0.532669] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug  2 16:12:27 mja-desktop kernel: [    0.532680] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  2 16:12:27 mja-desktop kernel: [    0.532718] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Aug  2 16:12:27 mja-desktop kernel: [    0.532749] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
Aug  2 16:12:27 mja-desktop kernel: [    0.532851] usb usb3: configuration #1 chosen from 1 choice
Aug  2 16:12:27 mja-desktop kernel: [    0.532886] hub 3-0:1.0: USB hub found
Aug  2 16:12:27 mja-desktop kernel: [    0.532896] hub 3-0:1.0: 2 ports detected
Aug  2 16:12:27 mja-desktop kernel: [    0.532946] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  2 16:12:27 mja-desktop kernel: [    0.532957] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  2 16:12:27 mja-desktop kernel: [    0.532995] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Aug  2 16:12:27 mja-desktop kernel: [    0.533017] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Aug  2 16:12:27 mja-desktop kernel: [    0.533119] usb usb4: configuration #1 chosen from 1 choice
Aug  2 16:12:27 mja-desktop kernel: [    0.533154] hub 4-0:1.0: USB hub found
Aug  2 16:12:27 mja-desktop kernel: [    0.533164] hub 4-0:1.0: 2 ports detected
Aug  2 16:12:27 mja-desktop kernel: [    0.533214] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 16:12:27 mja-desktop kernel: [    0.533225] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug  2 16:12:27 mja-desktop kernel: [    0.533269] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Aug  2 16:12:27 mja-desktop kernel: [    0.533292] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
Aug  2 16:12:27 mja-desktop kernel: [    0.533393] usb usb5: configuration #1 chosen from 1 choice
Aug  2 16:12:27 mja-desktop kernel: [    0.533425] hub 5-0:1.0: USB hub found
Aug  2 16:12:27 mja-desktop kernel: [    0.533434] hub 5-0:1.0: 2 ports detected
Aug  2 16:12:27 mja-desktop kernel: [    0.533540] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
Aug  2 16:12:27 mja-desktop kernel: [    0.533543] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug  2 16:12:27 mja-desktop kernel: [    0.534220] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  2 16:12:27 mja-desktop kernel: [    0.534366] mice: PS/2 mouse device common for all mice
Aug  2 16:12:27 mja-desktop kernel: [    0.534509] rtc_cmos 00:05: RTC can wake from S4
Aug  2 16:12:27 mja-desktop kernel: [    0.534560] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Aug  2 16:12:27 mja-desktop kernel: [    0.534589] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
Aug  2 16:12:27 mja-desktop kernel: [    0.534728] device-mapper: uevent: version 1.0.3
Aug  2 16:12:27 mja-desktop kernel: [    0.539832] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Aug  2 16:12:27 mja-desktop kernel: [    0.539946] device-mapper: multipath: version 1.1.0 loaded
Aug  2 16:12:27 mja-desktop kernel: [    0.539950] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug  2 16:12:27 mja-desktop kernel: [    0.540106] EISA: Probing bus 0 at eisa.0
Aug  2 16:12:27 mja-desktop kernel: [    0.540145] EISA: Detected 0 cards.
Aug  2 16:12:27 mja-desktop kernel: [    0.544325] cpuidle: using governor ladder
Aug  2 16:12:27 mja-desktop kernel: [    0.544329] cpuidle: using governor menu
Aug  2 16:12:27 mja-desktop kernel: [    0.544982] TCP cubic registered
Aug  2 16:12:27 mja-desktop kernel: [    0.545137] NET: Registered protocol family 10
Aug  2 16:12:27 mja-desktop kernel: [    0.545670] lo: Disabled Privacy Extensions
Aug  2 16:12:27 mja-desktop kernel: [    0.546058] NET: Registered protocol family 17
Aug  2 16:12:27 mja-desktop kernel: [    0.546128] Using IPI No-Shortcut mode
Aug  2 16:12:27 mja-desktop kernel: [    0.546272] registered taskstats version 1
Aug  2 16:12:27 mja-desktop kernel: [    0.546544]   Magic number: 6:812:231
Aug  2 16:12:27 mja-desktop kernel: [    0.546628] rtc_cmos 00:05: setting system clock to 2010-08-02 14:12:16 UTC (1280758336)
Aug  2 16:12:27 mja-desktop kernel: [    0.546632] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  2 16:12:27 mja-desktop kernel: [    0.546634] EDD information not available.
Aug  2 16:12:27 mja-desktop kernel: [    0.614291] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Aug  2 16:12:27 mja-desktop kernel: [    0.701027] ata3.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
Aug  2 16:12:27 mja-desktop kernel: [    0.701033] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug  2 16:12:27 mja-desktop kernel: [    0.701139] ata4.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
Aug  2 16:12:27 mja-desktop kernel: [    0.701143] ata4.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug  2 16:12:27 mja-desktop kernel: [    0.701579] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-252S, R901, max UDMA/33
Aug  2 16:12:27 mja-desktop kernel: [    0.701623] ata2.01: ATAPI: HL-DT-STDVDRRW GCA-4164B, H.I0, max UDMA/33
Aug  2 16:12:27 mja-desktop kernel: [    0.708552] ata4.00: configured for UDMA/100
Aug  2 16:12:27 mja-desktop kernel: [    0.708613] ata3.00: configured for UDMA/100
Aug  2 16:12:27 mja-desktop kernel: [    0.716227] ata2.00: configured for UDMA/33
Aug  2 16:12:27 mja-desktop kernel: [    0.732296] ata2.01: configured for UDMA/33
Aug  2 16:12:27 mja-desktop kernel: [    0.892049] Freeing initrd memory: 7715k freed
Aug  2 16:12:27 mja-desktop kernel: [    1.030272] isapnp: No Plug & Play device found
Aug  2 16:12:27 mja-desktop kernel: [    1.031278] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-252S  R901 PQ: 0 ANSI: 5
Aug  2 16:12:27 mja-desktop kernel: [    1.035251] sr0: scsi3-mmc drive: 48x/16x writer cd/rw xa/form2 cdda tray
Aug  2 16:12:27 mja-desktop kernel: [    1.035255] Uniform CD-ROM driver Revision: 3.20
Aug  2 16:12:27 mja-desktop kernel: [    1.035485] sr 1:0:0:0: Attached scsi generic sg0 type 5
Aug  2 16:12:27 mja-desktop kernel: [    1.036986] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRRW GCA-4164B H.I0 PQ: 0 ANSI: 5
Aug  2 16:12:27 mja-desktop kernel: [    1.042041] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Aug  2 16:12:27 mja-desktop kernel: [    1.042212] sr 1:0:1:0: Attached scsi generic sg1 type 5
Aug  2 16:12:27 mja-desktop kernel: [    1.042347] scsi 2:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
Aug  2 16:12:27 mja-desktop kernel: [    1.042495] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug  2 16:12:27 mja-desktop kernel: [    1.042627] scsi 3:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
Aug  2 16:12:27 mja-desktop kernel: [    1.042762] sd 3:0:0:0: Attached scsi generic sg3 type 0
Aug  2 16:12:27 mja-desktop kernel: [    1.042846] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug  2 16:12:27 mja-desktop kernel: [    1.042893] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug  2 16:12:27 mja-desktop kernel: [    1.042962] sd 3:0:0:0: [sdb] Write Protect is off
Aug  2 16:12:27 mja-desktop kernel: [    1.043007] sd 2:0:0:0: [sda] Write Protect is off
Aug  2 16:12:27 mja-desktop kernel: [    1.043027] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 16:12:27 mja-desktop kernel: [    1.043109] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 16:12:27 mja-desktop kernel: [    1.043345]  sdb:
Aug  2 16:12:27 mja-desktop kernel: [    1.043441]  sda: sdb1 sdb2 < sda1
Aug  2 16:12:27 mja-desktop kernel: [    1.063790] sd 2:0:0:0: [sda] Attached SCSI disk
Aug  2 16:12:27 mja-desktop kernel: [    1.087543]  sdb5 >
Aug  2 16:12:27 mja-desktop kernel: [    1.087856] sd 3:0:0:0: [sdb] Attached SCSI disk
Aug  2 16:12:27 mja-desktop kernel: [    1.087882] Freeing unused kernel memory: 660k freed
Aug  2 16:12:27 mja-desktop kernel: [    1.088507] Write protecting the kernel text: 4680k
Aug  2 16:12:27 mja-desktop kernel: [    1.088539] Write protecting the kernel read-only data: 1840k
Aug  2 16:12:27 mja-desktop kernel: [    1.095919] usb 3-2: new low speed USB device using uhci_hcd and address 2
Aug  2 16:12:27 mja-desktop kernel: [    1.113494] udev: starting version 151
Aug  2 16:12:27 mja-desktop kernel: [    1.272734] usb 3-2: configuration #1 chosen from 1 choice
Aug  2 16:12:27 mja-desktop kernel: [    1.357221] Floppy drive(s): fd0 is 1.44M
Aug  2 16:12:27 mja-desktop kernel: [    1.366324] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
Aug  2 16:12:27 mja-desktop kernel: [    1.366330] Copyright (c) 1999-2006 Intel Corporation.
Aug  2 16:12:27 mja-desktop kernel: [    1.366441] e1000 0000:02:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 16:12:27 mja-desktop kernel: [    1.374379] FDC 0 is a post-1991 82077
Aug  2 16:12:27 mja-desktop kernel: [    1.386078] usbcore: registered new interface driver hiddev
Aug  2 16:12:27 mja-desktop kernel: [    1.642810] e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0f:1f:74:e1:be
Aug  2 16:12:27 mja-desktop kernel: [    1.643499] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
Aug  2 16:12:27 mja-desktop kernel: [    1.643768] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
Aug  2 16:12:27 mja-desktop kernel: [    1.643803] usbcore: registered new interface driver usbhid
Aug  2 16:12:27 mja-desktop kernel: [    1.643940] usbhid: v2.6:USB HID core driver
Aug  2 16:12:27 mja-desktop kernel: [    1.681612] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Aug  2 16:12:27 mja-desktop kernel: [    1.772503] kjournald starting.  Commit interval 5 seconds
Aug  2 16:12:27 mja-desktop kernel: [    1.772518] EXT3-fs: mounted filesystem with ordered data mode.
Aug  2 16:12:27 mja-desktop kernel: [   10.147653] Adding 1510068k swap on /dev/sdb5.  Priority:-1 extents:1 across:1510068k 
Aug  2 16:12:27 mja-desktop kernel: [   10.198839] udev: starting version 151
Aug  2 16:12:27 mja-desktop kernel: [   10.277954] EXT3 FS on sda1, internal journal
Aug  2 16:12:27 mja-desktop kernel: [   10.395634] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  2 16:12:27 mja-desktop kernel: [   10.398470] lp: driver loaded but no devices found
Aug  2 16:12:27 mja-desktop kernel: [   10.536905] Linux agpgart interface v0.103
Aug  2 16:12:27 mja-desktop kernel: [   10.547086] agpgart-intel 0000:00:00.0: Intel 865 Chipset
Aug  2 16:12:27 mja-desktop kernel: [   10.596607] intel_rng: FWH not detected
Aug  2 16:12:27 mja-desktop kernel: [   10.766518] parport_pc 00:09: reported by Plug and Play ACPI
Aug  2 16:12:27 mja-desktop kernel: [   10.766571] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Aug  2 16:12:27 mja-desktop kernel: [   10.815979] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xc0000000
Aug  2 16:12:27 mja-desktop kernel: [   10.860262] lp0: using parport0 (interrupt-driven).
Aug  2 16:12:27 mja-desktop kernel: [   10.916498] [drm] Initialized drm 1.1.0 20060810
Aug  2 16:12:27 mja-desktop kernel: [   10.933582] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Aug  2 16:12:27 mja-desktop kernel: [   10.942156] ppdev: user-space parallel port driver
Aug  2 16:12:27 mja-desktop kernel: [   10.949547] dell-wmi: No known WMI GUID found
Aug  2 16:12:27 mja-desktop kernel: [   11.069870] [drm] radeon defaulting to kernel modesetting.
Aug  2 16:12:27 mja-desktop kernel: [   11.069875] [drm] radeon kernel modesetting enabled.
Aug  2 16:12:27 mja-desktop kernel: [   11.069936] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 16:12:27 mja-desktop kernel: [   11.074971] [drm] radeon: Initializing kernel modesetting.
Aug  2 16:12:27 mja-desktop kernel: [   11.082120] [drm] register mmio base: 0xFE9E0000
Aug  2 16:12:27 mja-desktop kernel: [   11.082125] [drm] register mmio size: 65536
Aug  2 16:12:27 mja-desktop kernel: [   11.082401] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Aug  2 16:12:27 mja-desktop kernel: [   11.082431] [drm] Generation 2 PCI interface, using max accessible memory
Aug  2 16:12:27 mja-desktop kernel: [   11.082441] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Aug  2 16:12:27 mja-desktop kernel: [   11.082463] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Aug  2 16:12:27 mja-desktop kernel: [   11.082502] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
Aug  2 16:12:27 mja-desktop kernel: [   11.082520] [drm] radeon: VRAM 128M
Aug  2 16:12:27 mja-desktop kernel: [   11.082522] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
Aug  2 16:12:27 mja-desktop kernel: [   11.082524] [drm] radeon: GTT 128M
Aug  2 16:12:27 mja-desktop kernel: [   11.082526] [drm] radeon: GTT from 0xC0000000 to 0xC7FFFFFF
Aug  2 16:12:27 mja-desktop kernel: [   11.082548] [drm] radeon: irq initialized.
Aug  2 16:12:27 mja-desktop kernel: [   11.082653] [drm] Detected VRAM RAM=128M, BAR=256M
Aug  2 16:12:27 mja-desktop kernel: [   11.082658] [drm] RAM width 64bits DDR
Aug  2 16:12:27 mja-desktop kernel: [   11.085588] [TTM] Zone  kernel: Available graphics memory: 254288 kiB.
Aug  2 16:12:27 mja-desktop kernel: [   11.085612] [drm] radeon: 128M of VRAM memory ready
Aug  2 16:12:27 mja-desktop kernel: [   11.085615] [drm] radeon: 128M of GTT memory ready.
Aug  2 16:12:27 mja-desktop kernel: [   11.085849] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Aug  2 16:12:27 mja-desktop kernel: [   11.085861] [drm] radeon: cp idle (0x10000C03)
Aug  2 16:12:27 mja-desktop kernel: [   11.085992] [drm] Loading R300 Microcode
Aug  2 16:12:27 mja-desktop kernel: [   11.086360] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
Aug  2 16:12:27 mja-desktop kernel: [   11.110540] [drm] radeon: ring at 0x00000000C0000000
Aug  2 16:12:27 mja-desktop kernel: [   11.110563] [drm] ring test succeeded in 1 usecs
Aug  2 16:12:27 mja-desktop kernel: [   11.115919] type=1505 audit(1280758347.065:2):  operation="profile_load" pid=524 name="/sbin/dhclient3"
Aug  2 16:12:27 mja-desktop kernel: [   11.116534] type=1505 audit(1280758347.069:3):  operation="profile_load" pid=524 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug  2 16:12:27 mja-desktop kernel: [   11.116831] type=1505 audit(1280758347.069:4):  operation="profile_load" pid=524 name="/usr/lib/connman/scripts/dhclient-script"
Aug  2 16:12:27 mja-desktop kernel: [   11.140520] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  2 16:12:27 mja-desktop kernel: [   11.144381] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug  2 16:12:27 mja-desktop kernel: [   11.144568] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug  2 16:12:27 mja-desktop kernel: [   11.151597] [drm] radeon: ib pool ready.
Aug  2 16:12:27 mja-desktop kernel: [   11.151699] [drm] ib test succeeded in 0 usecs
Aug  2 16:12:27 mja-desktop kernel: [   11.152807] [drm] Default TV standard: PAL
Aug  2 16:12:27 mja-desktop kernel: [   11.152812] [drm] 27.000000000 MHz TV ref clk
Aug  2 16:12:27 mja-desktop kernel: [   11.152816] [drm] DFP table revision: 3
Aug  2 16:12:27 mja-desktop kernel: [   11.153598] [drm] Default TV standard: PAL
Aug  2 16:12:27 mja-desktop kernel: [   11.153602] [drm] 27.000000000 MHz TV ref clk
Aug  2 16:12:27 mja-desktop kernel: [   11.153751] [drm] Radeon Display Connectors
Aug  2 16:12:27 mja-desktop kernel: [   11.153754] [drm] Connector 0:
Aug  2 16:12:27 mja-desktop kernel: [   11.153756] [drm]   VGA
Aug  2 16:12:27 mja-desktop kernel: [   11.153760] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Aug  2 16:12:27 mja-desktop kernel: [   11.153762] [drm]   Encoders:
Aug  2 16:12:27 mja-desktop kernel: [   11.153764] [drm]     CRT1: INTERNAL_DAC1
Aug  2 16:12:27 mja-desktop kernel: [   11.153766] [drm] Connector 1:
Aug  2 16:12:27 mja-desktop kernel: [   11.153768] [drm]   DVI-I
Aug  2 16:12:27 mja-desktop kernel: [   11.153769] [drm]   HPD1
Aug  2 16:12:27 mja-desktop kernel: [   11.153772] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Aug  2 16:12:27 mja-desktop kernel: [   11.153774] [drm]   Encoders:
Aug  2 16:12:27 mja-desktop kernel: [   11.153776] [drm]     CRT2: INTERNAL_DAC2
Aug  2 16:12:27 mja-desktop kernel: [   11.153778] [drm]     DFP1: INTERNAL_TMDS1
Aug  2 16:12:27 mja-desktop kernel: [   11.153780] [drm] Connector 2:
Aug  2 16:12:27 mja-desktop kernel: [   11.153782] [drm]   S-video
Aug  2 16:12:27 mja-desktop kernel: [   11.153783] [drm]   Encoders:
Aug  2 16:12:27 mja-desktop kernel: [   11.153785] [drm]     TV1: INTERNAL_DAC2
Aug  2 16:12:27 mja-desktop kernel: [   11.581515] type=1505 audit(1280758347.533:5):  operation="profile_load" pid=688 name="/usr/share/gdm/guest-session/Xsession"
Aug  2 16:12:27 mja-desktop kernel: [   11.585100] type=1505 audit(1280758347.537:6):  operation="profile_replace" pid=689 name="/sbin/dhclient3"
Aug  2 16:12:27 mja-desktop kernel: [   11.585667] type=1505 audit(1280758347.537:7):  operation="profile_replace" pid=689 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug  2 16:12:27 mja-desktop kernel: [   11.585977] type=1505 audit(1280758347.537:8):  operation="profile_replace" pid=689 name="/usr/lib/connman/scripts/dhclient-script"
Aug  2 16:12:27 mja-desktop kernel: [   11.604185] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  2 16:12:27 mja-desktop kernel: [   11.617219] type=1505 audit(1280758347.569:9):  operation="profile_load" pid=690 name="/usr/bin/evince"
Aug  2 16:12:27 mja-desktop kernel: [   11.650324] type=1505 audit(1280758347.601:10):  operation="profile_load" pid=690 name="/usr/bin/evince-previewer"
Aug  2 16:12:27 mja-desktop kernel: [   11.670847] type=1505 audit(1280758347.621:11):  operation="profile_load" pid=690 name="/usr/bin/evince-thumbnailer"
Aug  2 16:12:27 mja-desktop kernel: [   11.745498] [drm] fb mappable at 0xE0040000
Aug  2 16:12:27 mja-desktop kernel: [   11.745502] [drm] vram apper at 0xE0000000
Aug  2 16:12:27 mja-desktop kernel: [   11.745505] [drm] size 5242880
Aug  2 16:12:27 mja-desktop kernel: [   11.745507] [drm] fb depth is 24
Aug  2 16:12:27 mja-desktop kernel: [   11.745509] [drm]    pitch is 5120
Aug  2 16:12:27 mja-desktop kernel: [   11.762017] fb0: radeondrmfb frame buffer device
Aug  2 16:12:27 mja-desktop kernel: [   11.762022] registered panic notifier
Aug  2 16:12:27 mja-desktop kernel: [   11.762032] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
Aug  2 16:12:27 mja-desktop kernel: [   11.770634] vga16fb: mapped to 0xc00a0000
Aug  2 16:12:27 mja-desktop kernel: [   11.770640] vga16fb: not registering due to another framebuffer present
Aug  2 16:12:27 mja-desktop kernel: [   11.927427] Console: switching to colour frame buffer device 160x64
Aug  2 16:12:27 mja-desktop kernel: [   12.024075] intel8x0_measure_ac97_clock: measured 52579 usecs (2534 samples)
Aug  2 16:12:27 mja-desktop kernel: [   12.024080] intel8x0: clocking to 48000
Aug  2 16:12:28 mja-desktop kernel: [   12.261425] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug  2 16:12:28 mja-desktop kernel: [   12.261429] apm: overridden by ACPI.
Aug  2 16:12:35 mja-desktop pulseaudio[1100]: ratelimit.c: 2 events suppressed
Aug  2 17:23:18 mja-desktop kernel: Kernel logging (proc) stopped.
Aug  2 17:23:18 mja-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="583" x-info="http://www.rsyslog.com"] exiting on signal 15.
Aug  2 17:23:48 mja-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug  2 17:23:48 mja-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="555" x-info="http://www.rsyslog.com"] (re)start
Aug  2 17:23:48 mja-desktop rsyslogd: rsyslogd's groupid changed to 103
Aug  2 17:23:48 mja-desktop rsyslogd: rsyslogd's userid changed to 102
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] KERNEL supported cpus:
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   Intel GenuineIntel
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   AMD AuthenticAMD
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   NSC Geode by NSC
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   Centaur CentaurHauls
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff72000 (ACPI NVS)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff72000 - 000000001ff93000 (ACPI data)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 000000001ff93000 - 0000000020000000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] DMI 2.3 present.
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] modified physical RAM map:
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000001ff70000 (usable)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 000000001ff70000 - 000000001ff72000 (ACPI NVS)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 000000001ff72000 - 000000001ff93000 (ACPI data)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 000000001ff93000 - 0000000020000000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] RAMDISK: 1f7d7000 - 1ff5ff90
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: RSDP 000feba0 00014 (v00 DELL  )
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: RSDT 000fd192 00038 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: FACP 000fd1ca 00074 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: DSDT fffd2759 02795 (v01   DELL    dt_ex 00001000 MSFT 0100000D)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: FACS 1ff70000 00040
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: SSDT fffd4eee 000A7 (v01   DELL    st_ex 00001000 MSFT 0100000D)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: APIC 000fd23e 0006C (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: BOOT 000fd2aa 00028 (v01 DELL    GX270   00000007 ASL  00000061)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: ASF! 000fd2d2 00067 (v16 DELL    GX270   00000007 ASL  00000061)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] 511MB LOWMEM available.
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   mapped low ram: 0 - 1ff70000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   low ram: 0 - 1ff70000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 1ff70000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bff0
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ff70000]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #4 [001f7d7000 - 001ff5ff90]          RAMDISK ==> [001f7d7000 - 001ff5ff90]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #6 [00008dc000 - 00008df18c]              BRK ==> [00008dc000 - 00008df18c]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] found SMP MP-table at [c00fe710] fe710
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Zone PFN ranges:
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x0001ff70
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]   HighMem  0x0001ff70 -> 0x0001ff70
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x000000a0
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0001ff70
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Using APIC driver default
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u1048576
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129805
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Kernel command line: root=UUID=baf3a80c-4e26-4d98-83d6-305197df60c3 ro quiet splash 
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Initializing CPU#0
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] allocated 2618560 bytes of page_cgroup
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Memory: 499660k/523712k available (4679k kernel code, 23108k reserved, 2116k data, 660k init, 0k highmem)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] virtual kernel memory layout:
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] console [tty0] enabled
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Aug  2 17:23:48 mja-desktop kernel: [    0.000000] Detected 2793.451 MHz processor.
Aug  2 17:23:48 mja-desktop kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5586.90 BogoMIPS (lpj=11173804)
Aug  2 17:23:48 mja-desktop kernel: [    0.004028] Security Framework initialized
Aug  2 17:23:48 mja-desktop kernel: [    0.004053] AppArmor: AppArmor initialized
Aug  2 17:23:48 mja-desktop kernel: [    0.004063] Mount-cache hash table entries: 512
Aug  2 17:23:48 mja-desktop kernel: [    0.004228] Initializing cgroup subsys ns
Aug  2 17:23:48 mja-desktop kernel: [    0.004234] Initializing cgroup subsys cpuacct
Aug  2 17:23:48 mja-desktop kernel: [    0.004240] Initializing cgroup subsys memory
Aug  2 17:23:48 mja-desktop kernel: [    0.004249] Initializing cgroup subsys devices
Aug  2 17:23:48 mja-desktop kernel: [    0.004253] Initializing cgroup subsys freezer
Aug  2 17:23:48 mja-desktop kernel: [    0.004256] Initializing cgroup subsys net_cls
Aug  2 17:23:48 mja-desktop kernel: [    0.004283] CPU: Trace cache: 12K uops, L1 D cache: 8K
Aug  2 17:23:48 mja-desktop kernel: [    0.004288] CPU: L2 cache: 512K
Aug  2 17:23:48 mja-desktop kernel: [    0.004290] CPU: Hyper-Threading is disabled
Aug  2 17:23:48 mja-desktop kernel: [    0.004295] mce: CPU supports 4 MCE banks
Aug  2 17:23:48 mja-desktop kernel: [    0.004307] CPU0: Thermal monitoring enabled (TM1)
Aug  2 17:23:48 mja-desktop kernel: [    0.004318] Performance Events: no PMU driver, software events only.
Aug  2 17:23:48 mja-desktop kernel: [    0.004326] Checking 'hlt' instruction... OK.
Aug  2 17:23:48 mja-desktop kernel: [    0.020924] SMP alternatives: switching to UP code
Aug  2 17:23:48 mja-desktop kernel: [    0.031919] ACPI: Core revision 20090903
Aug  2 17:23:48 mja-desktop kernel: [    0.069603] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug  2 17:23:48 mja-desktop kernel: [    0.069612] ftrace: allocating 21780 entries in 43 pages
Aug  2 17:23:48 mja-desktop kernel: [    0.072088] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug  2 17:23:48 mja-desktop kernel: [    0.072387] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  2 17:23:48 mja-desktop kernel: [    0.113814] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] Brought up 1 CPUs
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] Total of 1 processors activated (5586.90 BogoMIPS).
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] devtmpfs: initialized
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] regulator: core version 0.5
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] Time: 15:23:36  Date: 08/02/10
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] NET: Registered protocol family 16
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] EISA bus registered
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] ACPI: bus type pci registered
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] PCI: PCI BIOS revision 2.10 entry at 0xfbab0, last bus=2
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] PCI: Using configuration type 1 for base access
Aug  2 17:23:48 mja-desktop kernel: [    0.116001] bio: create slab <bio-0> at 0
Aug  2 17:23:48 mja-desktop kernel: [    0.144101] ACPI: Interpreter enabled
Aug  2 17:23:48 mja-desktop kernel: [    0.144121] ACPI: (supports S0 S1 S3 S4 S5)
Aug  2 17:23:48 mja-desktop kernel: [    0.144149] ACPI: Using IOAPIC for interrupt routing
Aug  2 17:23:48 mja-desktop kernel: [    0.171980] ACPI: No dock devices found.
Aug  2 17:23:48 mja-desktop kernel: [    0.176107] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  2 17:23:48 mja-desktop kernel: [    0.176155] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
Aug  2 17:23:48 mja-desktop kernel: [    0.176659] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug  2 17:23:48 mja-desktop kernel: [    0.176665] pci 0000:00:1d.7: PME# disabled
Aug  2 17:23:48 mja-desktop kernel: [    0.176761] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Aug  2 17:23:48 mja-desktop kernel: [    0.176765] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
Aug  2 17:23:48 mja-desktop kernel: [    0.177044] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Aug  2 17:23:48 mja-desktop kernel: [    0.177049] pci 0000:00:1f.5: PME# disabled
Aug  2 17:23:48 mja-desktop kernel: [    0.177386] pci 0000:02:0c.0: PME# supported from D0 D3hot D3cold
Aug  2 17:23:48 mja-desktop kernel: [    0.177391] pci 0000:02:0c.0: PME# disabled
Aug  2 17:23:48 mja-desktop kernel: [    0.177424] pci 0000:00:1e.0: transparent bridge
Aug  2 17:23:48 mja-desktop kernel: [    0.296354] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Aug  2 17:23:48 mja-desktop kernel: [    0.296668] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
Aug  2 17:23:48 mja-desktop kernel: [    0.296980] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Aug  2 17:23:48 mja-desktop kernel: [    0.297291] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Aug  2 17:23:48 mja-desktop kernel: [    0.297600] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 17:23:48 mja-desktop kernel: [    0.297912] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 17:23:48 mja-desktop kernel: [    0.298221] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  2 17:23:48 mja-desktop kernel: [    0.298534] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Aug  2 17:23:48 mja-desktop kernel: [    0.298713] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug  2 17:23:48 mja-desktop kernel: [    0.298717] vgaarb: loaded
Aug  2 17:23:48 mja-desktop kernel: [    0.298875] SCSI subsystem initialized
Aug  2 17:23:48 mja-desktop kernel: [    0.299047] usbcore: registered new interface driver usbfs
Aug  2 17:23:48 mja-desktop kernel: [    0.299063] usbcore: registered new interface driver hub
Aug  2 17:23:48 mja-desktop kernel: [    0.299092] usbcore: registered new device driver usb
Aug  2 17:23:48 mja-desktop kernel: [    0.299247] ACPI: WMI: Mapper loaded
Aug  2 17:23:48 mja-desktop kernel: [    0.299250] PCI: Using ACPI for IRQ routing
Aug  2 17:23:48 mja-desktop kernel: [    0.299420] NetLabel: Initializing
Aug  2 17:23:48 mja-desktop kernel: [    0.299423] NetLabel:  domain hash size = 128
Aug  2 17:23:48 mja-desktop kernel: [    0.299425] NetLabel:  protocols = UNLABELED CIPSOv4
Aug  2 17:23:48 mja-desktop kernel: [    0.299441] NetLabel:  unlabeled traffic allowed by default
Aug  2 17:23:48 mja-desktop kernel: [    0.299574] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug  2 17:23:48 mja-desktop kernel: [    0.299580] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug  2 17:23:48 mja-desktop kernel: [    0.299586] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Aug  2 17:23:48 mja-desktop kernel: [    0.304025] Switching to clocksource tsc
Aug  2 17:23:48 mja-desktop kernel: [    0.306255] AppArmor: AppArmor Filesystem Enabled
Aug  2 17:23:48 mja-desktop kernel: [    0.306280] pnp: PnP ACPI init
Aug  2 17:23:48 mja-desktop kernel: [    0.306302] ACPI: bus type pnp registered
Aug  2 17:23:48 mja-desktop kernel: [    0.333968] pnp 00:0a: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Aug  2 17:23:48 mja-desktop kernel: [    0.333974] pnp 00:0a: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Aug  2 17:23:48 mja-desktop kernel: [    0.334669] pnp: PnP ACPI: found 11 devices
Aug  2 17:23:48 mja-desktop kernel: [    0.334672] ACPI: ACPI bus type pnp unregistered
Aug  2 17:23:48 mja-desktop kernel: [    0.334679] PnPBIOS: Disabled by ACPI PNP
Aug  2 17:23:48 mja-desktop kernel: [    0.334692] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334697] system 00:00: iomem range 0x100000-0xffffff could not be reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334701] system 00:00: iomem range 0x1000000-0x1ff6ffff could not be reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334705] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334709] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334712] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334716] system 00:00: iomem range 0xfed20000-0xfed8ffff has been reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334719] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334723] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334726] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.334738] system 00:0a: ioport range 0xc00-0xc7f has been reserved
Aug  2 17:23:48 mja-desktop kernel: [    0.369486] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Aug  2 17:23:48 mja-desktop kernel: [    0.369490] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
Aug  2 17:23:48 mja-desktop kernel: [    0.369497] pci 0000:00:01.0:   MEM window: 0xfe900000-0xfeafffff
Aug  2 17:23:48 mja-desktop kernel: [    0.369502] pci 0000:00:01.0:   PREFETCH window: 0xc8000000-0xefffffff
Aug  2 17:23:48 mja-desktop kernel: [    0.369509] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Aug  2 17:23:48 mja-desktop kernel: [    0.369513] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Aug  2 17:23:48 mja-desktop kernel: [    0.369519] pci 0000:00:1e.0:   MEM window: 0xfe800000-0xfe8fffff
Aug  2 17:23:48 mja-desktop kernel: [    0.369523] pci 0000:00:1e.0:   PREFETCH window: disabled
Aug  2 17:23:48 mja-desktop kernel: [    0.369618] NET: Registered protocol family 2
Aug  2 17:23:48 mja-desktop kernel: [    0.369732] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Aug  2 17:23:48 mja-desktop kernel: [    0.370064] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Aug  2 17:23:48 mja-desktop kernel: [    0.370136] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Aug  2 17:23:48 mja-desktop kernel: [    0.370204] TCP: Hash tables configured (established 16384 bind 16384)
Aug  2 17:23:48 mja-desktop kernel: [    0.370207] TCP reno registered
Aug  2 17:23:48 mja-desktop kernel: [    0.370306] NET: Registered protocol family 1
Aug  2 17:23:48 mja-desktop kernel: [    0.370519] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Aug  2 17:23:48 mja-desktop kernel: [    0.370522] Simple Boot Flag at 0x7a set to 0x1
Aug  2 17:23:48 mja-desktop kernel: [    0.370623] cpufreq-nforce2: No nForce2 chipset.
Aug  2 17:23:48 mja-desktop kernel: [    0.370658] Scanning for low memory corruption every 60 seconds
Aug  2 17:23:48 mja-desktop kernel: [    0.370791] audit: initializing netlink socket (disabled)
Aug  2 17:23:48 mja-desktop kernel: [    0.370805] type=2000 audit(1280762616.367:1): initialized
Aug  2 17:23:48 mja-desktop kernel: [    0.379034] Trying to unpack rootfs image as initramfs...
Aug  2 17:23:48 mja-desktop kernel: [    0.388138] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug  2 17:23:48 mja-desktop kernel: [    0.394091] VFS: Disk quotas dquot_6.5.2
Aug  2 17:23:48 mja-desktop kernel: [    0.394166] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  2 17:23:48 mja-desktop kernel: [    0.394888] fuse init (API version 7.13)
Aug  2 17:23:48 mja-desktop kernel: [    0.394993] msgmni has been set to 976
Aug  2 17:23:48 mja-desktop kernel: [    0.400217] alg: No test for stdrng (krng)
Aug  2 17:23:48 mja-desktop kernel: [    0.400331] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug  2 17:23:48 mja-desktop kernel: [    0.400335] io scheduler noop registered
Aug  2 17:23:48 mja-desktop kernel: [    0.400337] io scheduler anticipatory registered
Aug  2 17:23:48 mja-desktop kernel: [    0.400339] io scheduler deadline registered
Aug  2 17:23:48 mja-desktop kernel: [    0.400396] io scheduler cfq registered (default)
Aug  2 17:23:48 mja-desktop kernel: [    0.400534] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  2 17:23:48 mja-desktop kernel: [    0.400562] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug  2 17:23:48 mja-desktop kernel: [    0.400668] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Aug  2 17:23:48 mja-desktop kernel: [    0.400678] ACPI: Power Button [VBTN]
Aug  2 17:23:48 mja-desktop kernel: [    0.400740] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Aug  2 17:23:48 mja-desktop kernel: [    0.400744] ACPI: Power Button [PWRF]
Aug  2 17:23:48 mja-desktop kernel: [    0.400974] processor LNXCPU:00: registered as cooling_device0
Aug  2 17:23:48 mja-desktop kernel: [    0.438589] isapnp: Scanning for PnP cards...
Aug  2 17:23:48 mja-desktop kernel: [    0.444325] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug  2 17:23:48 mja-desktop kernel: [    0.444426] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  2 17:23:48 mja-desktop kernel: [    0.444840] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  2 17:23:48 mja-desktop kernel: [    0.446073] brd: module loaded
Aug  2 17:23:48 mja-desktop kernel: [    0.446637] loop: module loaded
Aug  2 17:23:48 mja-desktop kernel: [    0.446754] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Aug  2 17:23:48 mja-desktop kernel: [    0.446907] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 17:23:48 mja-desktop kernel: [    0.452042] scsi0 : ata_piix
Aug  2 17:23:48 mja-desktop kernel: [    0.452207] scsi1 : ata_piix
Aug  2 17:23:48 mja-desktop kernel: [    0.452250] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Aug  2 17:23:48 mja-desktop kernel: [    0.452254] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Aug  2 17:23:48 mja-desktop kernel: [    0.452301] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 17:23:48 mja-desktop kernel: [    0.452308] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Aug  2 17:23:48 mja-desktop kernel: [    0.452441] scsi2 : ata_piix
Aug  2 17:23:48 mja-desktop kernel: [    0.500241] scsi3 : ata_piix
Aug  2 17:23:48 mja-desktop kernel: [    0.500316] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 18
Aug  2 17:23:48 mja-desktop kernel: [    0.500320] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 18
Aug  2 17:23:48 mja-desktop kernel: [    0.500754] Fixed MDIO Bus: probed
Aug  2 17:23:48 mja-desktop kernel: [    0.500797] PPP generic driver version 2.4.2
Aug  2 17:23:48 mja-desktop kernel: [    0.500882] tun: Universal TUN/TAP device driver, 1.6
Aug  2 17:23:48 mja-desktop kernel: [    0.500885] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug  2 17:23:48 mja-desktop kernel: [    0.500998] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug  2 17:23:48 mja-desktop kernel: [    0.501039] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Aug  2 17:23:48 mja-desktop kernel: [    0.501063] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug  2 17:23:48 mja-desktop kernel: [    0.501114] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Aug  2 17:23:48 mja-desktop kernel: [    0.501147] ehci_hcd 0000:00:1d.7: debug port 1
Aug  2 17:23:48 mja-desktop kernel: [    0.505393] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
Aug  2 17:23:48 mja-desktop kernel: [    0.524339] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug  2 17:23:48 mja-desktop kernel: [    0.524505] usb usb1: configuration #1 chosen from 1 choice
Aug  2 17:23:48 mja-desktop kernel: [    0.524544] hub 1-0:1.0: USB hub found
Aug  2 17:23:48 mja-desktop kernel: [    0.524557] hub 1-0:1.0: 8 ports detected
Aug  2 17:23:48 mja-desktop kernel: [    0.524646] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug  2 17:23:48 mja-desktop kernel: [    0.524667] uhci_hcd: USB Universal Host Controller Interface driver
Aug  2 17:23:48 mja-desktop kernel: [    0.524737] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 17:23:48 mja-desktop kernel: [    0.524753] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  2 17:23:48 mja-desktop kernel: [    0.524805] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug  2 17:23:48 mja-desktop kernel: [    0.524842] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
Aug  2 17:23:48 mja-desktop kernel: [    0.524949] usb usb2: configuration #1 chosen from 1 choice
Aug  2 17:23:48 mja-desktop kernel: [    0.524982] hub 2-0:1.0: USB hub found
Aug  2 17:23:48 mja-desktop kernel: [    0.524992] hub 2-0:1.0: 2 ports detected
Aug  2 17:23:48 mja-desktop kernel: [    0.525056] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug  2 17:23:48 mja-desktop kernel: [    0.525067] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  2 17:23:48 mja-desktop kernel: [    0.525111] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Aug  2 17:23:48 mja-desktop kernel: [    0.525140] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
Aug  2 17:23:48 mja-desktop kernel: [    0.525239] usb usb3: configuration #1 chosen from 1 choice
Aug  2 17:23:48 mja-desktop kernel: [    0.525273] hub 3-0:1.0: USB hub found
Aug  2 17:23:48 mja-desktop kernel: [    0.525283] hub 3-0:1.0: 2 ports detected
Aug  2 17:23:48 mja-desktop kernel: [    0.525334] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  2 17:23:48 mja-desktop kernel: [    0.525345] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  2 17:23:48 mja-desktop kernel: [    0.525383] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Aug  2 17:23:48 mja-desktop kernel: [    0.525406] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Aug  2 17:23:48 mja-desktop kernel: [    0.525510] usb usb4: configuration #1 chosen from 1 choice
Aug  2 17:23:48 mja-desktop kernel: [    0.525545] hub 4-0:1.0: USB hub found
Aug  2 17:23:48 mja-desktop kernel: [    0.525555] hub 4-0:1.0: 2 ports detected
Aug  2 17:23:48 mja-desktop kernel: [    0.525606] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 17:23:48 mja-desktop kernel: [    0.525616] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug  2 17:23:48 mja-desktop kernel: [    0.525655] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Aug  2 17:23:48 mja-desktop kernel: [    0.525678] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
Aug  2 17:23:48 mja-desktop kernel: [    0.525783] usb usb5: configuration #1 chosen from 1 choice
Aug  2 17:23:48 mja-desktop kernel: [    0.525815] hub 5-0:1.0: USB hub found
Aug  2 17:23:48 mja-desktop kernel: [    0.525825] hub 5-0:1.0: 2 ports detected
Aug  2 17:23:48 mja-desktop kernel: [    0.525931] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
Aug  2 17:23:48 mja-desktop kernel: [    0.525934] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug  2 17:23:48 mja-desktop kernel: [    0.526611] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  2 17:23:48 mja-desktop kernel: [    0.526756] mice: PS/2 mouse device common for all mice
Aug  2 17:23:48 mja-desktop kernel: [    0.526903] rtc_cmos 00:05: RTC can wake from S4
Aug  2 17:23:48 mja-desktop kernel: [    0.526954] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Aug  2 17:23:48 mja-desktop kernel: [    0.526982] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
Aug  2 17:23:48 mja-desktop kernel: [    0.527121] device-mapper: uevent: version 1.0.3
Aug  2 17:23:48 mja-desktop kernel: [    0.532291] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Aug  2 17:23:48 mja-desktop kernel: [    0.532383] device-mapper: multipath: version 1.1.0 loaded
Aug  2 17:23:48 mja-desktop kernel: [    0.532386] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug  2 17:23:48 mja-desktop kernel: [    0.532541] EISA: Probing bus 0 at eisa.0
Aug  2 17:23:48 mja-desktop kernel: [    0.532580] EISA: Detected 0 cards.
Aug  2 17:23:48 mja-desktop kernel: [    0.536242] cpuidle: using governor ladder
Aug  2 17:23:48 mja-desktop kernel: [    0.536247] cpuidle: using governor menu
Aug  2 17:23:48 mja-desktop kernel: [    0.536898] TCP cubic registered
Aug  2 17:23:48 mja-desktop kernel: [    0.537053] NET: Registered protocol family 10
Aug  2 17:23:48 mja-desktop kernel: [    0.537618] lo: Disabled Privacy Extensions
Aug  2 17:23:48 mja-desktop kernel: [    0.538005] NET: Registered protocol family 17
Aug  2 17:23:48 mja-desktop kernel: [    0.538075] Using IPI No-Shortcut mode
Aug  2 17:23:48 mja-desktop kernel: [    0.538210] registered taskstats version 1
Aug  2 17:23:48 mja-desktop kernel: [    0.538484]   Magic number: 6:574:385
Aug  2 17:23:48 mja-desktop kernel: [    0.538494] usb usb3: hash matches
Aug  2 17:23:48 mja-desktop kernel: [    0.538527] thermal cooling_device0: hash matches
Aug  2 17:23:48 mja-desktop kernel: [    0.538572] rtc_cmos 00:05: setting system clock to 2010-08-02 15:23:37 UTC (1280762617)
Aug  2 17:23:48 mja-desktop kernel: [    0.538576] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  2 17:23:48 mja-desktop kernel: [    0.538578] EDD information not available.
Aug  2 17:23:48 mja-desktop kernel: [    0.608894] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Aug  2 17:23:48 mja-desktop kernel: [    0.696995] ata3.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
Aug  2 17:23:48 mja-desktop kernel: [    0.697000] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug  2 17:23:48 mja-desktop kernel: [    0.697107] ata4.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
Aug  2 17:23:48 mja-desktop kernel: [    0.697110] ata4.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug  2 17:23:48 mja-desktop kernel: [    0.697547] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-252S, R901, max UDMA/33
Aug  2 17:23:48 mja-desktop kernel: [    0.697591] ata2.01: ATAPI: HL-DT-STDVDRRW GCA-4164B, H.I0, max UDMA/33
Aug  2 17:23:48 mja-desktop kernel: [    0.704515] ata4.00: configured for UDMA/100
Aug  2 17:23:48 mja-desktop kernel: [    0.704576] ata3.00: configured for UDMA/100
Aug  2 17:23:48 mja-desktop kernel: [    0.712168] ata2.00: configured for UDMA/33
Aug  2 17:23:48 mja-desktop kernel: [    0.728341] ata2.01: configured for UDMA/33
Aug  2 17:23:48 mja-desktop kernel: [    0.888132] Freeing initrd memory: 7715k freed
Aug  2 17:23:48 mja-desktop kernel: [    1.026332] isapnp: No Plug & Play device found
Aug  2 17:23:48 mja-desktop kernel: [    1.027365] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-252S  R901 PQ: 0 ANSI: 5
Aug  2 17:23:48 mja-desktop kernel: [    1.031319] sr0: scsi3-mmc drive: 48x/16x writer cd/rw xa/form2 cdda tray
Aug  2 17:23:48 mja-desktop kernel: [    1.031324] Uniform CD-ROM driver Revision: 3.20
Aug  2 17:23:48 mja-desktop kernel: [    1.031554] sr 1:0:0:0: Attached scsi generic sg0 type 5
Aug  2 17:23:48 mja-desktop kernel: [    1.033136] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRRW GCA-4164B H.I0 PQ: 0 ANSI: 5
Aug  2 17:23:48 mja-desktop kernel: [    1.038235] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Aug  2 17:23:48 mja-desktop kernel: [    1.038405] sr 1:0:1:0: Attached scsi generic sg1 type 5
Aug  2 17:23:48 mja-desktop kernel: [    1.038539] scsi 2:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
Aug  2 17:23:48 mja-desktop kernel: [    1.038686] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug  2 17:23:48 mja-desktop kernel: [    1.038823] scsi 3:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
Aug  2 17:23:48 mja-desktop kernel: [    1.038960] sd 3:0:0:0: Attached scsi generic sg3 type 0
Aug  2 17:23:48 mja-desktop kernel: [    1.039043] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug  2 17:23:48 mja-desktop kernel: [    1.039090] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug  2 17:23:48 mja-desktop kernel: [    1.039159] sd 3:0:0:0: [sdb] Write Protect is off
Aug  2 17:23:48 mja-desktop kernel: [    1.039204] sd 2:0:0:0: [sda] Write Protect is off
Aug  2 17:23:48 mja-desktop kernel: [    1.039225] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 17:23:48 mja-desktop kernel: [    1.039306] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 17:23:48 mja-desktop kernel: [    1.039543]  sdb:
Aug  2 17:23:48 mja-desktop kernel: [    1.039638]  sda: sdb1 sdb2 < sda1
Aug  2 17:23:48 mja-desktop kernel: [    1.061879] sd 2:0:0:0: [sda] Attached SCSI disk
Aug  2 17:23:48 mja-desktop kernel: [    1.079910] usb 3-2: new low speed USB device using uhci_hcd and address 2
Aug  2 17:23:48 mja-desktop kernel: [    1.083431]  sdb5 >
Aug  2 17:23:48 mja-desktop kernel: [    1.083752] sd 3:0:0:0: [sdb] Attached SCSI disk
Aug  2 17:23:48 mja-desktop kernel: [    1.083769] Freeing unused kernel memory: 660k freed
Aug  2 17:23:48 mja-desktop kernel: [    1.084415] Write protecting the kernel text: 4680k
Aug  2 17:23:48 mja-desktop kernel: [    1.084444] Write protecting the kernel read-only data: 1840k
Aug  2 17:23:48 mja-desktop kernel: [    1.109349] udev: starting version 151
Aug  2 17:23:48 mja-desktop kernel: [    1.257124] usb 3-2: configuration #1 chosen from 1 choice
Aug  2 17:23:48 mja-desktop kernel: [    1.363418] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
Aug  2 17:23:48 mja-desktop kernel: [    1.363424] Copyright (c) 1999-2006 Intel Corporation.
Aug  2 17:23:48 mja-desktop kernel: [    1.363473] e1000 0000:02:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 17:23:48 mja-desktop kernel: [    1.371077] Floppy drive(s): fd0 is 1.44M
Aug  2 17:23:48 mja-desktop kernel: [    1.377891] usbcore: registered new interface driver hiddev
Aug  2 17:23:48 mja-desktop kernel: [    1.386232] FDC 0 is a post-1991 82077
Aug  2 17:23:48 mja-desktop kernel: [    1.634786] e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0f:1f:74:e1:be
Aug  2 17:23:48 mja-desktop kernel: [    1.635743] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
Aug  2 17:23:48 mja-desktop kernel: [    1.636049] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
Aug  2 17:23:48 mja-desktop kernel: [    1.636086] usbcore: registered new interface driver usbhid
Aug  2 17:23:48 mja-desktop kernel: [    1.636220] usbhid: v2.6:USB HID core driver
Aug  2 17:23:48 mja-desktop kernel: [    1.673557] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Aug  2 17:23:48 mja-desktop kernel: [    1.728943] kjournald starting.  Commit interval 5 seconds
Aug  2 17:23:48 mja-desktop kernel: [    1.728959] EXT3-fs: mounted filesystem with ordered data mode.
Aug  2 17:23:48 mja-desktop kernel: [   10.451802] Adding 1510068k swap on /dev/sdb5.  Priority:-1 extents:1 across:1510068k 
Aug  2 17:23:48 mja-desktop kernel: [   10.525045] udev: starting version 151
Aug  2 17:23:48 mja-desktop kernel: [   10.644719] EXT3 FS on sda1, internal journal
Aug  2 17:23:48 mja-desktop kernel: [   10.678033] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  2 17:23:48 mja-desktop kernel: [   10.727962] lp: driver loaded but no devices found
Aug  2 17:23:48 mja-desktop kernel: [   10.826534] Linux agpgart interface v0.103
Aug  2 17:23:48 mja-desktop kernel: [   10.884110] intel_rng: FWH not detected
Aug  2 17:23:48 mja-desktop kernel: [   10.973247] agpgart-intel 0000:00:00.0: Intel 865 Chipset
Aug  2 17:23:48 mja-desktop kernel: [   11.004053] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Aug  2 17:23:48 mja-desktop kernel: [   11.005843] parport_pc 00:09: reported by Plug and Play ACPI
Aug  2 17:23:48 mja-desktop kernel: [   11.005895] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Aug  2 17:23:48 mja-desktop kernel: [   11.108237] lp0: using parport0 (interrupt-driven).
Aug  2 17:23:48 mja-desktop kernel: [   11.140192] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xc0000000
Aug  2 17:23:48 mja-desktop kernel: [   11.213691] dell-wmi: No known WMI GUID found
Aug  2 17:23:48 mja-desktop kernel: [   11.225481] [drm] Initialized drm 1.1.0 20060810
Aug  2 17:23:48 mja-desktop kernel: [   11.247163] ppdev: user-space parallel port driver
Aug  2 17:23:48 mja-desktop kernel: [   11.251625] type=1505 audit(1280762628.209:2):  operation="profile_load" pid=488 name="/sbin/dhclient3"
Aug  2 17:23:48 mja-desktop kernel: [   11.252225] type=1505 audit(1280762628.213:3):  operation="profile_load" pid=488 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug  2 17:23:48 mja-desktop kernel: [   11.252521] type=1505 audit(1280762628.213:4):  operation="profile_load" pid=488 name="/usr/lib/connman/scripts/dhclient-script"
Aug  2 17:23:48 mja-desktop kernel: [   11.459585] [drm] radeon defaulting to kernel modesetting.
Aug  2 17:23:48 mja-desktop kernel: [   11.459591] [drm] radeon kernel modesetting enabled.
Aug  2 17:23:48 mja-desktop kernel: [   11.459652] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 17:23:48 mja-desktop kernel: [   11.463942] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  2 17:23:48 mja-desktop kernel: [   11.464400] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug  2 17:23:48 mja-desktop kernel: [   11.464561] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug  2 17:23:48 mja-desktop kernel: [   11.477034] [drm] radeon: Initializing kernel modesetting.
Aug  2 17:23:48 mja-desktop kernel: [   11.479107] [drm] register mmio base: 0xFE9E0000
Aug  2 17:23:48 mja-desktop kernel: [   11.479111] [drm] register mmio size: 65536
Aug  2 17:23:48 mja-desktop kernel: [   11.479372] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Aug  2 17:23:48 mja-desktop kernel: [   11.479399] [drm] Generation 2 PCI interface, using max accessible memory
Aug  2 17:23:48 mja-desktop kernel: [   11.479409] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Aug  2 17:23:48 mja-desktop kernel: [   11.479430] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Aug  2 17:23:48 mja-desktop kernel: [   11.479469] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
Aug  2 17:23:48 mja-desktop kernel: [   11.479487] [drm] radeon: VRAM 128M
Aug  2 17:23:48 mja-desktop kernel: [   11.479490] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
Aug  2 17:23:48 mja-desktop kernel: [   11.479492] [drm] radeon: GTT 128M
Aug  2 17:23:48 mja-desktop kernel: [   11.479494] [drm] radeon: GTT from 0xC0000000 to 0xC7FFFFFF
Aug  2 17:23:48 mja-desktop kernel: [   11.479516] [drm] radeon: irq initialized.
Aug  2 17:23:48 mja-desktop kernel: [   11.479624] [drm] Detected VRAM RAM=128M, BAR=256M
Aug  2 17:23:48 mja-desktop kernel: [   11.479628] [drm] RAM width 64bits DDR
Aug  2 17:23:48 mja-desktop kernel: [   11.481887] [TTM] Zone  kernel: Available graphics memory: 254288 kiB.
Aug  2 17:23:48 mja-desktop kernel: [   11.481912] [drm] radeon: 128M of VRAM memory ready
Aug  2 17:23:48 mja-desktop kernel: [   11.481915] [drm] radeon: 128M of GTT memory ready.
Aug  2 17:23:48 mja-desktop kernel: [   11.482151] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Aug  2 17:23:48 mja-desktop kernel: [   11.482163] [drm] radeon: cp idle (0x10000C03)
Aug  2 17:23:48 mja-desktop kernel: [   11.482283] [drm] Loading R300 Microcode
Aug  2 17:23:48 mja-desktop kernel: [   11.482651] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
Aug  2 17:23:48 mja-desktop kernel: [   11.503845] [drm] radeon: ring at 0x00000000C0000000
Aug  2 17:23:48 mja-desktop kernel: [   11.503868] [drm] ring test succeeded in 1 usecs
Aug  2 17:23:48 mja-desktop kernel: [   11.521026] [drm] radeon: ib pool ready.
Aug  2 17:23:48 mja-desktop kernel: [   11.521123] [drm] ib test succeeded in 0 usecs
Aug  2 17:23:48 mja-desktop kernel: [   11.522387] [drm] Default TV standard: PAL
Aug  2 17:23:48 mja-desktop kernel: [   11.522392] [drm] 27.000000000 MHz TV ref clk
Aug  2 17:23:48 mja-desktop kernel: [   11.522396] [drm] DFP table revision: 3
Aug  2 17:23:48 mja-desktop kernel: [   11.523473] [drm] Default TV standard: PAL
Aug  2 17:23:48 mja-desktop kernel: [   11.523478] [drm] 27.000000000 MHz TV ref clk
Aug  2 17:23:48 mja-desktop kernel: [   11.524274] [drm] Radeon Display Connectors
Aug  2 17:23:48 mja-desktop kernel: [   11.524278] [drm] Connector 0:
Aug  2 17:23:48 mja-desktop kernel: [   11.524280] [drm]   VGA
Aug  2 17:23:48 mja-desktop kernel: [   11.524284] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Aug  2 17:23:48 mja-desktop kernel: [   11.524286] [drm]   Encoders:
Aug  2 17:23:48 mja-desktop kernel: [   11.524288] [drm]     CRT1: INTERNAL_DAC1
Aug  2 17:23:48 mja-desktop kernel: [   11.524290] [drm] Connector 1:
Aug  2 17:23:48 mja-desktop kernel: [   11.524292] [drm]   DVI-I
Aug  2 17:23:48 mja-desktop kernel: [   11.524294] [drm]   HPD1
Aug  2 17:23:48 mja-desktop kernel: [   11.524297] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Aug  2 17:23:48 mja-desktop kernel: [   11.524299] [drm]   Encoders:
Aug  2 17:23:48 mja-desktop kernel: [   11.524301] [drm]     CRT2: INTERNAL_DAC2
Aug  2 17:23:48 mja-desktop kernel: [   11.524303] [drm]     DFP1: INTERNAL_TMDS1
Aug  2 17:23:48 mja-desktop kernel: [   11.524305] [drm] Connector 2:
Aug  2 17:23:48 mja-desktop kernel: [   11.524307] [drm]   S-video
Aug  2 17:23:48 mja-desktop kernel: [   11.524309] [drm]   Encoders:
Aug  2 17:23:48 mja-desktop kernel: [   11.524311] [drm]     TV1: INTERNAL_DAC2
Aug  2 17:23:48 mja-desktop kernel: [   11.702040] type=1505 audit(1280762628.661:5):  operation="profile_load" pid=637 name="/usr/share/gdm/guest-session/Xsession"
Aug  2 17:23:48 mja-desktop kernel: [   11.706695] type=1505 audit(1280762628.665:6):  operation="profile_replace" pid=640 name="/sbin/dhclient3"
Aug  2 17:23:48 mja-desktop kernel: [   11.707266] type=1505 audit(1280762628.665:7):  operation="profile_replace" pid=640 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug  2 17:23:48 mja-desktop kernel: [   11.707574] type=1505 audit(1280762628.665:8):  operation="profile_replace" pid=640 name="/usr/lib/connman/scripts/dhclient-script"
Aug  2 17:23:48 mja-desktop kernel: [   11.762096] type=1505 audit(1280762628.721:9):  operation="profile_load" pid=642 name="/usr/bin/evince"
Aug  2 17:23:48 mja-desktop kernel: [   11.815176] type=1505 audit(1280762628.773:10):  operation="profile_load" pid=642 name="/usr/bin/evince-previewer"
Aug  2 17:23:48 mja-desktop kernel: [   11.850557] type=1505 audit(1280762628.809:11):  operation="profile_load" pid=642 name="/usr/bin/evince-thumbnailer"
Aug  2 17:23:48 mja-desktop kernel: [   11.973204] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  2 17:23:49 mja-desktop kernel: [   12.084022] [drm] fb mappable at 0xE0040000
Aug  2 17:23:49 mja-desktop kernel: [   12.084026] [drm] vram apper at 0xE0000000
Aug  2 17:23:49 mja-desktop kernel: [   12.084029] [drm] size 5242880
Aug  2 17:23:49 mja-desktop kernel: [   12.084031] [drm] fb depth is 24
Aug  2 17:23:49 mja-desktop kernel: [   12.084033] [drm]    pitch is 5120
Aug  2 17:23:49 mja-desktop kernel: [   12.092906] fb0: radeondrmfb frame buffer device
Aug  2 17:23:49 mja-desktop kernel: [   12.092910] registered panic notifier
Aug  2 17:23:49 mja-desktop kernel: [   12.092919] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
Aug  2 17:23:49 mja-desktop kernel: [   12.101973] vga16fb: mapped to 0xc00a0000
Aug  2 17:23:49 mja-desktop kernel: [   12.101978] vga16fb: not registering due to another framebuffer present
Aug  2 17:23:49 mja-desktop kernel: [   12.272760] Console: switching to colour frame buffer device 160x64
Aug  2 17:23:49 mja-desktop kernel: [   12.408057] intel8x0_measure_ac97_clock: measured 54328 usecs (2618 samples)
Aug  2 17:23:49 mja-desktop kernel: [   12.408062] intel8x0: clocking to 48000
Aug  2 17:23:49 mja-desktop kernel: [   12.430685] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug  2 17:23:49 mja-desktop kernel: [   12.430690] apm: overridden by ACPI.
Aug  2 17:23:57 mja-desktop pulseaudio[1092]: ratelimit.c: 1 events suppressed
Aug  2 17:24:14 mja-desktop pulseaudio[1279]: ratelimit.c: 1 events suppressed
Aug  2 20:25:38 mja-desktop kernel: [ 4697.264259] PM: Syncing filesystems ... done.
Aug  2 20:25:38 mja-desktop kernel: [ 4697.280052] Freezing user space processes ... (elapsed 0.00 seconds) done.
Aug  2 20:25:38 mja-desktop kernel: [ 4697.284127] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Aug  2 20:25:38 mja-desktop kernel: [ 4697.284263] Suspending console(s) (use no_console_suspend to debug)
Aug  2 20:25:38 mja-desktop kernel: [ 4697.304026] sd 3:0:0:0: [sdb] Synchronizing SCSI cache
Aug  2 20:25:38 mja-desktop kernel: [ 4697.304133] sd 3:0:0:0: [sdb] Stopping disk
Aug  2 20:25:38 mja-desktop kernel: [ 4697.304271] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Aug  2 20:25:38 mja-desktop kernel: [ 4697.326036] sd 2:0:0:0: [sda] Stopping disk
Aug  2 20:25:38 mja-desktop kernel: [ 4697.430726] PM: suspend of drv:sd dev:2:0:0:0 complete after 126.454 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4697.996011] PM: suspend of drv:atkbd dev:serio0 complete after 565.235 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4697.996835] parport_pc 00:09: disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4697.997264] serial 00:08: disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4698.046003] e1000 0000:02:0c.0: PCI INT A disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4698.046011] e1000 0000:02:0c.0: PME# enabled
Aug  2 20:25:38 mja-desktop kernel: [ 4698.046025] pci 0000:00:1e.0: wake-up capability enabled by ACPI
Aug  2 20:25:38 mja-desktop kernel: [ 4699.932423] radeon 0000:01:00.0: PCI INT A disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948022] PM: suspend of drv:radeon dev:0000:01:00.0 complete after 1888.001 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948213] Intel ICH 0000:00:1f.5: PCI INT B disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948339] ata_piix 0000:00:1f.2: PCI INT A disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948451] ata_piix 0000:00:1f.1: PCI INT A disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948463] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948471] uhci_hcd 0000:00:1d.3: PCI INT A disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948478] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948485] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948492] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948650] PM: suspend of devices complete after 2664.220 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4699.948654] PM: suspend devices took 2.664 seconds
Aug  2 20:25:38 mja-desktop kernel: [ 4699.964172] PM: late suspend of devices complete after 15.513 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4699.964277] ACPI: Preparing to enter system sleep state S3
Aug  2 20:25:38 mja-desktop kernel: [ 4699.965049] Disabling non-boot CPUs ...
Aug  2 20:25:38 mja-desktop kernel: [ 4699.965071] CPU0: Thermal monitoring enabled (TM1)
Aug  2 20:25:38 mja-desktop kernel: [ 4699.965071] ACPI: Waking up from system sleep state S3
Aug  2 20:25:38 mja-desktop kernel: [ 4699.971683] PM: early resume of devices complete after 0.759 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4699.971903] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 20:25:38 mja-desktop kernel: [ 4699.971929] usb usb2: root hub lost power or was reset
Aug  2 20:25:38 mja-desktop kernel: [ 4699.971947] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug  2 20:25:38 mja-desktop kernel: [ 4699.971971] usb usb3: root hub lost power or was reset
Aug  2 20:25:38 mja-desktop kernel: [ 4699.972011] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  2 20:25:38 mja-desktop kernel: [ 4699.972036] usb usb4: root hub lost power or was reset
Aug  2 20:25:38 mja-desktop kernel: [ 4699.972052] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 20:25:38 mja-desktop kernel: [ 4699.972076] usb usb5: root hub lost power or was reset
Aug  2 20:25:38 mja-desktop kernel: [ 4699.972091] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Aug  2 20:25:38 mja-desktop kernel: [ 4699.972119] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 20:25:38 mja-desktop kernel: [ 4699.972296] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 20:25:38 mja-desktop kernel: [ 4699.972339] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  2 20:25:38 mja-desktop kernel: [ 4699.981883] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 20:25:38 mja-desktop kernel: [ 4699.981891] [drm] AGP mode requested: 8
Aug  2 20:25:38 mja-desktop kernel: [ 4699.981894] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Aug  2 20:25:38 mja-desktop kernel: [ 4699.981911] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Aug  2 20:25:38 mja-desktop kernel: [ 4699.981951] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
Aug  2 20:25:38 mja-desktop kernel: [ 4699.982175] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Aug  2 20:25:38 mja-desktop kernel: [ 4700.086568] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Aug  2 20:25:38 mja-desktop kernel: [ 4700.086572] [drm] radeon: cp idle (0x10000C03)
Aug  2 20:25:38 mja-desktop kernel: [ 4700.086611] [drm] radeon: ring at 0x00000000C0000000
Aug  2 20:25:38 mja-desktop kernel: [ 4700.086645] [drm] ring test succeeded in 1 usecs
Aug  2 20:25:38 mja-desktop kernel: [ 4700.086656] [drm] ib test succeeded in 0 usecs
Aug  2 20:25:38 mja-desktop kernel: [ 4700.143005] PM: resume of drv:radeon dev:0000:01:00.0 complete after 161.126 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4700.143020] e1000 0000:02:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 20:25:38 mja-desktop kernel: [ 4700.143038] pci 0000:00:1e.0: wake-up capability disabled by ACPI
Aug  2 20:25:38 mja-desktop kernel: [ 4700.143043] e1000 0000:02:0c.0: PME# disabled
Aug  2 20:25:38 mja-desktop kernel: [ 4700.177113] serial 00:08: activated
Aug  2 20:25:38 mja-desktop kernel: [ 4700.182310] parport_pc 00:09: activated
Aug  2 20:25:38 mja-desktop kernel: [ 4700.204199] ata2.00: configured for UDMA/33
Aug  2 20:25:38 mja-desktop kernel: [ 4700.220277] ata2.01: configured for UDMA/33
Aug  2 20:25:38 mja-desktop kernel: [ 4700.480012] PM: resume of drv:usb dev:usb3 complete after 247.968 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4700.480292] sd 2:0:0:0: [sda] Starting disk
Aug  2 20:25:38 mja-desktop kernel: [ 4701.864367] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug  2 20:25:38 mja-desktop kernel: [ 4704.184252] ata3.00: configured for UDMA/100
Aug  2 20:25:38 mja-desktop kernel: [ 4704.198002] PM: resume of drv:sd dev:2:0:0:0 complete after 3717.710 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4704.198011] sd 3:0:0:0: [sdb] Starting disk
Aug  2 20:25:38 mja-desktop kernel: [ 4704.296252] ata4.00: configured for UDMA/100
Aug  2 20:25:38 mja-desktop kernel: [ 4704.316850] PM: resume of drv:sd dev:3:0:0:0 complete after 118.839 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4704.576012] usb 3-2: reset low speed USB device using uhci_hcd and address 2
Aug  2 20:25:38 mja-desktop kernel: [ 4704.883811] PM: resume of drv:usb dev:3-2 complete after 566.949 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880005] 
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880007] floppy driver state
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880008] -------------------
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880012] now=1101970 last interrupt=4294896198 diff=1173068 last called handler=e083f2a0
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880014] timeout_message=lock fdc
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880016] last output bytes:
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880018]  8 80 4294892642
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880020]  8 80 4294892642
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880022]  8 80 4294892642
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880024]  8 80 4294892642
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880026] 12 80 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880027]  0 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880029] 13 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880031]  0 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880033] 1a 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880035]  0 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880037]  3 80 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880039] c1 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880041] 10 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880043]  7 80 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880044]  0 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880046]  8 81 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880048]  f 80 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880050]  0 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880052]  1 90 4294896197
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880054]  8 81 4294896198
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880056] last result at 4294896198
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880057] last redo_fd_request at 4294896203
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880059] 20  1 
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880068] status=0
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880070] fdc_busy=1
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880071] do_floppy=e083a5b0
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880073] cont=e0841290
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880075] current_req=(null)
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880077] command_status=-1
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880078] 
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880082] floppy0: floppy timeout called
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880096] PM: resume of drv:floppy dev:floppy.0 complete after 2996.276 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880142] PM: resume of devices complete after 7908.423 msecs
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880292] PM: resume devices took 7.912 seconds
Aug  2 20:25:38 mja-desktop kernel: [ 4707.880333] Restarting tasks ... done.

```and the out put of dmesg =

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff72000 - 000000001ff93000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff93000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  modified: 000000001ff70000 - 000000001ff72000 (ACPI NVS)
[    0.000000]  modified: 000000001ff72000 - 000000001ff93000 (ACPI data)
[    0.000000]  modified: 000000001ff93000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 7000-c000
[    0.000000] RAMDISK: 1f7d7000 - 1ff5ff90
[    0.000000] ACPI: RSDP 000feba0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000fd192 00038 (v01 DELL    GX270   00000007 ASL  00000061)
[    0.000000] ACPI: FACP 000fd1ca 00074 (v01 DELL    GX270   00000007 ASL  00000061)
[    0.000000] ACPI: DSDT fffd2759 02795 (v01   DELL    dt_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 1ff70000 00040
[    0.000000] ACPI: SSDT fffd4eee 000A7 (v01   DELL    st_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: APIC 000fd23e 0006C (v01 DELL    GX270   00000007 ASL  00000061)
[    0.000000] ACPI: BOOT 000fd2aa 00028 (v01 DELL    GX270   00000007 ASL  00000061)
[    0.000000] ACPI: ASF! 000fd2d2 00067 (v16 DELL    GX270   00000007 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000]   node 0 low ram: 00000000 - 1ff70000
[    0.000000]   node 0 bootmap 00008000 - 0000bff0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ff70000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [001f7d7000 - 001ff5ff90]          RAMDISK ==> [001f7d7000 - 001ff5ff90]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008dc000 - 00008df18c]              BRK ==> [00008dc000 - 00008df18c]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  0x0001ff70 -> 0x0001ff70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130828
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129805
[    0.000000] Kernel command line: root=UUID=baf3a80c-4e26-4d98-83d6-305197df60c3 ro quiet splash 
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2618560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 499660k/523712k available (4679k kernel code, 23108k reserved, 2116k data, 660k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2793.451 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5586.90 BogoMIPS (lpj=11173804)
[    0.004028] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004063] Mount-cache hash table entries: 512
[    0.004228] Initializing cgroup subsys ns
[    0.004234] Initializing cgroup subsys cpuacct
[    0.004240] Initializing cgroup subsys memory
[    0.004249] Initializing cgroup subsys devices
[    0.004253] Initializing cgroup subsys freezer
[    0.004256] Initializing cgroup subsys net_cls
[    0.004283] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004288] CPU: L2 cache: 512K
[    0.004290] CPU: Hyper-Threading is disabled
[    0.004295] mce: CPU supports 4 MCE banks
[    0.004307] CPU0: Thermal monitoring enabled (TM1)
[    0.004318] Performance Events: no PMU driver, software events only.
[    0.004326] Checking 'hlt' instruction... OK.
[    0.020924] SMP alternatives: switching to UP code
[    0.031919] ACPI: Core revision 20090903
[    0.069603] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.069612] ftrace: allocating 21780 entries in 43 pages
[    0.072088] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.072387] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.113814] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[    0.116001] Brought up 1 CPUs
[    0.116001] Total of 1 processors activated (5586.90 BogoMIPS).
[    0.116001] CPU0 attaching NULL sched-domain.
[    0.116001] devtmpfs: initialized
[    0.116001] regulator: core version 0.5
[    0.116001] Time: 15:23:36  Date: 08/02/10
[    0.116001] NET: Registered protocol family 16
[    0.116001] EISA bus registered
[    0.116001] ACPI: bus type pci registered
[    0.116001] PCI: PCI BIOS revision 2.10 entry at 0xfbab0, last bus=2
[    0.116001] PCI: Using configuration type 1 for base access
[    0.116001] bio: create slab <bio-0> at 0
[    0.116001] ACPI: EC: Look up EC in DSDT
[    0.144101] ACPI: Interpreter enabled
[    0.144121] ACPI: (supports S0 S1 S3 S4 S5)
[    0.144149] ACPI: Using IOAPIC for interrupt routing
[    0.171980] ACPI: No dock devices found.
[    0.176107] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.176155] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.176167] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xc0000000-0xc7ffffff]
[    0.176272] pci 0000:00:06.0: reg 10 32bit mmio: [0xfecf0000-0xfecf0fff]
[    0.176370] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.176426] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.176481] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.176536] pci 0000:00:1d.3: reg 20 io port: [0xff20-0xff3f]
[    0.176599] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[    0.176659] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.176665] pci 0000:00:1d.7: PME# disabled
[    0.176754] pci 0000:00:1f.0: HPET at 0xfed00000
[    0.176761] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.176765] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.176791] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.176798] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.176806] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.176813] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.176820] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.176828] pci 0000:00:1f.1: reg 24 32bit mmio: [0xfebffc00-0xfebfffff]
[    0.176860] pci 0000:00:1f.2: reg 10 io port: [0xfe00-0xfe07]
[    0.176867] pci 0000:00:1f.2: reg 14 io port: [0xfe10-0xfe13]
[    0.176874] pci 0000:00:1f.2: reg 18 io port: [0xfe20-0xfe27]
[    0.176881] pci 0000:00:1f.2: reg 1c io port: [0xfe30-0xfe33]
[    0.176888] pci 0000:00:1f.2: reg 20 io port: [0xfea0-0xfeaf]
[    0.176941] pci 0000:00:1f.3: reg 20 io port: [0xeda0-0xedbf]
[    0.176991] pci 0000:00:1f.5: reg 10 io port: [0xee00-0xeeff]
[    0.176998] pci 0000:00:1f.5: reg 14 io port: [0xedc0-0xedff]
[    0.177006] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfebffa00-0xfebffbff]
[    0.177013] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfebff900-0xfebff9ff]
[    0.177044] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.177049] pci 0000:00:1f.5: PME# disabled
[    0.177092] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.177099] pci 0000:01:00.0: reg 14 io port: [0xde00-0xdeff]
[    0.177105] pci 0000:01:00.0: reg 18 32bit mmio: [0xfe9e0000-0xfe9effff]
[    0.177122] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfea00000-0xfea1ffff]
[    0.177144] pci 0000:01:00.0: supports D1 D2
[    0.177174] pci 0000:01:00.1: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.177180] pci 0000:01:00.1: reg 14 32bit mmio: [0xfe9f0000-0xfe9fffff]
[    0.177214] pci 0000:01:00.1: supports D1 D2
[    0.177258] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.177263] pci 0000:00:01.0: bridge 32bit mmio: [0xfe900000-0xfeafffff]
[    0.177268] pci 0000:00:01.0: bridge 32bit mmio pref: [0xc8000000-0xefffffff]
[    0.177329] pci 0000:02:0c.0: reg 10 32bit mmio: [0xfe8e0000-0xfe8fffff]
[    0.177342] pci 0000:02:0c.0: reg 18 io port: [0xcf40-0xcf7f]
[    0.177386] pci 0000:02:0c.0: PME# supported from D0 D3hot D3cold
[    0.177391] pci 0000:02:0c.0: PME# disabled
[    0.177424] pci 0000:00:1e.0: transparent bridge
[    0.177429] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.177434] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.177449] pci_bus 0000:00: on NUMA node 0
[    0.177455] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.177770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.296354] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.296668] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.296980] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.297291] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.297600] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.297912] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.298221] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.298534] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.298713] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.298717] vgaarb: loaded
[    0.298875] SCSI subsystem initialized
[    0.298958] libata version 3.00 loaded.
[    0.299047] usbcore: registered new interface driver usbfs
[    0.299063] usbcore: registered new interface driver hub
[    0.299092] usbcore: registered new device driver usb
[    0.299247] ACPI: WMI: Mapper loaded
[    0.299250] PCI: Using ACPI for IRQ routing
[    0.299420] NetLabel: Initializing
[    0.299423] NetLabel:  domain hash size = 128
[    0.299425] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.299441] NetLabel:  unlabeled traffic allowed by default
[    0.299569] hpet clockevent registered
[    0.299574] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.299580] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.299586] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.304025] Switching to clocksource tsc
[    0.306255] AppArmor: AppArmor Filesystem Enabled
[    0.306280] pnp: PnP ACPI init
[    0.306302] ACPI: bus type pnp registered
[    0.333968] pnp 00:0a: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.333974] pnp 00:0a: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.334669] pnp: PnP ACPI: found 11 devices
[    0.334672] ACPI: ACPI bus type pnp unregistered
[    0.334679] PnPBIOS: Disabled by ACPI PNP
[    0.334692] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.334697] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.334701] system 00:00: iomem range 0x1000000-0x1ff6ffff could not be reserved
[    0.334705] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
[    0.334709] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.334712] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.334716] system 00:00: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.334719] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
[    0.334723] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.334726] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    0.334738] system 00:0a: ioport range 0xc00-0xc7f has been reserved
[    0.369486] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.369490] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.369497] pci 0000:00:01.0:   MEM window: 0xfe900000-0xfeafffff
[    0.369502] pci 0000:00:01.0:   PREFETCH window: 0xc8000000-0xefffffff
[    0.369509] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.369513] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.369519] pci 0000:00:1e.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.369523] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.369541] pci 0000:00:1e.0: setting latency timer to 64
[    0.369547] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.369550] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.369553] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.369556] pci_bus 0000:01: resource 1 mem: [0xfe900000-0xfeafffff]
[    0.369560] pci_bus 0000:01: resource 2 pref mem [0xc8000000-0xefffffff]
[    0.369564] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.369567] pci_bus 0000:02: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.369570] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.369573] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.369618] NET: Registered protocol family 2
[    0.369732] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.370064] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.370136] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.370204] TCP: Hash tables configured (established 16384 bind 16384)
[    0.370207] TCP reno registered
[    0.370306] NET: Registered protocol family 1
[    0.370417] pci 0000:01:00.0: Boot video device
[    0.370519] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.370522] Simple Boot Flag at 0x7a set to 0x1
[    0.370623] cpufreq-nforce2: No nForce2 chipset.
[    0.370658] Scanning for low memory corruption every 60 seconds
[    0.370791] audit: initializing netlink socket (disabled)
[    0.370805] type=2000 audit(1280762616.367:1): initialized
[    0.379034] Trying to unpack rootfs image as initramfs...
[    0.388138] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.394091] VFS: Disk quotas dquot_6.5.2
[    0.394166] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.394888] fuse init (API version 7.13)
[    0.394993] msgmni has been set to 976
[    0.400217] alg: No test for stdrng (krng)
[    0.400331] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.400335] io scheduler noop registered
[    0.400337] io scheduler anticipatory registered
[    0.400339] io scheduler deadline registered
[    0.400396] io scheduler cfq registered (default)
[    0.400534] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.400562] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.400668] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.400678] ACPI: Power Button [VBTN]
[    0.400740] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.400744] ACPI: Power Button [PWRF]
[    0.400974] processor LNXCPU:00: registered as cooling_device0
[    0.438589] isapnp: Scanning for PnP cards...
[    0.444325] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.444426] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.444840] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.446073] brd: module loaded
[    0.446637] loop: module loaded
[    0.446754] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.446878] ata_piix 0000:00:1f.1: version 2.13
[    0.446896]   alloc irq_desc for 18 on node -1
[    0.446899]   alloc kstat_irqs on node -1
[    0.446907] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.446959] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.452042] scsi0 : ata_piix
[    0.452207] scsi1 : ata_piix
[    0.452250] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.452254] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.452301] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.452308] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.452358] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.452441] scsi2 : ata_piix
[    0.452538] ata1: port disabled. ignoring.
[    0.500241] scsi3 : ata_piix
[    0.500316] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 18
[    0.500320] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 18
[    0.500754] Fixed MDIO Bus: probed
[    0.500797] PPP generic driver version 2.4.2
[    0.500882] tun: Universal TUN/TAP device driver, 1.6
[    0.500885] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.500998] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.501027]   alloc irq_desc for 23 on node -1
[    0.501030]   alloc kstat_irqs on node -1
[    0.501039] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.501059] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.501063] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.501114] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.501147] ehci_hcd 0000:00:1d.7: debug port 1
[    0.505041] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.505393] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[    0.524339] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.524505] usb usb1: configuration #1 chosen from 1 choice
[    0.524544] hub 1-0:1.0: USB hub found
[    0.524557] hub 1-0:1.0: 8 ports detected
[    0.524646] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.524667] uhci_hcd: USB Universal Host Controller Interface driver
[    0.524725]   alloc irq_desc for 16 on node -1
[    0.524728]   alloc kstat_irqs on node -1
[    0.524737] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.524749] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.524753] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.524805] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.524842] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    0.524949] usb usb2: configuration #1 chosen from 1 choice
[    0.524982] hub 2-0:1.0: USB hub found
[    0.524992] hub 2-0:1.0: 2 ports detected
[    0.525047]   alloc irq_desc for 19 on node -1
[    0.525050]   alloc kstat_irqs on node -1
[    0.525056] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.525064] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.525067] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.525111] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.525140] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    0.525239] usb usb3: configuration #1 chosen from 1 choice
[    0.525273] hub 3-0:1.0: USB hub found
[    0.525283] hub 3-0:1.0: 2 ports detected
[    0.525334] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.525341] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.525345] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.525383] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.525406] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.525510] usb usb4: configuration #1 chosen from 1 choice
[    0.525545] hub 4-0:1.0: USB hub found
[    0.525555] hub 4-0:1.0: 2 ports detected
[    0.525606] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.525613] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.525616] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.525655] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.525678] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[    0.525783] usb usb5: configuration #1 chosen from 1 choice
[    0.525815] hub 5-0:1.0: USB hub found
[    0.525825] hub 5-0:1.0: 2 ports detected
[    0.525931] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[    0.525934] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.526611] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.526756] mice: PS/2 mouse device common for all mice
[    0.526903] rtc_cmos 00:05: RTC can wake from S4
[    0.526954] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.526982] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    0.527121] device-mapper: uevent: version 1.0.3
[    0.532291] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.532383] device-mapper: multipath: version 1.1.0 loaded
[    0.532386] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.532541] EISA: Probing bus 0 at eisa.0
[    0.532580] EISA: Detected 0 cards.
[    0.536242] cpuidle: using governor ladder
[    0.536247] cpuidle: using governor menu
[    0.536898] TCP cubic registered
[    0.537053] NET: Registered protocol family 10
[    0.537618] lo: Disabled Privacy Extensions
[    0.538005] NET: Registered protocol family 17
[    0.538075] Using IPI No-Shortcut mode
[    0.538196] PM: Resume from disk failed.
[    0.538210] registered taskstats version 1
[    0.538484]   Magic number: 6:574:385
[    0.538494] usb usb3: hash matches
[    0.538527] thermal cooling_device0: hash matches
[    0.538572] rtc_cmos 00:05: setting system clock to 2010-08-02 15:23:37 UTC (1280762617)
[    0.538576] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.538578] EDD information not available.
[    0.608894] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.696995] ata3.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
[    0.697000] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.697107] ata4.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
[    0.697110] ata4.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.697547] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-252S, R901, max UDMA/33
[    0.697591] ata2.01: ATAPI: HL-DT-STDVDRRW GCA-4164B, H.I0, max UDMA/33
[    0.704515] ata4.00: configured for UDMA/100
[    0.704576] ata3.00: configured for UDMA/100
[    0.712168] ata2.00: configured for UDMA/33
[    0.728341] ata2.01: configured for UDMA/33
[    0.888132] Freeing initrd memory: 7715k freed
[    1.026332] isapnp: No Plug & Play device found
[    1.027365] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-252S  R901 PQ: 0 ANSI: 5
[    1.031319] sr0: scsi3-mmc drive: 48x/16x writer cd/rw xa/form2 cdda tray
[    1.031324] Uniform CD-ROM driver Revision: 3.20
[    1.031462] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.031554] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.033136] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRRW GCA-4164B H.I0 PQ: 0 ANSI: 5
[    1.038235] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.038341] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.038405] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    1.038539] scsi 2:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
[    1.038686] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.038823] scsi 3:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
[    1.038960] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.039043] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.039090] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.039159] sd 3:0:0:0: [sdb] Write Protect is off
[    1.039163] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.039204] sd 2:0:0:0: [sda] Write Protect is off
[    1.039209] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.039225] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.039306] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.039543]  sdb:
[    1.039638]  sda: sdb1 sdb2 < sda1
[    1.061879] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.079910] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.083431]  sdb5 >
[    1.083752] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.083769] Freeing unused kernel memory: 660k freed
[    1.084415] Write protecting the kernel text: 4680k
[    1.084444] Write protecting the kernel read-only data: 1840k
[    1.109349] udev: starting version 151
[    1.257124] usb 3-2: configuration #1 chosen from 1 choice
[    1.363418] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
[    1.363424] Copyright (c) 1999-2006 Intel Corporation.
[    1.363473] e1000 0000:02:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.371077] Floppy drive(s): fd0 is 1.44M
[    1.377891] usbcore: registered new interface driver hiddev
[    1.386232] FDC 0 is a post-1991 82077
[    1.634786] e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0f:1f:74:e1:be
[    1.635743] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    1.636049] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
[    1.636086] usbcore: registered new interface driver usbhid
[    1.636220] usbhid: v2.6:USB HID core driver
[    1.673557] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    1.728943] kjournald starting.  Commit interval 5 seconds
[    1.728959] EXT3-fs: mounted filesystem with ordered data mode.
[   10.451802] Adding 1510068k swap on /dev/sdb5.  Priority:-1 extents:1 across:1510068k 
[   10.525045] udev: starting version 151
[   10.644719] EXT3 FS on sda1, internal journal
[   10.678033] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.727962] lp: driver loaded but no devices found
[   10.826534] Linux agpgart interface v0.103
[   10.884110] intel_rng: FWH not detected
[   10.973247] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   11.004053] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.005843] parport_pc 00:09: reported by Plug and Play ACPI
[   11.005895] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   11.108237] lp0: using parport0 (interrupt-driven).
[   11.140192] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xc0000000
[   11.213691] dell-wmi: No known WMI GUID found
[   11.225481] [drm] Initialized drm 1.1.0 20060810
[   11.247163] ppdev: user-space parallel port driver
[   11.251625] type=1505 audit(1280762628.209:2):  operation="profile_load" pid=488 name="/sbin/dhclient3"
[   11.252225] type=1505 audit(1280762628.213:3):  operation="profile_load" pid=488 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.252521] type=1505 audit(1280762628.213:4):  operation="profile_load" pid=488 name="/usr/lib/connman/scripts/dhclient-script"
[   11.459585] [drm] radeon defaulting to kernel modesetting.
[   11.459591] [drm] radeon kernel modesetting enabled.
[   11.459652] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.463942] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.464400] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   11.464561] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   11.477034] [drm] radeon: Initializing kernel modesetting.
[   11.479107] [drm] register mmio base: 0xFE9E0000
[   11.479111] [drm] register mmio size: 65536
[   11.479372] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   11.479399] [drm] Generation 2 PCI interface, using max accessible memory
[   11.479409] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   11.479430] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   11.479469] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[   11.479487] [drm] radeon: VRAM 128M
[   11.479490] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   11.479492] [drm] radeon: GTT 128M
[   11.479494] [drm] radeon: GTT from 0xC0000000 to 0xC7FFFFFF
[   11.479516] [drm] radeon: irq initialized.
[   11.479624] [drm] Detected VRAM RAM=128M, BAR=256M
[   11.479628] [drm] RAM width 64bits DDR
[   11.481887] [TTM] Zone  kernel: Available graphics memory: 254288 kiB.
[   11.481912] [drm] radeon: 128M of VRAM memory ready
[   11.481915] [drm] radeon: 128M of GTT memory ready.
[   11.482151] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   11.482163] [drm] radeon: cp idle (0x10000C03)
[   11.482283] [drm] Loading R300 Microcode
[   11.482651] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   11.503845] [drm] radeon: ring at 0x00000000C0000000
[   11.503868] [drm] ring test succeeded in 1 usecs
[   11.521026] [drm] radeon: ib pool ready.
[   11.521123] [drm] ib test succeeded in 0 usecs
[   11.522387] [drm] Default TV standard: PAL
[   11.522392] [drm] 27.000000000 MHz TV ref clk
[   11.522396] [drm] DFP table revision: 3
[   11.523473] [drm] Default TV standard: PAL
[   11.523478] [drm] 27.000000000 MHz TV ref clk
[   11.524274] [drm] Radeon Display Connectors
[   11.524278] [drm] Connector 0:
[   11.524280] [drm]   VGA
[   11.524284] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   11.524286] [drm]   Encoders:
[   11.524288] [drm]     CRT1: INTERNAL_DAC1
[   11.524290] [drm] Connector 1:
[   11.524292] [drm]   DVI-I
[   11.524294] [drm]   HPD1
[   11.524297] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   11.524299] [drm]   Encoders:
[   11.524301] [drm]     CRT2: INTERNAL_DAC2
[   11.524303] [drm]     DFP1: INTERNAL_TMDS1
[   11.524305] [drm] Connector 2:
[   11.524307] [drm]   S-video
[   11.524309] [drm]   Encoders:
[   11.524311] [drm]     TV1: INTERNAL_DAC2
[   11.702040] type=1505 audit(1280762628.661:5):  operation="profile_load" pid=637 name="/usr/share/gdm/guest-session/Xsession"
[   11.706695] type=1505 audit(1280762628.665:6):  operation="profile_replace" pid=640 name="/sbin/dhclient3"
[   11.707266] type=1505 audit(1280762628.665:7):  operation="profile_replace" pid=640 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.707574] type=1505 audit(1280762628.665:8):  operation="profile_replace" pid=640 name="/usr/lib/connman/scripts/dhclient-script"
[   11.762096] type=1505 audit(1280762628.721:9):  operation="profile_load" pid=642 name="/usr/bin/evince"
[   11.815176] type=1505 audit(1280762628.773:10):  operation="profile_load" pid=642 name="/usr/bin/evince-previewer"
[   11.850557] type=1505 audit(1280762628.809:11):  operation="profile_load" pid=642 name="/usr/bin/evince-thumbnailer"
[   11.973189]   alloc irq_desc for 17 on node -1
[   11.973194]   alloc kstat_irqs on node -1
[   11.973204] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.973242] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   12.084022] [drm] fb mappable at 0xE0040000
[   12.084026] [drm] vram apper at 0xE0000000
[   12.084029] [drm] size 5242880
[   12.084031] [drm] fb depth is 24
[   12.084033] [drm]    pitch is 5120
[   12.092906] fb0: radeondrmfb frame buffer device
[   12.092910] registered panic notifier
[   12.092919] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   12.101964] vga16fb: initializing
[   12.101973] vga16fb: mapped to 0xc00a0000
[   12.101978] vga16fb: not registering due to another framebuffer present
[   12.272760] Console: switching to colour frame buffer device 160x64
[   12.408057] intel8x0_measure_ac97_clock: measured 54328 usecs (2618 samples)
[   12.408062] intel8x0: clocking to 48000
[   12.430685] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   12.430690] apm: overridden by ACPI.
[   21.772010] eth0: no IPv6 routers present
[ 4697.264259] PM: Syncing filesystems ... done.
[ 4697.280047] PM: Preparing system for mem sleep
[ 4697.280052] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 4697.284127] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 4697.284246] PM: Entering mem sleep
[ 4697.284263] Suspending console(s) (use no_console_suspend to debug)
[ 4697.304026] sd 3:0:0:0: [sdb] Synchronizing SCSI cache
[ 4697.304133] sd 3:0:0:0: [sdb] Stopping disk
[ 4697.304271] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 4697.326036] sd 2:0:0:0: [sda] Stopping disk
[ 4697.430726] PM: suspend of drv:sd dev:2:0:0:0 complete after 126.454 msecs
[ 4697.996011] PM: suspend of drv:atkbd dev:serio0 complete after 565.235 msecs
[ 4697.996835] parport_pc 00:09: disabled
[ 4697.997264] serial 00:08: disabled
[ 4698.046003] e1000 0000:02:0c.0: PCI INT A disabled
[ 4698.046011] e1000 0000:02:0c.0: PME# enabled
[ 4698.046025] pci 0000:00:1e.0: wake-up capability enabled by ACPI
[ 4699.932423] radeon 0000:01:00.0: PCI INT A disabled
[ 4699.948022] PM: suspend of drv:radeon dev:0000:01:00.0 complete after 1888.001 msecs
[ 4699.948213] Intel ICH 0000:00:1f.5: PCI INT B disabled
[ 4699.948339] ata_piix 0000:00:1f.2: PCI INT A disabled
[ 4699.948375] ata1: port disabled. ignoring.
[ 4699.948451] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 4699.948463] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[ 4699.948471] uhci_hcd 0000:00:1d.3: PCI INT A disabled
[ 4699.948478] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 4699.948485] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 4699.948492] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 4699.948650] PM: suspend of devices complete after 2664.220 msecs
[ 4699.948654] PM: suspend devices took 2.664 seconds
[ 4699.964172] PM: late suspend of devices complete after 15.513 msecs
[ 4699.964277] ACPI: Preparing to enter system sleep state S3
[ 4699.965049] Disabling non-boot CPUs ...
[ 4699.965071] Back to C!
[ 4699.965071] CPU0: Thermal monitoring enabled (TM1)
[ 4699.965071] ACPI: Waking up from system sleep state S3
[ 4699.970959] agpgart-intel 0000:00:00.0: restoring config space at offset 0x1 (was 0x900006, writing 0x20900106)
[ 4699.970983] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2a0d0d0, writing 0x22a0d0d0)
[ 4699.970991] pci 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x14000)
[ 4699.971004] pci 0000:00:06.0: restoring config space at offset 0xf (was 0xffffffff, writing 0x0)
[ 4699.971009] pci 0000:00:06.0: restoring config space at offset 0xe (was 0xffffffff, writing 0x0)
[ 4699.971014] pci 0000:00:06.0: restoring config space at offset 0xd (was 0xffffffff, writing 0x0)
[ 4699.971019] pci 0000:00:06.0: restoring config space at offset 0xc (was 0xffffffff, writing 0x0)
[ 4699.971024] pci 0000:00:06.0: restoring config space at offset 0xb (was 0xffffffff, writing 0x0)
[ 4699.971029] pci 0000:00:06.0: restoring config space at offset 0xa (was 0xffffffff, writing 0x0)
[ 4699.971034] pci 0000:00:06.0: restoring config space at offset 0x9 (was 0xffffffff, writing 0x0)
[ 4699.971039] pci 0000:00:06.0: restoring config space at offset 0x8 (was 0xffffffff, writing 0x0)
[ 4699.971045] pci 0000:00:06.0: restoring config space at offset 0x7 (was 0xffffffff, writing 0x0)
[ 4699.971050] pci 0000:00:06.0: restoring config space at offset 0x6 (was 0xffffffff, writing 0x0)
[ 4699.971055] pci 0000:00:06.0: restoring config space at offset 0x5 (was 0xffffffff, writing 0x0)
[ 4699.971060] pci 0000:00:06.0: restoring config space at offset 0x4 (was 0xffffffff, writing 0xfecf0000)
[ 4699.971065] pci 0000:00:06.0: restoring config space at offset 0x3 (was 0xffffffff, writing 0x0)
[ 4699.971070] pci 0000:00:06.0: restoring config space at offset 0x2 (was 0xffffffff, writing 0x8800002)
[ 4699.971076] pci 0000:00:06.0: restoring config space at offset 0x1 (was 0xffffffff, writing 0x800002)
[ 4699.971081] pci 0000:00:06.0: restoring config space at offset 0x0 (was 0xffffffff, writing 0x25768086)
[ 4699.971093] uhci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 4699.971114] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 4699.971125] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 4699.971145] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 4699.971156] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
[ 4699.971177] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 4699.971187] uhci_hcd 0000:00:1d.3: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 4699.971208] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 4699.971227] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x400, writing 0x405)
[ 4699.971246] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x0, writing 0xffa80800)
[ 4699.971254] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[ 4699.971272] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0x20000)
[ 4699.971284] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xfe80fe80)
[ 4699.971289] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x228000f0, writing 0x280c0c0)
[ 4699.971295] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x20200, writing 0x20020200)
[ 4699.971305] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x800005, writing 0x800107)
[ 4699.971331] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x280000f, writing 0x280010f)
[ 4699.971341] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x109)
[ 4699.971352] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0xfebffc00)
[ 4699.971371] ata_piix 0000:00:1f.2: restoring config space at offset 0xf (was 0x100, writing 0x109)
[ 4699.971394] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x203)
[ 4699.971407] pci 0000:00:1f.3: restoring config space at offset 0x8 (was 0x8c1, writing 0xeda1)
[ 4699.971429] Intel ICH 0000:00:1f.5: restoring config space at offset 0xf (was 0x200, writing 0x203)
[ 4699.971441] Intel ICH 0000:00:1f.5: restoring config space at offset 0x7 (was 0x0, writing 0xfebff900)
[ 4699.971446] Intel ICH 0000:00:1f.5: restoring config space at offset 0x6 (was 0x0, writing 0xfebffa00)
[ 4699.971451] Intel ICH 0000:00:1f.5: restoring config space at offset 0x5 (was 0x1, writing 0xedc1)
[ 4699.971456] Intel ICH 0000:00:1f.5: restoring config space at offset 0x4 (was 0x1, writing 0xee01)
[ 4699.971463] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900003)
[ 4699.971482] radeon 0000:01:00.0: restoring config space at offset 0xf (was 0x801ff, writing 0x8010b)
[ 4699.971488] radeon 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfea00000)
[ 4699.971498] radeon 0000:01:00.0: restoring config space at offset 0x6 (was 0x0, writing 0xfe9e0000)
[ 4699.971502] radeon 0000:01:00.0: restoring config space at offset 0x5 (was 0x1, writing 0xde01)
[ 4699.971507] radeon 0000:01:00.0: restoring config space at offset 0x4 (was 0x8, writing 0xe0000008)
[ 4699.971512] radeon 0000:01:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 4699.971518] radeon 0000:01:00.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00107)
[ 4699.971544] pci 0000:01:00.1: restoring config space at offset 0x5 (was 0x0, writing 0xfe9f0000)
[ 4699.971548] pci 0000:01:00.1: restoring config space at offset 0x4 (was 0x8, writing 0xd0000008)
[ 4699.971553] pci 0000:01:00.1: restoring config space at offset 0x3 (was 0x0, writing 0x4010)
[ 4699.971559] pci 0000:01:00.1: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00007)
[ 4699.971580] e1000 0000:02:0c.0: restoring config space at offset 0xf (was 0xff0100, writing 0xff0109)
[ 4699.971594] e1000 0000:02:0c.0: restoring config space at offset 0x6 (was 0x1, writing 0xcf41)
[ 4699.971601] e1000 0000:02:0c.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe8e0000)
[ 4699.971606] e1000 0000:02:0c.0: restoring config space at offset 0x3 (was 0x0, writing 0x4010)
[ 4699.971612] e1000 0000:02:0c.0: restoring config space at offset 0x1 (was 0x2300000, writing 0x2300117)
[ 4699.971683] PM: early resume of devices complete after 0.759 msecs
[ 4699.971883] pm_op(): pci_pm_resume+0x0/0xa0 returns -16
[ 4699.971886] PM: Device 0000:00:00.0 failed to resume: error -16
[ 4699.971903] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4699.971909] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 4699.971929] usb usb2: root hub lost power or was reset
[ 4699.971947] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4699.971953] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 4699.971971] usb usb3: root hub lost power or was reset
[ 4699.972011] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 4699.972018] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 4699.972036] usb usb4: root hub lost power or was reset
[ 4699.972052] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4699.972058] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 4699.972076] usb usb5: root hub lost power or was reset
[ 4699.972091] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[ 4699.972098] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 4699.972110] pci 0000:00:1e.0: setting latency timer to 64
[ 4699.972119] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 4699.972124] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 4699.972176] ata1: port disabled. ignoring.
[ 4699.972296] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 4699.972302] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 4699.972339] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 4699.972345] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 4699.981883] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4699.981891] [drm] AGP mode requested: 8
[ 4699.981894] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[ 4699.981911] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[ 4699.981951] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[ 4699.982175] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[ 4700.086568] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[ 4700.086572] [drm] radeon: cp idle (0x10000C03)
[ 4700.086611] [drm] radeon: ring at 0x00000000C0000000
[ 4700.086645] [drm] ring test succeeded in 1 usecs
[ 4700.086656] [drm] ib test succeeded in 0 usecs
[ 4700.143005] PM: resume of drv:radeon dev:0000:01:00.0 complete after 161.126 msecs
[ 4700.143020] e1000 0000:02:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 4700.143038] pci 0000:00:1e.0: wake-up capability disabled by ACPI
[ 4700.143043] e1000 0000:02:0c.0: PME# disabled
[ 4700.177113] serial 00:08: activated
[ 4700.182310] parport_pc 00:09: activated
[ 4700.204199] ata2.00: configured for UDMA/33
[ 4700.220277] ata2.01: configured for UDMA/33
[ 4700.480012] PM: resume of drv:usb dev:usb3 complete after 247.968 msecs
[ 4700.480292] sd 2:0:0:0: [sda] Starting disk
[ 4701.864367] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4704.184252] ata3.00: configured for UDMA/100
[ 4704.198002] PM: resume of drv:sd dev:2:0:0:0 complete after 3717.710 msecs
[ 4704.198011] sd 3:0:0:0: [sdb] Starting disk
[ 4704.296252] ata4.00: configured for UDMA/100
[ 4704.316850] PM: resume of drv:sd dev:3:0:0:0 complete after 118.839 msecs
[ 4704.576012] usb 3-2: reset low speed USB device using uhci_hcd and address 2
[ 4704.883811] PM: resume of drv:usb dev:3-2 complete after 566.949 msecs
[ 4707.880005] 
[ 4707.880007] floppy driver state
[ 4707.880008] -------------------
[ 4707.880012] now=1101970 last interrupt=4294896198 diff=1173068 last called handler=e083f2a0
[ 4707.880014] timeout_message=lock fdc
[ 4707.880016] last output bytes:
[ 4707.880018]  8 80 4294892642
[ 4707.880020]  8 80 4294892642
[ 4707.880022]  8 80 4294892642
[ 4707.880024]  8 80 4294892642
[ 4707.880026] 12 80 4294896197
[ 4707.880027]  0 90 4294896197
[ 4707.880029] 13 90 4294896197
[ 4707.880031]  0 90 4294896197
[ 4707.880033] 1a 90 4294896197
[ 4707.880035]  0 90 4294896197
[ 4707.880037]  3 80 4294896197
[ 4707.880039] c1 90 4294896197
[ 4707.880041] 10 90 4294896197
[ 4707.880043]  7 80 4294896197
[ 4707.880044]  0 90 4294896197
[ 4707.880046]  8 81 4294896197
[ 4707.880048]  f 80 4294896197
[ 4707.880050]  0 90 4294896197
[ 4707.880052]  1 90 4294896197
[ 4707.880054]  8 81 4294896198
[ 4707.880056] last result at 4294896198
[ 4707.880057] last redo_fd_request at 4294896203
[ 4707.880059] 20  1 
[ 4707.880068] status=0
[ 4707.880070] fdc_busy=1
[ 4707.880071] do_floppy=e083a5b0
[ 4707.880073] cont=e0841290
[ 4707.880075] current_req=(null)
[ 4707.880077] command_status=-1
[ 4707.880078] 
[ 4707.880082] floppy0: floppy timeout called
[ 4707.880096] PM: resume of drv:floppy dev:floppy.0 complete after 2996.276 msecs
[ 4707.880142] PM: resume of devices complete after 7908.423 msecs
[ 4707.880292] PM: resume devices took 7.912 seconds
[ 4707.880331] PM: Finishing wakeup.
[ 4707.880333] Restarting tasks ... done.

```I hope this helps! kind regards,

Maarten

---

### Post by Iowan on 2010-08-02
> **Hetepeperfan said:**
> 
```
ipconfig eth0 inet 192.168.1.123
```**sudo ifconfig eth0 inet 192.168.1.123** might work better. ;)
The "Never used" message is common - my system displays that whilst connected.
Remember to hit [ENTER] after adding gateway - otherwise it doesn't take (but *looks* like it did...).

---

### Post by Hetepeperfan on 2010-08-02
> **Iowan said:**
> **sudo ifconfig eth0 inet 192.168.1.123** might work better. ;)
The "Never used" message is common - my system displays that whilst connected.
Remember to hit [ENTER] after adding gateway - otherwise it doesn't take (but *looks* like it did...).

Dear Iowan,

I've experienced first hand that I need to run the ifconfig and route utilities as **su**. But that is not my problem, I want to save the settings. If i use the ifconfig and route utils, than these utilities help me for the current session. Thus if I reboot I need to run these CLI instructions in order to get my connection. So far so good, but I would really like that these settings are saved; used for the next session.
Therefore I tried to use the gnome-network-connections menu. However if I use it ifconfig will not echo the inet line (IPv4) but does echo the inet6 line. Therfore, I really feel that I'm not able to save network settings with the gnome System->preferences->network connections menu. If I open the menu and edit 'auto eth0' I see the picture attached to this post which shows the correct parameters.

I hope you can help me!

Best, Maarten

---

