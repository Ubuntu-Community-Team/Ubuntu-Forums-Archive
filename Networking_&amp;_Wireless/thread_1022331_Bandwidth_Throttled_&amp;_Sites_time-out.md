---
title: "Bandwidth Throttled &amp; Sites time-out"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by Zizzech on 2008-12-26
8.10;
Computer Model: Gateway FX6800
Browsers: Firefox, Lynx, and Konquorer
ISP/Package: RoadRunner Turbo

I'm suppose to be getting 1.5MB/s DL & 1MB/s UL, 
I get this on Mac & Windows on the same computer, 
but on Ubuntu I get a max of 465KB/s DL & 128KB/s UL

Some websites time-out, (pinging aswell), eg. h33t.com 
(use an adblocker & popup blocker)
It's not random, just that
Yes I've checked traceroute (and any other of the like), useless

My DNS, Gateway, and DHCP are the same on the OSs, 
IPv6 is disabled
My bandwidth are at their tops when on Mac & Windows, no websites blocked
this is not the same for Ubuntu

It isn't server-side or my router, 
as I said already everything is fine with Mac and Windows

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:22:68:38:44:82  
          inet addr:72.224.170.255  Bcast:72.224.175.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:11318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1508216 (1.5 MB)  TX bytes:171252 (171.2 KB)
          Memory:fbac0000-fbae0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:784 (784.0 B)  TX bytes:784 (784.0 B)

```

/etc/modprobe.d/aliases
```

# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
#alias net-pf-3  ax25
#alias net-pf-4  ipx
#alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
#####EDIT START#####
#alias net-pf-10 ipv6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
######EDIT END######
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

alias net-pf-16-proto-1 wire
alias net-pf-16-proto-3 ip_queue
alias net-pf-16-proto-4 tcp_diag
alias net-pf-16-proto-8 scsi_transport_iscsi
alias net-pf-16-proto-9 audit
alias net-pf-16-proto-11 cn
alias net-pf-16-proto-13 ip6_queue

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-187 irnet
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore

```

Changing the MTU doesn't help with the bandwidth

I've tried connection to h33t from the LiveCD, timed out

/etc/network/interfaces
```

#auto eth0
#iface eth0 inet dhcp
auto lo
iface lo inet loopback

```

/etc/resolv.conf
```

# Generated by NetworkManager
domain maine.rr.com
search maine.rr.com
nameserver 24.92.226.40
nameserver 24.92.226.41

```

Found these users who also share the problem:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59331](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59331)
[http://www.linuxquestions.org/questions/linux-software-2/how-can-i-increase-net-speed-on-ubuntu-xp-is-faster-weird-673804/](http://www.linuxquestions.org/questions/linux-software-2/how-can-i-increase-net-speed-on-ubuntu-xp-is-faster-weird-673804/)
[http://www.mydatabasesupport.com/forums/unix-os-discussions/156427-re-only-some-websites-will-open-ubuntu.html](http://www.mydatabasesupport.com/forums/unix-os-discussions/156427-re-only-some-websites-will-open-ubuntu.html)

---

### Post by Zizzech on 2008-12-26
Bump :/

---

### Post by Zizzech on 2008-12-27
I've changed my DNS to OpenDNS
208.67.222.222
208.67.220.220

Nothing has changed; connection still throttled & can't view site h33t.com
But I can use a proxy to visit it, just like before

EDIT]
I have 2 computers, 1 I upgraded from 8.04 to 8.10 and another I installed fresh 8.10;
before the upgrade, my bandwidth was fine and I could view h33t.com,
after I upgraded/used 8.10 my bandwidth was throttled and h33t timed out always, though it didn't in 8.04

---

### Post by Zizzech on 2008-12-27
bump!

---

### Post by Zizzech on 2008-12-27
bump :/

---

### Post by Zizzech on 2008-12-28
bump

---

### Post by Tom--d on 2008-12-28
Post the outcome of please
```
lspci
```


It could be many things.
To me, it may be a driver issue, but don't take my word on that.

---

### Post by Zizzech on 2008-12-28
root32@D3RGPS31:~$ lspci
00:00.0 Host bridge: Intel Corporation QuickPath Architecture I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 7 (rev 12)
00:10.0 PIC: Intel Corporation QuickPath Interconnect Physical and Link Layer Registers Port 0 (rev 12)
00:10.1 PIC: Intel Corporation QuickPath Interconnect Routing and Protocol Layer Registers Port 0 (rev 12)
00:13.0 PIC: Intel Corporation QuickPath Architecture I/O Hub I/OxAPIC Interrupt Controller (rev 12)
00:14.0 PIC: Intel Corporation QuickPath Architecture I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation QuickPath Architecture I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation QuickPath Architecture I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation QuickPath Architecture I/O Hub Throttle Registers (rev 12)
00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
02:00.0 Communication controller: Agere Systems Device 0630 (rev 01)
04:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
04:00.1 Audio device: ATI Technologies Inc HD48x0 audio
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)

---

### Post by Tom--d on 2008-12-28
Thanks,

Your ethernet card is:

00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection

It should work properly.
Maybe your dreaming :P

Can you post the outcome of dmesg but put it in [*code] dmesg output [*/code] (Remove the *) Please.

---

### Post by Dr Small on 2008-12-28
> **Tom--d said:**
> 
Can you post the outcome of dmesg but put it in [*code] dmesg output [*/code] (Remove the *) Please.

Isn't easier just to say it like this?
[noparse]```
dmesg output
```[/noparse]

:D

---

### Post by Zizzech on 2008-12-28
```

