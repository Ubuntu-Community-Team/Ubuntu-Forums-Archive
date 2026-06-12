---
title: "Two ubuntu machines + crossover cable"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by andydrizen on 2009-06-01
Hi all, 

I'm finding it much tougher than I think it should be to connect two ubuntu machines via a crossover cable. Both machines have Jaunty on them although the desktop environment has been removed on one of them. They are connected by ethernet cable. The setup is this:

One machine (the server) is connected to the internet via eth0 and my client PC via eth1.

The client pc only has the one connection to the server (via eth0).

I just want to be able to SSH between them. I tried this:

On the Client
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up 10.0.0.2

```

On the Server
```
sudo ifconfig eth1 down
sudo ifconfig eth1 up 10.0.0.1

```

but when I try to ping, it tells me that the network is unreachable.

Any help would be great,
Thanks
Andy

---

### Post by madverb on 2009-06-01
Have you tried setting the IP in the config file?

---

### Post by andydrizen on 2009-06-01
I tried following [this guide ]("http://www.ax697.org/sharing-internet-connection-with-a-crossover-cable-2008238.html") but it didn't work for me... Incidentally, I can use ethtool to wake my client computer up from the server... so the cable is definitely working and able to transmit..

---

### Post by andydrizen on 2009-06-01
I've also just tried following [this guide]("http://ubuntuforums.org/archive/index.php/t-112713.html") which didn't work either... I can't think how to fix this : (((

---

### Post by puppywhacker on 2009-06-01
troubleshooting! =) Beware that ping runs over ICMP and has as sole purpose to check if a host is responding, but hosts can disable ICMP as well.

first check the ethernet link parameters , they are negotiated and can be changed
```
sudo mii-tool
```

check if arp resolving is working properly (IP address to MAC address mapping)
```
arp -a
```

check on both machines what iptable rules are active
```
sudo iptables -L -v
```

check if the Tx and Rx counters are increasing
```
ifconfig
```

run tcpdump to see if packets are being on the link
```
tcpdump -i eth0 
```

anything in the kernel log
```
dmesg
tail -50 /var/log/messages
```

check if there are ports actually listening on the server
```
netstat -na | grep LIST | grep '*'
```

---

### Post by superprash2003 on 2009-06-01
on the client machine set the gateway ip to the ip of the server. do you have other interfaces running?

---

### Post by andydrizen on 2009-06-01
Hi, thanks for taking the time to help :)


Here are the results for the server

```
sudo mii-tool
```

```
andy@server:~$ sudo mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not supported
eth1: negotiated 1000baseT-FD flow-control, link ok
```

```
arp -a
```

```
andy@server:~$ sudo arp -a
lappy.local (192.168.1.102) at 00:04:23:93:1d:45 [ether] on eth0
lappy.local (192.168.1.102) at 00:04:23:93:1d:45 [ether] on eth0[CODE]

Note that "lappy" is an indifferent, not either the server nor the PC.

[CODE]sudo iptables -L -v
```

```
andy@server:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
```

```
ifconfig
```

```
andy@server:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:2d:bf:42:99  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:febf:4299/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:165156 (165.1 KB)  TX bytes:236333 (236.3 KB)
          Interrupt:3 Base address:0x100 