root32@D3RGPS31:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf790000 (usable)
[    0.000000]  BIOS-e820: 00000000bf790000 - 00000000bf79e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf79e000 - 00000000bf7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7d0000 - 00000000bf7e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf7ec000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xbf790 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781e000 - 37fef751
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000FA3B0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT BF790100, 0064 (r1 ACRSYS ACRPRDCT 20080927 MSFT       97)
[    0.000000] ACPI: FACP BF790290, 00F4 (r4 GATEWA FACP1520 20080927 MSFT       97)
[    0.000000] ACPI: DSDT BF7905F0, 6EBC (r2  842P0 842P091G        4 INTL 20051117)
[    0.000000] ACPI: FACS BF79E000, 0040
[    0.000000] ACPI: APIC BF790390, 0098 (r2 GATEWA APIC1520 20080927 MSFT       97)
[    0.000000] ACPI: MCFG BF790430, 003C (r1 GATEWA OEMMCFG  20080927 MSFT       97)
[    0.000000] ACPI: SLIC BF790470, 0176 (r1 ACRSYS ACRPRDCT 20080927 MSFT       97)
[    0.000000] ACPI: OEMB BF79E040, 0072 (r1 GATEWA OEMB1520 20080927 MSFT       97)
[    0.000000] ACPI: DMAR BF79E0C0, 0138 (r1    AMI  OEMDMAR        1 MSFT       97)
[    0.000000] ACPI: AWMI BF79E200, 004E (r1 GATEWA OEMB1520 20080927 MSFT       97)
[    0.000000] ACPI: SSDT BF7A0880, 1298 (r1 DpgPmm    CpuPm       12 INTL 20051117)
[    0.000000] 2167MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003781e000 - 0037fef751]          RAMDISK ==> [003781e000 - 0037fef751]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000bf790
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bf790
[    0.000000] On node 0 totalpages: 784173
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 550018 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec8a000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 32, address 0xfec8a000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fec8a000)
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ee00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777279
[    0.000000] Kernel command line: root=UUID=9e215603-fde3-4dc7-a7cd-e56661ae8903 ro quiet vga=775 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2666.231 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3094056k/3137088k available (2572k kernel code, 41700k reserved, 1160k data, 424k init, 2219584k highmem)
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
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5332.46 BogoMIPS (lpj=10664924)
[    0.004015] Security Framework initialized
[    0.004018] SELinux:  Disabled at boot.
[    0.004031] AppArmor: AppArmor initialized
[    0.004035] Mount-cache hash table entries: 512
[    0.004132] Initializing cgroup subsys ns
[    0.004135] Initializing cgroup subsys cpuacct
[    0.004137] Initializing cgroup subsys memory
[    0.004146] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004148] CPU: L2 cache: 256K
[    0.004149] CPU: L3 cache: 8192K
[    0.004151] CPU: Physical Processor ID: 0
[    0.004152] CPU: Processor Core ID: 0
[    0.004154] using mwait in idle threads.
[    0.004158] Checking 'hlt' instruction... OK.
[    0.021274] ACPI: Core revision 20080609
[    0.023095] ACPI: Checking initramfs for custom DSDT
[    0.288331] ENABLING IO-APIC IRQs
[    0.288501] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.330606] CPU0: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.332020] Booting processor 1/2 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 13331.64 BogoMIPS (lpj=26663290)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.416453] CPU1: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.416468] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.420026] Measured 56 cycles TSC warp between CPUs, turning off TSC clock.
[    0.420026] Marking TSC unstable due to check_tsc_sync_source failed
[    0.420090] Booting processor 2/4 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 5332.68 BogoMIPS (lpj=10665370)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.508471] CPU2: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.508557] Booting processor 3/6 ip 6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 5332.69 BogoMIPS (lpj=10665380)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.596474] CPU3: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.596556] Booting processor 4/1 ip 6000
[    0.004000] Initializing CPU#4
[    0.004000] Calibrating delay using timer specific routine.. 5332.68 BogoMIPS (lpj=10665375)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.684515] CPU4: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.684600] Booting processor 5/3 ip 6000
[    0.004000] Initializing CPU#5
[    0.004000] Calibrating delay using timer specific routine.. 5332.68 BogoMIPS (lpj=10665372)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.772523] CPU5: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.772609] Booting processor 6/5 ip 6000
[    0.004000] Initializing CPU#6
[    0.004000] Calibrating delay using timer specific routine.. 5332.68 BogoMIPS (lpj=10665365)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.860614] CPU6: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.860698] Booting processor 7/7 ip 6000
[    0.004000] Initializing CPU#7
[    0.004000] Calibrating delay using timer specific routine.. 5332.68 BogoMIPS (lpj=10665370)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.948522] CPU7: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 04
[    0.948554] Brought up 8 CPUs
[    0.948556] Total of 8 processors activated (50660.22 BogoMIPS).
[    0.948577] CPU0 attaching sched-domain:
[    0.948579]  domain 0: span 0,4 level SIBLING
[    0.948581]   groups: 0 4
[    0.948584]   domain 1: span 0-7 level MC
[    0.948585]    groups: 0,4 1,5 2,6 3,7
[    0.948589] CPU1 attaching sched-domain:
[    0.948591]  domain 0: span 1,5 level SIBLING
[    0.948592]   groups: 1 5
[    0.948594]   domain 1: span 0-7 level MC
[    0.948596]    groups: 1,5 2,6 3,7 0,4
[    0.948599] CPU2 attaching sched-domain:
[    0.948600]  domain 0: span 2,6 level SIBLING
[    0.948602]   groups: 2 6
[    0.948604]   domain 1: span 0-7 level MC
[    0.948605]    groups: 2,6 3,7 0,4 1,5
[    0.948609] CPU3 attaching sched-domain:
[    0.948610]  domain 0: span 3,7 level SIBLING
[    0.948611]   groups: 3 7
[    0.948614]   domain 1: span 0-7 level MC
[    0.948615]    groups: 3,7 0,4 1,5 2,6
[    0.948618] CPU4 attaching sched-domain:
[    0.948620]  domain 0: span 0,4 level SIBLING
[    0.948621]   groups: 4 0
[    0.948623]   domain 1: span 0-7 level MC
[    0.948625]    groups: 0,4 1,5 2,6 3,7
[    0.948628] CPU5 attaching sched-domain:
[    0.948629]  domain 0: span 1,5 level SIBLING
[    0.948631]   groups: 5 1
[    0.948633]   domain 1: span 0-7 level MC
[    0.948634]    groups: 1,5 2,6 3,7 0,4
[    0.948638] CPU6 attaching sched-domain:
[    0.948639]  domain 0: span 2,6 level SIBLING
[    0.948640]   groups: 6 2
[    0.948643]   domain 1: span 0-7 level MC
[    0.948644]    groups: 2,6 3,7 0,4 1,5
[    0.948648] CPU7 attaching sched-domain:
[    0.948649]  domain 0: span 3,7 level SIBLING
[    0.948650]   groups: 7 3
[    0.948652]   domain 1: span 0-7 level MC
[    0.948654]    groups: 3,7 0,4 1,5 2,6
[    0.948774] net_namespace: 840 bytes
[    0.948774] Booting paravirtualized kernel on bare hardware
[    0.948774] Time:  6:14:50  Date: 12/28/08
[    0.948774] NET: Registered protocol family 16
[    0.948774] EISA bus registered
[    0.948774] ACPI: bus type pci registered
[    0.948774] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.948774] PCI: Not using MMCONFIG.
[    0.948774] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.948774] PCI: Using configuration type 1 for base access
[    0.948774] ACPI: EC: Look up EC in DSDT
[    0.960925] ACPI: Interpreter enabled
[    0.960927] ACPI: (supports S0 S1 S3 S4 S5)
[    0.960939] ACPI: Using IOAPIC for interrupt routing
[    0.960992] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.967118] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.967120] PCI: Using MMCONFIG for extended config space
[    0.976146] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.976146] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.976146] pci 0000:00:01.0: PME# disabled
[    0.976156] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.976158] pci 0000:00:03.0: PME# disabled
[    0.976199] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.976202] pci 0000:00:07.0: PME# disabled
[    0.976296] PCI: 0000:00:13.0 reg 10 32bit mmio: [fec8a000, fec8afff]
[    0.976322] pci 0000:00:13.0: PME# supported from D0 D3hot D3cold
[    0.976325] pci 0000:00:13.0: PME# disabled
[    0.976500] PCI: 0000:00:19.0 reg 10 32bit mmio: [fbac0000, fbadffff]
[    0.976505] PCI: 0000:00:19.0 reg 14 32bit mmio: [fbaf2000, fbaf2fff]
[    0.976510] PCI: 0000:00:19.0 reg 18 io port: [a080, a09f]
[    0.976538] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.976541] pci 0000:00:19.0: PME# disabled
[    0.976577] PCI: 0000:00:1a.0 reg 20 io port: [a400, a41f]
[    0.976631] PCI: 0000:00:1a.1 reg 20 io port: [a480, a49f]
[    0.976685] PCI: 0000:00:1a.2 reg 20 io port: [a800, a81f]
[    0.976742] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fbaf8000, fbaf83ff]
[    0.976784] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.976787] pci 0000:00:1a.7: PME# disabled
[    0.976814] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fbaf4000, fbaf7fff]
[    0.976846] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.976849] pci 0000:00:1b.0: PME# disabled
[    0.976890] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.976892] pci 0000:00:1c.0: PME# disabled
[    0.976935] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.976938] pci 0000:00:1c.4: PME# disabled
[    0.976977] PCI: 0000:00:1d.0 reg 20 io port: [a880, a89f]
[    0.977031] PCI: 0000:00:1d.1 reg 20 io port: [ac00, ac1f]
[    0.977085] PCI: 0000:00:1d.2 reg 20 io port: [b000, b01f]
[    0.977142] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fbafa000, fbafa3ff]
[    0.977183] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.977187] pci 0000:00:1d.7: PME# disabled
[    0.977320] PCI: 0000:00:1f.2 reg 10 io port: [b880, b887]
[    0.977324] PCI: 0000:00:1f.2 reg 14 io port: [b800, b803]
[    0.977329] PCI: 0000:00:1f.2 reg 18 io port: [b480, b487]
[    0.977333] PCI: 0000:00:1f.2 reg 1c io port: [b400, b403]
[    0.977338] PCI: 0000:00:1f.2 reg 20 io port: [b080, b09f]
[    0.977342] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fbafc000, fbafc7ff]
[    0.977362] pci 0000:00:1f.2: PME# supported from D3hot
[    0.977365] pci 0000:00:1f.2: PME# disabled
[    0.977381] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fbaffc00, fbaffcff]
[    0.977392] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.977473] PCI: 0000:06:00.0 reg 24 32bit mmio: [fbefe000, fbefffff]
[    0.977495] pci 0000:06:00.0: PME# supported from D3hot
[    0.977499] pci 0000:06:00.0: PME# disabled
[    0.977528] PCI: 0000:06:00.1 reg 10 io port: [ec00, ec07]
[    0.977535] PCI: 0000:06:00.1 reg 14 io port: [e880, e883]
[    0.977541] PCI: 0000:06:00.1 reg 18 io port: [e800, e807]
[    0.977548] PCI: 0000:06:00.1 reg 1c io port: [e480, e483]
[    0.977554] PCI: 0000:06:00.1 reg 20 io port: [e400, e40f]
[    0.977603] PCI: bridge 0000:00:01.0 io port: [e000, efff]
[    0.977606] PCI: bridge 0000:00:01.0 32bit mmio: [fbe00000, fbefffff]
[    0.977654] PCI: 0000:04:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.977664] PCI: 0000:04:00.0 reg 18 64bit mmio: [fbde0000, fbdeffff]
[    0.977669] PCI: 0000:04:00.0 reg 20 io port: [d000, d0ff]
[    0.977677] PCI: 0000:04:00.0 reg 30 32bit mmio: [fbdc0000, fbddffff]
[    0.977689] pci 0000:04:00.0: supports D1
[    0.977691] pci 0000:04:00.0: supports D2
[    0.977712] PCI: 0000:04:00.1 reg 10 64bit mmio: [fbdfc000, fbdfffff]
[    0.977740] pci 0000:04:00.1: supports D1
[    0.977741] pci 0000:04:00.1: supports D2
[    0.977761] PCI: bridge 0000:00:07.0 io port: [d000, dfff]
[    0.977764] PCI: bridge 0000:00:07.0 32bit mmio: [fbd00000, fbdfffff]
[    0.977769] PCI: bridge 0000:00:07.0 64bit mmio pref: [d0000000, dfffffff]
[    0.977852] PCI: 0000:02:00.0 reg 10 64bit mmio: [fbcff000, fbcfffff]
[    0.977901] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.977905] pci 0000:02:00.0: PME# disabled
[    0.977934] PCI: bridge 0000:00:1c.4 32bit mmio: [fbc00000, fbcfffff]
[    0.977975] PCI: 0000:01:06.0 reg 10 32bit mmio: [fbbff800, fbbfffff]
[    0.977981] PCI: 0000:01:06.0 reg 14 io port: [cc00, cc7f]
[    0.978016] pci 0000:01:06.0: supports D2
[    0.978018] pci 0000:01:06.0: PME# supported from D2 D3hot D3cold
[    0.978021] pci 0000:01:06.0: PME# disabled
[    0.978050] pci 0000:00:1e.0: transparent bridge
[    0.978053] PCI: bridge 0000:00:1e.0 io port: [c000, cfff]
[    0.978056] PCI: bridge 0000:00:1e.0 32bit mmio: [fbb00000, fbbfffff]
[    0.978081] bus 00 -> node 0
[    0.978086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.978442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE1._PRT]
[    0.978548] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE3._PRT]
[    0.978653] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE7._PRT]
[    0.978758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.980033] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.980140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    1.004996] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.004996] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    1.004996] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    1.004996] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 14 *15)
[    1.004996] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *6 7 10 11 12 14 15)
[    1.004996] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 *7 10 11 12 14 15)
[    1.004996] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    1.008116] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 10 11 12 *14 15)
[    1.008174] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - CA, should be C9 [20080609]
[    1.008174] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.008174] pnp: PnP ACPI init
[    1.008174] ACPI: bus type pnp registered
[    1.012376] pnp: PnP ACPI: found 13 devices
[    1.012378] ACPI: ACPI bus type pnp unregistered
[    1.012379] PnPBIOS: Disabled by ACPI PNP
[    1.012389] PCI: Using ACPI for IRQ routing
[    1.024042] NET: Registered protocol family 8
[    1.024045] NET: Registered protocol family 20
[    1.024062] NetLabel: Initializing
[    1.024062] NetLabel:  domain hash size = 128
[    1.024062] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.024062] NetLabel:  unlabeled traffic allowed by default
[    1.025142] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.025144]    actual entries 65620
[    1.025184] AppArmor: AppArmor Filesystem Enabled
[    1.025201] ACPI: RTC can wake from S4
[    1.032054] system 00:01: iomem range 0xfbf00000-0xfbffffff has been reserved
[    1.032056] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
[    1.032057] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
[    1.032059] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
[    1.032067] system 00:07: ioport range 0xa00-0xa0f has been reserved
[    1.032068] system 00:07: ioport range 0xa10-0xa1f has been reserved
[    1.032070] system 00:07: ioport range 0xa20-0xa2f has been reserved
[    1.032072] system 00:07: ioport range 0xa30-0xa3f has been reserved
[    1.032075] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.032077] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.032079] system 00:08: ioport range 0x480-0x4bf has been reserved
[    1.032081] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.032084] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.032086] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
[    1.032090] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.032092] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.032095] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    1.032099] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    1.032101] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    1.032103] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    1.032104] system 00:0c: iomem range 0x100000-0xbfffffff could not be reserved
[    1.032106] system 00:0c: iomem range 0xfed90000-0xffffffff could not be reserved
[    1.067495] pci 0000:00:01.0: PCI bridge, secondary bus 0000:06
[    1.067498] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    1.067501] pci 0000:00:01.0:   MEM window: 0xfbe00000-0xfbefffff
[    1.067504] pci 0000:00:01.0:   PREFETCH window: disabled
[    1.067508] pci 0000:00:03.0: PCI bridge, secondary bus 0000:05
[    1.067509] pci 0000:00:03.0:   IO window: disabled
[    1.067512] pci 0000:00:03.0:   MEM window: disabled
[    1.067515] pci 0000:00:03.0:   PREFETCH window: disabled
[    1.067519] pci 0000:00:07.0: PCI bridge, secondary bus 0000:04
[    1.067521] pci 0000:00:07.0:   IO window: 0xd000-0xdfff
[    1.067525] pci 0000:00:07.0:   MEM window: 0xfbd00000-0xfbdfffff
[    1.067527] pci 0000:00:07.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.067532] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    1.067533] pci 0000:00:1c.0:   IO window: disabled
[    1.067537] pci 0000:00:1c.0:   MEM window: disabled
[    1.067539] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.067544] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:02
[    1.067545] pci 0000:00:1c.4:   IO window: disabled
[    1.067549] pci 0000:00:1c.4:   MEM window: 0xfbc00000-0xfbcfffff
[    1.067552] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.067556] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    1.067558] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    1.067562] pci 0000:00:1e.0:   MEM window: 0xfbb00000-0xfbbfffff
[    1.067565] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.067575] pci 0000:00:01.0: setting latency timer to 64
[    1.067581] pci 0000:00:03.0: setting latency timer to 64
[    1.067587] pci 0000:00:07.0: setting latency timer to 64
[    1.067594] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.067597] pci 0000:00:1c.0: setting latency timer to 64
[    1.067602] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.067605] pci 0000:00:1c.4: setting latency timer to 64
[    1.067610] pci 0000:00:1e.0: setting latency timer to 64
[    1.067613] bus: 00 index 0 io port: [0, ffff]
[    1.067614] bus: 00 index 1 mmio: [0, ffffffff]
[    1.067616] bus: 06 index 0 io port: [e000, efff]
[    1.067617] bus: 06 index 1 mmio: [fbe00000, fbefffff]
[    1.067618] bus: 06 index 2 mmio: [0, 0]
[    1.067619] bus: 06 index 3 mmio: [0, 0]
[    1.067621] bus: 05 index 0 mmio: [0, 0]
[    1.067622] bus: 05 index 1 mmio: [0, 0]
[    1.067623] bus: 05 index 2 mmio: [0, 0]
[    1.067624] bus: 05 index 3 mmio: [0, 0]
[    1.067625] bus: 04 index 0 io port: [d000, dfff]
[    1.067626] bus: 04 index 1 mmio: [fbd00000, fbdfffff]
[    1.067627] bus: 04 index 2 mmio: [d0000000, dfffffff]
[    1.067629] bus: 04 index 3 mmio: [0, 0]
[    1.067630] bus: 03 index 0 mmio: [0, 0]
[    1.067631] bus: 03 index 1 mmio: [0, 0]
[    1.067632] bus: 03 index 2 mmio: [0, 0]
[    1.067633] bus: 03 index 3 mmio: [0, 0]
[    1.067634] bus: 02 index 0 mmio: [0, 0]
[    1.067635] bus: 02 index 1 mmio: [fbc00000, fbcfffff]
[    1.067637] bus: 02 index 2 mmio: [0, 0]
[    1.067638] bus: 02 index 3 mmio: [0, 0]
[    1.067639] bus: 01 index 0 io port: [c000, cfff]
[    1.067640] bus: 01 index 1 mmio: [fbb00000, fbbfffff]
[    1.067641] bus: 01 index 2 mmio: [0, 0]
[    1.067642] bus: 01 index 3 io port: [0, ffff]
[    1.067644] bus: 01 index 4 mmio: [0, ffffffff]
[    1.067649] NET: Registered protocol family 2
[    1.068044] Switched to high resolution mode on CPU 0
[    1.068495] Switched to high resolution mode on CPU 1
[    1.068510] Switched to high resolution mode on CPU 2
[    1.068515] Switched to high resolution mode on CPU 3
[    1.068550] Switched to high resolution mode on CPU 4
[    1.068565] Switched to high resolution mode on CPU 5
[    1.068571] Switched to high resolution mode on CPU 7
[    1.068652] Switched to high resolution mode on CPU 6
[    1.080065] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.080207] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.080371] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.080454] TCP: Hash tables configured (established 131072 bind 65536)
[    1.080456] TCP reno registered
[    1.088089] NET: Registered protocol family 1
[    1.088155] checking if image is initramfs... it is
[    1.612261] Freeing initrd memory: 8005k freed
[    1.617136] audit: initializing netlink socket (disabled)
[    1.617149] type=2000 audit(1230444889.616:1): initialized
[    1.621877] highmem bounce pool size: 64 pages
[    1.621882] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.624539] VFS: Disk quotas dquot_6.5.1
[    1.624614] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.624698] msgmni has been set to 1725
[    1.624797] io scheduler noop registered
[    1.624799] io scheduler anticipatory registered
[    1.624800] io scheduler deadline registered
[    1.624809] io scheduler cfq registered (default)
[    1.624981] pci 0000:04:00.0: Boot video device
[    1.625087] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.625120] pcieport-driver 0000:00:01.0: found MSI capability
[    1.625146] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.625192] pci_express 0000:00:01.0:pcie01: allocate port service
[    1.625282] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.625313] pcieport-driver 0000:00:03.0: found MSI capability
[    1.625337] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.625383] pci_express 0000:00:03.0:pcie01: allocate port service
[    1.625470] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.625502] pcieport-driver 0000:00:07.0: found MSI capability
[    1.625525] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.625571] pci_express 0000:00:07.0:pcie01: allocate port service
[    1.625661] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.625689] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.625716] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.625761] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.625807] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.625893] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.625921] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.625948] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.625992] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.626039] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.626183] aer 0000:00:01.0:pcie01: AER service couldn't init device: no _OSC support
[    1.626196] aer 0000:00:03.0:pcie01: AER service couldn't init device: no _OSC support
[    1.626206] aer 0000:00:07.0:pcie01: AER service couldn't init device: no _OSC support
[    1.626441] isapnp: Scanning for PnP cards...
[    1.979394] isapnp: No Plug & Play device found
[    2.012488] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.012610] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.013180] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.015009] brd: module loaded
[    2.015070] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.015181] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.015182] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.015308] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.017931] mice: PS/2 mouse device common for all mice
[    2.018050] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.018070] rtc0: alarms up to one month, y3k
[    2.018209] EISA: Probing bus 0 at eisa.0
[    2.018232] EISA: Detected 0 cards.
[    2.018234] cpuidle: using governor ladder
[    2.018236] cpuidle: using governor menu
[    2.018564] TCP cubic registered
[    2.018584] Using IPI No-Shortcut mode
[    2.018742] registered taskstats version 1
[    2.018843]   Magic number: 4:942:216
[    2.018849] tty ttyu0: hash matches
[    2.018913] rtc_cmos 00:03: setting system clock to 2008-12-28 06:14:51 UTC (1230444891)
[    2.018915] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.018916] EDD information not available.
[    2.019001] Freeing unused kernel memory: 424k freed
[    2.019052] Write protecting the kernel text: 2576k
[    2.019095] Write protecting the kernel read-only data: 936k
[    2.039923] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.056595] vesafb: framebuffer at 0xd0000000, mapped to 0xf8880000, using 2560k, total 16384k
[    2.056597] vesafb: mode is 1280x1024x8, linelength=1280, pages=11
[    2.056599] vesafb: protected mode interface info at c000:9fe0
[    2.056601] vesafb: pmi: set display start = c00ca082, set palette = c00ca140
[    2.056602] vesafb: scrolling: redraw
[    2.056604] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
[    2.056731] Console: switching to colour frame buffer device 160x64

[    2.103490] fb0: VESA VGA frame buffer device
[    2.194101] fuse init (API version 7.9)
[    2.206862] ACPI: SSDT BF79E250, 03C1 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    2.207149] ACPI: SSDT BF7A00D0, 03B2 (r1  PmRef  P001Cst     3001 INTL 20051117)
[    2.209609] Monitor-Mwait will be used to enter C-1 state
[    2.209612] Monitor-Mwait will be used to enter C-2 state
[    2.209614] Monitor-Mwait will be used to enter C-3 state
[    2.209845] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.209901] processor ACPI0007:00: registered as cooling_device0
[    2.210193] ACPI: SSDT BF79E620, 03C1 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    2.210472] ACPI: SSDT BF7A0490, 0085 (r1  PmRef  P002Cst     3000 INTL 20051117)
[    2.213173] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.213233] processor ACPI0007:01: registered as cooling_device1
[    2.213537] ACPI: SSDT BF79E9F0, 03C1 (r1 DpgPmm  P003Ist       12 INTL 20051117)
[    2.213820] ACPI: SSDT BF7A0520, 0085 (r1  PmRef  P003Cst     3000 INTL 20051117)
[    2.216536] ACPI: CPU2 (power states: C1[C1] C2[C2] C3[C3])
[    2.216600] processor ACPI0007:02: registered as cooling_device2
[    2.216902] ACPI: SSDT BF79EDC0, 03C1 (r1 DpgPmm  P004Ist       12 INTL 20051117)
[    2.217189] ACPI: SSDT BF7A05B0, 0085 (r1  PmRef  P004Cst     3000 INTL 20051117)
[    2.219912] ACPI: CPU3 (power states: C1[C1] C2[C2] C3[C3])
[    2.219973] processor ACPI0007:03: registered as cooling_device3
[    2.220306] ACPI: SSDT BF79F190, 03C1 (r1 DpgPmm  P005Ist       12 INTL 20051117)
[    2.220595] ACPI: SSDT BF7A0640, 0085 (r1  PmRef  P005Cst     3000 INTL 20051117)
[    2.223300] ACPI: CPU4 (power states: C1[C1] C2[C2] C3[C3])
[    2.223357] processor ACPI0007:04: registered as cooling_device4
[    2.223662] ACPI: SSDT BF79F560, 03C1 (r1 DpgPmm  P006Ist       12 INTL 20051117)
[    2.223965] ACPI: SSDT BF7A06D0, 0085 (r1  PmRef  P006Cst     3000 INTL 20051117)
[    2.226694] ACPI: CPU5 (power states: C1[C1] C2[C2] C3[C3])
[    2.226756] processor ACPI0007:05: registered as cooling_device5
[    2.227065] ACPI: SSDT BF79F930, 03C1 (r1 DpgPmm  P007Ist       12 INTL 20051117)
[    2.227399] ACPI: SSDT BF7A0760, 0085 (r1  PmRef  P007Cst     3000 INTL 20051117)
[    2.230172] ACPI: CPU6 (power states: C1[C1] C2[C2] C3[C3])
[    2.230237] processor ACPI0007:06: registered as cooling_device6
[    2.230576] ACPI: SSDT BF79FD00, 03C1 (r1 DpgPmm  P008Ist       12 INTL 20051117)
[    2.230904] ACPI: SSDT BF7A07F0, 0085 (r1  PmRef  P008Cst     3000 INTL 20051117)
[    2.234642] ACPI: CPU7 (power states: C1[C1] C2[C2] C3[C3])
[    2.234704] processor ACPI0007:07: registered as cooling_device7
[    2.237882] thermal LNXTHERM:01: registered as thermal_zone0
[    2.238231] ACPI: Thermal Zone [THRM] (24 C)
[    2.300032] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.300035] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.300073] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.300080] e1000e 0000:00:19.0: setting latency timer to 64
[    2.332412] usbcore: registered new interface driver usbfs
[    2.332430] usbcore: registered new interface driver hub
[    2.332662] usbcore: registered new device driver usb
[    2.335093] USB Universal Host Controller Interface driver v3.0
[    2.344718] No dock devices found.
[    2.369941] SCSI subsystem initialized
[    2.390014] libata version 3.00 loaded.
[    2.392002] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:22:68:38:44:82
[    2.392005] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.392068] 0000:00:19.0: eth0: MAC: 5, PHY: 8, PBA No: ffffff-0ff
[    2.392402] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.392410] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.392414] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.392450] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.392481] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a400
[    2.392592] usb usb1: configuration #1 chosen from 1 choice
[    2.392617] hub 1-0:1.0: USB hub found
[    2.392623] hub 1-0:1.0: 2 ports detected
[    2.600479] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.600487] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.600490] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.600513] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.600543] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a480
[    2.600625] usb usb2: configuration #1 chosen from 1 choice
[    2.600655] hub 2-0:1.0: USB hub found
[    2.600661] hub 2-0:1.0: 2 ports detected
[    2.712067] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    2.808414] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.808420] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.808423] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.808449] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.808477] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000a800
[    2.808533] usb usb3: configuration #1 chosen from 1 choice
[    2.808550] hub 3-0:1.0: USB hub found
[    2.808554] hub 3-0:1.0: 2 ports detected
[    2.870636] usb 1-2: configuration #1 chosen from 1 choice
[    2.984088] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.016458] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.016469] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.016472] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.016491] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    3.020387] ehci_hcd 0000:00:1a.7: debug port 1
[    3.020392] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.020400] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbaf8000
[    3.112088] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.112176] usb usb4: configuration #1 chosen from 1 choice
[    3.112200] hub 4-0:1.0: USB hub found
[    3.112205] hub 4-0:1.0: 6 ports detected
[    3.320826] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.320834] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.320837] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.320867] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.320891] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a880
[    3.320949] usb usb5: configuration #1 chosen from 1 choice
[    3.320965] hub 5-0:1.0: USB hub found
[    3.320968] hub 5-0:1.0: 2 ports detected
[    3.424367] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.424374] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.424377] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.424404] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.424426] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ac00
[    3.424505] usb usb6: configuration #1 chosen from 1 choice
[    3.424528] hub 6-0:1.0: USB hub found
[    3.424533] hub 6-0:1.0: 2 ports detected
[    3.508085] usb 2-1: device not accepting address 2, error -71
[    3.564120] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.632379] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.632386] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.632390] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.632411] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.632433] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b000
[    3.632512] usb usb7: configuration #1 chosen from 1 choice
[    3.632535] hub 7-0:1.0: USB hub found
[    3.632540] hub 7-0:1.0: 2 ports detected
[    3.692099] usb 1-2: USB disconnect, address 2
[    3.840394] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.840402] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.840404] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.840422] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.844333] ehci_hcd 0000:00:1d.7: debug port 1
[    3.844338] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.844342] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbafa000
[    3.932096] usb 4-2: new high speed USB device using ehci_hcd and address 2
[    3.944106] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.944193] usb usb8: configuration #1 chosen from 1 choice
[    3.944220] hub 8-0:1.0: USB hub found
[    3.944228] hub 8-0:1.0: 6 ports detected
[    4.081470] usb 4-2: configuration #1 chosen from 1 choice
[    4.153235] ahci 0000:00:1f.2: version 3.0
[    4.153245] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.153333] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    4.153336] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    4.153339] ahci 0000:00:1f.2: setting latency timer to 64
[    4.153561] scsi0 : ahci
[    4.153662] scsi1 : ahci
[    4.153749] scsi2 : ahci
[    4.153836] scsi3 : ahci
[    4.153897] scsi4 : ahci
[    4.153973] scsi5 : ahci
[    4.154057] ata1: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc100 irq 218
[    4.154060] ata2: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc180 irq 218
[    4.154062] ata3: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc200 irq 218
[    4.154065] ata4: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc280 irq 218
[    4.154067] ata5: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc300 irq 218
[    4.154069] ata6: SATA max UDMA/133 abar m2048@0xfbafc000 port 0xfbafc380 irq 218
[    4.192084] usb 4-3: new high speed USB device using ehci_hcd and address 3
[    4.327033] usb 4-3: config 1 interface 1 altsetting 0 endpoint 0x83 has an invalid bInterval 30, changing to 8
[    4.332245] usb 4-3: configuration #1 chosen from 1 choice
[    4.476081] ata1: SATA link down (SStatus 0 SControl 300)
[    4.812079] ata2: SATA link down (SStatus 0 SControl 300)
[    4.812094] usb 8-6: new high speed USB device using ehci_hcd and address 3
[    4.952291] usb 8-6: configuration #1 chosen from 1 choice
[    4.953373] usbcore: registered new interface driver libusual
[    4.953382] usbcore: registered new interface driver hiddev
[    4.959053] Initializing USB Mass Storage driver...
[    5.148071] ata3: SATA link down (SStatus 0 SControl 300)
[    5.192094] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.371893] usb 3-1: configuration #1 chosen from 1 choice
[    5.488093] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.490857] ata4.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
[    5.494864] ata4.00: configured for UDMA/100
[    5.612065] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    5.780638] usb 6-1: configuration #1 chosen from 1 choice
[    5.784020] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.784235] usb-storage: device found at 2
[    5.784237] usb-storage: waiting for device to settle before scanning
[    5.828095] ata5: SATA link down (SStatus 0 SControl 300)
[    6.164104] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.165612] ata6.00: ATA-8: ST3750630AS, SD46, max UDMA/133
[    6.165615] ata6.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.167568] ata6.00: configured for UDMA/133
[    6.183140] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
[    6.183244] scsi 3:0:0:0: Attached scsi generic sg0 type 5
[    6.183310] scsi 5:0:0:0: Direct-Access     ATA      ST3750630AS      SD46 PQ: 0 ANSI: 5
[    6.183363] scsi 5:0:0:0: Attached scsi generic sg1 type 0
[    6.183417] ahci 0000:06:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    6.196128] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    6.196132] ahci 0000:06:00.0: flags: 64bit ncq led clo pmp pio 
[    6.196138] ahci 0000:06:00.0: setting latency timer to 64
[    6.196355] scsi7 : ahci
[    6.196643] scsi8 : ahci
[    6.196696] ata7: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 28
[    6.196699] ata8: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe180 irq 28