eth1      Link encap:Ethernet  HWaddr 00:11:50:e7:bc:7f  
          inet addr:10.0.1.1  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fee7:bc7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10836 (10.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

run tcpdump to see if packets are being on the link
```
tcpdump -i eth0 
```

```
andy@server:~$ sudo tcpdump -i eth1
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
17:14:21.890154 IP server.local.netbios-dgm > 10.0.1.255.netbios-dgm: NBT UDP PACKET(138)
17:14:21.890271 IP server.local.netbios-dgm > 10.0.1.255.netbios-dgm: NBT UDP PACKET(138)
17:14:22.021206 IP server.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.0.10.in-addr.arpa. (41)
17:14:23.022828 IP server.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.0.10.in-addr.arpa. (41)
17:14:25.025458 IP server.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.0.10.in-addr.arpa. (41)
17:14:27.051629 IP server.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.1.0.10.in-addr.arpa. (39)
17:14:27.052255 IP server.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 (Cache flush) PTR[|domain]
17:14:27.173445 IP server.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
17:14:28.174399 IP server.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
17:14:30.176153 IP server.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)

```

```
dmesg
tail -50 /var/log/messages
```

```

andy@lappy:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004ffca000 (usable)
[    0.000000]  BIOS-e820: 000000004ffca000 - 000000004ffd0000 (reserved)
[    0.000000]  BIOS-e820: 000000004ffd0000 - 000000004ffe0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004ffe0000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x4ffca max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  modified: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  modified: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000004ffca000 (usable)
[    0.000000]  modified: 000000004ffca000 - 000000004ffd0000 (reserved)
[    0.000000]  modified: 000000004ffd0000 - 000000004ffe0000 (ACPI data)
[    0.000000]  modified: 000000004ffe0000 - 0000000050000000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  modified: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378cf000 - 37fef1c4
[    0.000000] Allocated new RAMDISK: 00881000 - 00fa11c4
[    0.000000] Move RAMDISK from 00000000378cf000 - 0000000037fef1c3 to 00881000 - 00fa11c3
[    0.000000] ACPI: RSDP 000F01E0, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 4FFD0000, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: FACP 4FFD005C, 0084 (r2 TOSHIB 750      20030101 TASM  4010000)
[    0.000000] ACPI: DSDT 4FFD0114, 5266 (r1 TOSHIB R100     20030313 MSFT  100000E)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: SSDT 4FFD537A, 0231 (r1 TOSHIB R100     20030220 MSFT  100000E)
[    0.000000] ACPI: DBGP 4FFD00E0, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: BOOT 4FFD0034, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] 395MB HIGHMEM available.
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
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fa11c4]      NEW RAMDISK ==> [0000881000 - 0000fa11c4]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0004ffca
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0004ffca
[    0.000000] On node 0 totalpages: 327503
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 792 pages used for memmap
[    0.000000]   HighMem zone: 100532 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000ee000
[    0.000000] PM: Registered nosave memory: 00000000000ee000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aeda0000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324943
[    0.000000] Kernel command line: root=UUID=8d7fa741-5972-46c1-946f-fb5e4ac6a854 ro quiet splash vga=0x318 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 997.478 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 6552520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1276648k/1310504k available (4126k kernel code, 32524k reserved, 2208k data, 532k init, 405296k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 1994.95 BogoMIPS (lpj=3989912)
[    0.004059] Security Framework initialized
[    0.004080] SELinux:  Disabled at boot.
[    0.004123] AppArmor: AppArmor initialized
[    0.004139] Mount-cache hash table entries: 512
[    0.004403] Initializing cgroup subsys ns
[    0.004412] Initializing cgroup subsys cpuacct
[    0.004416] Initializing cgroup subsys memory
[    0.004424] Initializing cgroup subsys freezer
[    0.004453] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004459] CPU: L2 cache: 1024K
[    0.004486] Checking 'hlt' instruction... OK.
[    0.021182] SMP alternatives: switching to UP code
[    0.208770] Freeing SMP alternatives: 18k freed
[    0.208777] ACPI: Core revision 20080926
[    0.212216] ACPI: Checking initramfs for custom DSDT
[    0.800597] ACPI: setting ELCR to 0200 (from 0a00)
[    0.801132] weird, boot CPU (#0) not listedby the BIOS.
[    0.801136] SMP motherboard not detected.
[    0.801141] Local APIC not detected. Using dummy APIC emulation.
[    0.801145] SMP disabled
[    0.801556] Brought up 1 CPUs
[    0.801560] Total of 1 processors activated (1994.95 BogoMIPS).
[    0.801580] CPU0 attaching NULL sched-domain.
[    0.801965] net_namespace: 776 bytes
[    0.801981] Booting paravirtualized kernel on bare hardware
[    0.802492] Time:  9:18:09  Date: 06/01/09
[    0.802500] regulator: core version 0.5
[    0.802551] NET: Registered protocol family 16
[    0.802770] EISA bus registered
[    0.802794] ACPI: bus type pci registered
[    0.803090] PCI: PCI BIOS revision 2.10 entry at 0xfd81a, last bus=4
[    0.803094] PCI: Using configuration type 1 for base access
[    0.806196] ACPI: EC: Look up EC in DSDT
[    0.810134] ACPI Warning (dsobject-0501): Package List length (10) larger than NumElements count (4), truncated
[    0.810142]  [20080926]
[    0.813148] ACPI: Interpreter enabled
[    0.813155] ACPI: (supports S0 S3 S4 S5)
[    0.813187] ACPI: Using PIC for interrupt routing
[    0.823375] ACPI: No dock devices found.
[    0.823395] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.823464] pci 0000:00:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.823590] pci 0000:00:1d.0: reg 20 io port: [0xefe0-0xefff]
[    0.823650] pci 0000:00:1d.1: reg 20 io port: [0xef80-0xef9f]
[    0.823718] pci 0000:00:1d.7: reg 10 32bit mmio: [0x000000-0x0003ff]
[    0.823767] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.823774] pci 0000:00:1d.7: PME# disabled
[    0.823869] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.823879] pci 0000:00:1f.0: quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
[    0.823885] pci 0000:00:1f.0: quirk: region eec0-eeff claimed by ICH4 GPIO
[    0.823911] pci 0000:00:1f.1: reg 10 io port: [0xbff8-0xbfff]
[    0.823920] pci 0000:00:1f.1: reg 14 io port: [0xbff4-0xbff7]
[    0.823930] pci 0000:00:1f.1: reg 18 io port: [0xbfe8-0xbfef]
[    0.823939] pci 0000:00:1f.1: reg 1c io port: [0xbfe4-0xbfe7]
[    0.823949] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.823958] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.824019] pci 0000:00:1f.5: reg 10 io port: [0x00-0xff]
[    0.824028] pci 0000:00:1f.5: reg 14 io port: [0x00-0x3f]
[    0.824037] pci 0000:00:1f.5: reg 18 32bit mmio: [0x000000-0x0001ff]
[    0.824046] pci 0000:00:1f.5: reg 1c 32bit mmio: [0x000000-0x0000ff]
[    0.824072] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.824079] pci 0000:00:1f.5: PME# disabled
[    0.824113] pci 0000:00:1f.6: reg 10 io port: [0x00-0xff]
[    0.824122] pci 0000:00:1f.6: reg 14 io port: [0x00-0x7f]
[    0.824157] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.824163] pci 0000:00:1f.6: PME# disabled
[    0.824207] pci 0000:01:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.824216] pci 0000:01:00.0: reg 14 32bit mmio: [0xefc00000-0xefffffff]
[    0.824224] pci 0000:01:00.0: reg 18 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.824233] pci 0000:01:00.0: reg 1c 32bit mmio: [0xdfff8000-0xdfffffff]
[    0.824249] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x03ffff]
[    0.824261] pci 0000:01:00.0: supports D1 D2
[    0.824306] pci 0000:00:01.0: bridge 32bit mmio: [0xdff00000-0xf7ffffff]
[    0.824356] pci 0000:02:08.0: reg 10 32bit mmio: [0xdfdff000-0xdfdfffff]
[    0.824366] pci 0000:02:08.0: reg 14 io port: [0xcf40-0xcf7f]
[    0.824401] pci 0000:02:08.0: supports D1 D2
[    0.824405] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.824412] pci 0000:02:08.0: PME# disabled
[    0.824453] pci 0000:02:0a.0: reg 10 32bit mmio: [0xdfdfe000-0xdfdfefff]
[    0.824533] pci 0000:02:0b.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.824585] pci 0000:02:0d.0: reg 10 32bit mmio: [0x000000-0x0001ff]
[    0.824629] pci 0000:02:0d.0: supports D1 D2
[    0.824633] pci 0000:02:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.824640] pci 0000:02:0d.0: PME# disabled
[    0.824672] pci 0000:00:1e.0: transparent bridge
[    0.824679] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.824686] pci 0000:00:1e.0: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
[    0.824721] bus 00 -> node 0
[    0.824731] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.824812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.824924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.828748] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11)
[    0.828985] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11)
[    0.829219] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11)
[    0.829451] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11)
[    0.829683] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11)
[    0.829915] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11)
[    0.830147] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[    0.830380] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11)
[    0.830705] ACPI: Power Resource [PFAN] (off)
[    0.830840] ACPI: WMI: Mapper loaded
[    0.831136] SCSI subsystem initialized
[    0.831200] libata version 3.00 loaded.
[    0.831278] usbcore: registered new interface driver usbfs
[    0.831308] usbcore: registered new interface driver hub
[    0.831357] usbcore: registered new device driver usb
[    0.831551] PCI: Using ACPI for IRQ routing
[    0.831676] Bluetooth: Core ver 2.13
[    0.831676] NET: Registered protocol family 31
[    0.831676] Bluetooth: HCI device and connection manager initialized
[    0.831676] Bluetooth: HCI socket layer initialized
[    0.831676] NET: Registered protocol family 8
[    0.831676] NET: Registered protocol family 20
[    0.831676] NetLabel: Initializing
[    0.831676] NetLabel:  domain hash size = 128
[    0.831676] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.831676] NetLabel:  unlabeled traffic allowed by default
[    0.831676] AppArmor: AppArmor Filesystem Enabled
[    0.831676] pnp: PnP ACPI init
[    0.832020] ACPI: bus type pnp registered
[    0.835099] pnp 00:08: io resource (0x62-0x62) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835106] pnp 00:08: io resource (0x66-0x66) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835113] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835118] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835124] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835130] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835136] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835145] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835151] pnp 00:08: io resource (0x24-0x25) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835157] pnp 00:08: io resource (0x28-0x29) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835164] pnp 00:08: io resource (0x2c-0x2d) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835170] pnp 00:08: io resource (0x30-0x31) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835176] pnp 00:08: io resource (0x34-0x35) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835182] pnp 00:08: io resource (0x38-0x39) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835188] pnp 00:08: io resource (0x3c-0x3d) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835194] pnp 00:08: io resource (0x50-0x53) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835200] pnp 00:08: io resource (0x63-0x63) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835206] pnp 00:08: io resource (0x65-0x65) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835213] pnp 00:08: io resource (0x72-0x77) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835219] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835225] pnp 00:08: io resource (0xa4-0xa5) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835231] pnp 00:08: io resource (0xa8-0xa9) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835237] pnp 00:08: io resource (0xac-0xad) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835244] pnp 00:08: io resource (0xb0-0xb5) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835250] pnp 00:08: io resource (0xb8-0xb9) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835256] pnp 00:08: io resource (0xbc-0xbd) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.835267] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.835273] pnp 00:08: io resource (0x24-0x25) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.835279] pnp 00:08: io resource (0x28-0x29) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.835285] pnp 00:08: io resource (0x2c-0x2d) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.835291] pnp 00:08: io resource (0x30-0x31) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.835297] pnp 00:08: io resource (0x34-0x35) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.835303] pnp 00:08: io resource (0x38-0x39) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.835310] pnp 00:08: io resource (0x3c-0x3d) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.835322] pnp 00:08: io resource (0x62-0x62) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835328] pnp 00:08: io resource (0x66-0x66) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835334] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835340] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835346] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835352] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835358] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835367] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835373] pnp 00:08: io resource (0x24-0x25) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835379] pnp 00:08: io resource (0x28-0x29) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835385] pnp 00:08: io resource (0x2c-0x2d) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835391] pnp 00:08: io resource (0x30-0x31) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835397] pnp 00:08: io resource (0x34-0x35) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835403] pnp 00:08: io resource (0x38-0x39) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835410] pnp 00:08: io resource (0x3c-0x3d) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835416] pnp 00:08: io resource (0x50-0x53) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835422] pnp 00:08: io resource (0x63-0x63) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835428] pnp 00:08: io resource (0x65-0x65) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835434] pnp 00:08: io resource (0x72-0x77) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835440] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835447] pnp 00:08: io resource (0xa4-0xa5) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835453] pnp 00:08: io resource (0xa8-0xa9) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835459] pnp 00:08: io resource (0xac-0xad) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835465] pnp 00:08: io resource (0xb0-0xb5) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835471] pnp 00:08: io resource (0xb8-0xb9) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835478] pnp 00:08: io resource (0xbc-0xbd) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.835484] pnp 00:08: io resource (0x62-0x62) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835490] pnp 00:08: io resource (0x66-0x66) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835500] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835506] pnp 00:08: io resource (0x24-0x25) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835512] pnp 00:08: io resource (0x28-0x29) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835518] pnp 00:08: io resource (0x2c-0x2d) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835524] pnp 00:08: io resource (0x30-0x31) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835530] pnp 00:08: io resource (0x34-0x35) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835537] pnp 00:08: io resource (0x38-0x39) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835543] pnp 00:08: io resource (0x3c-0x3d) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835549] pnp 00:08: io resource (0x50-0x53) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835555] pnp 00:08: io resource (0x63-0x63) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835561] pnp 00:08: io resource (0x65-0x65) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.835568] pnp 00:08: io resource (0x72-0x77) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.836379] pnp: PnP ACPI: found 9 devices
[    0.836383] ACPI: ACPI bus type pnp unregistered
[    0.836388] PnPBIOS: Disabled by ACPI PNP
[    0.836405] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.836410] system 00:00: iomem range 0xe0000-0xeffff could not be reserved
[    0.836416] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.836421] system 00:00: iomem range 0x100000-0x4ffc9fff could not be reserved
[    0.836426] system 00:00: iomem range 0x4ffca000-0x4ffcffff has been reserved
[    0.836432] system 00:00: iomem range 0x4ffd0000-0x4ffdffff could not be reserved
[    0.836437] system 00:00: iomem range 0x4ffe0000-0x4fffffff has been reserved
[    0.836443] system 00:00: iomem range 0xfeda0000-0xfedbffff has been reserved
[    0.836448] system 00:00: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.836453] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.836468] system 00:08: ioport range 0x1e0-0x1e7 has been reserved
[    0.836473] system 00:08: ioport range 0x480-0x48f has been reserved
[    0.836478] system 00:08: ioport range 0x680-0x6ff has been reserved
[    0.836483] system 00:08: ioport range 0xd800-0xd87f has been reserved
[    0.836488] system 00:08: ioport range 0xd880-0xd89f has been reserved
[    0.836493] system 00:08: ioport range 0xd8a0-0xd8bf has been reserved
[    0.836499] system 00:08: ioport range 0xe000-0xe07f has been reserved
[    0.836504] system 00:08: ioport range 0xe080-0xe0ff has been reserved
[    0.836509] system 00:08: ioport range 0xe400-0xe47f has been reserved
[    0.836514] system 00:08: ioport range 0xe480-0xe4ff has been reserved
[    0.836519] system 00:08: ioport range 0xe800-0xe87f has been reserved
[    0.836524] system 00:08: ioport range 0xe880-0xe8ff has been reserved
[    0.836529] system 00:08: ioport range 0xec00-0xec7f has been reserved
[    0.836535] system 00:08: ioport range 0xec80-0xecff has been reserved
[    0.836540] system 00:08: ioport range 0xeeac-0xeeac has been reserved
[    0.836545] system 00:08: ioport range 0xeeb0-0xeebf has been reserved
[    0.836551] system 00:08: ioport range 0xeec0-0xeeff has been reserved
[    0.836563] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.871443] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.871447] pci 0000:00:01.0:   IO window: disabled
[    0.871454] pci 0000:00:01.0:   MEM window: 0xdff00000-0xf7ffffff
[    0.871460] pci 0000:00:01.0:   PREFETCH window: 0x00000064000000-0x000000640fffff
[    0.871478] pci 0000:02:0b.0: CardBus bridge, secondary bus 0000:03
[    0.871483] pci 0000:02:0b.0:   IO window: 0x00c000-0x00c0ff
[    0.871489] pci 0000:02:0b.0:   IO window: 0x00c400-0x00c4ff
[    0.871496] pci 0000:02:0b.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.871503] pci 0000:02:0b.0:   MEM window: 0x68000000-0x6bffffff
[    0.871510] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.871516] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.871523] pci 0000:00:1e.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.871530] pci 0000:00:1e.0:   PREFETCH window: 0x00000060000000-0x00000063ffffff
[    0.871552] pci 0000:00:1e.0: setting latency timer to 64
[    0.871564] pci 0000:02:0b.0: enabling device (0000 -> 0003)
[    0.871945] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.871950] PCI: setting IRQ 11 as level-triggered
[    0.871958] pci 0000:02:0b.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.871969] bus: 00 index 0 io port: [0x00-0xffff]
[    0.871974] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.871978] bus: 01 index 0 mmio: [0x0-0x0]
[    0.871982] bus: 01 index 1 mmio: [0xdff00000-0xf7ffffff]
[    0.871987] bus: 01 index 2 mmio: [0x64000000-0x640fffff]
[    0.871990] bus: 01 index 3 mmio: [0x0-0x0]
[    0.871995] bus: 02 index 0 io port: [0xc000-0xcfff]
[    0.872011] bus: 02 index 1 mmio: [0xdfd00000-0xdfdfffff]
[    0.872016] bus: 02 index 2 mmio: [0x60000000-0x63ffffff]
[    0.872020] bus: 02 index 3 io port: [0x00-0xffff]
[    0.872024] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.872028] bus: 03 index 0 io port: [0xc000-0xc0ff]
[    0.872032] bus: 03 index 1 io port: [0xc400-0xc4ff]
[    0.872036] bus: 03 index 2 mmio: [0x60000000-0x63ffffff]
[    0.872041] bus: 03 index 3 mmio: [0x68000000-0x6bffffff]
[    0.872057] NET: Registered protocol family 2
[    0.872265] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.872813] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.874352] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.875502] TCP: Hash tables configured (established 131072 bind 65536)
[    0.875508] TCP reno registered
[    0.875766] NET: Registered protocol family 1
[    0.876045] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.456063]  it is
[    2.087946] Freeing initrd memory: 7296k freed
[    2.088076] Simple Boot Flag at 0x7c set to 0x1
[    2.088124] cpufreq: No nForce2 chipset.
[    2.088359] audit: initializing netlink socket (disabled)
[    2.088403] type=2000 audit(1243847890.088:1): initialized
[    2.103420] highmem bounce pool size: 64 pages
[    2.103432] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.106217] VFS: Disk quotas dquot_6.5.1
[    2.106351] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.107637] fuse init (API version 7.10)
[    2.107808] msgmni has been set to 1717
[    2.108163] alg: No test for stdrng (krng)
[    2.108186] io scheduler noop registered
[    2.108190] io scheduler anticipatory registered
[    2.108193] io scheduler deadline registered
[    2.108230] io scheduler cfq registered (default)
[    2.108302] pci 0000:01:00.0: Boot video device
[    2.108335] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    2.112705] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.112722] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.112915] ACPI: AC Adapter [ADP1] (off-line)
[    2.113794] ACPI Warning (nspredef-0858): \_SB_.BAT1._BIF: Return Package type mismatch at index 12 - found Integer, expected String/Buffer [20080926]
[    2.114318] ACPI: Battery Slot [BAT1] (battery present)
[    2.115152] ACPI Warning (nspredef-0858): \_SB_.BAT2._BIF: Return Package type mismatch at index 12 - found Integer, expected String/Buffer [20080926]
[    2.115662] ACPI: Battery Slot [BAT2] (battery present)
[    2.115779] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.115784] ACPI: Power Button (FF) [PWRF]
[    2.115876] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.115911] ACPI: Power Button (CM) [PWRB]
[    2.116001] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    2.116119] ACPI: Lid Switch [LID]
[    2.116623] fan PNP0C0B:00: registered as cooling_device0
[    2.116634] ACPI: Fan [FAN] (off)
[    2.116882] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.116914] processor ACPI_CPU:00: registered as cooling_device1
[    2.120233] thermal LNXTHERM:01: registered as thermal_zone0
[    2.120870] ACPI: Thermal Zone [THRM] (33 C)
[    2.120945] isapnp: Scanning for PnP cards...
[    2.473934] isapnp: No Plug & Play device found
[    2.477002] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.477602] serial 0000:00:1f.6: power state changed by ACPI to D0
[    2.477611] serial 0000:00:1f.6: enabling device (0000 -> 0001)
[    2.477988] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    2.477996] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.478005] serial 0000:00:1f.6: PCI INT B disabled
[    2.479207] brd: module loaded
[    2.479770] loop: module loaded
[    2.479906] Fixed MDIO Bus: probed
[    2.479917] PPP generic driver version 2.4.2
[    2.480048] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.480100] Driver 'sd' needs updating - please use bus_type methods
[    2.480117] Driver 'sr' needs updating - please use bus_type methods
[    2.480240] ata_piix 0000:00:1f.1: version 2.12
[    2.480614] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    2.480621] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.480681] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.480811] scsi0 : ata_piix
[    2.480963] scsi1 : ata_piix
[    2.481503] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    2.481508] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    2.644463] ata1.00: ATA-5: TOSHIBA MK4004GAH, JC001A, max UDMA/100
[    2.644468] ata1.00: 78126048 sectors, multi 16: LBA 
[    2.652425] ata1.00: configured for UDMA/100
[    2.652464] ata2: port disabled. ignoring.
[    2.652642] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4004GA JC00 PQ: 0 ANSI: 5
[    2.652813] sd 0:0:0:0: [sda] 78126048 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.652842] sd 0:0:0:0: [sda] Write Protect is off
[    2.652847] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.652891] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.652997] sd 0:0:0:0: [sda] 78126048 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.653022] sd 0:0:0:0: [sda] Write Protect is off
[    2.653026] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.653069] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.653076]  sda: sda1 sda2 < sda5 sda6 >
[    2.756400] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.756481] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.757631] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.757662] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    2.758055] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    2.758062] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    2.758100] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.758106] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.758218] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.762145] ehci_hcd 0000:00:1d.7: debug port 1
[    2.762154] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.762167] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x64100000
[    2.776033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.776158] usb usb1: configuration #1 chosen from 1 choice
[    2.776210] hub 1-0:1.0: USB hub found
[    2.776224] hub 1-0:1.0: 6 ports detected
[    2.776417] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.776448] uhci_hcd: USB Universal Host Controller Interface driver
[    2.776504] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.776515] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.776520] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.776594] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.776619] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000efe0
[    2.776757] usb usb2: configuration #1 chosen from 1 choice
[    2.776804] hub 2-0:1.0: USB hub found
[    2.776816] hub 2-0:1.0: 2 ports detected
[    2.777333] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    2.777340] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.777349] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.777355] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.777431] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.777457] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000ef80
[    2.777620] usb usb3: configuration #1 chosen from 1 choice
[    2.777666] hub 3-0:1.0: USB hub found
[    2.777677] hub 3-0:1.0: 2 ports detected
[    2.777874] usbcore: registered new interface driver libusual
[    2.777930] usbcore: registered new interface driver usbserial
[    2.777949] USB Serial support registered for generic
[    2.777974] usbcore: registered new interface driver usbserial_generic
[    2.777978] usbserial: USB Serial Driver core
[    2.778054] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.783614] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.783624] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.783814] mice: PS/2 mouse device common for all mice
[    2.784087] rtc_cmos 00:07: RTC can wake from S4
[    2.784147] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.784168] rtc0: alarms up to one year, 114 bytes nvram
[    2.784354] device-mapper: uevent: version 1.0.3
[    2.784588] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.784674] device-mapper: multipath: version 1.0.5 loaded
[    2.784679] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.784833] EISA: Probing bus 0 at eisa.0
[    2.784843] Cannot allocate resource for EISA slot 1
[    2.784870] EISA: Detected 0 cards.
[    2.784981] cpuidle: using governor ladder
[    2.785091] cpuidle: using governor menu
[    2.786398] TCP cubic registered
[    2.786621] NET: Registered protocol family 10
[    2.787439] lo: Disabled Privacy Extensions
[    2.788118] NET: Registered protocol family 17
[    2.788147] Bluetooth: L2CAP ver 2.11
[    2.788151] Bluetooth: L2CAP socket layer initialized
[    2.788156] Bluetooth: SCO (Voice Link) ver 0.6
[    2.788159] Bluetooth: SCO socket layer initialized
[    2.788200] Bluetooth: RFCOMM socket layer initialized
[    2.788212] Bluetooth: RFCOMM TTY layer initialized
[    2.788216] Bluetooth: RFCOMM ver 1.10
[    2.788510] IO APIC resources could be not be allocated.
[    2.788521] Using IPI No-Shortcut mode
[    2.788652] registered taskstats version 1
[    2.788835]   Magic number: 13:297:322
[    2.788873] tty tty47: hash matches
[    2.788974] rtc_cmos 00:07: setting system clock to 2009-06-01 09:18:11 UTC (1243847891)
[    2.788980] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.788983] EDD information not available.
[    2.789502] Freeing unused kernel memory: 532k freed
[    2.789707] Write protecting the kernel text: 4128k
[    2.789779] Write protecting the kernel read-only data: 1532k
[    2.825973] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.927064] vesafb: framebuffer at 0xf0000000, mapped to 0xf7d00000, using 6144k, total 32768k
[    2.927072] vesafb: mode is 1024x768x32, linelength=4096, pages=9
[    2.927076] vesafb: protected mode interface info at c000:85ba
[    2.927081] vesafb: pmi: set display start = c00c85e9, set palette = c00c8652
[    2.927085] vesafb: scrolling: redraw
[    2.927090] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    2.927251] Console: switching to colour frame buffer device 128x48
[    2.987329] fb0: VESA VGA frame buffer device
[    3.467307] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    3.467313] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.467820] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    3.467828] e100 0000:02:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    3.492333] e100 0000:02:08.0: PME# disabled
[    3.502796] e100: eth0: e100_probe: addr 0xdfdff000, irq 11, MAC addr 00:08:0d:91:5c:d8
[    3.884322] Marking TSC unstable due to TSC halts in idle
[    4.317572] PM: Starting manual resume from disk
[    4.317578] PM: Resume from partition 8:6
[    4.317581] PM: Checking hibernation image.
[    4.317796] PM: Resume from disk failed.
[    4.379139] kjournald starting.  Commit interval 5 seconds
[    4.379156] EXT3-fs: mounted filesystem with ordered data mode.
[   20.499451] udev: starting version 141
[   20.926119] acpi device:1b: registered as cooling_device2
[   20.926531] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a/input/input5
[   20.956260] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   21.306232] Linux agpgart interface v0.103
[   21.344567] intel_rng: FWH not detected
[   21.423100] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   21.452605] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.667262] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   21.681498] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   22.188440] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   22.412332] iTCO_vendor_support: vendor-support=0
[   22.416559] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   22.416754] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
[   22.416887] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   22.453808] ieee80211_crypt: registered algorithm 'NULL'
[   22.464701] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   22.464707] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   22.583202] yenta_cardbus 0000:02:0b.0: CardBus bridge found [1179:0001]
[   22.608465] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   22.608471] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   22.713443] yenta_cardbus 0000:02:0b.0: ISA IRQ mask 0x04b8, PCI irq 11
[   22.713452] yenta_cardbus 0000:02:0b.0: Socket status: 30000007
[   22.713461] yenta_cardbus 0000:02:0b.0: pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   22.713468] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc000-0xcfff: clean.
[   22.713836] yenta_cardbus 0000:02:0b.0: pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[   22.713843] yenta_cardbus 0000:02:0b.0: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x63ffffff
[   22.725772] ipw2100 0000:02:0a.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   22.726646] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   22.726672] ipw2100 0000:02:0a.0: firmware: requesting ipw2100-1.3.fw
[   22.926655] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   23.003249] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   23.146140] Intel ICH 0000:00:1f.5: power state changed by ACPI to D0
[   23.146153] Intel ICH 0000:00:1f.5: enabling device (0000 -> 0003)
[   23.146165] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   23.146364] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   23.185492] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   23.186544] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   23.186997] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   23.187399] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   23.188050] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   23.368220] Clocksource tsc unstable (delta = -150997505 ns)
[   24.072053] intel8x0_measure_ac97_clock: measured 55168 usecs
[   24.072058] intel8x0: clocking to 48000
[   24.383641] lp: driver loaded but no devices found
[   24.595402] Adding 859436k swap on /dev/sda6.  Priority:-1 extents:1 across:859436k
[   24.641048] EXT3 FS on sda5, internal journal
[   25.822465] type=1505 audit(1243844314.531:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1899
[   25.925847] type=1505 audit(1243844314.635:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1904
[   25.926125] type=1505 audit(1243844314.635:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1904
[   25.926212] type=1505 audit(1243844314.635:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1904
[   25.926292] type=1505 audit(1243844314.635:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1904
[   26.222606] type=1505 audit(1243844314.931:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1909
[   26.223051] type=1505 audit(1243844314.931:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1909
[   26.313587] type=1505 audit(1243844315.023:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=1913
[   26.368145] type=1505 audit(1243844315.079:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1917
[   27.005445] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19-dev-acpikeys
[   27.005451] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   27.006305] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   27.006310] toshiba_acpi: ktoshkeyd will check 2 times per second
[   27.007017] toshiba_acpi: Dropped 0 keys from the queue on startup
[   28.942741] Intel ICH Modem 0000:00:1f.6: power state changed by ACPI to D0
[   28.942759] Intel ICH Modem 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   28.942784] Intel ICH Modem 0000:00:1f.6: setting latency timer to 64
[   44.521037] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   44.521042] Bluetooth: BNEP filters: protocol multicast
[   44.572002] Bridge firewalling registered
[   47.414175] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.369036] ppdev: user-space parallel port driver
[   62.884043] eth1: no IPv6 routers present
[  464.180086] usb 1-1: new high speed USB device using ehci_hcd and address 2
[  464.316658] usb 1-1: configuration #1 chosen from 1 choice
[  464.493889] Initializing USB Mass Storage driver...
[  464.496834] scsi2 : SCSI emulation for USB Mass Storage devices
[  464.497357] usbcore: registered new interface driver usb-storage
[  464.497368] USB Mass Storage support registered.
[  464.499214] usb-storage: device found at 2
[  464.499222] usb-storage: waiting for device to settle before scanning
[  469.496504] usb-storage: device scan complete
[  469.497603] scsi 2:0:0:0: Direct-Access     Freecom  DataBar USB2.0   1100 PQ: 0 ANSI: 0 CCS
[  469.547896] sd 2:0:0:0: [sdb] 31326208 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[  469.554481] sd 2:0:0:0: [sdb] Write Protect is off
[  469.554491] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  469.554500] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  469.562584] sd 2:0:0:0: [sdb] 31326208 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[  469.563442] sd 2:0:0:0: [sdb] Write Protect is off
[  469.563451] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  469.563459] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  469.563471]  sdb: sdb1
[  469.566153] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  469.566332] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  519.448614] usb 1-1: USB disconnect, address 2
[23736.000245] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[23736.001098] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[23746.436128] eth0: no IPv6 routers present
[23838.000424] e100: eth0: e100_watchdog: link down
[28482.940152] usb 1-2: new high speed USB device using ehci_hcd and address 3
[28483.120817] usb 1-2: configuration #1 chosen from 1 choice
[28483.166472] scsi3 : SCSI emulation for USB Mass Storage devices
[28483.167106] usb-storage: device found at 3
[28483.167113] usb-storage: waiting for device to settle before scanning
[28488.173201] usb-storage: device scan complete
[28488.174390] scsi 3:0:0:0: Direct-Access     Freecom  DataBar USB2.0   1100 PQ: 0 ANSI: 0 CCS
[28488.180597] sd 3:0:0:0: [sdb] 31326208 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[28488.184986] sd 3:0:0:0: [sdb] Write Protect is off
[28488.184997] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
[28488.185006] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[28488.187453] sd 3:0:0:0: [sdb] 31326208 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[28488.190002] sd 3:0:0:0: [sdb] Write Protect is off
[28488.190011] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
[28488.190018] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[28488.190030]  sdb: sdb1
[28488.191020] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[28488.191204] sd 3:0:0:0: Attached scsi generic sg1 type 0

```


```
netstat -na | grep LIST | grep '*'
```

```
andy@server:~$ sudo netstat -na | grep LIST | grep '*'
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::139                  :::*                    LISTEN     
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN    
```


And on the PC....

mii-tool produced
```
eth0: negotiated 1000baseT-FD flow-control, link ok
```

arp -a produced nothing on the PC..?

iptables -L -v produced

```

Chain INPUT (policy ACCEPT 62 packets, 8909 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 33 packets, 4292 bytes)
 pkts bytes target     prot opt in     out     source               destination         
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:19:db:f2:36:7a  
          inet addr:10.0.1.2  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fef2:367a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4697 (4.6 KB)  TX bytes:5392 (5.3 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1316 (1.3 KB)  TX bytes:1316 (1.3 KB)

```

tcpdump -i eth0

```
17:10:51.081774 IP server.local.netbios-dgm > 10.0.1.255.netbios-dgm: NBT UDP PACKET(138)
17:10:51.182453 IP desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.0.10.in-addr.arpa. (41)
17:10:52.183539 IP desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.0.10.in-addr.arpa. (41)
17:10:54.185651 IP desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.0.10.in-addr.arpa. (41)
17:10:56.184108 IP desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
17:10:57.185183 IP desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
17:10:59.186082 IP desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
17:11:31.124489 IP server.local.netbios-ns > 10.0.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
17:11:33.137381 IP server.local.netbios-ns > 10.0.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
17:11:33.137495 IP server.local.netbios-ns > 10.0.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
17:11:35.141279 IP server.local.netbios-ns > 10.0.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
17:11:46.152850 IP server.local.netbios-dgm > 10.0.1.255.netbios-dgm: NBT UDP PACKET(138)
17:11:48.155744 IP server.local.netbios-dgm > 10.0.1.255.netbios-dgm: NBT UDP PACKET(138)
17:11:50.158638 IP server.local.netbios-dgm > 10.0.1.255.netbios-dgm: NBT UDP PACKET(138)
17:11:52.161538 IP server.local.netbios-dgm > 10.0.1.255.netbios-dgm: NBT UDP PACKET(138)

```

dmesg

```
[    0.000000] BIOS EBDA/lowmem at: 00099c00/00099c00
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
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099c00 (usable)
[    0.000000]  BIOS-e820: 0000000000099c00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000099c00 (usable)
[    0.000000]  modified: 0000000000099c00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  modified: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bd000 - 37feff92
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb3f92
[    0.000000] Move RAMDISK from 00000000378bd000 - 0000000037feff91 to 00881000 - 00fb3f91
[    0.000000] ACPI: RSDP 000F9810, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFB0000, 003C (r1 110207 RSDT1540 20071102 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0200, 0084 (r2 110207 FACP1540 20071102 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB0440, 5503 (r1  0AAAA 0AAAA000        0 INTL 20051117)
[    0.000000] ACPI: FACS 7FFBE000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 006C (r1 110207 APIC1540 20071102 MSFT       97)
[    0.000000] ACPI: MCFG 7FFB0400, 003C (r1 110207 OEMMCFG  20071102 MSFT       97)
[    0.000000] ACPI: OEMB 7FFBE040, 0061 (r1 110207 OEMB1540 20071102 MSFT       97)
[    0.000000] ACPI: ASF! 7FFB5950, 0099 (r32 LEGEND I865PASF        1 INTL 20051117)
[    0.000000] ACPI: GSCI 7FFBE0B0, 2024 (r1 110207 GMCHSCI  20071102 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1163MB HIGHMEM available.
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
[    0.000000]   #5 [0000099c00 - 0000100000]    BIOS reserved ==> [0000099c00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb3f92]      NEW RAMDISK ==> [0000881000 - 0000fb3f92]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000099
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524089
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3945 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2328 pages used for memmap
[    0.000000]   HighMem zone: 295578 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000099000 - 000000000009a000
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e3000
[    0.000000] PM: Registered nosave memory: 00000000000e3000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519993
[    0.000000] Kernel command line: root=UUID=47a8e3e8-4af6-448c-b68b-969e2272d5c8 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2669.648 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10483840 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2052776k/2096832k available (4126k kernel code, 42716k reserved, 2208k data, 532k init, 1191624k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5339.29 BogoMIPS (lpj=10678592)
[    0.004020] Security Framework initialized
[    0.004026] SELinux:  Disabled at boot.
[    0.004039] AppArmor: AppArmor initialized
[    0.004044] Mount-cache hash table entries: 512
[    0.004140] Initializing cgroup subsys ns
[    0.004143] Initializing cgroup subsys cpuacct
[    0.004145] Initializing cgroup subsys memory
[    0.004148] Initializing cgroup subsys freezer
[    0.004158] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004160] CPU: L2 cache: 4096K
[    0.004162] CPU: Physical Processor ID: 0
[    0.004163] CPU: Processor Core ID: 0
[    0.004166] using mwait in idle threads.
[    0.004172] Checking 'hlt' instruction... OK.
[    0.021782] ACPI: Core revision 20080926
[    0.023350] ACPI: Checking initramfs for custom DSDT
[    0.244001] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.283736] CPU0: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.284001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5339.70 BogoMIPS (lpj=10679400)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.368477] CPU1: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.368489] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.372027] Brought up 2 CPUs
[    0.372029] Total of 2 processors activated (10678.99 BogoMIPS).
[    0.372072] CPU0 attaching sched-domain:
[    0.372074]  domain 0: span 0-1 level MC
[    0.372075]   groups: 0 1
[    0.372080] CPU1 attaching sched-domain:
[    0.372081]  domain 0: span 0-1 level MC
[    0.372083]   groups: 1 0
[    0.372133] net_namespace: 776 bytes
[    0.372133] Booting paravirtualized kernel on bare hardware
[    0.372248] Time: 17:02:43  Date: 06/01/09
[    0.372248] regulator: core version 0.5
[    0.372248] NET: Registered protocol family 16
[    0.372248] EISA bus registered
[    0.372248] ACPI: bus type pci registered
[    0.372248] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.372248] PCI: Not using MMCONFIG.
[    0.372280] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.372281] PCI: Using configuration type 1 for base access
[    0.372914] ACPI: EC: Look up EC in DSDT
[    0.380986] ACPI: Interpreter enabled
[    0.380992] ACPI: (supports S0 S1 S3 S4 S5)
[    0.381007] ACPI: Using IOAPIC for interrupt routing
[    0.381048] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.383767] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.383769] PCI: Using MMCONFIG for extended config space
[    0.389212] ACPI: No dock devices found.
[    0.389259] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.389327] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.389329] pci 0000:00:01.0: PME# disabled
[    0.389386] pci 0000:00:1a.0: reg 20 io port: [0x9c00-0x9c1f]
[    0.389437] pci 0000:00:1a.1: reg 20 io port: [0x9880-0x989f]
[    0.389492] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe6ffc00-0xfe6fffff]
[    0.389524] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.389527] pci 0000:00:1a.7: PME# disabled
[    0.389560] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe6f8000-0xfe6fbfff]
[    0.389583] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.389586] pci 0000:00:1b.0: PME# disabled
[    0.389624] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.389627] pci 0000:00:1c.0: PME# disabled
[    0.389664] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.389667] pci 0000:00:1c.1: PME# disabled
[    0.389705] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.389707] pci 0000:00:1c.2: PME# disabled
[    0.389746] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.389749] pci 0000:00:1c.5: PME# disabled
[    0.389793] pci 0000:00:1d.0: reg 20 io port: [0x9800-0x981f]
[    0.389844] pci 0000:00:1d.1: reg 20 io port: [0x9480-0x949f]
[    0.389894] pci 0000:00:1d.2: reg 20 io port: [0x9400-0x941f]
[    0.389945] pci 0000:00:1d.3: reg 20 io port: [0x9080-0x909f]
[    0.389998] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe6ff800-0xfe6ffbff]
[    0.390029] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.390033] pci 0000:00:1d.7: PME# disabled
[    0.390127] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.390130] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.390163] pci 0000:00:1f.2: reg 10 io port: [0x9000-0x9007]
[    0.390167] pci 0000:00:1f.2: reg 14 io port: [0x8c00-0x8c03]
[    0.390172] pci 0000:00:1f.2: reg 18 io port: [0x8880-0x8887]
[    0.390176] pci 0000:00:1f.2: reg 1c io port: [0x8800-0x8803]
[    0.390181] pci 0000:00:1f.2: reg 20 io port: [0x8480-0x848f]
[    0.390185] pci 0000:00:1f.2: reg 24 io port: [0x8400-0x840f]
[    0.390213] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe6ff400-0xfe6ff4ff]
[    0.390224] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.390258] pci 0000:00:1f.5: reg 10 io port: [0x8000-0x8007]
[    0.390262] pci 0000:00:1f.5: reg 14 io port: [0x7c00-0x7c03]
[    0.390266] pci 0000:00:1f.5: reg 18 io port: [0x7880-0x7887]
[    0.390271] pci 0000:00:1f.5: reg 1c io port: [0x7800-0x7803]
[    0.390275] pci 0000:00:1f.5: reg 20 io port: [0x7480-0x748f]
[    0.390280] pci 0000:00:1f.5: reg 24 io port: [0x7400-0x740f]
[    0.390317] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.390325] pci 0000:01:00.0: reg 18 64bit mmio: [0xfe7f0000-0xfe7fffff]
[    0.390329] pci 0000:01:00.0: reg 20 io port: [0xa000-0xa0ff]
[    0.390337] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe7c0000-0xfe7dffff]
[    0.390343] pci 0000:01:00.0: supports D1 D2
[    0.390371] pci 0000:01:00.1: reg 10 64bit mmio: [0xfe7ec000-0xfe7effff]
[    0.390391] pci 0000:01:00.1: supports D1 D2
[    0.390427] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.390430] pci 0000:00:01.0: bridge 32bit mmio: [0xfe700000-0xfe7fffff]
[    0.390433] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.390487] pci 0000:02:00.0: reg 10 64bit mmio: [0xfe8ffc00-0xfe8ffc7f]
[    0.390502] pci 0000:02:00.0: reg 18 64bit mmio: [0xfe8f8000-0xfe8fbfff]
[    0.390510] pci 0000:02:00.0: reg 20 io port: [0xbc00-0xbc7f]
[    0.390524] pci 0000:02:00.0: reg 30 32bit mmio: [0xfe800000-0xfe87ffff]
[    0.390536] pci 0000:02:00.0: supports D1 D2
[    0.390578] pci 0000:00:1c.0: bridge io port: [0xb000-0xbfff]
[    0.390581] pci 0000:00:1c.0: bridge 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.390623] pci 0000:03:00.0: reg 10 io port: [0xcc00-0xcc07]
[    0.390630] pci 0000:03:00.0: reg 14 io port: [0xc880-0xc883]
[    0.390637] pci 0000:03:00.0: reg 18 io port: [0xc800-0xc807]
[    0.390644] pci 0000:03:00.0: reg 1c io port: [0xc480-0xc483]
[    0.390650] pci 0000:03:00.0: reg 20 io port: [0xc400-0xc40f]
[    0.390657] pci 0000:03:00.0: reg 24 32bit mmio: [0xfe9ffc00-0xfe9fffff]
[    0.390673] pci 0000:03:00.0: supports D1
[    0.390675] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.390679] pci 0000:03:00.0: PME# disabled
[    0.390717] pci 0000:00:1c.1: bridge io port: [0xc000-0xcfff]
[    0.390720] pci 0000:00:1c.1: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.390774] pci 0000:04:00.0: reg 10 64bit mmio: [0xfeafc000-0xfeafffff]
[    0.390782] pci 0000:04:00.0: reg 18 io port: [0xd800-0xd8ff]
[    0.390805] pci 0000:04:00.0: reg 30 32bit mmio: [0xfeac0000-0xfeadffff]
[    0.390815] pci 0000:04:00.0: supports D1 D2
[    0.390816] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.390820] pci 0000:04:00.0: PME# disabled
[    0.390855] pci 0000:00:1c.2: bridge io port: [0xd000-0xdfff]
[    0.390858] pci 0000:00:1c.2: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.390929] pci 0000:06:00.0: reg 10 32bit mmio: [0xfebf0000-0xfebfffff]
[    0.390935] pci 0000:06:00.0: reg 14 32bit mmio: [0xfebe0000-0xfebeffff]
[    0.390998] pci 0000:06:02.0: reg 10 32bit mmio: [0xfebdf800-0xfebdffff]
[    0.391004] pci 0000:06:02.0: reg 14 io port: [0xec00-0xec7f]
[    0.391034] pci 0000:06:02.0: supports D2
[    0.391035] pci 0000:06:02.0: PME# supported from D2 D3hot D3cold
[    0.391039] pci 0000:06:02.0: PME# disabled
[    0.391076] pci 0000:00:1e.0: transparent bridge
[    0.391079] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.391082] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.391105] bus 00 -> node 0
[    0.391109] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.391311] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.391445] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.391528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.391610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.394250] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.394347] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.394443] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.394539] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.394634] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.394730] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.394825] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.394920] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.395015] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 08, should be 07 [20080926]
[    0.395631] ACPI: WMI: Mapper loaded
[    0.395657] SCSI subsystem initialized
[    0.395657] libata version 3.00 loaded.
[    0.395657] usbcore: registered new interface driver usbfs
[    0.395657] usbcore: registered new interface driver hub
[    0.395657] usbcore: registered new device driver usb
[    0.395657] PCI: Using ACPI for IRQ routing
[    0.400008] Bluetooth: Core ver 2.13
[    0.400019] NET: Registered protocol family 31
[    0.400019] Bluetooth: HCI device and connection manager initialized
[    0.400019] Bluetooth: HCI socket layer initialized
[    0.400019] NET: Registered protocol family 8
[    0.400019] NET: Registered protocol family 20
[    0.400024] NetLabel: Initializing
[    0.400025] NetLabel:  domain hash size = 128
[    0.400026] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400035] NetLabel:  unlabeled traffic allowed by default
[    0.400079] AppArmor: AppArmor Filesystem Enabled
[    0.404008] pnp: PnP ACPI init
[    0.404013] ACPI: bus type pnp registered
[    0.406625] pnp: PnP ACPI: found 15 devices
[    0.406627] ACPI: ACPI bus type pnp unregistered
[    0.406630] PnPBIOS: Disabled by ACPI PNP
[    0.406637] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.406643] system 00:08: ioport range 0xa10-0xaef has been reserved
[    0.406645] system 00:08: ioport range 0xae0-0xaef has been reserved
[    0.406649] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.406651] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.406653] system 00:09: ioport range 0x480-0x4bf has been reserved
[    0.406655] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.406657] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.406661] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
[    0.406665] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.406667] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.406671] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.406675] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.406677] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.406679] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.406681] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.441323] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.441326] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.441329] pci 0000:00:01.0:   MEM window: 0xfe700000-0xfe7fffff
[    0.441331] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.441334] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.441337] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
[    0.441340] pci 0000:00:1c.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.441343] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.441348] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.441350] pci 0000:00:1c.1:   IO window: 0xc000-0xcfff
[    0.441354] pci 0000:00:1c.1:   MEM window: 0xfe900000-0xfe9fffff
[    0.441357] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.441361] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.441363] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
[    0.441367] pci 0000:00:1c.2:   MEM window: 0xfea00000-0xfeafffff
[    0.441370] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.441374] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:05
[    0.441376] pci 0000:00:1c.5:   IO window: disabled
[    0.441379] pci 0000:00:1c.5:   MEM window: disabled
[    0.441382] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.441387] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.441389] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.441393] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.441395] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.441404] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.441407] pci 0000:00:01.0: setting latency timer to 64
[    0.441413] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.441416] pci 0000:00:1c.0: setting latency timer to 64
[    0.441421] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.441424] pci 0000:00:1c.1: setting latency timer to 64
[    0.441430] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441433] pci 0000:00:1c.2: setting latency timer to 64
[    0.441438] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.441441] pci 0000:00:1c.5: setting latency timer to 64
[    0.441446] pci 0000:00:1e.0: setting latency timer to 64
[    0.441449] bus: 00 index 0 io port: [0x00-0xffff]
[    0.441451] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.441452] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.441454] bus: 01 index 1 mmio: [0xfe700000-0xfe7fffff]
[    0.441455] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.441457] bus: 01 index 3 mmio: [0x0-0x0]
[    0.441458] bus: 02 index 0 io port: [0xb000-0xbfff]
[    0.441460] bus: 02 index 1 mmio: [0xfe800000-0xfe8fffff]
[    0.441461] bus: 02 index 2 mmio: [0x0-0x0]
[    0.441462] bus: 02 index 3 mmio: [0x0-0x0]
[    0.441463] bus: 03 index 0 io port: [0xc000-0xcfff]
[    0.441465] bus: 03 index 1 mmio: [0xfe900000-0xfe9fffff]
[    0.441466] bus: 03 index 2 mmio: [0x0-0x0]
[    0.441467] bus: 03 index 3 mmio: [0x0-0x0]
[    0.441469] bus: 04 index 0 io port: [0xd000-0xdfff]
[    0.441470] bus: 04 index 1 mmio: [0xfea00000-0xfeafffff]
[    0.441472] bus: 04 index 2 mmio: [0x0-0x0]
[    0.441473] bus: 04 index 3 mmio: [0x0-0x0]
[    0.441474] bus: 05 index 0 mmio: [0x0-0x0]
[    0.441475] bus: 05 index 1 mmio: [0x0-0x0]
[    0.441476] bus: 05 index 2 mmio: [0x0-0x0]
[    0.441478] bus: 05 index 3 mmio: [0x0-0x0]
[    0.441479] bus: 06 index 0 io port: [0xe000-0xefff]
[    0.441481] bus: 06 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.441482] bus: 06 index 2 mmio: [0x0-0x0]
[    0.441483] bus: 06 index 3 io port: [0x00-0xffff]
[    0.441485] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.441490] NET: Registered protocol family 2
[    0.456040] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.456199] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.456424] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.456537] TCP: Hash tables configured (established 131072 bind 65536)
[    0.456539] TCP reno registered
[    0.464054] NET: Registered protocol family 1
[    0.464130] checking if image is initramfs... it is
[    0.911204] Freeing initrd memory: 7371k freed
[    0.911361] cpufreq: No nForce2 chipset.
[    0.911463] audit: initializing netlink socket (disabled)
[    0.911480] type=2000 audit(1243875762.908:1): initialized
[    0.916725] highmem bounce pool size: 64 pages
[    0.916728] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.917671] VFS: Disk quotas dquot_6.5.1
[    0.917711] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.918137] fuse init (API version 7.10)
[    0.918196] msgmni has been set to 1698
[    0.918324] alg: No test for stdrng (krng)
[    0.918331] io scheduler noop registered
[    0.918333] io scheduler anticipatory registered
[    0.918334] io scheduler deadline registered
[    0.918344] io scheduler cfq registered (default)
[    0.918458] pci 0000:01:00.0: Boot video device
[    0.921167] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.921192] pcieport-driver 0000:00:01.0: found MSI capability
[    0.921209] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    0.921216] pci_express 0000:00:01.0:pcie00: allocate port service
[    0.921226] pci_express 0000:00:01.0:pcie03: allocate port service
[    0.921259] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.921285] pcieport-driver 0000:00:1c.0: found MSI capability
[    0.921304] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    0.921312] pci_express 0000:00:1c.0:pcie00: allocate port service
[    0.921321] pci_express 0000:00:1c.0:pcie02: allocate port service
[    0.921329] pci_express 0000:00:1c.0:pcie03: allocate port service
[    0.921371] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.921397] pcieport-driver 0000:00:1c.1: found MSI capability
[    0.921415] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    0.921424] pci_express 0000:00:1c.1:pcie00: allocate port service
[    0.921432] pci_express 0000:00:1c.1:pcie02: allocate port service
[    0.921443] pci_express 0000:00:1c.1:pcie03: allocate port service
[    0.921484] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.921510] pcieport-driver 0000:00:1c.2: found MSI capability
[    0.921528] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    0.921536] pci_express 0000:00:1c.2:pcie00: allocate port service
[    0.921545] pci_express 0000:00:1c.2:pcie02: allocate port service
[    0.921553] pci_express 0000:00:1c.2:pcie03: allocate port service
[    0.921595] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.921621] pcieport-driver 0000:00:1c.5: found MSI capability
[    0.921639] pcieport-driver 0000:00:1c.5: irq 2299 for MSI/MSI-X
[    0.921648] pci_express 0000:00:1c.5:pcie00: allocate port service
[    0.921656] pci_express 0000:00:1c.5:pcie02: allocate port service
[    0.921665] pci_express 0000:00:1c.5:pcie03: allocate port service
[    0.921715] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.922249] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.922351] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.922353] ACPI: Power Button (FF) [PWRF]
[    0.922390] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.922391] ACPI: Power Button (CM) [PWRB]
[    0.922585] processor ACPI_CPU:00: registered as cooling_device0
[    0.922613] processor ACPI_CPU:01: registered as cooling_device1
[    0.924449] isapnp: Scanning for PnP cards...
[    0.940553] Switched to high resolution mode on CPU 1
[    0.944039] Switched to high resolution mode on CPU 0
[    1.277256] isapnp: No Plug & Play device found
[    1.284582] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.284661] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.284924] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.285520] brd: module loaded
[    1.285736] loop: module loaded
[    1.285782] Fixed MDIO Bus: probed
[    1.285786] PPP generic driver version 2.4.2
[    1.285823] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.285842] Driver 'sd' needs updating - please use bus_type methods
[    1.285850] Driver 'sr' needs updating - please use bus_type methods
[    1.285880] ahci 0000:03:00.0: version 3.0
[    1.285910] ata_piix 0000:00:1f.2: version 2.12
[    1.285920] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.285922] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.285952] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.285993] scsi0 : ata_piix
[    1.286044] scsi1 : ata_piix
[    1.286912] ata1: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 19
[    1.286915] ata2: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 19
[    1.614539] ata1: SATA link down (SStatus 0 SControl 300)
[    1.942538] ata2: SATA link down (SStatus 0 SControl 300)
[    1.942554] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.942557] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.942583] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.942609] scsi2 : ata_piix
[    1.942646] scsi3 : ata_piix
[    1.943503] ata3: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7480 irq 19
[    1.943506] ata4: SATA max UDMA/133 cmd 0x7880 ctl 0x7800 bmdma 0x7488 irq 19
[    2.270514] ata3: SATA link down (SStatus 0 SControl 300)
[    2.598513] ata4: SATA link down (SStatus 0 SControl 300)
[    2.598567] sata_sil24 0000:02:00.0: version 1.1
[    2.598575] sata_sil24 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.598632] sata_sil24 0000:02:00.0: setting latency timer to 64
[    2.598736] scsi4 : sata_sil24
[    2.598775] scsi5 : sata_sil24
[    2.598801] ata5: SATA max UDMA/100 host m128@0xfe8ffc00 port 0xfe8f8000 irq 16
[    2.598804] ata6: SATA max UDMA/100 host m128@0xfe8ffc00 port 0xfe8fa000 irq 16
[    4.780036] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 0)
[    4.806107] ata5.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   11.996026] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 0)
[   11.996610] ata5.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[   11.996612] ata5.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   11.997332] ata5.00: configured for UDMA/100
[   14.180036] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 0)
[   14.206261] ata6.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   21.396026] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 0)
[   21.396599] ata6.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[   21.396600] ata6.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   21.397315] ata6.00: configured for UDMA/100
[   21.397389] scsi 4:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   21.397454] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   21.397466] sd 4:0:0:0: [sda] Write Protect is off
[   21.397467] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.397485] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.397528] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   21.397538] sd 4:0:0:0: [sda] Write Protect is off
[   21.397540] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.397557] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.397560]  sda: sda1 sda2 < sda5 sda6 >
[   21.453654] sd 4:0:0:0: [sda] Attached SCSI disk
[   21.453682] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   21.453739] scsi 5:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   21.453799] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   21.453810] sd 5:0:0:0: [sdb] Write Protect is off
[   21.453811] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   21.453829] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.453863] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   21.453873] sd 5:0:0:0: [sdb] Write Protect is off
[   21.453875] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   21.453892] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.453894]  sdb: sdb1
[   21.478488] sd 5:0:0:0: [sdb] Attached SCSI disk
[   21.478513] sd 5:0:0:0: Attached scsi generic sg1 type 0
[   21.478787] pata_marvell 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.478807] pata_marvell 0000:03:00.0: setting latency timer to 64
[   21.478851] scsi6 : pata_marvell
[   21.478888] scsi7 : pata_marvell
[   21.478914] ata7: PATA max UDMA/100 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 17
[   21.478915] ata8: PATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 17
[   21.640345] ata7.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB02, max UDMA/33
[   21.656359] ata7.00: configured for UDMA/33
[   21.823857] scsi 6:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB02 PQ: 0 ANSI: 5
[   21.831126] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.831128] Uniform CD-ROM driver Revision: 3.20
[   21.831190] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   21.831217] sr 6:0:0:0: Attached scsi generic sg2 type 5
[   21.831394] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   21.831407] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   21.831416] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   21.831419] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   21.831456] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   21.835359] ehci_hcd 0000:00:1a.7: debug port 1
[   21.835363] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[   21.835374] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe6ffc00
[   21.848006] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[   21.848051] usb usb1: configuration #1 chosen from 1 choice
[   21.848070] hub 1-0:1.0: USB hub found
[   21.848074] hub 1-0:1.0: 4 ports detected
[   21.848147] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   21.848155] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   21.848157] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.848185] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   21.852081] ehci_hcd 0000:00:1d.7: debug port 1
[   21.852086] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   21.852095] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe6ff800
[   21.864006] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   21.864053] usb usb2: configuration #1 chosen from 1 choice
[   21.864071] hub 2-0:1.0: USB hub found
[   21.864075] hub 2-0:1.0: 8 ports detected
[   21.864148] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.864160] uhci_hcd: USB Universal Host Controller Interface driver
[   21.864173] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.864177] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[   21.864180] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   21.864209] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   21.864227] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00009c00
[   21.864276] usb usb3: configuration #1 chosen from 1 choice
[   21.864294] hub 3-0:1.0: USB hub found
[   21.864298] hub 3-0:1.0: 2 ports detected
[   21.864355] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   21.864359] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[   21.864361] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   21.864391] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   21.864414] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00009880
[   21.864464] usb usb4: configuration #1 chosen from 1 choice
[   21.864481] hub 4-0:1.0: USB hub found
[   21.864485] hub 4-0:1.0: 2 ports detected
[   21.864546] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   21.864550] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   21.864552] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.864579] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   21.864597] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009800
[   21.864645] usb usb5: configuration #1 chosen from 1 choice
[   21.864664] hub 5-0:1.0: USB hub found
[   21.864668] hub 5-0:1.0: 2 ports detected
[   21.864724] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   21.864728] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   21.864730] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.864757] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   21.864775] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009480
[   21.864823] usb usb6: configuration #1 chosen from 1 choice
[   21.864840] hub 6-0:1.0: USB hub found
[   21.864844] hub 6-0:1.0: 2 ports detected
[   21.864899] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   21.864903] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   21.864905] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.864937] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   21.864955] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009400
[   21.865002] usb usb7: configuration #1 chosen from 1 choice
[   21.865019] hub 7-0:1.0: USB hub found
[   21.865023] hub 7-0:1.0: 2 ports detected
[   21.865081] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[   21.865085] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   21.865087] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   21.865115] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[   21.865132] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00009080
[   21.865185] usb usb8: configuration #1 chosen from 1 choice
[   21.865202] hub 8-0:1.0: USB hub found
[   21.865206] hub 8-0:1.0: 2 ports detected
[   21.865292] usbcore: registered new interface driver libusual
[   21.865315] usbcore: registered new interface driver usbserial
[   21.865322] USB Serial support registered for generic
[   21.865334] usbcore: registered new interface driver usbserial_generic
[   21.865336] usbserial: USB Serial Driver core
[   21.865373] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   21.865374] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   21.865708] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.868527] mice: PS/2 mouse device common for all mice
[   21.880547] rtc_cmos 00:03: RTC can wake from S4
[   21.880569] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[   21.880588] rtc0: alarms up to one month, y3k, 114 bytes nvram
[   21.880628] device-mapper: uevent: version 1.0.3
[   21.880686] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   21.880736] device-mapper: multipath: version 1.0.5 loaded
[   21.880738] device-mapper: multipath round-robin: version 1.0.0 loaded
[   21.880790] EISA: Probing bus 0 at eisa.0
[   21.880808] Cannot allocate resource for EISA slot 7
[   21.880809] Cannot allocate resource for EISA slot 8
[   21.880811] EISA: Detected 0 cards.
[   21.880845] cpuidle: using governor ladder
[   21.880846] cpuidle: using governor menu
[   21.881197] TCP cubic registered
[   21.881266] NET: Registered protocol family 10
[   21.881566] lo: Disabled Privacy Extensions
[   21.881796] NET: Registered protocol family 17
[   21.881807] Bluetooth: L2CAP ver 2.11
[   21.881808] Bluetooth: L2CAP socket layer initialized
[   21.881810] Bluetooth: SCO (Voice Link) ver 0.6
[   21.881811] Bluetooth: SCO socket layer initialized
[   21.881828] Bluetooth: RFCOMM socket layer initialized
[   21.881832] Bluetooth: RFCOMM TTY layer initialized
[   21.881833] Bluetooth: RFCOMM ver 1.10
[   21.881871] Using IPI No-Shortcut mode
[   21.881918] registered taskstats version 1
[   21.882018]   Magic number: 13:836:35
[   21.882026] bdi 7:0: hash matches
[   21.882064] rtc_cmos 00:03: setting system clock to 2009-06-01 17:03:05 UTC (1243875785)
[   21.882066] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.882067] EDD information not available.
[   21.882231] Freeing unused kernel memory: 532k freed
[   21.882317] Write protecting the kernel text: 4128k
[   21.882348] Write protecting the kernel read-only data: 1532k
[   21.899765] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   22.053519] ohci1394 0000:06:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.106202] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[febdf800-febdffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   22.116421] sky2 driver version 1.22
[   22.116456] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.116466] sky2 0000:04:00.0: setting latency timer to 64
[   22.116501] sky2 0000:04:00.0: Yukon-2 EC Ultra chip revision 3
[   22.148394] sky2 0000:04:00.0: Marvell Yukon 88E8056 Gigabit Ethernet Controller
[   22.148397]  Part Number: Yukon 88E8056
[   22.148398]  Engineering Level: Rev. 1.2
[   22.148399]  Manufacturer: Marvell
[   22.148449] sky2 0000:04:00.0: irq 2298 for MSI/MSI-X
[   22.165283] sky2 eth0: addr 00:19:db:f2:36:7a
[   22.328508] usb 2-3: new high speed USB device using ehci_hcd and address 2
[   22.460229] PM: Starting manual resume from disk
[   22.460231] PM: Resume from partition 8:6
[   22.460232] PM: Checking hibernation image.
[   22.460343] PM: Resume from disk failed.
[   22.469201] usb 2-3: configuration #1 chosen from 1 choice
[   22.472336] Initializing USB Mass Storage driver...
[   22.472403] scsi8 : SCSI emulation for USB Mass Storage devices
[   22.472458] usbcore: registered new interface driver usb-storage
[   22.472460] USB Mass Storage support registered.
[   22.472513] usb-storage: device found at 2
[   22.472515] usb-storage: waiting for device to settle before scanning
[   22.475993] EXT4-fs: barriers enabled
[   22.486186] kjournald2 starting.  Commit interval 5 seconds
[   22.486198] EXT4-fs: delayed allocation enabled
[   22.486199] EXT4-fs: file extents enabled
[   22.492565] EXT4-fs: mballoc enabled
[   22.492568] EXT4-fs: mounted filesystem with ordered data mode.
[   22.708009] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   22.888315] usb 3-1: configuration #1 chosen from 1 choice
[   23.128011] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   23.304504] usb 4-1: configuration #1 chosen from 1 choice
[   23.469546] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a270002ad5cb0]
[   23.469593] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0010dc00012e3ef5]
[   25.851338] udev: starting version 141
[   25.946687] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   25.946753] usbcore: registered new interface driver btusb
[   26.166673] Linux agpgart interface v0.103
[   26.218987] iTCO_vendor_support: vendor-support=0
[   26.220185] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   26.220360] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0860)
[   26.220420] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.223394] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   26.230987] scsi9 : SBP-2 IEEE-1394
[   26.231066] ieee1394: sbp2: Workarounds for node 0-00:1023: 0x8 (firmware_revision 0x0a2700, vendor_id 0x000a27, model_id 0x000021)
[   26.280902] usbcore: registered new interface driver hiddev
[   26.294653] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input5
[   26.304406] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.1-1/input0
[   26.304422] usbcore: registered new interface driver usbhid
[   26.304438] usbhid: v2.6:USB HID core driver
[   26.635367] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.635411] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.665914] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   26.699243] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   26.699270] HDA Intel 0000:01:00.1: setting latency timer to 64
[   27.235177] ieee1394: sbp2: Logged into SBP-2 device
[   27.235700] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   27.239155] scsi 9:0:0:0: Direct-Access-RBC Apple    iPod             1.62 PQ: 0 ANSI: 0
[   27.259945] sd 9:0:0:0: [sdc] Spinning up disk...<7>usb-storage: device scan complete
[   27.472591] scsi 8:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
[   27.473605] sd 8:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[   27.474080] sd 8:0:0:0: [sdd] Write Protect is off
[   27.474082] sd 8:0:0:0: [sdd] Mode Sense: 23 00 00 00
[   27.474083] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[   27.474706] sd 8:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[   27.475204] sd 8:0:0:0: [sdd] Write Protect is off
[   27.475206] sd 8:0:0:0: [sdd] Mode Sense: 23 00 00 00
[   27.475207] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[   27.475210]  sdd:...ready
[   30.318922] sd 9:0:0:0: [sdc] 39063023 512-byte hardware sectors: (20.0 GB/18.6 GiB)
[   30.320492] sd 9:0:0:0: [sdc] Write Protect is off
[   30.320494] sd 9:0:0:0: [sdc] Mode Sense: 04 00 00 00
[   30.323841] sd 9:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   30.328683] sd 9:0:0:0: [sdc] 39063023 512-byte hardware sectors: (20.0 GB/18.6 GiB)
[   30.330215] sd 9:0:0:0: [sdc] Write Protect is off
[   30.330217] sd 9:0:0:0: [sdc] Mode Sense: 04 00 00 00
[   30.333290] sd 9:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   30.333293]  sdc: sdc1 sdc2
[   30.409472] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[   30.409552] sd 9:0:0:0: Attached scsi generic sg3 type 14
[   30.839432] lp: driver loaded but no devices found
[   30.888457] Adding 4867652k swap on /dev/sda6.  Priority:-1 extents:1 across:4867652k
[   31.413253] EXT4 FS on sda5, internal journal on sda5:8
[   32.252378] type=1505 audit(1243872195.869:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2134
[   32.284972] type=1505 audit(1243872195.901:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2138
[   32.285032] type=1505 audit(1243872195.901:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2138
[   32.285060] type=1505 audit(1243872195.901:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2138
[   32.285086] type=1505 audit(1243872195.901:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2138
[   32.375320] type=1505 audit(1243872195.989:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2143
[   32.375418] type=1505 audit(1243872195.989:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2143
[   32.394660] type=1505 audit(1243872196.009:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2147
[   34.046709] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.046711] Bluetooth: BNEP filters: protocol multicast
[   34.057329] Bridge firewalling registered
[   34.789624]  sdd1
[   34.789717] sd 8:0:0:0: [sdd] Attached SCSI disk
[   34.789768] sd 8:0:0:0: Attached scsi generic sg4 type 0
[   34.819792] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   34.912124] [drm] Initialized drm 1.1.0 20060810
[   35.100618] ppdev: user-space parallel port driver
[   35.174727] pci 0000:01:00.0: setting latency timer to 64
[   35.174829] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   35.438241] [drm] Setting GART location based on new memory map
[   35.453758] [drm] Loading RV670 CP Microcode
[   35.453891] [drm] Loading RV670 PFP Microcode
[   35.468801] [drm] Resetting GPU
[   35.468856] [drm] writeback test succeeded in 1 usecs
[   39.385614] sky2 eth0: enabling interface
[   39.385762] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.049667] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   42.049807] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   52.124004] eth0: no IPv6 routers present
[  327.079503] ip_tables: (C) 2000-2006 Netfilter Core Team
[  334.448008] usb 2-4: new high speed USB device using ehci_hcd and address 3
[  334.583950] usb 2-4: configuration #1 chosen from 1 choice
[  334.588567] scsi10 : SCSI emulation for USB Mass Storage devices
[  334.597018] usb-storage: device found at 3
[  334.597020] usb-storage: waiting for device to settle before scanning
[  339.596338] usb-storage: device scan complete
[  339.597208] scsi 10:0:0:0: Direct-Access     Freecom  DataBar USB2.0   1100 PQ: 0 ANSI: 0 CCS
[  339.599320] sd 10:0:0:0: [sde] 31326208 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[  339.600869] sd 10:0:0:0: [sde] Write Protect is off
[  339.600872] sd 10:0:0:0: [sde] Mode Sense: 43 00 00 00
[  339.600873] sd 10:0:0:0: [sde] Assuming drive cache: write through
[  339.603946] sd 10:0:0:0: [sde] 31326208 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[  339.605195] sd 10:0:0:0: [sde] Write Protect is off
[  339.605197] sd 10:0:0:0: [sde] Mode Sense: 43 00 00 00
[  339.605198] sd 10:0:0:0: [sde] Assuming drive cache: write through
[  339.605202]  sde: sde1
[  339.606205] sd 10:0:0:0: [sde] Attached SCSI removable disk
[  339.606370] sd 10:0:0:0: Attached scsi generic sg5 type 0
[  354.675521] tcpdump uses obsolete (PF_INET,SOCK_PACKET)
[  357.436512] device eth0 entered promiscuous mode
[  365.004507] device eth0 left promiscuous mode
[  415.311406] device eth0 entered promiscuous mode
[  446.608582] device eth0 left promiscuous mode
[  483.395039] device eth0 entered promiscuous mode
```

tail -50 /var/log/messages

```
Jun  1 17:03:16 desktop kernel: [   30.409472] sd 9:0:0:0: [sdc] Attached SCSI removable disk
Jun  1 17:03:16 desktop kernel: [   30.409552] sd 9:0:0:0: Attached scsi generic sg3 type 14
Jun  1 17:03:16 desktop kernel: [   30.839432] lp: driver loaded but no devices found
Jun  1 17:03:16 desktop kernel: [   30.888457] Adding 4867652k swap on /dev/sda6.  Priority:-1 extents:1 across:4867652k
Jun  1 17:03:16 desktop kernel: [   31.413253] EXT4 FS on sda5, internal journal on sda5:8
Jun  1 17:03:16 desktop kernel: [   32.252378] type=1505 audit(1243872195.869:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2134
Jun  1 17:03:16 desktop kernel: [   32.284972] type=1505 audit(1243872195.901:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2138
Jun  1 17:03:16 desktop kernel: [   32.285032] type=1505 audit(1243872195.901:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2138
Jun  1 17:03:16 desktop kernel: [   32.285060] type=1505 audit(1243872195.901:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2138
Jun  1 17:03:16 desktop kernel: [   32.285086] type=1505 audit(1243872195.901:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2138
Jun  1 17:03:16 desktop kernel: [   32.375320] type=1505 audit(1243872195.989:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2143
Jun  1 17:03:16 desktop kernel: [   32.375418] type=1505 audit(1243872195.989:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2143
Jun  1 17:03:16 desktop kernel: [   32.394660] type=1505 audit(1243872196.009:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2147
Jun  1 17:03:17 desktop kernel: [   34.046709] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun  1 17:03:17 desktop kernel: [   34.046711] Bluetooth: BNEP filters: protocol multicast
Jun  1 17:03:17 desktop kernel: [   34.057329] Bridge firewalling registered
Jun  1 17:03:18 desktop kernel: [   34.789624]  sdd1
Jun  1 17:03:18 desktop kernel: [   34.789717] sd 8:0:0:0: [sdd] Attached SCSI disk
Jun  1 17:03:18 desktop kernel: [   34.789768] sd 8:0:0:0: Attached scsi generic sg4 type 0
Jun  1 17:03:18 desktop kernel: [   34.819792] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  1 17:03:18 desktop kernel: [   34.912124] [drm] Initialized drm 1.1.0 20060810
Jun  1 17:03:18 desktop kernel: [   35.100618] ppdev: user-space parallel port driver
Jun  1 17:03:18 desktop kernel: [   35.174829] [drm] Initialized radeon 1.29.0 20080528 on minor 0
Jun  1 17:03:19 desktop kernel: [   35.438241] [drm] Setting GART location based on new memory map
Jun  1 17:03:19 desktop kernel: [   35.453758] [drm] Loading RV670 CP Microcode
Jun  1 17:03:19 desktop kernel: [   35.453891] [drm] Loading RV670 PFP Microcode
Jun  1 17:03:19 desktop kernel: [   35.468801] [drm] Resetting GPU
Jun  1 17:03:19 desktop kernel: [   35.468856] [drm] writeback test succeeded in 1 usecs
Jun  1 17:03:23 desktop kernel: [   39.385614] sky2 eth0: enabling interface
Jun  1 17:03:23 desktop kernel: [   39.385762] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  1 17:03:25 desktop kernel: [   42.049667] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
Jun  1 17:03:25 desktop kernel: [   42.049807] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  1 17:08:10 desktop kernel: [  327.079503] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun  1 17:08:18 desktop kernel: [  334.448008] usb 2-4: new high speed USB device using ehci_hcd and address 3
Jun  1 17:08:18 desktop kernel: [  334.583950] usb 2-4: configuration #1 chosen from 1 choice
Jun  1 17:08:18 desktop kernel: [  334.588567] scsi10 : SCSI emulation for USB Mass Storage devices
Jun  1 17:08:23 desktop kernel: [  339.597208] scsi 10:0:0:0: Direct-Access     Freecom  DataBar USB2.0   1100 PQ: 0 ANSI: 0 CCS
Jun  1 17:08:23 desktop kernel: [  339.599320] sd 10:0:0:0: [sde] 31326208 512-byte hardware sectors: (16.0 GB/14.9 GiB)
Jun  1 17:08:23 desktop kernel: [  339.600869] sd 10:0:0:0: [sde] Write Protect is off
Jun  1 17:08:23 desktop kernel: [  339.603946] sd 10:0:0:0: [sde] 31326208 512-byte hardware sectors: (16.0 GB/14.9 GiB)
Jun  1 17:08:23 desktop kernel: [  339.605195] sd 10:0:0:0: [sde] Write Protect is off
Jun  1 17:08:23 desktop kernel: [  339.605202]  sde: sde1
Jun  1 17:08:23 desktop kernel: [  339.606205] sd 10:0:0:0: [sde] Attached SCSI removable disk
Jun  1 17:08:23 desktop kernel: [  339.606370] sd 10:0:0:0: Attached scsi generic sg5 type 0
Jun  1 17:08:38 desktop kernel: [  354.675521] tcpdump uses obsolete (PF_INET,SOCK_PACKET)
Jun  1 17:08:41 desktop kernel: [  357.436512] device eth0 entered promiscuous mode
Jun  1 17:08:48 desktop kernel: [  365.004507] device eth0 left promiscuous mode
Jun  1 17:09:38 desktop kernel: [  415.311406] device eth0 entered promiscuous mode
Jun  1 17:10:10 desktop kernel: [  446.608582] device eth0 left promiscuous mode
Jun  1 17:10:47 desktop kernel: [  483.395039] device eth0 entered promiscuous mode
```

and netstat -na | grep LIST | grep '*'

```
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
```


Man that was a lot, I hope it means more to you than it does to me... !


[/QUOTE]

---

### Post by andydrizen on 2009-06-01
Thanks for your response - I've tried setting the gateway of the client to the ip of the other machine, but this didn't work - i tried doing it by adding a "route". I'm not really sure what I should be doing - do you know the commands that would do that? The "server" has a wifi interface too, the other machine has just an ethernet card.

---

### Post by puppywhacker on 2009-06-01
I suspect a faulty cable

boy, that sure was a lot of info =) I can't really find anything wrong except the server doesn't receive anything. maybe there is a little cable break, or the autosensing of the crossover-cable doesn't work