[    6.516104] ata7: SATA link down (SStatus 0 SControl 300)
[    6.836100] ata8: SATA link down (SStatus 0 SControl 300)
[    6.836264] ohci1394 0000:01:06.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.888944] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbbff800-fbbfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.897326] Driver 'sd' needs updating - please use bus_type methods
[    6.897412] sd 5:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[    6.897437] sd 5:0:0:0: [sda] Write Protect is off
[    6.897438] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.897480] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.897574] sd 5:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[    6.897600] sd 5:0:0:0: [sda] Write Protect is off
[    6.897602] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.897645] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.897648]  sda:<6>pata_jmicron 0000:06:00.1: enabling device (0000 -> 0001)
[    6.901126] pata_jmicron 0000:06:00.1: PCI INT B -> GSI 40 (level, low) -> IRQ 40
[    6.901147] pata_jmicron 0000:06:00.1: setting latency timer to 64
[    6.903566] scsi9 : pata_jmicron
[    6.903817] scsi10 : pata_jmicron
[    6.903847] ata9: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 40
[    6.903849] ata10: PATA max UDMA/100 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 40
[    6.904527] Driver 'sr' needs updating - please use bus_type methods
[    6.917240]  sda1 sda2
[    6.917873] sd 5:0:0:0: [sda] Attached SCSI disk
[    7.127874] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.127877] Uniform CD-ROM driver Revision: 3.20
[    7.128258] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    8.164258] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c2000975f9d]
[   10.784400] usb-storage: device scan complete
[   10.785043] scsi 6:0:0:0: Direct-Access     Maxtor   OneTouch         0122 PQ: 0 ANSI: 4
[   10.786512] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   10.787260] sd 6:0:0:0: [sdb] Write Protect is off
[   10.787262] sd 6:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[   10.787264] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   10.788283] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   10.789018] sd 6:0:0:0: [sdb] Write Protect is off
[   10.789020] sd 6:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[   10.789021] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   10.789347]  sdb: sdb1
[   10.810816] sd 6:0:0:0: [sdb] Attached SCSI disk
[   10.811371] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   15.784131] usbhid: timeout initializing reports
[   15.784230] hiddev96hidraw0: USB HID v1.11 Device [Generic USB2.0-CRW] on usb-0000:00:1a.7-3
[   15.784487] scsi11 : SCSI emulation for USB Mass Storage devices
[   15.784636] usb-storage: device found at 3
[   15.784637] usb-storage: waiting for device to settle before scanning
[   15.784863] scsi12 : SCSI emulation for USB Mass Storage devices
[   15.785081] usb-storage: device found at 3
[   15.785082] usb-storage: waiting for device to settle before scanning
[   15.814027] input: Device Media Center Interface as /devices/pci0000:00/0000:00:1a.2/usb3/3-1/3-1:1.0/input/input2
[   15.814244] input,hiddev97,hidraw1: USB HID v1.10 Keyboard [Device Media Center Interface] on usb-0000:00:1a.2-1
[   15.828043] hiddev98hidraw2: USB HID v1.10 Device [Device Media Center Interface] on usb-0000:00:1a.2-1
[   15.841079] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input3
[   15.845918] input,hidraw3: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-1
[   15.845949] usbcore: registered new interface driver usbhid
[   15.845951] usbhid: v2.6:USB HID core driver
[   15.846100] usbcore: registered new interface driver usb-storage
[   15.846102] USB Mass Storage support registered.
[   15.944734] kjournald starting.  Commit interval 5 seconds
[   15.944744] EXT3-fs: mounted filesystem with ordered data mode.
[   20.784536] usb-storage: device scan complete
[   20.784622] usb-storage: device scan complete
[   20.785408] scsi 12:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9404 PQ: 0 ANSI: 0
[   20.787136] scsi 11:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   20.789633] scsi 11:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   20.792152] scsi 11:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   20.794760] scsi 11:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   20.796338] sd 11:0:0:0: [sdc] Attached SCSI removable disk
[   20.796391] sd 11:0:0:0: Attached scsi generic sg3 type 0
[   20.797681] sd 11:0:0:1: [sdd] Attached SCSI removable disk
[   20.797737] sd 11:0:0:1: Attached scsi generic sg4 type 0
[   20.799073] sd 11:0:0:2: [sde] Attached SCSI removable disk
[   20.799129] sd 11:0:0:2: Attached scsi generic sg5 type 0
[   20.800418] sd 11:0:0:3: [sdf] Attached SCSI removable disk
[   20.800454] sd 11:0:0:3: Attached scsi generic sg6 type 0
[   20.908560] udevd version 124 started
[   20.912639] sd 12:0:0:0: [sdg] 1984000 512-byte hardware sectors (1016 MB)
[   20.913864] sd 12:0:0:0: [sdg] Write Protect is off
[   20.913866] sd 12:0:0:0: [sdg] Mode Sense: 03 00 00 00
[   20.913868] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[   20.915988] sd 12:0:0:0: [sdg] 1984000 512-byte hardware sectors (1016 MB)
[   20.917108] sd 12:0:0:0: [sdg] Write Protect is off
[   20.917110] sd 12:0:0:0: [sdg] Mode Sense: 03 00 00 00
[   20.917111] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[   20.917440]  sdg: sdg1
[   20.918852] sd 12:0:0:0: [sdg] Attached SCSI removable disk
[   20.918906] sd 12:0:0:0: Attached scsi generic sg7 type 0
[   21.127029] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   21.156021] ACPI: Power Button (FF) [PWRF]
[   21.156137] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   21.161938] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.172038] ACPI: Power Button (CM) [PWRB]
[   21.176462] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.329618] ACPI: WMI: Mapper loaded
[   21.440561] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.440578] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.519334] HDA Intel 0000:04:00.1: PCI INT B -> GSI 37 (level, low) -> IRQ 37
[   21.519359] HDA Intel 0000:04:00.1: setting latency timer to 64
[   21.624688] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   22.928175] lp: driver loaded but no devices found
[   23.355156] EXT3 FS on sda1, internal journal
[   23.706621] type=1505 audit(1230444912.877:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5282
[   23.822890] type=1505 audit(1230444912.991:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5287
[   23.823080] type=1505 audit(1230444912.991:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5287
[   23.931032] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.465395] Linux agpgart interface v0.103
[   51.468958] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   51.496259] [fglrx] Maximum main memory to use for locked dma buffers: 2884 MBytes.
[   51.496741] [fglrx]   vendor: 1002 device: 9442 count: 1
[   51.497533] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[   51.497548] pci 0000:04:00.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
[   51.497553] pci 0000:04:00.0: setting latency timer to 64
[   51.501818] [fglrx] PAT is enabled successfully!
[   51.501842] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   56.135199] [fglrx] CMM init INV FB MC:0xf10000000, length:0x30000000
[   56.135203] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   56.135205] [fglrx] Reserved FB block: Unshared offset:ff77000, size:88000 
[   59.360839] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   59.360842] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   59.495753] NET: Registered protocol family 17
[   59.639447] warning: `pulseaudio' uses 32-bit capabilities (legacy support in use)
[   64.015366] 0000:00:19.0: eth0: changing MTU from 1500 to 576
[   65.984800] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   65.984808] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   86.881242] NET: Registered protocol family 10
[   86.881875] lo: Disabled Privacy Extensions
[ 4878.010025] usb 8-6: USB disconnect, address 3
[ 4881.664849] usb 4-2: USB disconnect, address 2
[26843.356068] usb 4-2: new high speed USB device using ehci_hcd and address 5
[26843.489920] usb 4-2: configuration #1 chosen from 1 choice
[26843.490405] scsi13 : SCSI emulation for USB Mass Storage devices
[26843.490857] usb-storage: device found at 5
[26843.490860] usb-storage: waiting for device to settle before scanning
[26848.488456] usb-storage: device scan complete
[26848.488978] scsi 13:0:0:0: Direct-Access     Maxtor   OneTouch         0122 PQ: 0 ANSI: 4
[26848.490806] sd 13:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[26848.491434] sd 13:0:0:0: [sdb] Write Protect is off
[26848.491438] sd 13:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[26848.491441] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[26848.492160] sd 13:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[26848.492777] sd 13:0:0:0: [sdb] Write Protect is off
[26848.492780] sd 13:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[26848.492782] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[26848.492787]  sdb: sdb1
[26848.509276] sd 13:0:0:0: [sdb] Attached SCSI disk
[26848.509677] sd 13:0:0:0: Attached scsi generic sg2 type 0
[26880.696890] Buffer I/O error on device sr0, logical block 0
[26880.696897] Buffer I/O error on device sr0, logical block 1
[26880.696901] Buffer I/O error on device sr0, logical block 2
[26880.696904] Buffer I/O error on device sr0, logical block 3
[26880.696908] Buffer I/O error on device sr0, logical block 4
[26880.696911] Buffer I/O error on device sr0, logical block 5
[26880.696915] Buffer I/O error on device sr0, logical block 6
[26880.696918] Buffer I/O error on device sr0, logical block 7
[26880.696922] Buffer I/O error on device sr0, logical block 8
[26880.696926] Buffer I/O error on device sr0, logical block 9

```

---

### Post by Tom--d on 2008-12-28
> **Dr Small said:**
> Isn't easier just to say it like this?
[noparse]```
dmesg output
```[/noparse]

:D

How did you do that without making the code bit? ;)

---

### Post by Zizzech on 2008-12-28
bump :/

---

### Post by Zizzech on 2008-12-28
bump :/

---

### Post by WattoDaToydarian on 2009-01-01
Zizzech,

try the command "sudo ifconfig eth0 mtu 1500"
I believe your current mtu of 576 from your first post is causing it to go slow.

---