```
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0

```

routing wise, once you set the ip address, the route that fits in the netmask 10.0.1.255 is automatically set

as a way of testing use ssh from the client to the server like this, I bet for now it only shows local commands
```
ssh -v user@10.0.1.1
```

the tcpdumps show broadcast traffic from the server reaching the client, and the client broadcasting to the server, but not being received on the server side.

arp should have shown the addresses it learned, but that means no responses were received.

purely maybe 1000baseT-FD is too fast, with mii-tool you can also manually override the speedsetting, try 100baseT-FD on both sides and see that your server receives something. but that is just guessing.

---

### Post by andydrizen on 2009-06-01
ah. Ok. Well I just switched cables and still have the same problem :-(

Also,

```
andy@server:~$ sudo mii-tool -F 100baseTx-FD
SIOCGMIIPHY on 'eth0' failed: Operation not supported
```

nothing about eth1...? Perhaps a fresh install will be useful...

---

### Post by Iowan on 2009-06-01
Just a li'l sidenote from [here]("http://www.mail-archive.com/netdev@vger.kernel.org/msg08511.html"):> Not all cards support MII, since MII is fairly old and isn't really
applicable everywhere.  It's not really "standard", just happens to be
around on a lot of cards.  You would probably get better luck with
ethtool, which is the way of the future, and card/media independent.I can't vouch for accuracy...
One other thing... have you tried a straight cable on the 1000baseT-FD cards? I read somewhere that they don't need (want?) crossover.

---

