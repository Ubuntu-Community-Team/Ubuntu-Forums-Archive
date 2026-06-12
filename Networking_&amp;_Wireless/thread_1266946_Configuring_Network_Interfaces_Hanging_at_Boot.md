---
title: "Configuring Network Interfaces Hanging at Boot"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by dkurtz on 2009-09-15
Greetings,

I have been reading through various forums and searching for an answer to why my Ubuntu 9.04 server is getting stuck at Configuring Network Interfaces on boot. (I can skip this step and continue booting using Ctrl+Alt+Del) I recently inherited administration of this box and the person who set it up is no longer at this company, so I'm not exactly sure what all is running on the box or anything about the configs. I do know that if I comment out the lines in /etc/network/interfaces and bounce the box, it will come up fine and not hang. Unfortunately, I need to assign 2 static ip addresses to the NIC on this box, so leaving those lines commented out isn't an option. Also, once the box is up, if I uncomment the lines in /etc/network/interfaces,  and try to start the network using /etc/init.d/networking start, the interfaces are created and all is well. Any ideas?  I'm sorta stumped.

Thanks!
Dave

---

### Post by x33a on 2009-09-15
please post the contents of
```
cat /etc/network/interfaces
cat /var/log/messages
dmesg
```

---

### Post by dkurtz on 2009-09-15
```
Thanks x33a, hope this helps! I am posting my output in two separate threads due to size...

cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.100.36
netmask 255.255.255.0
gateway 192.168.100.161


auto eth0:1
iface eth0:1 inet static
address 192.168.100.152
netmask 255.255.255.0

cat /var/log/messages

Sep 15 07:15:15 webapps syslogd 1.5.0#5ubuntu3: restart.
Sep 15 07:15:15 webapps kernel: Inspecting /boot/System.map-2.6.28-11-server
Sep 15 07:15:15 webapps kernel: Cannot find map file.
Sep 15 07:15:15 webapps kernel: Loaded 49115 symbols from 27 modules.
Sep 15 07:15:15 webapps kernel: [    0.000000] BIOS EBDA/lowmem at: 00097400/00097400
Sep 15 07:15:15 webapps kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 15 07:15:15 webapps kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 15 07:15:15 webapps kernel: [    0.000000] Linux version 2.6.28-11-server (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 (Ubuntu 2.6.28-11.42-server)
Sep 15 07:15:15 webapps kernel: [    0.000000] Command line: root=/dev/mapper/webapps-root ro quiet splash
Sep 15 07:15:15 webapps kernel: [    0.000000] KERNEL supported cpus:
Sep 15 07:15:15 webapps kernel: [    0.000000]   Intel GenuineIntel
Sep 15 07:15:15 webapps kernel: [    0.000000]   AMD AuthenticAMD
Sep 15 07:15:15 webapps kernel: [    0.000000]   Centaur CentaurHauls
Sep 15 07:15:15 webapps kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000097400 (usable)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 0000000000097400 - 00000000000a0000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7fa0000 (usable)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000d7fae000 - 00000000d7fb0000 (usable)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000d7fb0000 - 00000000d7fbe000 (ACPI data)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000d7fbe000 - 00000000d7ff0000 (ACPI NVS)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000d7ff0000 - 00000000d8000000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000428000000 (usable)
Sep 15 07:15:15 webapps kernel: [    0.000000] DMI present.
Sep 15 07:15:15 webapps kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
Sep 15 07:15:15 webapps kernel: [    0.000000] last_pfn = 0x428000 max_arch_pfn = 0x3ffffffff
Sep 15 07:15:15 webapps kernel: [    0.000000] last_pfn = 0xd7fb0 max_arch_pfn = 0x3ffffffff
Sep 15 07:15:15 webapps kernel: [    0.000000] Scanning 0 areas for low memory corruption
Sep 15 07:15:15 webapps kernel: [    0.000000] modified physical RAM map:
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 0000000000010000 - 0000000000097400 (usable)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 0000000000097400 - 00000000000a0000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 0000000000100000 - 00000000d7fa0000 (usable)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000d7fae000 - 00000000d7fb0000 (usable)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000d7fb0000 - 00000000d7fbe000 (ACPI data)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000d7fbe000 - 00000000d7ff0000 (ACPI NVS)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000d7ff0000 - 00000000d8000000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
Sep 15 07:15:15 webapps kernel: [    0.000000]  modified: 0000000100000000 - 0000000428000000 (usable)
Sep 15 07:15:15 webapps kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000d7fb0000
Sep 15 07:15:15 webapps kernel: [    0.000000] last_map_addr: d7fb0000 end: d7fb0000
Sep 15 07:15:15 webapps kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000428000000
Sep 15 07:15:15 webapps kernel: [    0.000000] last_map_addr: 428000000 end: 428000000
Sep 15 07:15:15 webapps kernel: [    0.000000] RAMDISK: 377e3000 - 37fef57b
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: RSDP 000FAF20, 0014 (r0 ACPIAM)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: RSDT D7FB0000, 005C (r1 SUN    X4x40          65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: FACP D7FB0200, 0084 (r2 SUN    X4x40          65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: DSDT D7FB0610, 7F1C (r1 SUN    X4x40          65 INTL 20051117)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: FACS D7FBE000, 0040
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: APIC D7FB0390, 012C (r1 SUN    X4x40          65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: SPCR D7FB04C0, 0050 (r1 SUN    X4x40          65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: MCFG D7FB0510, 003C (r1 SUN    OEMMCFG        65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: SLIT D7FB0580, 003C (r1 SUN    OEMSLIT        65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: SPMI D7FB05C0, 0041 (r1 SUN    OEMSPMI        65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: OEMB D7FBE040, 00AE (r1 SUN    X4x40          65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: SRAT D7FB8530, 0220 (r1 AMD    FAM_F_10        2 AMD         1)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: HPET D7FB8750, 0038 (r1 SUN    OEMHPET0       65 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: EINJ D7FB8790, 0130 (r1  AMIER AMI_EINJ  6000915 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: BERT D7FB8920, 0030 (r1  AMIER AMI_BERT  6000915 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: ERST D7FB8950, 01B0 (r1  AMIER AMI_ERST  6000915 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: HEST D7FB8B00, 00A8 (r1  AMIER AMI_HEST  6000915 MSFT       97)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: SSDT D7FB8BB0, 2854 (r1 A M I  POWERNOW        1 AMD         1)
Sep 15 07:15:15 webapps kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0428000000]
Sep 15 07:15:15 webapps kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep 15 07:15:15 webapps kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Sep 15 07:15:15 webapps kernel: [    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
Sep 15 07:15:15 webapps kernel: [    0.000000]   #3 [00377e3000 - 0037fef57b]          RAMDISK ==> [00377e3000 - 0037fef57b]
Sep 15 07:15:15 webapps kernel: [    0.000000]   #4 [0000097400 - 0000100000]    BIOS reserved ==> [0000097400 - 0000100000]
Sep 15 07:15:15 webapps kernel: [    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
Sep 15 07:15:15 webapps kernel: [    0.000000]   #6 [0000014000 - 0000021000]          PGTABLE ==> [0000014000 - 0000021000]
Sep 15 07:15:15 webapps kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
Sep 15 07:15:15 webapps kernel: [    0.000000] Zone PFN ranges:
Sep 15 07:15:15 webapps kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Sep 15 07:15:15 webapps kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Sep 15 07:15:15 webapps kernel: [    0.000000]   Normal   0x00100000 -> 0x00428000
Sep 15 07:15:15 webapps kernel: [    0.000000] Movable zone start PFN for each node
Sep 15 07:15:15 webapps kernel: [    0.000000] early_node_map[4] active PFN ranges
Sep 15 07:15:15 webapps kernel: [    0.000000]     0: 0x00000010 -> 0x00000097
Sep 15 07:15:15 webapps kernel: [    0.000000]     0: 0x00000100 -> 0x000d7fa0
Sep 15 07:15:15 webapps kernel: [    0.000000]     0: 0x000d7fae -> 0x000d7fb0
Sep 15 07:15:15 webapps kernel: [    0.000000]     0: 0x00100000 -> 0x00428000
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe008
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x05] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x08] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x09] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x0a] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x0b] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x0c] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x0d] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0e] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0f] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x10] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x11] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x12] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x13] enabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x11] lapic_id[0x90] disabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x12] lapic_id[0x91] disabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x13] lapic_id[0x92] disabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x14] lapic_id[0x93] disabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x15] lapic_id[0x94] disabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x16] lapic_id[0x95] disabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x17] lapic_id[0x96] disabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x18] lapic_id[0x97] disabled)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Sep 15 07:15:15 webapps kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 0, address 0xfec00000, GSI 0-23
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xddfff000] gsi_base[24])
Sep 15 07:15:15 webapps kernel: [    0.000000] IOAPIC[1]: apic_id 1, version 0, address 0xddfff000, GSI 24-47
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Sep 15 07:15:15 webapps kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Sep 15 07:15:15 webapps kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 15 07:15:15 webapps kernel: [    0.000000] SMP: Allowing 24 CPUs, 8 hotplug CPUs
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 0000000000097000 - 0000000000098000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 0000000000098000 - 00000000000a0000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000d7fa0000 - 00000000d7fae000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000d7fb0000 - 00000000d7fbe000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000d7fbe000 - 00000000d7ff0000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000d7ff0000 - 00000000d8000000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000d8000000 - 00000000e0000000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000ff700000
Sep 15 07:15:15 webapps kernel: [    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
Sep 15 07:15:15 webapps kernel: [    0.000000] Allocating PCI resources starting at f1000000 (gap: f0000000:ec00000)
Sep 15 07:15:15 webapps kernel: [    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
Sep 15 07:15:15 webapps kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4131942
Sep 15 07:15:15 webapps kernel: [    0.000000] Kernel command line: root=/dev/mapper/webapps-root ro quiet splash
Sep 15 07:15:15 webapps kernel: [    0.000000] Initializing CPU#0
Sep 15 07:15:15 webapps kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Sep 15 07:15:15 webapps kernel: [    0.000000] Fast TSC calibration using PIT
Sep 15 07:15:15 webapps kernel: [    0.000000] Detected 1898.613 MHz processor.
Sep 15 07:15:15 webapps kernel: [    0.010000] Console: colour VGA+ 80x25
Sep 15 07:15:15 webapps kernel: [    0.010000] console [tty0] enabled
Sep 15 07:15:15 webapps kernel: [    0.010000] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Sep 15 07:15:15 webapps kernel: [    0.010000] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Sep 15 07:15:15 webapps kernel: [    0.010000] allocated 174325760 bytes of page_cgroup
Sep 15 07:15:15 webapps kernel: [    0.010000] please try cgroup_disable=memory option if you don't want
Sep 15 07:15:15 webapps kernel: [    0.010000] Scanning for low memory corruption every 60 seconds
Sep 15 07:15:15 webapps kernel: [    0.010000] Checking aperture...
Sep 15 07:15:15 webapps kernel: [    0.010000] No AGP bridge found
Sep 15 07:15:15 webapps kernel: [    0.010000] Node 0: aperture @ 20000000 size 32 MB
Sep 15 07:15:15 webapps kernel: [    0.010000] Aperture pointing to e820 RAM. Ignoring.
Sep 15 07:15:15 webapps kernel: [    0.010000] Your BIOS doesn't leave a aperture memory hole
Sep 15 07:15:15 webapps kernel: [    0.010000] Please enable the IOMMU option in the BIOS setup
Sep 15 07:15:15 webapps kernel: [    0.010000] This costs you 64 MB of RAM
Sep 15 07:15:15 webapps kernel: [    0.010000] Mapping aperture over 65536 KB of RAM @ 20000000
Sep 15 07:15:15 webapps kernel: [    0.010000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
Sep 15 07:15:15 webapps kernel: [    0.010000] Memory: 16255408k/17432576k available (4758k kernel code, 656220k absent, 519968k reserved, 2542k data, 536k init)
Sep 15 07:15:15 webapps kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=24, Nodes=1
Sep 15 07:15:15 webapps kernel: [    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3797.22 BogoMIPS (lpj=18986110)
Sep 15 07:15:15 webapps kernel: [    0.010000] Security Framework initialized
Sep 15 07:15:15 webapps kernel: [    0.010000] SELinux:  Disabled at boot.
Sep 15 07:15:15 webapps kernel: [    0.010000] AppArmor: AppArmor initialized
Sep 15 07:15:15 webapps kernel: [    0.010000] Mount-cache hash table entries: 256
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing cgroup subsys ns
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing cgroup subsys cpuacct
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing cgroup subsys memory
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing cgroup subsys freezer
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 0
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 0
Sep 15 07:15:15 webapps kernel: [    0.010000] using C1E aware idle routine
Sep 15 07:15:15 webapps kernel: [    0.010000] ACPI: Core revision 20080926
Sep 15 07:15:15 webapps kernel: [    0.010000] ACPI: Checking initramfs for custom DSDT
Sep 15 07:15:15 webapps kernel: [    0.330078] Setting APIC routing to physical flat
Sep 15 07:15:15 webapps kernel: [    0.330693] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Sep 15 07:15:15 webapps kernel: [    0.438529] CPU0: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    0.440000] Booting processor 1 APIC 0x5 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#1
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3803.85 BogoMIPS (lpj=19019273)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 0
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 1
Sep 15 07:15:15 webapps kernel: [    0.590478] CPU1: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    0.590488] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Sep 15 07:15:15 webapps kernel: [    0.600128] Booting processor 2 APIC 0x6 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#2
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3803.74 BogoMIPS (lpj=19018739)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 0
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 2
Sep 15 07:15:15 webapps kernel: [    0.760446] CPU2: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    0.760453] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Sep 15 07:15:15 webapps kernel: [    0.770124] Booting processor 3 APIC 0x7 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#3
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3803.75 BogoMIPS (lpj=19018763)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 0
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 3
Sep 15 07:15:15 webapps kernel: [    0.930409] CPU3: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    0.930417] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Sep 15 07:15:15 webapps kernel: [    0.940123] Booting processor 4 APIC 0x8 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#4
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.81 BogoMIPS (lpj=19004074)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 1
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 0
Sep 15 07:15:15 webapps kernel: [    1.100484] CPU4: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    1.100491] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
Sep 15 07:15:15 webapps kernel: [    1.110124] Booting processor 5 APIC 0x9 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#5
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3801.04 BogoMIPS (lpj=19005247)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 1
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 1
Sep 15 07:15:15 webapps kernel: [    1.270461] CPU5: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    1.270468] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
Sep 15 07:15:15 webapps kernel: [    1.280126] Booting processor 6 APIC 0xa ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#6
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3801.07 BogoMIPS (lpj=19005351)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 1
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 2
Sep 15 07:15:15 webapps kernel: [    1.440445] CPU6: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    1.440452] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
Sep 15 07:15:15 webapps kernel: [    1.450132] Booting processor 7 APIC 0xb ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#7
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.83 BogoMIPS (lpj=19004168)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 1
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 3
Sep 15 07:15:15 webapps kernel: [    1.610443] CPU7: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    1.610450] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
Sep 15 07:15:15 webapps kernel: [    1.620127] Booting processor 8 APIC 0xc ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#8
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.82 BogoMIPS (lpj=19004147)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 2
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 0
Sep 15 07:15:15 webapps kernel: [    1.780433] CPU8: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    1.780440] checking TSC synchronization [CPU#0 -> CPU#8]: passed.
Sep 15 07:15:15 webapps kernel: [    1.790128] Booting processor 9 APIC 0xd ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#9
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.20 BogoMIPS (lpj=19001022)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 2
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 1
Sep 15 07:15:15 webapps kernel: [    1.950427] CPU9: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    1.950434] checking TSC synchronization [CPU#0 -> CPU#9]: passed.
Sep 15 07:15:15 webapps kernel: [    1.960125] Booting processor 10 APIC 0xe ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#10
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.42 BogoMIPS (lpj=19002133)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 2
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 2
Sep 15 07:15:15 webapps kernel: [    2.120510] CPU10: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    2.120517] checking TSC synchronization [CPU#0 -> CPU#10]: passed.
Sep 15 07:15:15 webapps kernel: [    2.130133] Booting processor 11 APIC 0xf ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#11
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.63 BogoMIPS (lpj=19003184)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 2
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 3
Sep 15 07:15:15 webapps kernel: [    2.290488] CPU11: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    2.290495] checking TSC synchronization [CPU#0 -> CPU#11]: passed.
Sep 15 07:15:15 webapps kernel: [    2.300129] Booting processor 12 APIC 0x10 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#12
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.22 BogoMIPS (lpj=19001116)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 3
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 0
Sep 15 07:15:15 webapps kernel: [    2.460504] CPU12: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    2.460511] checking TSC synchronization [CPU#0 -> CPU#12]: passed.
Sep 15 07:15:15 webapps kernel: [    2.470129] Booting processor 13 APIC 0x11 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#13
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.25 BogoMIPS (lpj=19001272)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 3
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 1
Sep 15 07:15:15 webapps kernel: [    2.630484] CPU13: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    2.630491] checking TSC synchronization [CPU#0 -> CPU#13]: passed.
Sep 15 07:15:15 webapps kernel: [    2.640131] Booting processor 14 APIC 0x12 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#14
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.68 BogoMIPS (lpj=19003439)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 3
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 2
Sep 15 07:15:15 webapps kernel: [    2.800472] CPU14: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    2.800479] checking TSC synchronization [CPU#0 -> CPU#14]: passed.
Sep 15 07:15:15 webapps kernel: [    2.810135] Booting processor 15 APIC 0x13 ip 0x6000
Sep 15 07:15:15 webapps kernel: [    0.010000] Initializing CPU#15
Sep 15 07:15:15 webapps kernel: [    0.010000] Calibrating delay using timer specific routine.. 3800.23 BogoMIPS (lpj=19001179)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Physical Processor ID: 3
Sep 15 07:15:15 webapps kernel: [    0.010000] CPU: Processor Core ID: 3
Sep 15 07:15:15 webapps kernel: [    2.970460] CPU15: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
Sep 15 07:15:15 webapps kernel: [    2.970467] checking TSC synchronization [CPU#0 -> CPU#15]: passed.
Sep 15 07:15:15 webapps kernel: [    2.980066] Brought up 16 CPUs
Sep 15 07:15:15 webapps kernel: [    2.980072] Total of 16 processors activated (60815.84 BogoMIPS).
Sep 15 07:15:15 webapps kernel: [    2.980683] net_namespace: 1400 bytes
Sep 15 07:15:15 webapps kernel: [    2.980683] Booting paravirtualized kernel on bare hardware
Sep 15 07:15:15 webapps kernel: [    2.980683] Time: 11:14:58  Date: 09/15/09
Sep 15 07:15:15 webapps kernel: [    2.980683] regulator: core version 0.5
Sep 15 07:15:15 webapps kernel: [    2.980683] NET: Registered protocol family 16
Sep 15 07:15:15 webapps kernel: [    2.980683] TOM: 00000000d8000000 aka 3456M
Sep 15 07:15:15 webapps kernel: [    2.980683] TOM2: 0000000428000000 aka 17024M
Sep 15 07:15:15 webapps kernel: [    2.980683] ACPI: bus type pci registered
Sep 15 07:15:15 webapps kernel: [    2.980683] PCI: Found AMD Family 10h NB with MMCONFIG support.
Sep 15 07:15:15 webapps kernel: [    2.997024] PCI: Using MMCONFIG at e0000000 - efffffff
Sep 15 07:15:15 webapps kernel: [    2.997026] PCI: Using configuration type 1 for base access
Sep 15 07:15:15 webapps kernel: [    3.028449] ACPI: Interpreter enabled
Sep 15 07:15:15 webapps kernel: [    3.028452] ACPI: (supports S0 S1 S5)
Sep 15 07:15:15 webapps kernel: [    3.028467] ACPI: Using IOAPIC for interrupt routing
Sep 15 07:15:15 webapps kernel: [    3.048833] ACPI: No dock devices found.
Sep 15 07:15:15 webapps kernel: [    3.048952] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 15 07:15:15 webapps kernel: [    3.049292] pci 0000:00:01.1: PME# supported from D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.049297] pci 0000:00:01.1: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.049364] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.049366] pci 0000:00:02.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.049421] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.049431] pci 0000:00:02.1: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.049968] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.049980] pci 0000:00:08.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.050103] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.050107] pci 0000:00:09.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.050135] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.050147] pci 0000:00:0a.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.050195] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.050197] pci 0000:00:0e.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.050244] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.050256] pci 0000:00:0f.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.051015] pci 0000:00:06.0: transparent bridge
Sep 15 07:15:15 webapps kernel: [    3.073168] ACPI: PCI Root Bridge [PCIB] (0000:80)
Sep 15 07:15:15 webapps kernel: [    3.073479] pci 0000:80:01.1: PME# supported from D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.073493] pci 0000:80:01.1: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.074026] pci 0000:80:08.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.074037] pci 0000:80:08.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.074161] pci 0000:80:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.074165] pci 0000:80:09.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.074201] pci 0000:80:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.074204] pci 0000:80:0b.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.074253] pci 0000:80:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.074265] pci 0000:80:0e.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.074307] pci 0000:80:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 15 07:15:15 webapps kernel: [    3.074312] pci 0000:80:0f.0: PME# disabled
Sep 15 07:15:15 webapps kernel: [    3.076674] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *7
Sep 15 07:15:15 webapps kernel: [    3.077049] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.077434] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.077819] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *7
Sep 15 07:15:15 webapps kernel: [    3.078201] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.078576] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *15
Sep 15 07:15:15 webapps kernel: [    3.078953] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.079348] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.079722] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
Sep 15 07:15:15 webapps kernel: [    3.080101] ACPI: PCI Interrupt Link [LMAD] (IRQs 20 21 22 23) *11
Sep 15 07:15:15 webapps kernel: [    3.080478] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *5
Sep 15 07:15:15 webapps kernel: [    3.080854] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
Sep 15 07:15:15 webapps kernel: [    3.081238] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.081622] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
Sep 15 07:15:15 webapps kernel: [    3.082007] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.082386] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15
Sep 15 07:15:15 webapps kernel: [    3.082765] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *14
Sep 15 07:15:15 webapps kernel: [    3.083218] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.083603] ACPI: PCI Interrupt Link [LSA2] (IRQs 20 21 22 23) *7
Sep 15 07:15:15 webapps kernel: [    3.083988] ACPI: PCI Interrupt Link [LE3A] (IRQs 40 41 42 43) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.084371] ACPI: PCI Interrupt Link [LE3B] (IRQs 40 41 42 43) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.084738] ACPI: PCI Interrupt Link [LE3C] (IRQs 40 41 42 43) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.085122] ACPI: PCI Interrupt Link [LE3D] (IRQs 40 41 42 43) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.085498] ACPI: PCI Interrupt Link [IIM0] (IRQs 44 45 46 47) *7
Sep 15 07:15:15 webapps kernel: [    3.085877] ACPI: PCI Interrupt Link [IIM1] (IRQs 44 45 46 47) *7
Sep 15 07:15:15 webapps kernel: [    3.086257] ACPI: PCI Interrupt Link [ISI0] (IRQs 44 45 46 47) *7
Sep 15 07:15:15 webapps kernel: [    3.086636] ACPI: PCI Interrupt Link [ISI1] (IRQs 44 45 46 47) *7
Sep 15 07:15:15 webapps kernel: [    3.087015] ACPI: PCI Interrupt Link [ISI2] (IRQs 44 45 46 47) *7
Sep 15 07:15:15 webapps kernel: [    3.087392] ACPI: PCI Interrupt Link [ILSM] (IRQs 44 45 46 47) *7
Sep 15 07:15:15 webapps kernel: [    3.087775] ACPI: PCI Interrupt Link [ILPM] (IRQs 44 45 46 47) *0, disabled.
Sep 15 07:15:15 webapps kernel: [    3.088164] ACPI: PCI Interrupt Link [LN2A] (IRQs 40 41 42 43) *15
Sep 15 07:15:15 webapps kernel: [    3.088550] ACPI: PCI Interrupt Link [LN2B] (IRQs 40 41 42 43) *15
Sep 15 07:15:15 webapps kernel: [    3.088915] ACPI: PCI Interrupt Link [LN2C] (IRQs 40 41 42 43) *15
Sep 15 07:15:15 webapps kernel: [    3.089292] ACPI: PCI Interrupt Link [LN2D] (IRQs 40 41 42 43) *15
Sep 15 07:15:15 webapps kernel: [    3.089666] ACPI: PCI Interrupt Link [IIM2] (IRQs 44 45 46 47) *15
Sep 15 07:15:15 webapps kernel: [    3.090046] ACPI: PCI Interrupt Link [IIM3] (IRQs 44 45 46 47) *15
Sep 15 07:15:15 webapps kernel: [    3.090425] ACPI: PCI Interrupt Link [ISI3] (IRQs 44 45 46 47) *15
Sep 15 07:15:15 webapps kernel: [    3.090794] ACPI: PCI Interrupt Link [ISI4] (IRQs 44 45 46 47) *15
Sep 15 07:15:15 webapps kernel: [    3.091171] ACPI: PCI Interrupt Link [ISI5] (IRQs 44 45 46 47) *15
Sep 15 07:15:15 webapps kernel: [    3.091542] ACPI: PCI Interrupt Link [ILSN] (IRQs 44 45 46 47) *15
Sep 15 07:15:15 webapps kernel: [    3.091919] ACPI: PCI Interrupt Link [ILPN] (IRQs 44 45 46 47) *15
Sep 15 07:15:15 webapps kernel: [    3.092502] ACPI: WMI: Mapper loaded
Sep 15 07:15:15 webapps kernel: [    3.092565] SCSI subsystem initialized
Sep 15 07:15:15 webapps kernel: [    3.092565] usbcore: registered new interface driver usbfs
Sep 15 07:15:15 webapps kernel: [    3.092565] usbcore: registered new interface driver hub
Sep 15 07:15:15 webapps kernel: [    3.092565] usbcore: registered new device driver usb
Sep 15 07:15:15 webapps kernel: [    3.092565] PCI: Using ACPI for IRQ routing
Sep 15 07:15:15 webapps kernel: [    3.130014] Bluetooth: Core ver 2.13
Sep 15 07:15:15 webapps kernel: [    3.130037] NET: Registered protocol family 31
Sep 15 07:15:15 webapps kernel: [    3.130037] Bluetooth: HCI device and connection manager initialized
Sep 15 07:15:15 webapps kernel: [    3.130037] Bluetooth: HCI socket layer initialized
Sep 15 07:15:15 webapps kernel: [    3.130037] NET: Registered protocol family 8
Sep 15 07:15:15 webapps kernel: [    3.130037] NET: Registered protocol family 20
Sep 15 07:15:15 webapps kernel: [    3.130037] NetLabel: Initializing
Sep 15 07:15:15 webapps kernel: [    3.130038] NetLabel:  domain hash size = 128
Sep 15 07:15:15 webapps kernel: [    3.130039] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 15 07:15:15 webapps kernel: [    3.130055] NetLabel:  unlabeled traffic allowed by default
Sep 15 07:15:15 webapps kernel: [    3.130328] PCI-DMA: Disabling AGP.
Sep 15 07:15:15 webapps kernel: [    3.130489] PCI-DMA: aperture base @ 20000000 size 65536 KB
Sep 15 07:15:15 webapps kernel: [    3.130491] PCI-DMA: using GART IOMMU.
Sep 15 07:15:15 webapps kernel: [    3.130496] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Sep 15 07:15:15 webapps kernel: [    3.134563] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Sep 15 07:15:15 webapps kernel: [    3.134571] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Sep 15 07:15:15 webapps kernel: [    3.260124] AppArmor: AppArmor Filesystem Enabled
Sep 15 07:15:15 webapps kernel: [    3.290042] pnp: PnP ACPI init
Sep 15 07:15:15 webapps kernel: [    3.290071] ACPI: bus type pnp registered
Sep 15 07:15:15 webapps kernel: [    3.300219] pnp: PnP ACPI: found 15 devices
Sep 15 07:15:15 webapps kernel: [    3.300221] ACPI: ACPI bus type pnp unregistered
Sep 15 07:15:15 webapps kernel: [    3.300237] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300240] system 00:05: ioport range 0x800-0x80f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300243] system 00:05: ioport range 0xe000-0xe07f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300246] system 00:05: ioport range 0xe080-0xe0ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300249] system 00:05: ioport range 0xe400-0xe47f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300251] system 00:05: ioport range 0xe480-0xe4ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300254] system 00:05: ioport range 0xe800-0xe87f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300256] system 00:05: ioport range 0xe880-0xe8ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300259] system 00:05: ioport range 0xec00-0xec7f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300261] system 00:05: ioport range 0xec80-0xecff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300265] system 00:05: iomem range 0xdfc80000-0xdfcbffff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300271] system 00:05: iomem range 0xfee01000-0xfeefffff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300276] system 00:06: ioport range 0xf000-0xf07f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300279] system 00:06: ioport range 0xf080-0xf0ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300281] system 00:06: ioport range 0xf400-0xf47f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300284] system 00:06: ioport range 0xf480-0xf4ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300286] system 00:06: ioport range 0xf800-0xf87f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300289] system 00:06: ioport range 0xf880-0xf8ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300292] system 00:06: iomem range 0xfee01000-0xfef00fff could not be reserved
Sep 15 07:15:15 webapps kernel: [    3.300297] system 00:0a: ioport range 0xca0-0xca1 has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300300] system 00:0a: ioport range 0xca4-0xcaf has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300309] system 00:0a: ioport range 0xcf9-0xcf9 could not be reserved
Sep 15 07:15:15 webapps kernel: [    3.300312] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300315] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300319] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300324] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Sep 15 07:15:15 webapps kernel: [    3.300327] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300332] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Sep 15 07:15:15 webapps kernel: [    3.300334] system 00:0c: iomem range 0x100000-0xddffffff could not be reserved
Sep 15 07:15:15 webapps kernel: [    3.300337] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
Sep 15 07:15:15 webapps kernel: [    3.300342] system 00:0e: ioport range 0xf000-0xf07f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300344] system 00:0e: ioport range 0xf080-0xf0ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300347] system 00:0e: ioport range 0xf400-0xf47f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300349] system 00:0e: ioport range 0xf480-0xf4ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300352] system 00:0e: ioport range 0xf800-0xf87f has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300354] system 00:0e: ioport range 0xf880-0xf8ff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.300357] system 00:0e: iomem range 0xfee01000-0xfef00fff could not be reserved
Sep 15 07:15:15 webapps kernel: [    3.300359] system 00:0e: iomem range 0xddf80000-0xddfbffff has been reserved
Sep 15 07:15:15 webapps kernel: [    3.305136] pci 0000:00:06.0: PCI bridge, secondary bus 0000:01
Sep 15 07:15:15 webapps kernel: [    3.305139] pci 0000:00:06.0:   IO window: 0x9000-0x9fff
Sep 15 07:15:15 webapps kernel: [    3.305143] pci 0000:00:06.0:   MEM window: 0xdef00000-0xdf7fffff
Sep 15 07:15:15 webapps kernel: [    3.305146] pci 0000:00:06.0:   PREFETCH window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305149] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
Sep 15 07:15:15 webapps kernel: [    3.305151] pci 0000:00:0a.0:   IO window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305153] pci 0000:00:0a.0:   MEM window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305156] pci 0000:00:0a.0:   PREFETCH window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305159] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:03
Sep 15 07:15:15 webapps kernel: [    3.305161] pci 0000:00:0e.0:   IO window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305163] pci 0000:00:0e.0:   MEM window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305166] pci 0000:00:0e.0:   PREFETCH window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305169] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:04
Sep 15 07:15:15 webapps kernel: [    3.305171] pci 0000:00:0f.0:   IO window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305173] pci 0000:00:0f.0:   MEM window: 0xdfd00000-0xdfffffff
Sep 15 07:15:15 webapps kernel: [    3.305176] pci 0000:00:0f.0:   PREFETCH window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305202] pci 0000:80:0b.0: PCI bridge, secondary bus 0000:81
Sep 15 07:15:15 webapps kernel: [    3.305204] pci 0000:80:0b.0:   IO window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305206] pci 0000:80:0b.0:   MEM window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305209] pci 0000:80:0b.0:   PREFETCH window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305212] pci 0000:80:0e.0: PCI bridge, secondary bus 0000:82
Sep 15 07:15:15 webapps kernel: [    3.305214] pci 0000:80:0e.0:   IO window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305217] pci 0000:80:0e.0:   MEM window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305219] pci 0000:80:0e.0:   PREFETCH window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305223] pci 0000:80:0f.0: PCI bridge, secondary bus 0000:83
Sep 15 07:15:15 webapps kernel: [    3.305224] pci 0000:80:0f.0:   IO window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305227] pci 0000:80:0f.0:   MEM window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305229] pci 0000:80:0f.0:   PREFETCH window: disabled
Sep 15 07:15:15 webapps kernel: [    3.305248] bus: 00 index 0 io port: [0x9000-0xdfff]
Sep 15 07:15:15 webapps kernel: [    3.305250] bus: 00 index 1 io port: [0xe000-0xefff]
Sep 15 07:15:15 webapps kernel: [    3.305252] bus: 00 index 2 io port: [0x00-0x5fff]
Sep 15 07:15:15 webapps kernel: [    3.305253] bus: 00 index 3 mmio: [0xde000000-0xdfffffff]
Sep 15 07:15:15 webapps kernel: [    3.305255] bus: 00 index 4 mmio: [0x0a0000-0x0bffff]
Sep 15 07:15:15 webapps kernel: [    3.305257] bus: 00 index 5 mmio: [0xd8000000-0xdcffffff]
Sep 15 07:15:15 webapps kernel: [    3.305259] bus: 00 index 6 mmio: [0xf0000000-0xffffffff]
Sep 15 07:15:15 webapps kernel: [    3.305261] bus: 00 index 7 mmio: [0x428000000-0xfcffffffff]
Sep 15 07:15:15 webapps kernel: [    3.305263] bus: 01 index 0 io port: [0x9000-0x9fff]
Sep 15 07:15:15 webapps kernel: [    3.305265] bus: 01 index 1 mmio: [0xdef00000-0xdf7fffff]
Sep 15 07:15:15 webapps kernel: [    3.305267] bus: 01 index 2 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305269] bus: 01 index 3 io port: [0x9000-0xdfff]
Sep 15 07:15:15 webapps kernel: [    3.305270] bus: 01 index 4 io port: [0xe000-0xefff]
Sep 15 07:15:15 webapps kernel: [    3.305272] bus: 01 index 5 io port: [0x00-0x5fff]
Sep 15 07:15:15 webapps kernel: [    3.305274] bus: 01 index 6 mmio: [0xde000000-0xdfffffff]
Sep 15 07:15:15 webapps kernel: [    3.305276] bus: 01 index 7 mmio: [0x0a0000-0x0bffff]
Sep 15 07:15:15 webapps kernel: [    3.305278] bus: 01 index 8 mmio: [0xd8000000-0xdcffffff]
Sep 15 07:15:15 webapps kernel: [    3.305280] bus: 01 index 9 mmio: [0xf0000000-0xffffffff]
Sep 15 07:15:15 webapps kernel: [    3.305282] bus: 01 index a mmio: [0x428000000-0xfcffffffff]
Sep 15 07:15:15 webapps kernel: [    3.305284] bus: 02 index 0 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305285] bus: 02 index 1 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305287] bus: 02 index 2 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305288] bus: 02 index 3 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305290] bus: 03 index 0 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305292] bus: 03 index 1 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305293] bus: 03 index 2 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305295] bus: 03 index 3 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305296] bus: 04 index 0 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305298] bus: 04 index 1 mmio: [0xdfd00000-0xdfffffff]
Sep 15 07:15:15 webapps kernel: [    3.305300] bus: 04 index 2 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305301] bus: 04 index 3 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305303] bus: 80 index 0 io port: [0x6000-0x8fff]
Sep 15 07:15:15 webapps kernel: [    3.305305] bus: 80 index 1 io port: [0xf000-0xffff]
Sep 15 07:15:15 webapps kernel: [    3.305307] bus: 80 index 2 mmio: [0xdd000000-0xddffffff]
Sep 15 07:15:15 webapps kernel: [    3.305309] bus: 81 index 0 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305311] bus: 81 index 1 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305312] bus: 81 index 2 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305314] bus: 81 index 3 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305315] bus: 82 index 0 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305317] bus: 82 index 1 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305318] bus: 82 index 2 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305320] bus: 82 index 3 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305321] bus: 83 index 0 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305323] bus: 83 index 1 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305325] bus: 83 index 2 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305326] bus: 83 index 3 mmio: [0x0-0x0]
Sep 15 07:15:15 webapps kernel: [    3.305348] NET: Registered protocol family 2
Sep 15 07:15:15 webapps kernel: [    3.390157] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
Sep 15 07:15:15 webapps kernel: [    3.392397] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Sep 15 07:15:15 webapps kernel: [    3.394849] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Sep 15 07:15:15 webapps kernel: [    3.395462] TCP: Hash tables configured (established 262144 bind 65536)
Sep 15 07:15:15 webapps kernel: [    3.395465] TCP reno registered
Sep 15 07:15:15 webapps kernel: [    3.420396] NET: Registered protocol family 1
Sep 15 07:15:15 webapps kernel: [    3.420549] checking if image is initramfs... it is
Sep 15 07:15:15 webapps kernel: [    4.062611] Freeing initrd memory: 8241k freed
Sep 15 07:15:15 webapps kernel: [    4.069016] audit: initializing netlink socket (disabled)
Sep 15 07:15:15 webapps kernel: [    4.069048] type=2000 audit(1253013298.060:1): initialized
Sep 15 07:15:15 webapps kernel: [    4.078788] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Sep 15 07:15:15 webapps kernel: [    4.080997] VFS: Disk quotas dquot_6.5.1
Sep 15 07:15:15 webapps kernel: [    4.081058] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Sep 15 07:15:15 webapps kernel: [    4.081784] fuse init (API version 7.10)
Sep 15 07:15:15 webapps kernel: [    4.081879] msgmni has been set to 31766
Sep 15 07:15:15 webapps kernel: [    4.082140] alg: No test for stdrng (krng)
Sep 15 07:15:15 webapps kernel: [    4.082158] io scheduler noop registered
Sep 15 07:15:15 webapps kernel: [    4.082161] io scheduler anticipatory registered
Sep 15 07:15:15 webapps kernel: [    4.082163] io scheduler deadline registered (default)
Sep 15 07:15:15 webapps kernel: [    4.082201] io scheduler cfq registered
Sep 15 07:15:15 webapps kernel: [    4.082255] pci 0000:00:00.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599209] pci 0000:00:05.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599249] pci 0000:00:05.1: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599292] pci 0000:00:05.2: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599331] pci 0000:00:06.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599367] pci 0000:00:08.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599422] pci 0000:00:09.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599472] pci 0000:00:0a.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599521] pci 0000:00:0e.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599570] pci 0000:00:0f.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599672] pci 0000:80:00.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599782] pci 0000:80:05.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599821] pci 0000:80:05.1: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599861] pci 0000:80:05.2: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599905] pci 0000:80:08.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.599959] pci 0000:80:09.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.600013] pci 0000:80:0b.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.600030] pci 0000:80:0e.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.600049] pci 0000:80:0f.0: Enabling HT MSI Mapping
Sep 15 07:15:15 webapps kernel: [    4.611804] pcieport-driver 0000:00:0a.0: found MSI capability
Sep 15 07:15:15 webapps kernel: [    4.611945] pcieport-driver 0000:00:0e.0: found MSI capability
Sep 15 07:15:15 webapps kernel: [    4.612107] pcieport-driver 0000:00:0f.0: found MSI capability
Sep 15 07:15:15 webapps kernel: [    4.612294] pcieport-driver 0000:80:0b.0: found MSI capability
Sep 15 07:15:15 webapps kernel: [    4.612462] pcieport-driver 0000:80:0e.0: found MSI capability
Sep 15 07:15:15 webapps kernel: [    4.612631] pcieport-driver 0000:80:0f.0: found MSI capability
Sep 15 07:15:15 webapps kernel: [    4.648604] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 15 07:15:15 webapps kernel: [    4.648614] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 15 07:15:15 webapps kernel: [    4.648810] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Sep 15 07:15:15 webapps kernel: [    4.648813] ACPI: Power Button (FF) [PWRF]
Sep 15 07:15:15 webapps kernel: [    4.648873] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Sep 15 07:15:15 webapps kernel: [    4.648875] ACPI: Power Button (CM) [PWRB]
Sep 15 07:15:15 webapps kernel: [    4.649557] processor ACPI_CPU:00: registered as cooling_device0
Sep 15 07:15:15 webapps kernel: [    4.649594] processor ACPI_CPU:01: registered as cooling_device1
Sep 15 07:15:15 webapps kernel: [    4.649635] processor ACPI_CPU:02: registered as cooling_device2
Sep 15 07:15:15 webapps kernel: [    4.649668] processor ACPI_CPU:03: registered as cooling_device3
Sep 15 07:15:15 webapps kernel: [    4.649704] processor ACPI_CPU:04: registered as cooling_device4
Sep 15 07:15:15 webapps kernel: [    4.649737] processor ACPI_CPU:05: registered as cooling_device5
Sep 15 07:15:15 webapps kernel: [    4.649774] processor ACPI_CPU:06: registered as cooling_device6
Sep 15 07:15:15 webapps kernel: [    4.649809] processor ACPI_CPU:07: registered as cooling_device7
Sep 15 07:15:15 webapps kernel: [    4.649849] processor ACPI_CPU:08: registered as cooling_device8
Sep 15 07:15:15 webapps kernel: [    4.649888] processor ACPI_CPU:09: registered as cooling_device9
Sep 15 07:15:15 webapps kernel: [    4.649926] processor ACPI_CPU:0a: registered as cooling_device10
Sep 15 07:15:15 webapps kernel: [    4.649969] processor ACPI_CPU:0b: registered as cooling_device11
Sep 15 07:15:15 webapps kernel: [    4.650011] processor ACPI_CPU:0c: registered as cooling_device12
Sep 15 07:15:15 webapps kernel: [    4.650058] processor ACPI_CPU:0d: registered as cooling_device13
Sep 15 07:15:15 webapps kernel: [    4.650100] processor ACPI_CPU:0e: registered as cooling_device14
Sep 15 07:15:15 webapps kernel: [    4.650142] processor ACPI_CPU:0f: registered as cooling_device15
Sep 15 07:15:15 webapps kernel: [    4.723455] Linux agpgart interface v0.103
Sep 15 07:15:15 webapps kernel: [    4.723469] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Sep 15 07:15:15 webapps kernel: [    4.723550] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 15 07:15:15 webapps kernel: [    4.723827] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 15 07:15:15 webapps kernel: [    4.724824] brd: module loaded
Sep 15 07:15:15 webapps kernel: [    4.725209] loop: module loaded
Sep 15 07:15:15 webapps kernel: [    4.725278] Fixed MDIO Bus: probed
Sep 15 07:15:15 webapps kernel: [    4.725285] PPP generic driver version 2.4.2
Sep 15 07:15:15 webapps kernel: [    4.725340] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Sep 15 07:15:15 webapps kernel: [    4.725369] Driver 'sd' needs updating - please use bus_type methods
Sep 15 07:15:15 webapps kernel: [    4.725379] Driver 'sr' needs updating - please use bus_type methods
Sep 15 07:15:15 webapps kernel: [    4.726234] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
Sep 15 07:15:15 webapps kernel: [    4.726248] sata_nv 0000:00:05.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
Sep 15 07:15:15 webapps kernel: [    4.726252] sata_nv 0000:00:05.0: Using SWNCQ mode
Sep 15 07:15:15 webapps kernel: [    4.726499] scsi0 : sata_nv
Sep 15 07:15:15 webapps kernel: [    4.726618] scsi1 : sata_nv
Sep 15 07:15:15 webapps kernel: [    4.726832] ata1: SATA max UDMA/133 cmd 0xc480 ctl 0xc400 bmdma 0xbc00 irq 23
Sep 15 07:15:15 webapps kernel: [    4.726835] ata2: SATA max UDMA/133 cmd 0xc080 ctl 0xc000 bmdma 0xbc08 irq 23
Sep 15 07:15:15 webapps kernel: [    5.480445] ata1: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [    6.240418] ata2: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [    6.240950] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
Sep 15 07:15:15 webapps kernel: [    6.240959] sata_nv 0000:00:05.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
Sep 15 07:15:15 webapps kernel: [    6.240965] sata_nv 0000:00:05.1: Using SWNCQ mode
Sep 15 07:15:15 webapps kernel: [    6.241172] scsi2 : sata_nv
Sep 15 07:15:15 webapps kernel: [    6.241249] scsi3 : sata_nv
Sep 15 07:15:15 webapps kernel: [    6.241454] ata3: SATA max UDMA/133 cmd 0xb880 ctl 0xb800 bmdma 0xb080 irq 22
Sep 15 07:15:15 webapps kernel: [    6.241457] ata4: SATA max UDMA/133 cmd 0xb480 ctl 0xb400 bmdma 0xb088 irq 22
Sep 15 07:15:15 webapps kernel: [    7.000442] ata3: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [    7.760420] ata4: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [    7.760943] ACPI: PCI Interrupt Link [LSA2] enabled at IRQ 21
Sep 15 07:15:15 webapps kernel: [    7.760951] sata_nv 0000:00:05.2: PCI INT C -> Link[LSA2] -> GSI 21 (level, low) -> IRQ 21
Sep 15 07:15:15 webapps kernel: [    7.760957] sata_nv 0000:00:05.2: Using SWNCQ mode
Sep 15 07:15:15 webapps kernel: [    7.761172] scsi4 : sata_nv
Sep 15 07:15:15 webapps kernel: [    7.761254] scsi5 : sata_nv
Sep 15 07:15:15 webapps kernel: [    7.761452] ata5: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 21
Sep 15 07:15:15 webapps kernel: [    7.761455] ata6: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 21
Sep 15 07:15:15 webapps kernel: [    8.520449] ata5: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [    9.280430] ata6: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [    9.280980] ACPI: PCI Interrupt Link [ISI0] enabled at IRQ 47
Sep 15 07:15:15 webapps kernel: [    9.280985] sata_nv 0000:80:05.0: PCI INT A -> Link[ISI0] -> GSI 47 (level, low) -> IRQ 47
Sep 15 07:15:15 webapps kernel: [    9.280988] sata_nv 0000:80:05.0: Using SWNCQ mode
Sep 15 07:15:15 webapps kernel: [    9.281193] scsi6 : sata_nv
Sep 15 07:15:15 webapps kernel: [    9.281272] scsi7 : sata_nv
Sep 15 07:15:15 webapps kernel: [    9.281517] ata7: SATA max UDMA/133 cmd 0x8400 ctl 0x8080 bmdma 0x7880 irq 47
Sep 15 07:15:15 webapps kernel: [    9.281520] ata8: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7888 irq 47
Sep 15 07:15:15 webapps kernel: [   10.040450] ata7: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [   10.800418] ata8: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [   10.800949] ACPI: PCI Interrupt Link [ISI1] enabled at IRQ 46
Sep 15 07:15:15 webapps kernel: [   10.800955] sata_nv 0000:80:05.1: PCI INT B -> Link[ISI1] -> GSI 46 (level, low) -> IRQ 46
Sep 15 07:15:15 webapps kernel: [   10.800957] sata_nv 0000:80:05.1: Using SWNCQ mode
Sep 15 07:15:15 webapps kernel: [   10.801134] scsi8 : sata_nv
Sep 15 07:15:15 webapps kernel: [   10.801212] scsi9 : sata_nv
Sep 15 07:15:15 webapps kernel: [   10.801401] ata9: SATA max UDMA/133 cmd 0x7800 ctl 0x7480 bmdma 0x7000 irq 46
Sep 15 07:15:15 webapps kernel: [   10.801404] ata10: SATA max UDMA/133 cmd 0x7400 ctl 0x7080 bmdma 0x7008 irq 46
Sep 15 07:15:15 webapps kernel: [   11.560478] ata9: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [   12.320473] ata10: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [   12.321004] ACPI: PCI Interrupt Link [ISI2] enabled at IRQ 45
Sep 15 07:15:15 webapps kernel: [   12.321010] sata_nv 0000:80:05.2: PCI INT C -> Link[ISI2] -> GSI 45 (level, low) -> IRQ 45
Sep 15 07:15:15 webapps kernel: [   12.321012] sata_nv 0000:80:05.2: Using SWNCQ mode
Sep 15 07:15:15 webapps kernel: [   12.321203] scsi10 : sata_nv
Sep 15 07:15:15 webapps kernel: [   12.321280] scsi11 : sata_nv
Sep 15 07:15:15 webapps kernel: [   12.321488] ata11: SATA max UDMA/133 cmd 0x6c00 ctl 0x6880 bmdma 0x6400 irq 45
Sep 15 07:15:15 webapps kernel: [   12.321494] ata12: SATA max UDMA/133 cmd 0x6800 ctl 0x6480 bmdma 0x6408 irq 45
Sep 15 07:15:15 webapps kernel: [   13.080488] ata11: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [   13.840473] ata12: SATA link down (SStatus 0 SControl 300)
Sep 15 07:15:15 webapps kernel: [   13.841175] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 15 07:15:15 webapps kernel: [   13.841686] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
Sep 15 07:15:15 webapps kernel: [   13.841698] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 20 (level, low) -> IRQ 20
Sep 15 07:15:15 webapps kernel: [   13.841717] ehci_hcd 0000:00:02.1: EHCI Host Controller
Sep 15 07:15:15 webapps kernel: [   13.841797] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Sep 15 07:15:15 webapps kernel: [   13.841828] ehci_hcd 0000:00:02.1: debug port 1
Sep 15 07:15:15 webapps kernel: [   13.841875] ehci_hcd 0000:00:02.1: irq 20, io mem 0xdfcfac00
Sep 15 07:15:15 webapps kernel: [   13.860054] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Sep 15 07:15:15 webapps kernel: [   13.860130] usb usb1: configuration #1 chosen from 1 choice
Sep 15 07:15:15 webapps kernel: [   13.860158] hub 1-0:1.0: USB hub found
Sep 15 07:15:15 webapps kernel: [   13.860168] hub 1-0:1.0: 10 ports detected
Sep 15 07:15:15 webapps kernel: [   13.860286] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 15 07:15:15 webapps kernel: [   13.860801] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
Sep 15 07:15:15 webapps kernel: [   13.860805] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
Sep 15 07:15:15 webapps kernel: [   13.860821] ohci_hcd 0000:00:02.0: OHCI Host Controller
Sep 15 07:15:15 webapps kernel: [   13.860862] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Sep 15 07:15:15 webapps kernel: [   13.860875] ohci_hcd 0000:00:02.0: irq 23, io mem 0xdfcfb000
Sep 15 07:15:15 webapps kernel: [   13.922134] usb usb2: configuration #1 chosen from 1 choice
Sep 15 07:15:15 webapps kernel: [   13.922160] hub 2-0:1.0: USB hub found
Sep 15 07:15:15 webapps kernel: [   13.922169] hub 2-0:1.0: 10 ports detected
Sep 15 07:15:15 webapps kernel: [   13.922279] uhci_hcd: USB Universal Host Controller Interface driver
Sep 15 07:15:15 webapps kernel: [   13.922333] usbcore: registered new interface driver libusual
Sep 15 07:15:15 webapps kernel: [   13.922362] usbcore: registered new interface driver usbserial
Sep 15 07:15:15 webapps kernel: [   13.922373] USB Serial support registered for generic
Sep 15 07:15:15 webapps kernel: [   13.922383] usbcore: registered new interface driver usbserial_generic
Sep 15 07:15:15 webapps kernel: [   13.922389] usbserial: USB Serial Driver core
Sep 15 07:15:15 webapps kernel: [   13.922441] PNP: No PS/2 controller found. Probing ports directly.
Sep 15 07:15:15 webapps kernel: [   13.953181] mice: PS/2 mouse device common for all mice
Sep 15 07:15:15 webapps kernel: [   14.043246] rtc_cmos 00:02: RTC can wake from S4
Sep 15 07:15:15 webapps kernel: [   14.043279] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Sep 15 07:15:15 webapps kernel: [   14.043319] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Sep 15 07:15:15 webapps kernel: [   14.043382] device-mapper: uevent: version 1.0.3
Sep 15 07:15:15 webapps kernel: [   14.043498] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Sep 15 07:15:15 webapps kernel: [   14.044262] device-mapper: multipath: version 1.0.5 loaded
Sep 15 07:15:15 webapps kernel: [   14.044265] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 15 07:15:15 webapps kernel: [   14.045034] cpuidle: using governor ladder
Sep 15 07:15:15 webapps kernel: [   14.045036] cpuidle: using governor menu
Sep 15 07:15:15 webapps kernel: [   14.045620] TCP cubic registered
Sep 15 07:15:15 webapps kernel: [   14.045693] NET: Registered protocol family 10
Sep 15 07:15:15 webapps kernel: [   14.046437] lo: Disabled Privacy Extensions
Sep 15 07:15:15 webapps kernel: [   14.046777] NET: Registered protocol family 17
Sep 15 07:15:15 webapps kernel: [   14.046801] Bluetooth: L2CAP ver 2.11
Sep 15 07:15:15 webapps kernel: [   14.046803] Bluetooth: L2CAP socket layer initialized
Sep 15 07:15:15 webapps kernel: [   14.046806] Bluetooth: SCO (Voice Link) ver 0.6
Sep 15 07:15:15 webapps kernel: [   14.046808] Bluetooth: SCO socket layer initialized
Sep 15 07:15:15 webapps kernel: [   14.046864] Bluetooth: RFCOMM socket layer initialized
Sep 15 07:15:15 webapps kernel: [   14.046870] Bluetooth: RFCOMM TTY layer initialized
Sep 15 07:15:15 webapps kernel: [   14.046872] Bluetooth: RFCOMM ver 1.10
Sep 15 07:15:15 webapps kernel: [   14.047125] powernow-k8: Found 1 Quad-Core AMD Opteron(tm) Processor 8347 HE processors (16 cpu cores) (version 2.20.00)
Sep 15 07:15:15 webapps kernel: [   14.047203] powernow-k8:    0 : pstate 0 (1900 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047206] powernow-k8:    1 : pstate 1 (1700 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047208] powernow-k8:    2 : pstate 2 (1400 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047210] powernow-k8:    3 : pstate 3 (1200 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047211] powernow-k8:    4 : pstate 4 (1000 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047685] powernow-k8:    0 : pstate 0 (1900 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047687] powernow-k8:    1 : pstate 1 (1700 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047689] powernow-k8:    2 : pstate 2 (1400 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047691] powernow-k8:    3 : pstate 3 (1200 MHz)
Sep 15 07:15:15 webapps kernel: [   14.047692] powernow-k8:    4 : pstate 4 (1000 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048171] powernow-k8:    0 : pstate 0 (1900 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048174] powernow-k8:    1 : pstate 1 (1700 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048176] powernow-k8:    2 : pstate 2 (1400 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048177] powernow-k8:    3 : pstate 3 (1200 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048178] powernow-k8:    4 : pstate 4 (1000 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048647] powernow-k8:    0 : pstate 0 (1900 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048651] powernow-k8:    1 : pstate 1 (1700 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048652] powernow-k8:    2 : pstate 2 (1400 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048654] powernow-k8:    3 : pstate 3 (1200 MHz)
Sep 15 07:15:15 webapps kernel: [   14.048655] powernow-k8:    4 : pstate 4 (1000 MHz)
Sep 15 07:15:15 webapps kernel: [   14.049099] registered taskstats version 1
Sep 15 07:15:15 webapps kernel: [   14.049486]   Magic number: 9:478:226
Sep 15 07:15:15 webapps kernel: [   14.049662] rtc_cmos 00:02: setting system clock to 2009-09-15 11:15:09 UTC (1253013309)
Sep 15 07:15:15 webapps kernel: [   14.049668] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 15 07:15:15 webapps kernel: [   14.049670] EDD information not available.
Sep 15 07:15:15 webapps kernel: [   14.049726] Freeing unused kernel memory: 536k freed
Sep 15 07:15:15 webapps kernel: [   14.050060] Write protecting the kernel read-only data: 6708k
Sep 15 07:15:15 webapps kernel: [   14.180259] usb 1-1: new high speed USB device using ehci_hcd and address 2
Sep 15 07:15:15 webapps kernel: [   14.274866] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Sep 15 07:15:15 webapps kernel: [   14.275465] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
Sep 15 07:15:15 webapps kernel: [   14.275471] forcedeth 0000:00:08.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
Sep 15 07:15:15 webapps kernel: [   14.276701] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 2, addr 00:21:28:00:1a:f6
Sep 15 07:15:15 webapps kernel: [   14.276704] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
Sep 15 07:15:15 webapps kernel: [   14.277194] ACPI: PCI Interrupt Link [LMAD] enabled at IRQ 21
Sep 15 07:15:15 webapps kernel: [   14.277197] forcedeth 0000:00:09.0: PCI INT A -> Link[LMAD] -> GSI 21 (level, low) -> IRQ 21
Sep 15 07:15:15 webapps kernel: [   14.278296] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 3, addr 00:21:28:00:1a:f7
Sep 15 07:15:15 webapps kernel: [   14.278299] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
Sep 15 07:15:15 webapps kernel: [   14.278840] ACPI: PCI Interrupt Link [IIM0] enabled at IRQ 44
Sep 15 07:15:15 webapps kernel: [   14.278850] forcedeth 0000:80:08.0: PCI INT A -> Link[IIM0] -> GSI 44 (level, low) -> IRQ 44
Sep 15 07:15:15 webapps kernel: [   14.279935] forcedeth 0000:80:08.0: ifname eth2, PHY OUI 0x5043 @ 2, addr 00:21:28:00:1a:f8
Sep 15 07:15:15 webapps kernel: [   14.279938] forcedeth 0000:80:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
Sep 15 07:15:15 webapps kernel: [   14.280441] ACPI: PCI Interrupt Link [IIM1] enabled at IRQ 47
Sep 15 07:15:15 webapps kernel: [   14.280443] forcedeth 0000:80:09.0: PCI INT A -> Link[IIM1] -> GSI 47 (level, low) -> IRQ 47
Sep 15 07:15:15 webapps kernel: [   14.281011] Adaptec aacraid driver 1.1-5[2456]-ms
Sep 15 07:15:15 webapps kernel: [   14.281604] forcedeth 0000:80:09.0: ifname eth3, PHY OUI 0x5043 @ 3, addr 00:21:28:00:1a:f9
Sep 15 07:15:15 webapps kernel: [   14.281607] forcedeth 0000:80:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
Sep 15 07:15:15 webapps kernel: [   14.281771] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
Sep 15 07:15:15 webapps kernel: [   14.281790] aacraid 0000:04:00.0: PCI INT A -> Link[LNEB] -> GSI 19 (level, low) -> IRQ 19
Sep 15 07:15:15 webapps kernel: [   14.403816] usb 1-1: configuration #1 chosen from 1 choice
Sep 15 07:15:15 webapps kernel: [   14.407889] Initializing USB Mass Storage driver...
Sep 15 07:15:15 webapps kernel: [   14.408067] scsi13 : SCSI emulation for USB Mass Storage devices
Sep 15 07:15:15 webapps kernel: [   14.408205] usbcore: registered new interface driver usb-storage
Sep 15 07:15:15 webapps kernel: [   14.408208] USB Mass Storage support registered.
Sep 15 07:15:15 webapps kernel: [   14.540317] AAC0: kernel 5.2-0[15825] Jun 28 2008
Sep 15 07:15:15 webapps kernel: [   14.540321] AAC0: monitor 5.2-0[15825]
Sep 15 07:15:15 webapps kernel: [   14.540323] AAC0: bios 5.2-0[15825]
Sep 15 07:15:15 webapps kernel: [   14.540326] AAC0: serial 00909AA0727
Sep 15 07:15:15 webapps kernel: [   14.540328] AAC0: Non-DASD support enabled.
Sep 15 07:15:15 webapps kernel: [   14.540329] AAC0: 64bit support enabled.
Sep 15 07:15:15 webapps kernel: [   14.540333] AAC0: 64 Bit DAC enabled
Sep 15 07:15:15 webapps kernel: [   14.547436] scsi12 : aacraid
Sep 15 07:15:15 webapps kernel: [   14.547774] scsi 12:0:0:0: Direct-Access     Sun      WEBAPPS          V1.0 PQ: 0 ANSI: 2
Sep 15 07:15:15 webapps kernel: [   14.558976] scsi 12:1:0:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.560964] scsi 12:1:1:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.562660] scsi 12:1:2:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.564414] scsi 12:1:3:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.566165] scsi 12:1:4:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.567885] scsi 12:1:5:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.569637] scsi 12:1:6:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.571359] scsi 12:1:7:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.673777] scsi 12:3:0:0: Enclosure         ADAPTEC  Virtual SGPIO  0 0001 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.700022] usb 1-6: new high speed USB device using ehci_hcd and address 5
Sep 15 07:15:15 webapps kernel: [   14.765395] scsi 12:3:1:0: Enclosure         ADAPTEC  Virtual SGPIO  1 0001 PQ: 0 ANSI: 5
Sep 15 07:15:15 webapps kernel: [   14.820870] sd 12:0:0:0: [sda] 2005585920 512-byte hardware sectors: (1.02 TB/956 GiB)
Sep 15 07:15:15 webapps kernel: [   14.820891] sd 12:0:0:0: [sda] Write Protect is off
Sep 15 07:15:15 webapps kernel: [   14.820928] sd 12:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
Sep 15 07:15:15 webapps kernel: [   14.821050] sd 12:0:0:0: [sda] 2005585920 512-byte hardware sectors: (1.02 TB/956 GiB)
Sep 15 07:15:15 webapps kernel: [   14.821067] sd 12:0:0:0: [sda] Write Protect is off
Sep 15 07:15:15 webapps kernel: [   14.821099] sd 12:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
Sep 15 07:15:15 webapps kernel: [   14.821104]  sda: sda1 sda2 < sda5 >
Sep 15 07:15:15 webapps kernel: [   14.827776] sd 12:0:0:0: [sda] Attached SCSI removable disk
Sep 15 07:15:15 webapps kernel: [   14.827854] sd 12:0:0:0: Attached scsi generic sg0 type 0
Sep 15 07:15:15 webapps kernel: [   14.827931] scsi 12:1:0:0: Attached scsi generic sg1 type 0
Sep 15 07:15:15 webapps kernel: [   14.828004] scsi 12:1:1:0: Attached scsi generic sg2 type 0
Sep 15 07:15:15 webapps kernel: [   14.828116] scsi 12:1:2:0: Attached scsi generic sg3 type 0
Sep 15 07:15:15 webapps kernel: [   14.828234] scsi 12:1:3:0: Attached scsi generic sg4 type 0
Sep 15 07:15:15 webapps kernel: [   14.828325] scsi 12:1:4:0: Attached scsi generic sg5 type 0
Sep 15 07:15:15 webapps kernel: [   14.828397] scsi 12:1:5:0: Attached scsi generic sg6 type 0
Sep 15 07:15:15 webapps kernel: [   14.828471] scsi 12:1:6:0: Attached scsi generic sg7 type 0
Sep 15 07:15:15 webapps kernel: [   14.828563] scsi 12:1:7:0: Attached scsi generic sg8 type 0
Sep 15 07:15:15 webapps kernel: [   14.828654] scsi 12:3:0:0: Attached scsi generic sg9 type 13
Sep 15 07:15:15 webapps kernel: [   14.828763] scsi 12:3:1:0: Attached scsi generic sg10 type 13
Sep 15 07:15:15 webapps kernel: [   14.851140] usb 1-6: configuration #1 chosen from 1 choice
Sep 15 07:15:15 webapps kernel: [   14.851333] hub 1-6:1.0: USB hub found
Sep 15 07:15:15 webapps kernel: [   14.851426] hub 1-6:1.0: 4 ports detected
Sep 15 07:15:15 webapps kernel: [   14.860834] Driver 'ses' needs updating - please use bus_type methods
Sep 15 07:15:15 webapps kernel: [   14.860865] ses 12:3:0:0: Attached Enclosure device
Sep 15 07:15:15 webapps kernel: [   14.860872] ses 12:3:1:0: Attached Enclosure device
Sep 15 07:15:15 webapps kernel: [   15.050725] PM: Starting manual resume from disk
Sep 15 07:15:15 webapps kernel: [   15.080770] kjournald starting.  Commit interval 5 seconds
Sep 15 07:15:15 webapps kernel: [   15.080782] EXT3-fs: mounted filesystem with ordered data mode.
Sep 15 07:15:15 webapps kernel: [   15.190045] usb 2-2: new full speed USB device using ohci_hcd and address 2
Sep 15 07:15:15 webapps kernel: [   15.430324] usb 2-2: configuration #1 chosen from 1 choice
Sep 15 07:15:15 webapps kernel: [   15.780061] usb 2-5: new low speed USB device using ohci_hcd and address 3
Sep 15 07:15:15 webapps kernel: [   16.012786] usb 2-5: configuration #1 chosen from 1 choice
Sep 15 07:15:15 webapps kernel: [   16.657579] udev: starting version 141
Sep 15 07:15:15 webapps kernel: [   16.825805] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xed00
Sep 15 07:15:15 webapps kernel: [   16.825832] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xee00
Sep 15 07:15:15 webapps kernel: [   16.825908] i2c-adapter i2c-2: nForce2 SMBus adapter at 0x8800
Sep 15 07:15:15 webapps kernel: [   16.825923] i2c-adapter i2c-3: nForce2 SMBus adapter at 0x8480
Sep 15 07:15:15 webapps kernel: [   16.862468] usbcore: registered new interface driver hiddev
Sep 15 07:15:15 webapps kernel: [   16.866547] input: PC Speaker as /devices/platform/pcspkr/input/input3
Sep 15 07:15:15 webapps kernel: [   16.872813] input: RU RU-CIM as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input4
Sep 15 07:15:15 webapps kernel: [   16.890046] resource map sanity check conflict: 0xff000000 0xffffffff 0xff700000 0xffffffff reserved
Sep 15 07:15:15 webapps kernel: [   16.890058] ------------[ cut here ]------------
Sep 15 07:15:15 webapps kernel: [   16.890061] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
Sep 15 07:15:15 webapps kernel: [   16.890064] Modules linked in: ck804xrom(+) mtd chipreg map_funcs pcspkr(+) usbhid(+) i2c_nforce2 ses enclosure usb_storage aacraid forcedeth fbcon tileblit font bitblit softcursor
Sep 15 07:15:15 webapps kernel: [   16.890078] Pid: 1391, comm: modprobe Not tainted 2.6.28-11-server #42-Ubuntu
Sep 15 07:15:15 webapps kernel: [   16.890081] Call Trace:
Sep 15 07:15:15 webapps kernel: [   16.890089]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
Sep 15 07:15:15 webapps kernel: [   16.890094]  [<ffffffff80257686>] ? iomem_map_sanity_check+0x46/0xd0
Sep 15 07:15:15 webapps kernel: [   16.890098]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
Sep 15 07:15:15 webapps kernel: [   16.890103]  [<ffffffffa00bc2db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Sep 15 07:15:15 webapps kernel: [   16.890107]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
Sep 15 07:15:15 webapps kernel: [   16.890111]  [<ffffffffa00bc2db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Sep 15 07:15:15 webapps kernel: [   16.890115]  [<ffffffffa00c2041>] init_ck804xrom+0x41/0x59 [ck804xrom]
Sep 15 07:15:15 webapps kernel: [   16.890119]  [<ffffffffa00c2000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
Sep 15 07:15:15 webapps kernel: [   16.890123]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
Sep 15 07:15:15 webapps kernel: [   16.890129]  [<ffffffff8041b919>] ? rb_insert_color+0x109/0x140
Sep 15 07:15:15 webapps kernel: [   16.890135]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0
Sep 15 07:15:15 webapps kernel: [   16.890138]  [<ffffffff8024870b>] ? enqueue_task_fair+0x7b/0x80
Sep 15 07:15:15 webapps kernel: [   16.890142]  [<ffffffff8023e6a0>] ? enqueue_task+0x50/0x60
Sep 15 07:15:15 webapps kernel: [   16.890145]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0
Sep 15 07:15:15 webapps kernel: [   16.890152]  [<ffffffff8027eecd>] sys_init_module+0xad/0x1e0
Sep 15 07:15:15 webapps kernel: [   16.890155]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Sep 15 07:15:15 webapps kernel: [   16.890158] ---[ end trace 2df41ba1dd6e3af1 ]---
Sep 15 07:15:15 webapps kernel: [   17.090134] generic-usb 0003:14DD:1005.0001: input,hidraw0: USB HID v1.11 Keyboard [RU RU-CIM] on usb-0000:00:02.0-2/input0
Sep 15 07:15:15 webapps kernel: [   17.098851] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input5
Sep 15 07:15:15 webapps kernel: [   17.200139] generic-usb 0003:046B:FF10.0002: input,hidraw1: USB HID v1.10 Keyboard [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:02.0-5/input0
Sep 15 07:15:15 webapps kernel: [   17.208911] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.1/input/input6
Sep 15 07:15:15 webapps kernel: [   17.310070] generic-usb 0003:046B:FF10.0003: input,hidraw2: USB HID v1.10 Mouse [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:02.0-5/input1
Sep 15 07:15:15 webapps kernel: [   17.310095] usbcore: registered new interface driver usbhid
Sep 15 07:15:15 webapps kernel: [   17.310099] usbhid: v2.6:USB HID core driver
Sep 15 07:15:15 webapps kernel: [   17.423827] lp: driver loaded but no devices found
Sep 15 07:15:15 webapps kernel: [   17.639511] Adding 39526392k swap on /dev/mapper/webapps-swap_1.  Priority:-1 extents:1 across:39526392k
Sep 15 07:15:15 webapps kernel: [   18.181298] EXT3 FS on dm-0, internal journal
Sep 15 07:15:15 webapps kernel: [   19.435017] scsi 13:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-T632A SR03 PQ: 0 ANSI: 0
Sep 15 07:15:15 webapps kernel: [   19.452742] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 15 07:15:15 webapps kernel: [   19.452746] Uniform CD-ROM driver Revision: 3.20
Sep 15 07:15:15 webapps kernel: [   19.452923] sr 13:0:0:0: Attached scsi generic sg11 type 5
```

---

### Post by dkurtz on 2009-09-15
```

[B]dmesg

[/B][    0.000000] BIOS EBDA/lowmem at: 00097400/00097400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-server (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 (Ubuntu 2.6.28-11.42-server)
[    0.000000] Command line: root=/dev/mapper/webapps-root ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000097400 (usable)
[    0.000000]  BIOS-e820: 0000000000097400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7fa0000 (usable)
[    0.000000]  BIOS-e820: 00000000d7fae000 - 00000000d7fb0000 (usable)
[    0.000000]  BIOS-e820: 00000000d7fb0000 - 00000000d7fbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d7fbe000 - 00000000d7ff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000d7ff0000 - 00000000d8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000428000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x428000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xd7fb0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000097400 (usable)
[    0.000000]  modified: 0000000000097400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000d7fa0000 (usable)
[    0.000000]  modified: 00000000d7fae000 - 00000000d7fb0000 (usable)
[    0.000000]  modified: 00000000d7fb0000 - 00000000d7fbe000 (ACPI data)
[    0.000000]  modified: 00000000d7fbe000 - 00000000d7ff0000 (ACPI NVS)
[    0.000000]  modified: 00000000d7ff0000 - 00000000d8000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000428000000 (usable)
[    0.000000] init_memory_mapping: 0000000000000000-00000000d7fb0000
[    0.000000]  0000000000 - 00d7e00000 page 2M
[    0.000000]  00d7e00000 - 00d7fb0000 page 4k
[    0.000000] kernel direct mapping tables up to d7fb0000 @ 10000-16000
[    0.000000] last_map_addr: d7fb0000 end: d7fb0000
[    0.000000] init_memory_mapping: 0000000100000000-0000000428000000
[    0.000000]  0100000000 - 0428000000 page 2M
[    0.000000] kernel direct mapping tables up to 428000000 @ 14000-26000
[    0.000000] last_map_addr: 428000000 end: 428000000
[    0.000000] RAMDISK: 377e3000 - 37fef57b
[    0.000000] ACPI: RSDP 000FAF20, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT D7FB0000, 005C (r1 SUN    X4x40          65 MSFT       97)
[    0.000000] ACPI: FACP D7FB0200, 0084 (r2 SUN    X4x40          65 MSFT       97)
[    0.000000] ACPI: DSDT D7FB0610, 7F1C (r1 SUN    X4x40          65 INTL 20051117)
[    0.000000] ACPI: FACS D7FBE000, 0040
[    0.000000] ACPI: APIC D7FB0390, 012C (r1 SUN    X4x40          65 MSFT       97)
[    0.000000] ACPI: SPCR D7FB04C0, 0050 (r1 SUN    X4x40          65 MSFT       97)
[    0.000000] ACPI: MCFG D7FB0510, 003C (r1 SUN    OEMMCFG        65 MSFT       97)
[    0.000000] ACPI: SLIT D7FB0580, 003C (r1 SUN    OEMSLIT        65 MSFT       97)
[    0.000000] ACPI: SPMI D7FB05C0, 0041 (r1 SUN    OEMSPMI        65 MSFT       97)
[    0.000000] ACPI: OEMB D7FBE040, 00AE (r1 SUN    X4x40          65 MSFT       97)
[    0.000000] ACPI: SRAT D7FB8530, 0220 (r1 AMD    FAM_F_10        2 AMD         1)
[    0.000000] ACPI: HPET D7FB8750, 0038 (r1 SUN    OEMHPET0       65 MSFT       97)
[    0.000000] ACPI: EINJ D7FB8790, 0130 (r1  AMIER AMI_EINJ  6000915 MSFT       97)
[    0.000000] ACPI: BERT D7FB8920, 0030 (r1  AMIER AMI_BERT  6000915 MSFT       97)
[    0.000000] ACPI: ERST D7FB8950, 01B0 (r1  AMIER AMI_ERST  6000915 MSFT       97)
[    0.000000] ACPI: HEST D7FB8B00, 00A8 (r1  AMIER AMI_HEST  6000915 MSFT       97)
[    0.000000] ACPI: SSDT D7FB8BB0, 2854 (r1 A M I  POWERNOW        1 AMD         1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0428000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [00377e3000 - 0037fef57b]          RAMDISK ==> [00377e3000 - 0037fef57b]
[    0.000000]   #4 [0000097400 - 0000100000]    BIOS reserved ==> [0000097400 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #6 [0000014000 - 0000021000]          PGTABLE ==> [0000014000 - 0000021000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe2000e9fffff] PMD -> [ffff880028200000-ffff880036bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00428000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000097
[    0.000000]     0: 0x00000100 -> 0x000d7fa0
[    0.000000]     0: 0x000d7fae -> 0x000d7fb0
[    0.000000]     0: 0x00100000 -> 0x00428000
[    0.000000] On node 0 totalpages: 4194089
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2563 pages reserved
[    0.000000]   DMA zone: 1356 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 866266 pages, LIFO batch:31
[    0.000000]   Normal zone: 45248 pages used for memmap
[    0.000000]   Normal zone: 3264320 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0xe008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x08] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x09] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x0a] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x0b] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x0c] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x0d] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0e] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0f] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x11] lapic_id[0x90] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x12] lapic_id[0x91] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x13] lapic_id[0x92] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x14] lapic_id[0x93] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x15] lapic_id[0x94] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x16] lapic_id[0x95] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x17] lapic_id[0x96] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x18] lapic_id[0x97] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xddfff000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 1, version 0, address 0xddfff000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 24 CPUs, 8 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000097000 - 0000000000098000
[    0.000000] PM: Registered nosave memory: 0000000000098000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000d7fa0000 - 00000000d7fae000
[    0.000000] PM: Registered nosave memory: 00000000d7fb0000 - 00000000d7fbe000
[    0.000000] PM: Registered nosave memory: 00000000d7fbe000 - 00000000d7ff0000
[    0.000000] PM: Registered nosave memory: 00000000d7ff0000 - 00000000d8000000
[    0.000000] PM: Registered nosave memory: 00000000d8000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at f1000000 (gap: f0000000:ec00000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 24, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4131942
[    0.000000] Kernel command line: root=/dev/mapper/webapps-root ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1898.613 MHz processor.
[    0.010000] spurious 8259A interrupt: IRQ7.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.010000] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.010000] allocated 174325760 bytes of page_cgroup
[    0.010000] please try cgroup_disable=memory option if you don't want
[    0.010000] Scanning for low memory corruption every 60 seconds
[    0.010000] Checking aperture...
[    0.010000] No AGP bridge found
[    0.010000] Node 0: aperture @ 20000000 size 32 MB
[    0.010000] Aperture pointing to e820 RAM. Ignoring.
[    0.010000] Your BIOS doesn't leave a aperture memory hole
[    0.010000] Please enable the IOMMU option in the BIOS setup
[    0.010000] This costs you 64 MB of RAM
[    0.010000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.010000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.010000] Memory: 16255408k/17432576k available (4758k kernel code, 656220k absent, 519968k reserved, 2542k data, 536k init)
[    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=24, Nodes=1
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3797.22 BogoMIPS (lpj=18986110)
[    0.010000] Security Framework initialized
[    0.010000] SELinux:  Disabled at boot.
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] tseg: 0000000000
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] using C1E aware idle routine
[    0.010000] ACPI: Core revision 20080926
[    0.010000] ACPI: Checking initramfs for custom DSDT
[    0.330078] Setting APIC routing to physical flat
[    0.330693] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.438529] CPU0: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    0.440000] Booting processor 1 APIC 0x5 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3803.85 BogoMIPS (lpj=19019273)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.590478] CPU1: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    0.590488] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.600128] Booting processor 2 APIC 0x6 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 3803.74 BogoMIPS (lpj=19018739)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.760446] CPU2: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    0.760453] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.770124] Booting processor 3 APIC 0x7 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 3803.75 BogoMIPS (lpj=19018763)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.930409] CPU3: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    0.930417] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.940123] Booting processor 4 APIC 0x8 ip 0x6000
[    0.010000] Initializing CPU#4
[    0.010000] Calibrating delay using timer specific routine.. 3800.81 BogoMIPS (lpj=19004074)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 1
[    0.010000] CPU: Processor Core ID: 0
[    1.100484] CPU4: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    1.100491] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
[    1.110124] Booting processor 5 APIC 0x9 ip 0x6000
[    0.010000] Initializing CPU#5
[    0.010000] Calibrating delay using timer specific routine.. 3801.04 BogoMIPS (lpj=19005247)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 1
[    0.010000] CPU: Processor Core ID: 1
[    1.270461] CPU5: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    1.270468] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
[    1.280126] Booting processor 6 APIC 0xa ip 0x6000
[    0.010000] Initializing CPU#6
[    0.010000] Calibrating delay using timer specific routine.. 3801.07 BogoMIPS (lpj=19005351)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 1
[    0.010000] CPU: Processor Core ID: 2
[    1.440445] CPU6: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    1.440452] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
[    1.450132] Booting processor 7 APIC 0xb ip 0x6000
[    0.010000] Initializing CPU#7
[    0.010000] Calibrating delay using timer specific routine.. 3800.83 BogoMIPS (lpj=19004168)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 1
[    0.010000] CPU: Processor Core ID: 3
[    1.610443] CPU7: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    1.610450] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
[    1.620127] Booting processor 8 APIC 0xc ip 0x6000
[    0.010000] Initializing CPU#8
[    0.010000] Calibrating delay using timer specific routine.. 3800.82 BogoMIPS (lpj=19004147)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 2
[    0.010000] CPU: Processor Core ID: 0
[    1.780433] CPU8: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    1.780440] checking TSC synchronization [CPU#0 -> CPU#8]: passed.
[    1.790128] Booting processor 9 APIC 0xd ip 0x6000
[    0.010000] Initializing CPU#9
[    0.010000] Calibrating delay using timer specific routine.. 3800.20 BogoMIPS (lpj=19001022)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 2
[    0.010000] CPU: Processor Core ID: 1
[    1.950427] CPU9: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    1.950434] checking TSC synchronization [CPU#0 -> CPU#9]: passed.
[    1.960125] Booting processor 10 APIC 0xe ip 0x6000
[    0.010000] Initializing CPU#10
[    0.010000] Calibrating delay using timer specific routine.. 3800.42 BogoMIPS (lpj=19002133)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 2
[    0.010000] CPU: Processor Core ID: 2
[    2.120510] CPU10: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    2.120517] checking TSC synchronization [CPU#0 -> CPU#10]: passed.
[    2.130133] Booting processor 11 APIC 0xf ip 0x6000
[    0.010000] Initializing CPU#11
[    0.010000] Calibrating delay using timer specific routine.. 3800.63 BogoMIPS (lpj=19003184)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 2
[    0.010000] CPU: Processor Core ID: 3
[    2.290488] CPU11: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    2.290495] checking TSC synchronization [CPU#0 -> CPU#11]: passed.
[    2.300129] Booting processor 12 APIC 0x10 ip 0x6000
[    0.010000] Initializing CPU#12
[    0.010000] Calibrating delay using timer specific routine.. 3800.22 BogoMIPS (lpj=19001116)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 3
[    0.010000] CPU: Processor Core ID: 0
[    2.460504] CPU12: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    2.460511] checking TSC synchronization [CPU#0 -> CPU#12]: passed.
[    2.470129] Booting processor 13 APIC 0x11 ip 0x6000
[    0.010000] Initializing CPU#13
[    0.010000] Calibrating delay using timer specific routine.. 3800.25 BogoMIPS (lpj=19001272)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 3
[    0.010000] CPU: Processor Core ID: 1
[    2.630484] CPU13: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    2.630491] checking TSC synchronization [CPU#0 -> CPU#13]: passed.
[    2.640131] Booting processor 14 APIC 0x12 ip 0x6000
[    0.010000] Initializing CPU#14
[    0.010000] Calibrating delay using timer specific routine.. 3800.68 BogoMIPS (lpj=19003439)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 3
[    0.010000] CPU: Processor Core ID: 2
[    2.800472] CPU14: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    2.800479] checking TSC synchronization [CPU#0 -> CPU#14]: passed.
[    2.810135] Booting processor 15 APIC 0x13 ip 0x6000
[    0.010000] Initializing CPU#15
[    0.010000] Calibrating delay using timer specific routine.. 3800.23 BogoMIPS (lpj=19001179)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 3
[    0.010000] CPU: Processor Core ID: 3
[    2.970460] CPU15: Quad-Core AMD Opteron(tm) Processor 8347 HE stepping 03
[    2.970467] checking TSC synchronization [CPU#0 -> CPU#15]: passed.
[    2.980066] Brought up 16 CPUs
[    2.980072] Total of 16 processors activated (60815.84 BogoMIPS).
[    2.980200] CPU0 attaching sched-domain:
[    2.980203]  domain 0: span 0-15 level CPU
[    2.980206]   groups: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
[    2.980218] CPU1 attaching sched-domain:
[    2.980220]  domain 0: span 0-15 level CPU
[    2.980222]   groups: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 0
[    2.980238] CPU2 attaching sched-domain:
[    2.980240]  domain 0: span 0-15 level CPU
[    2.980242]   groups: 2 3 4 5 6 7 8 9 10 11 12 13 14 15 0 1
[    2.980251] CPU3 attaching sched-domain:
[    2.980252]  domain 0: span 0-15 level CPU
[    2.980254]   groups: 3 4 5 6 7 8 9 10 11 12 13 14 15 0 1 2
[    2.980265] CPU4 attaching sched-domain:
[    2.980266]  domain 0: span 0-15 level CPU
[    2.980268]   groups: 4 5 6 7 8 9 10 11 12 13 14 15 0 1 2 3
[    2.980281] CPU5 attaching sched-domain:
[    2.980283]  domain 0: span 0-15 level CPU
[    2.980284]   groups: 5 6 7 8 9 10 11 12 13 14 15 0 1 2 3 4
[    2.980300] CPU6 attaching sched-domain:
[    2.980301]  domain 0: span 0-15 level CPU
[    2.980303]   groups: 6 7 8 9 10 11 12 13 14 15 0 1 2 3 4 5
[    2.980315] CPU7 attaching sched-domain:
[    2.980317]  domain 0: span 0-15 level CPU
[    2.980319]   groups: 7 8 9 10 11 12 13 14 15 0 1 2 3 4 5 6
[    2.980330] CPU8 attaching sched-domain:
[    2.980332]  domain 0: span 0-15 level CPU
[    2.980333]   groups: 8 9 10 11 12 13 14 15 0 1 2 3 4 5 6 7
[    2.980345] CPU9 attaching sched-domain:
[    2.980346]  domain 0: span 0-15 level CPU
[    2.980348]   groups: 9 10 11 12 13 14 15 0 1 2 3 4 5 6 7 8
[    2.980360] CPU10 attaching sched-domain:
[    2.980361]  domain 0: span 0-15 level CPU
[    2.980363]   groups: 10 11 12 13 14 15 0 1 2 3 4 5 6 7 8 9
[    2.980374] CPU11 attaching sched-domain:
[    2.980376]  domain 0: span 0-15 level CPU
[    2.980378]   groups: 11 12 13 14 15 0 1 2 3 4 5 6 7 8 9 10
[    2.980391] CPU12 attaching sched-domain:
[    2.980393]  domain 0: span 0-15 level CPU
[    2.980395]   groups: 12 13 14 15 0 1 2 3 4 5 6 7 8 9 10 11
[    2.980406] CPU13 attaching sched-domain:
[    2.980408]  domain 0: span 0-15 level CPU
[    2.980409]   groups: 13 14 15 0 1 2 3 4 5 6 7 8 9 10 11 12
[    2.980419] CPU14 attaching sched-domain:
[    2.980420]  domain 0: span 0-15 level CPU
[    2.980422]   groups: 14 15 0 1 2 3 4 5 6 7 8 9 10 11 12 13
[    2.980433] CPU15 attaching sched-domain:
[    2.980435]  domain 0: span 0-15 level CPU
[    2.980437]   groups: 15 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14
[    2.980683] net_namespace: 1400 bytes
[    2.980683] Booting paravirtualized kernel on bare hardware
[    2.980683] Time: 11:14:58  Date: 09/15/09
[    2.980683] regulator: core version 0.5
[    2.980683] NET: Registered protocol family 16
[    2.980683] node 0 link 1: io port [9000, cfff]
[    2.980683] node 1 link 2: io port [6000, 8fff]
[    2.980683] node 0 link 1: io port [e000, efff]
[    2.980683] node 1 link 2: io port [f000, ffff]
[    2.980683] TOM: 00000000d8000000 aka 3456M
[    2.980683] Fam 10h mmconf [e0000000, efffffff]
[    2.980683] node 0 link 1: mmio [de000000, dfffffff]
[    2.980683] node 1 link 2: mmio [dd000000, ddffffff]
[    2.980683] node 0 link 1: mmio [e0000000, e7ffffff] ==> none
[    2.980683] node 1 link 2: mmio [e8000000, efffffff] ==> none
[    2.980683] node 0 link 1: mmio [a0000, bffff]
[    2.980683] TOM2: 0000000428000000 aka 17024M
[    2.980683] bus: [00,04] on node 0 link 1
[    2.980683] bus: 00 index 0 io port: [9000, dfff]
[    2.980683] bus: 00 index 1 io port: [e000, efff]
[    2.980683] bus: 00 index 2 io port: [0, 5fff]
[    2.980683] bus: 00 index 3 mmio: [de000000, dfffffff]
[    2.980683] bus: 00 index 4 mmio: [a0000, bffff]
[    2.980683] bus: 00 index 5 mmio: [d8000000, dcffffff]
[    2.980683] bus: 00 index 6 mmio: [f0000000, ffffffff]
[    2.980683] bus: 00 index 7 mmio: [428000000, fcffffffff]
[    2.980683] bus: [80,83] on node 1 link 2
[    2.980683] bus: 80 index 0 io port: [6000, 8fff]
[    2.980683] bus: 80 index 1 io port: [f000, ffff]
[    2.980683] bus: 80 index 2 mmio: [dd000000, ddffffff]
[    2.980683] ACPI: bus type pci registered
[    2.980683] PCI: Found AMD Family 10h NB with MMCONFIG support.
[    2.997024] PCI: Using MMCONFIG at e0000000 - efffffff
[    2.997026] PCI: Using configuration type 1 for base access
[    2.997696] ACPI: EC: Look up EC in DSDT
[    3.028449] ACPI: Interpreter enabled
[    3.028452] ACPI: (supports S0 S1 S5)
[    3.028467] ACPI: Using IOAPIC for interrupt routing
[    3.048833] ACPI: No dock devices found.
[    3.048952] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    3.049188] pci 0000:00:01.0: reg 10 io port: [0xef00-0xef7f]
[    3.049233] pci 0000:00:01.1: reg 10 io port: [0xcc00-0xcc3f]
[    3.049254] pci 0000:00:01.1: reg 20 io port: [0xed00-0xed3f]
[    3.049268] pci 0000:00:01.1: reg 24 io port: [0xee00-0xee3f]
[    3.049292] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    3.049297] pci 0000:00:01.1: PME# disabled
[    3.049325] pci 0000:00:02.0: reg 10 32bit mmio: [0xdfcfb000-0xdfcfbfff]
[    3.049352] pci 0000:00:02.0: supports D1 D2
[    3.049364] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.049366] pci 0000:00:02.0: PME# disabled
[    3.049389] pci 0000:00:02.1: reg 10 32bit mmio: [0xdfcfac00-0xdfcfacff]
[    3.049409] pci 0000:00:02.1: supports D1 D2
[    3.049421] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    3.049431] pci 0000:00:02.1: PME# disabled
[    3.049474] pci 0000:00:05.0: reg 10 io port: [0xc480-0xc487]
[    3.049487] pci 0000:00:05.0: reg 14 io port: [0xc400-0xc403]
[    3.049500] pci 0000:00:05.0: reg 18 io port: [0xc080-0xc087]
[    3.049514] pci 0000:00:05.0: reg 1c io port: [0xc000-0xc003]
[    3.049527] pci 0000:00:05.0: reg 20 io port: [0xbc00-0xbc0f]
[    3.049541] pci 0000:00:05.0: reg 24 32bit mmio: [0xdfcf9000-0xdfcf9fff]
[    3.049599] pci 0000:00:05.1: reg 10 io port: [0xb880-0xb887]
[    3.049612] pci 0000:00:05.1: reg 14 io port: [0xb800-0xb803]
[    3.049626] pci 0000:00:05.1: reg 18 io port: [0xb480-0xb487]
[    3.049639] pci 0000:00:05.1: reg 1c io port: [0xb400-0xb403]
[    3.049652] pci 0000:00:05.1: reg 20 io port: [0xb080-0xb08f]
[    3.049666] pci 0000:00:05.1: reg 24 32bit mmio: [0xdfcf8000-0xdfcf8fff]
[    3.049724] pci 0000:00:05.2: reg 10 io port: [0xb000-0xb007]
[    3.049737] pci 0000:00:05.2: reg 14 io port: [0xac00-0xac03]
[    3.049751] pci 0000:00:05.2: reg 18 io port: [0xa880-0xa887]
[    3.049764] pci 0000:00:05.2: reg 1c io port: [0xa800-0xa803]
[    3.049778] pci 0000:00:05.2: reg 20 io port: [0xa480-0xa48f]
[    3.049791] pci 0000:00:05.2: reg 24 32bit mmio: [0xdfcf7000-0xdfcf7fff]
[    3.049937] pci 0000:00:08.0: reg 10 32bit mmio: [0xdfcf6000-0xdfcf6fff]
[    3.049940] pci 0000:00:08.0: reg 14 io port: [0xa400-0xa407]
[    3.049944] pci 0000:00:08.0: reg 18 32bit mmio: [0xdfcfa800-0xdfcfa8ff]
[    3.049947] pci 0000:00:08.0: reg 1c 32bit mmio: [0xdfcfa400-0xdfcfa40f]
[    3.049957] pci 0000:00:08.0: supports D1 D2
[    3.049968] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.049980] pci 0000:00:08.0: PME# disabled
[    3.050043] pci 0000:00:09.0: reg 10 32bit mmio: [0xdfcf5000-0xdfcf5fff]
[    3.050047] pci 0000:00:09.0: reg 14 io port: [0xa080-0xa087]
[    3.050050] pci 0000:00:09.0: reg 18 32bit mmio: [0xdfcfa000-0xdfcfa0ff]
[    3.050064] pci 0000:00:09.0: reg 1c 32bit mmio: [0xdfcf4c00-0xdfcf4c0f]
[    3.050093] pci 0000:00:09.0: supports D1 D2
[    3.050103] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.050107] pci 0000:00:09.0: PME# disabled
[    3.050135] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.050147] pci 0000:00:0a.0: PME# disabled
[    3.050195] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.050197] pci 0000:00:0e.0: PME# disabled
[    3.050244] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.050256] pci 0000:00:0f.0: PME# disabled
[    3.050924] pci 0000:01:05.0: reg 10 32bit mmio: [0xdf000000-0xdf7fffff]
[    3.050929] pci 0000:01:05.0: reg 14 32bit mmio: [0xdefe0000-0xdeffffff]
[    3.050943] pci 0000:01:05.0: reg 18 io port: [0x9c00-0x9c7f]
[    3.050971] pci 0000:01:05.0: supports D1 D2
[    3.051015] pci 0000:00:06.0: transparent bridge
[    3.051018] pci 0000:00:06.0: bridge io port: [0x9000-0x9fff]
[    3.051021] pci 0000:00:06.0: bridge 32bit mmio: [0xdef00000-0xdf7fffff]
[    3.051141] pci 0000:04:00.0: reg 10 64bit mmio: [0xdfe00000-0xdfffffff]
[    3.051158] pci 0000:04:00.0: reg 30 32bit mmio: [0xdfd80000-0xdfdfffff]
[    3.051176] pci 0000:04:00.0: supports D1
[    3.051223] pci 0000:00:0f.0: bridge 32bit mmio: [0xdfd00000-0xdfffffff]
[    3.051254] bus 00 -> node 0
[    3.051263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    3.051670] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    3.051823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    3.051992] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    3.052169] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    3.073168] ACPI: PCI Root Bridge [PCIB] (0000:80)
[    3.073347] pci 0000:80:01.0: reg 10 io port: [0xfc00-0xfc7f]
[    3.073354] pci 0000:80:01.0: reg 14 32bit mmio: [0xddfff000-0xddffffff]
[    3.073423] pci 0000:80:01.1: reg 10 io port: [0x8880-0x88bf]
[    3.073444] pci 0000:80:01.1: reg 20 io port: [0x8800-0x883f]
[    3.073458] pci 0000:80:01.1: reg 24 io port: [0x8480-0x84bf]
[    3.073479] pci 0000:80:01.1: PME# supported from D3hot D3cold
[    3.073493] pci 0000:80:01.1: PME# disabled
[    3.073553] pci 0000:80:05.0: reg 10 io port: [0x8400-0x8407]
[    3.073566] pci 0000:80:05.0: reg 14 io port: [0x8080-0x8083]
[    3.073580] pci 0000:80:05.0: reg 18 io port: [0x8000-0x8007]
[    3.073593] pci 0000:80:05.0: reg 1c io port: [0x7c00-0x7c03]
[    3.073607] pci 0000:80:05.0: reg 20 io port: [0x7880-0x788f]
[    3.073620] pci 0000:80:05.0: reg 24 32bit mmio: [0xddffe000-0xddffefff]
[    3.073681] pci 0000:80:05.1: reg 10 io port: [0x7800-0x7807]
[    3.073695] pci 0000:80:05.1: reg 14 io port: [0x7480-0x7483]
[    3.073708] pci 0000:80:05.1: reg 18 io port: [0x7400-0x7407]
[    3.073722] pci 0000:80:05.1: reg 1c io port: [0x7080-0x7083]
[    3.073736] pci 0000:80:05.1: reg 20 io port: [0x7000-0x700f]
[    3.073749] pci 0000:80:05.1: reg 24 32bit mmio: [0xddffd000-0xddffdfff]
[    3.073810] pci 0000:80:05.2: reg 10 io port: [0x6c00-0x6c07]
[    3.073823] pci 0000:80:05.2: reg 14 io port: [0x6880-0x6883]
[    3.073837] pci 0000:80:05.2: reg 18 io port: [0x6800-0x6807]
[    3.073850] pci 0000:80:05.2: reg 1c io port: [0x6480-0x6483]
[    3.073864] pci 0000:80:05.2: reg 20 io port: [0x6400-0x640f]
[    3.073877] pci 0000:80:05.2: reg 24 32bit mmio: [0xddffc000-0xddffcfff]
[    3.073953] pci 0000:80:08.0: reg 10 32bit mmio: [0xddffb000-0xddffbfff]
[    3.073966] pci 0000:80:08.0: reg 14 io port: [0x6080-0x6087]
[    3.073980] pci 0000:80:08.0: reg 18 32bit mmio: [0xddffac00-0xddffacff]
[    3.073993] pci 0000:80:08.0: reg 1c 32bit mmio: [0xddffa800-0xddffa80f]
[    3.074015] pci 0000:80:08.0: supports D1 D2
[    3.074026] pci 0000:80:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.074037] pci 0000:80:08.0: PME# disabled
[    3.074087] pci 0000:80:09.0: reg 10 32bit mmio: [0xddff9000-0xddff9fff]
[    3.074099] pci 0000:80:09.0: reg 14 io port: [0x6000-0x6007]
[    3.074121] pci 0000:80:09.0: reg 18 32bit mmio: [0xddffa400-0xddffa4ff]
[    3.074133] pci 0000:80:09.0: reg 1c 32bit mmio: [0xddffa000-0xddffa00f]
[    3.074152] pci 0000:80:09.0: supports D1 D2
[    3.074161] pci 0000:80:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.074165] pci 0000:80:09.0: PME# disabled
[    3.074201] pci 0000:80:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.074204] pci 0000:80:0b.0: PME# disabled
[    3.074253] pci 0000:80:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.074265] pci 0000:80:0e.0: PME# disabled
[    3.074307] pci 0000:80:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.074312] pci 0000:80:0f.0: PME# disabled
[    3.074483] bus 80 -> node 0
[    3.074488] ACPI: PCI Interrupt Routing Table [\_SB_.PCIB._PRT]
[    3.074818] ACPI: PCI Interrupt Routing Table [\_SB_.PCIB.BR81._PRT]
[    3.074996] ACPI: PCI Interrupt Routing Table [\_SB_.PCIB.BR82._PRT]
[    3.075172] ACPI: PCI Interrupt Routing Table [\_SB_.PCIB.BR83._PRT]
[    3.076674] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *7
[    3.077049] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    3.077434] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    3.077819] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *7
[    3.078201] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    3.078576] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *15
[    3.078953] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    3.079348] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    3.079722] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    3.080101] ACPI: PCI Interrupt Link [LMAD] (IRQs 20 21 22 23) *11
[    3.080478] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *5
[    3.080854] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    3.081238] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *0, disabled.
[    3.081622] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    3.082007] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    3.082386] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15
[    3.082765] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *14
[    3.083218] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    3.083603] ACPI: PCI Interrupt Link [LSA2] (IRQs 20 21 22 23) *7
[    3.083988] ACPI: PCI Interrupt Link [LE3A] (IRQs 40 41 42 43) *0, disabled.
[    3.084371] ACPI: PCI Interrupt Link [LE3B] (IRQs 40 41 42 43) *0, disabled.
[    3.084738] ACPI: PCI Interrupt Link [LE3C] (IRQs 40 41 42 43) *0, disabled.
[    3.085122] ACPI: PCI Interrupt Link [LE3D] (IRQs 40 41 42 43) *0, disabled.
[    3.085498] ACPI: PCI Interrupt Link [IIM0] (IRQs 44 45 46 47) *7
[    3.085877] ACPI: PCI Interrupt Link [IIM1] (IRQs 44 45 46 47) *7
[    3.086257] ACPI: PCI Interrupt Link [ISI0] (IRQs 44 45 46 47) *7
[    3.086636] ACPI: PCI Interrupt Link [ISI1] (IRQs 44 45 46 47) *7
[    3.087015] ACPI: PCI Interrupt Link [ISI2] (IRQs 44 45 46 47) *7
[    3.087392] ACPI: PCI Interrupt Link [ILSM] (IRQs 44 45 46 47) *7
[    3.087775] ACPI: PCI Interrupt Link [ILPM] (IRQs 44 45 46 47) *0, disabled.
[    3.088164] ACPI: PCI Interrupt Link [LN2A] (IRQs 40 41 42 43) *15
[    3.088550] ACPI: PCI Interrupt Link [LN2B] (IRQs 40 41 42 43) *15
[    3.088915] ACPI: PCI Interrupt Link [LN2C] (IRQs 40 41 42 43) *15
[    3.089292] ACPI: PCI Interrupt Link [LN2D] (IRQs 40 41 42 43) *15
[    3.089666] ACPI: PCI Interrupt Link [IIM2] (IRQs 44 45 46 47) *15
[    3.090046] ACPI: PCI Interrupt Link [IIM3] (IRQs 44 45 46 47) *15
[    3.090425] ACPI: PCI Interrupt Link [ISI3] (IRQs 44 45 46 47) *15
[    3.090794] ACPI: PCI Interrupt Link [ISI4] (IRQs 44 45 46 47) *15
[    3.091171] ACPI: PCI Interrupt Link [ISI5] (IRQs 44 45 46 47) *15
[    3.091542] ACPI: PCI Interrupt Link [ILSN] (IRQs 44 45 46 47) *15
[    3.091919] ACPI: PCI Interrupt Link [ILPN] (IRQs 44 45 46 47) *15
[    3.092502] ACPI: WMI: Mapper loaded
[    3.092565] SCSI subsystem initialized
[    3.092565] libata version 3.00 loaded.
[    3.092565] usbcore: registered new interface driver usbfs
[    3.092565] usbcore: registered new interface driver hub
[    3.092565] usbcore: registered new device driver usb
[    3.092565] PCI: Using ACPI for IRQ routing
[    3.130014] Bluetooth: Core ver 2.13
[    3.130037] NET: Registered protocol family 31
[    3.130037] Bluetooth: HCI device and connection manager initialized
[    3.130037] Bluetooth: HCI socket layer initialized
[    3.130037] NET: Registered protocol family 8
[    3.130037] NET: Registered protocol family 20
[    3.130037] NetLabel: Initializing
[    3.130038] NetLabel:  domain hash size = 128
[    3.130039] NetLabel:  protocols = UNLABELED CIPSOv4
[    3.130055] NetLabel:  unlabeled traffic allowed by default
[    3.130328] PCI-DMA: Disabling AGP.
[    3.130489] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    3.130491] PCI-DMA: using GART IOMMU.
[    3.130496] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    3.134563] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    3.134571] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    3.260124] AppArmor: AppArmor Filesystem Enabled
[    3.270015] Switched to high resolution mode on CPU 0
[    3.270494] Switched to high resolution mode on CPU 3
[    3.270502] Switched to high resolution mode on CPU 9
[    3.270511] Switched to high resolution mode on CPU 8
[    3.270519] Switched to high resolution mode on CPU 2
[    3.270527] Switched to high resolution mode on CPU 7
[    3.270537] Switched to high resolution mode on CPU 6
[    3.270546] Switched to high resolution mode on CPU 5
[    3.270555] Switched to high resolution mode on CPU 15
[    3.270565] Switched to high resolution mode on CPU 1
[    3.270574] Switched to high resolution mode on CPU 14
[    3.270583] Switched to high resolution mode on CPU 4
[    3.270592] Switched to high resolution mode on CPU 11
[    3.270601] Switched to high resolution mode on CPU 13
[    3.270611] Switched to high resolution mode on CPU 12
[    3.270619] Switched to high resolution mode on CPU 10
[    3.290042] pnp: PnP ACPI init
[    3.290071] ACPI: bus type pnp registered
[    3.300219] pnp: PnP ACPI: found 15 devices
[    3.300221] ACPI: ACPI bus type pnp unregistered
[    3.300237] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    3.300240] system 00:05: ioport range 0x800-0x80f has been reserved
[    3.300243] system 00:05: ioport range 0xe000-0xe07f has been reserved
[    3.300246] system 00:05: ioport range 0xe080-0xe0ff has been reserved
[    3.300249] system 00:05: ioport range 0xe400-0xe47f has been reserved
[    3.300251] system 00:05: ioport range 0xe480-0xe4ff has been reserved
[    3.300254] system 00:05: ioport range 0xe800-0xe87f has been reserved
[    3.300256] system 00:05: ioport range 0xe880-0xe8ff has been reserved
[    3.300259] system 00:05: ioport range 0xec00-0xec7f has been reserved
[    3.300261] system 00:05: ioport range 0xec80-0xecff has been reserved
[    3.300265] system 00:05: iomem range 0xdfc80000-0xdfcbffff has been reserved
[    3.300271] system 00:05: iomem range 0xfee01000-0xfeefffff has been reserved
[    3.300276] system 00:06: ioport range 0xf000-0xf07f has been reserved
[    3.300279] system 00:06: ioport range 0xf080-0xf0ff has been reserved
[    3.300281] system 00:06: ioport range 0xf400-0xf47f has been reserved
[    3.300284] system 00:06: ioport range 0xf480-0xf4ff has been reserved
[    3.300286] system 00:06: ioport range 0xf800-0xf87f has been reserved
[    3.300289] system 00:06: ioport range 0xf880-0xf8ff has been reserved
[    3.300292] system 00:06: iomem range 0xfee01000-0xfef00fff could not be reserved
[    3.300297] system 00:0a: ioport range 0xca0-0xca1 has been reserved
[    3.300300] system 00:0a: ioport range 0xca4-0xcaf has been reserved
[    3.300309] system 00:0a: ioport range 0xcf9-0xcf9 could not be reserved
[    3.300312] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    3.300315] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    3.300319] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    3.300324] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    3.300327] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    3.300332] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    3.300334] system 00:0c: iomem range 0x100000-0xddffffff could not be reserved
[    3.300337] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    3.300342] system 00:0e: ioport range 0xf000-0xf07f has been reserved
[    3.300344] system 00:0e: ioport range 0xf080-0xf0ff has been reserved
[    3.300347] system 00:0e: ioport range 0xf400-0xf47f has been reserved
[    3.300349] system 00:0e: ioport range 0xf480-0xf4ff has been reserved
[    3.300352] system 00:0e: ioport range 0xf800-0xf87f has been reserved
[    3.300354] system 00:0e: ioport range 0xf880-0xf8ff has been reserved
[    3.300357] system 00:0e: iomem range 0xfee01000-0xfef00fff could not be reserved
[    3.300359] system 00:0e: iomem range 0xddf80000-0xddfbffff has been reserved
[    3.305136] pci 0000:00:06.0: PCI bridge, secondary bus 0000:01
[    3.305139] pci 0000:00:06.0:   IO window: 0x9000-0x9fff
[    3.305143] pci 0000:00:06.0:   MEM window: 0xdef00000-0xdf7fffff
[    3.305146] pci 0000:00:06.0:   PREFETCH window: disabled
[    3.305149] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    3.305151] pci 0000:00:0a.0:   IO window: disabled
[    3.305153] pci 0000:00:0a.0:   MEM window: disabled
[    3.305156] pci 0000:00:0a.0:   PREFETCH window: disabled
[    3.305159] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:03
[    3.305161] pci 0000:00:0e.0:   IO window: disabled
[    3.305163] pci 0000:00:0e.0:   MEM window: disabled
[    3.305166] pci 0000:00:0e.0:   PREFETCH window: disabled
[    3.305169] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:04
[    3.305171] pci 0000:00:0f.0:   IO window: disabled
[    3.305173] pci 0000:00:0f.0:   MEM window: 0xdfd00000-0xdfffffff
[    3.305176] pci 0000:00:0f.0:   PREFETCH window: disabled
[    3.305185] pci 0000:00:06.0: setting latency timer to 64
[    3.305190] pci 0000:00:0a.0: setting latency timer to 64
[    3.305194] pci 0000:00:0e.0: setting latency timer to 64
[    3.305198] pci 0000:00:0f.0: setting latency timer to 64
[    3.305202] pci 0000:80:0b.0: PCI bridge, secondary bus 0000:81
[    3.305204] pci 0000:80:0b.0:   IO window: disabled
[    3.305206] pci 0000:80:0b.0:   MEM window: disabled
[    3.305209] pci 0000:80:0b.0:   PREFETCH window: disabled
[    3.305212] pci 0000:80:0e.0: PCI bridge, secondary bus 0000:82
[    3.305214] pci 0000:80:0e.0:   IO window: disabled
[    3.305217] pci 0000:80:0e.0:   MEM window: disabled
[    3.305219] pci 0000:80:0e.0:   PREFETCH window: disabled
[    3.305223] pci 0000:80:0f.0: PCI bridge, secondary bus 0000:83
[    3.305224] pci 0000:80:0f.0:   IO window: disabled
[    3.305227] pci 0000:80:0f.0:   MEM window: disabled
[    3.305229] pci 0000:80:0f.0:   PREFETCH window: disabled
[    3.305235] pci 0000:80:0b.0: setting latency timer to 64
[    3.305239] pci 0000:80:0e.0: setting latency timer to 64
[    3.305244] pci 0000:80:0f.0: setting latency timer to 64
[    3.305248] bus: 00 index 0 io port: [0x9000-0xdfff]
[    3.305250] bus: 00 index 1 io port: [0xe000-0xefff]
[    3.305252] bus: 00 index 2 io port: [0x00-0x5fff]
[    3.305253] bus: 00 index 3 mmio: [0xde000000-0xdfffffff]
[    3.305255] bus: 00 index 4 mmio: [0x0a0000-0x0bffff]
[    3.305257] bus: 00 index 5 mmio: [0xd8000000-0xdcffffff]
[    3.305259] bus: 00 index 6 mmio: [0xf0000000-0xffffffff]
[    3.305261] bus: 00 index 7 mmio: [0x428000000-0xfcffffffff]
[    3.305263] bus: 01 index 0 io port: [0x9000-0x9fff]
[    3.305265] bus: 01 index 1 mmio: [0xdef00000-0xdf7fffff]
[    3.305267] bus: 01 index 2 mmio: [0x0-0x0]
[    3.305269] bus: 01 index 3 io port: [0x9000-0xdfff]
[    3.305270] bus: 01 index 4 io port: [0xe000-0xefff]
[    3.305272] bus: 01 index 5 io port: [0x00-0x5fff]
[    3.305274] bus: 01 index 6 mmio: [0xde000000-0xdfffffff]
[    3.305276] bus: 01 index 7 mmio: [0x0a0000-0x0bffff]
[    3.305278] bus: 01 index 8 mmio: [0xd8000000-0xdcffffff]
[    3.305280] bus: 01 index 9 mmio: [0xf0000000-0xffffffff]
[    3.305282] bus: 01 index a mmio: [0x428000000-0xfcffffffff]
[    3.305284] bus: 02 index 0 mmio: [0x0-0x0]
[    3.305285] bus: 02 index 1 mmio: [0x0-0x0]
[    3.305287] bus: 02 index 2 mmio: [0x0-0x0]
[    3.305288] bus: 02 index 3 mmio: [0x0-0x0]
[    3.305290] bus: 03 index 0 mmio: [0x0-0x0]
[    3.305292] bus: 03 index 1 mmio: [0x0-0x0]
[    3.305293] bus: 03 index 2 mmio: [0x0-0x0]
[    3.305295] bus: 03 index 3 mmio: [0x0-0x0]
[    3.305296] bus: 04 index 0 mmio: [0x0-0x0]
[    3.305298] bus: 04 index 1 mmio: [0xdfd00000-0xdfffffff]
[    3.305300] bus: 04 index 2 mmio: [0x0-0x0]
[    3.305301] bus: 04 index 3 mmio: [0x0-0x0]
[    3.305303] bus: 80 index 0 io port: [0x6000-0x8fff]
[    3.305305] bus: 80 index 1 io port: [0xf000-0xffff]
[    3.305307] bus: 80 index 2 mmio: [0xdd000000-0xddffffff]
[    3.305309] bus: 81 index 0 mmio: [0x0-0x0]
[    3.305311] bus: 81 index 1 mmio: [0x0-0x0]
[    3.305312] bus: 81 index 2 mmio: [0x0-0x0]
[    3.305314] bus: 81 index 3 mmio: [0x0-0x0]
[    3.305315] bus: 82 index 0 mmio: [0x0-0x0]
[    3.305317] bus: 82 index 1 mmio: [0x0-0x0]
[    3.305318] bus: 82 index 2 mmio: [0x0-0x0]
[    3.305320] bus: 82 index 3 mmio: [0x0-0x0]
[    3.305321] bus: 83 index 0 mmio: [0x0-0x0]
[    3.305323] bus: 83 index 1 mmio: [0x0-0x0]
[    3.305325] bus: 83 index 2 mmio: [0x0-0x0]
[    3.305326] bus: 83 index 3 mmio: [0x0-0x0]
[    3.305348] NET: Registered protocol family 2
[    3.390157] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    3.392397] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    3.394849] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.395462] TCP: Hash tables configured (established 262144 bind 65536)
[    3.395465] TCP reno registered
[    3.420396] NET: Registered protocol family 1
[    3.420549] checking if image is initramfs... it is
[    4.062611] Freeing initrd memory: 8241k freed
[    4.069016] audit: initializing netlink socket (disabled)
[    4.069048] type=2000 audit(1253013298.060:1): initialized
[    4.078788] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.080997] VFS: Disk quotas dquot_6.5.1
[    4.081058] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    4.081784] fuse init (API version 7.10)
[    4.081879] msgmni has been set to 31766
[    4.082140] alg: No test for stdrng (krng)
[    4.082158] io scheduler noop registered
[    4.082161] io scheduler anticipatory registered
[    4.082163] io scheduler deadline registered (default)
[    4.082201] io scheduler cfq registered
[    4.082255] pci 0000:00:00.0: Enabling HT MSI Mapping
[    4.599209] pci 0000:00:05.0: Enabling HT MSI Mapping
[    4.599249] pci 0000:00:05.1: Enabling HT MSI Mapping
[    4.599292] pci 0000:00:05.2: Enabling HT MSI Mapping
[    4.599331] pci 0000:00:06.0: Enabling HT MSI Mapping
[    4.599367] pci 0000:00:08.0: Enabling HT MSI Mapping
[    4.599422] pci 0000:00:09.0: Enabling HT MSI Mapping
[    4.599472] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    4.599521] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    4.599570] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    4.599625] pci 0000:01:05.0: Boot video device
[    4.599672] pci 0000:80:00.0: Enabling HT MSI Mapping
[    4.599782] pci 0000:80:05.0: Enabling HT MSI Mapping
[    4.599821] pci 0000:80:05.1: Enabling HT MSI Mapping
[    4.599861] pci 0000:80:05.2: Enabling HT MSI Mapping
[    4.599905] pci 0000:80:08.0: Enabling HT MSI Mapping
[    4.599959] pci 0000:80:09.0: Enabling HT MSI Mapping
[    4.600013] pci 0000:80:0b.0: Enabling HT MSI Mapping
[    4.600030] pci 0000:80:0e.0: Enabling HT MSI Mapping
[    4.600049] pci 0000:80:0f.0: Enabling HT MSI Mapping
[    4.611760] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    4.611804] pcieport-driver 0000:00:0a.0: found MSI capability
[    4.611827] pcieport-driver 0000:00:0a.0: irq 2303 for MSI/MSI-X
[    4.611836] pci_express 0000:00:0a.0:pcie00: allocate port service
[    4.611848] pci_express 0000:00:0a.0:pcie01: allocate port service
[    4.611861] pci_express 0000:00:0a.0:pcie03: allocate port service
[    4.611910] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    4.611945] pcieport-driver 0000:00:0e.0: found MSI capability
[    4.611970] pcieport-driver 0000:00:0e.0: irq 2302 for MSI/MSI-X
[    4.611981] pci_express 0000:00:0e.0:pcie00: allocate port service
[    4.611991] pci_express 0000:00:0e.0:pcie01: allocate port service
[    4.612001] pci_express 0000:00:0e.0:pcie03: allocate port service
[    4.612072] pcieport-driver 0000:00:0f.0: setting latency timer to 64
[    4.612107] pcieport-driver 0000:00:0f.0: found MSI capability
[    4.612148] pcieport-driver 0000:00:0f.0: irq 2301 for MSI/MSI-X
[    4.612158] pci_express 0000:00:0f.0:pcie00: allocate port service
[    4.612168] pci_express 0000:00:0f.0:pcie01: allocate port service
[    4.612179] pci_express 0000:00:0f.0:pcie03: allocate port service
[    4.612254] pcieport-driver 0000:80:0b.0: setting latency timer to 64
[    4.612294] pcieport-driver 0000:80:0b.0: found MSI capability
[    4.612338] pcieport-driver 0000:80:0b.0: irq 2300 for MSI/MSI-X
[    4.612345] pci_express 0000:80:0b.0:pcie00: allocate port service
[    4.612355] pci_express 0000:80:0b.0:pcie01: allocate port service
[    4.612365] pci_express 0000:80:0b.0:pcie03: allocate port service
[    4.612429] pcieport-driver 0000:80:0e.0: setting latency timer to 64
[    4.612462] pcieport-driver 0000:80:0e.0: found MSI capability
[    4.612503] pcieport-driver 0000:80:0e.0: irq 2299 for MSI/MSI-X
[    4.612510] pci_express 0000:80:0e.0:pcie00: allocate port service
[    4.612521] pci_express 0000:80:0e.0:pcie01: allocate port service
[    4.612531] pci_express 0000:80:0e.0:pcie03: allocate port service
[    4.612598] pcieport-driver 0000:80:0f.0: setting latency timer to 64
[    4.612631] pcieport-driver 0000:80:0f.0: found MSI capability
[    4.612673] pcieport-driver 0000:80:0f.0: irq 2298 for MSI/MSI-X
[    4.612684] pci_express 0000:80:0f.0:pcie00: allocate port service
[    4.612694] pci_express 0000:80:0f.0:pcie01: allocate port service
[    4.612707] pci_express 0000:80:0f.0:pcie03: allocate port service
[    4.618742] aer 0000:00:0a.0:pcie01: service driver aer loaded
[    4.624695] aer 0000:00:0e.0:pcie01: service driver aer loaded
[    4.630672] aer 0000:00:0f.0:pcie01: service driver aer loaded
[    4.636642] aer 0000:80:0b.0:pcie01: service driver aer loaded
[    4.642606] aer 0000:80:0e.0:pcie01: service driver aer loaded
[    4.648577] aer 0000:80:0f.0:pcie01: service driver aer loaded
[    4.648604] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.648614] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.648810] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    4.648813] ACPI: Power Button (FF) [PWRF]
[    4.648873] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    4.648875] ACPI: Power Button (CM) [PWRB]
[    4.649557] processor ACPI_CPU:00: registered as cooling_device0
[    4.649594] processor ACPI_CPU:01: registered as cooling_device1
[    4.649635] processor ACPI_CPU:02: registered as cooling_device2
[    4.649668] processor ACPI_CPU:03: registered as cooling_device3
[    4.649704] processor ACPI_CPU:04: registered as cooling_device4
[    4.649737] processor ACPI_CPU:05: registered as cooling_device5
[    4.649774] processor ACPI_CPU:06: registered as cooling_device6
[    4.649809] processor ACPI_CPU:07: registered as cooling_device7
[    4.649849] processor ACPI_CPU:08: registered as cooling_device8
[    4.649888] processor ACPI_CPU:09: registered as cooling_device9
[    4.649926] processor ACPI_CPU:0a: registered as cooling_device10
[    4.649969] processor ACPI_CPU:0b: registered as cooling_device11
[    4.650011] processor ACPI_CPU:0c: registered as cooling_device12
[    4.650058] processor ACPI_CPU:0d: registered as cooling_device13
[    4.650100] processor ACPI_CPU:0e: registered as cooling_device14
[    4.650142] processor ACPI_CPU:0f: registered as cooling_device15
[    4.723455] Linux agpgart interface v0.103
[    4.723469] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    4.723550] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.723827] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.724824] brd: module loaded
[    4.725209] loop: module loaded
[    4.725278] Fixed MDIO Bus: probed
[    4.725285] PPP generic driver version 2.4.2
[    4.725340] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    4.725369] Driver 'sd' needs updating - please use bus_type methods
[    4.725379] Driver 'sr' needs updating - please use bus_type methods
[    4.725687] sata_nv 0000:00:05.0: version 3.5
[    4.726234] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    4.726248] sata_nv 0000:00:05.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    4.726252] sata_nv 0000:00:05.0: Using SWNCQ mode
[    4.726319] sata_nv 0000:00:05.0: setting latency timer to 64
[    4.726499] scsi0 : sata_nv
[    4.726618] scsi1 : sata_nv
[    4.726832] ata1: SATA max UDMA/133 cmd 0xc480 ctl 0xc400 bmdma 0xbc00 irq 23
[    4.726835] ata2: SATA max UDMA/133 cmd 0xc080 ctl 0xc000 bmdma 0xbc08 irq 23
[    5.480445] ata1: SATA link down (SStatus 0 SControl 300)
[    6.240418] ata2: SATA link down (SStatus 0 SControl 300)
[    6.240950] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    6.240959] sata_nv 0000:00:05.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    6.240965] sata_nv 0000:00:05.1: Using SWNCQ mode
[    6.241005] sata_nv 0000:00:05.1: setting latency timer to 64
[    6.241172] scsi2 : sata_nv
[    6.241249] scsi3 : sata_nv
[    6.241454] ata3: SATA max UDMA/133 cmd 0xb880 ctl 0xb800 bmdma 0xb080 irq 22
[    6.241457] ata4: SATA max UDMA/133 cmd 0xb480 ctl 0xb400 bmdma 0xb088 irq 22
[    7.000442] ata3: SATA link down (SStatus 0 SControl 300)
[    7.760420] ata4: SATA link down (SStatus 0 SControl 300)
[    7.760943] ACPI: PCI Interrupt Link [LSA2] enabled at IRQ 21
[    7.760951] sata_nv 0000:00:05.2: PCI INT C -> Link[LSA2] -> GSI 21 (level, low) -> IRQ 21
[    7.760957] sata_nv 0000:00:05.2: Using SWNCQ mode
[    7.760993] sata_nv 0000:00:05.2: setting latency timer to 64
[    7.761172] scsi4 : sata_nv
[    7.761254] scsi5 : sata_nv
[    7.761452] ata5: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 21
[    7.761455] ata6: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 21
[    8.520449] ata5: SATA link down (SStatus 0 SControl 300)
[    9.280430] ata6: SATA link down (SStatus 0 SControl 300)
[    9.280980] ACPI: PCI Interrupt Link [ISI0] enabled at IRQ 47
[    9.280985] sata_nv 0000:80:05.0: PCI INT A -> Link[ISI0] -> GSI 47 (level, low) -> IRQ 47
[    9.280988] sata_nv 0000:80:05.0: Using SWNCQ mode
[    9.281021] sata_nv 0000:80:05.0: setting latency timer to 64
[    9.281193] scsi6 : sata_nv
[    9.281272] scsi7 : sata_nv
[    9.281517] ata7: SATA max UDMA/133 cmd 0x8400 ctl 0x8080 bmdma 0x7880 irq 47
[    9.281520] ata8: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7888 irq 47
[   10.040450] ata7: SATA link down (SStatus 0 SControl 300)
[   10.800418] ata8: SATA link down (SStatus 0 SControl 300)
[   10.800949] ACPI: PCI Interrupt Link [ISI1] enabled at IRQ 46
[   10.800955] sata_nv 0000:80:05.1: PCI INT B -> Link[ISI1] -> GSI 46 (level, low) -> IRQ 46
[   10.800957] sata_nv 0000:80:05.1: Using SWNCQ mode
[   10.800989] sata_nv 0000:80:05.1: setting latency timer to 64
[   10.801134] scsi8 : sata_nv
[   10.801212] scsi9 : sata_nv
[   10.801401] ata9: SATA max UDMA/133 cmd 0x7800 ctl 0x7480 bmdma 0x7000 irq 46
[   10.801404] ata10: SATA max UDMA/133 cmd 0x7400 ctl 0x7080 bmdma 0x7008 irq 46
[   11.560478] ata9: SATA link down (SStatus 0 SControl 300)
[   12.320473] ata10: SATA link down (SStatus 0 SControl 300)
[   12.321004] ACPI: PCI Interrupt Link [ISI2] enabled at IRQ 45
[   12.321010] sata_nv 0000:80:05.2: PCI INT C -> Link[ISI2] -> GSI 45 (level, low) -> IRQ 45
[   12.321012] sata_nv 0000:80:05.2: Using SWNCQ mode
[   12.321045] sata_nv 0000:80:05.2: setting latency timer to 64
[   12.321203] scsi10 : sata_nv
[   12.321280] scsi11 : sata_nv
[   12.321488] ata11: SATA max UDMA/133 cmd 0x6c00 ctl 0x6880 bmdma 0x6400 irq 45
[   12.321494] ata12: SATA max UDMA/133 cmd 0x6800 ctl 0x6480 bmdma 0x6408 irq 45
[   13.080488] ata11: SATA link down (SStatus 0 SControl 300)
[   13.840473] ata12: SATA link down (SStatus 0 SControl 300)
[   13.841175] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   13.841686] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
[   13.841698] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 20 (level, low) -> IRQ 20
[   13.841714] ehci_hcd 0000:00:02.1: setting latency timer to 64
[   13.841717] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   13.841797] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   13.841828] ehci_hcd 0000:00:02.1: debug port 1
[   13.841833] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[   13.841875] ehci_hcd 0000:00:02.1: irq 20, io mem 0xdfcfac00
[   13.860054] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[   13.860130] usb usb1: configuration #1 chosen from 1 choice
[   13.860158] hub 1-0:1.0: USB hub found
[   13.860168] hub 1-0:1.0: 10 ports detected
[   13.860286] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   13.860801] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[   13.860805] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[   13.860815] ohci_hcd 0000:00:02.0: setting latency timer to 64
[   13.860821] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   13.860862] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   13.860875] ohci_hcd 0000:00:02.0: irq 23, io mem 0xdfcfb000
[   13.922134] usb usb2: configuration #1 chosen from 1 choice
[   13.922160] hub 2-0:1.0: USB hub found
[   13.922169] hub 2-0:1.0: 10 ports detected
[   13.922279] uhci_hcd: USB Universal Host Controller Interface driver
[   13.922333] usbcore: registered new interface driver libusual
[   13.922362] usbcore: registered new interface driver usbserial
[   13.922373] USB Serial support registered for generic
[   13.922383] usbcore: registered new interface driver usbserial_generic
[   13.922389] usbserial: USB Serial Driver core
[   13.922441] PNP: No PS/2 controller found. Probing ports directly.
[   13.923342] i8042.c: No controller found.
[   13.953181] mice: PS/2 mouse device common for all mice
[   14.043246] rtc_cmos 00:02: RTC can wake from S4
[   14.043279] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[   14.043319] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[   14.043382] device-mapper: uevent: version 1.0.3
[   14.043498] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[   14.044262] device-mapper: multipath: version 1.0.5 loaded
[   14.044265] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.045034] cpuidle: using governor ladder
[   14.045036] cpuidle: using governor menu
[   14.045620] TCP cubic registered
[   14.045693] NET: Registered protocol family 10
[   14.046437] lo: Disabled Privacy Extensions
[   14.046777] NET: Registered protocol family 17
[   14.046801] Bluetooth: L2CAP ver 2.11
[   14.046803] Bluetooth: L2CAP socket layer initialized
[   14.046806] Bluetooth: SCO (Voice Link) ver 0.6
[   14.046808] Bluetooth: SCO socket layer initialized
[   14.046864] Bluetooth: RFCOMM socket layer initialized
[   14.046870] Bluetooth: RFCOMM TTY layer initialized
[   14.046872] Bluetooth: RFCOMM ver 1.10
[   14.047125] powernow-k8: Found 1 Quad-Core AMD Opteron(tm) Processor 8347 HE processors (16 cpu cores) (version 2.20.00)
[   14.047203] powernow-k8:    0 : pstate 0 (1900 MHz)
[   14.047206] powernow-k8:    1 : pstate 1 (1700 MHz)
[   14.047208] powernow-k8:    2 : pstate 2 (1400 MHz)
[   14.047210] powernow-k8:    3 : pstate 3 (1200 MHz)
[   14.047211] powernow-k8:    4 : pstate 4 (1000 MHz)
[   14.047685] powernow-k8:    0 : pstate 0 (1900 MHz)
[   14.047687] powernow-k8:    1 : pstate 1 (1700 MHz)
[   14.047689] powernow-k8:    2 : pstate 2 (1400 MHz)
[   14.047691] powernow-k8:    3 : pstate 3 (1200 MHz)
[   14.047692] powernow-k8:    4 : pstate 4 (1000 MHz)
[   14.048171] powernow-k8:    0 : pstate 0 (1900 MHz)
[   14.048174] powernow-k8:    1 : pstate 1 (1700 MHz)
[   14.048176] powernow-k8:    2 : pstate 2 (1400 MHz)
[   14.048177] powernow-k8:    3 : pstate 3 (1200 MHz)
[   14.048178] powernow-k8:    4 : pstate 4 (1000 MHz)
[   14.048647] powernow-k8:    0 : pstate 0 (1900 MHz)
[   14.048651] powernow-k8:    1 : pstate 1 (1700 MHz)
[   14.048652] powernow-k8:    2 : pstate 2 (1400 MHz)
[   14.048654] powernow-k8:    3 : pstate 3 (1200 MHz)
[   14.048655] powernow-k8:    4 : pstate 4 (1000 MHz)
[   14.049099] registered taskstats version 1
[   14.049486]   Magic number: 9:478:226
[   14.049662] rtc_cmos 00:02: setting system clock to 2009-09-15 11:15:09 UTC (1253013309)
[   14.049668] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.049670] EDD information not available.
[   14.049726] Freeing unused kernel memory: 536k freed
[   14.050060] Write protecting the kernel read-only data: 6708k
[   14.180259] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   14.274866] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   14.275465] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[   14.275471] forcedeth 0000:00:08.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[   14.275476] forcedeth 0000:00:08.0: setting latency timer to 64
[   14.275584] nv_probe: set workaround bit for reversed mac addr
[   14.276701] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 2, addr 00:21:28:00:1a:f6
[   14.276704] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   14.277194] ACPI: PCI Interrupt Link [LMAD] enabled at IRQ 21
[   14.277197] forcedeth 0000:00:09.0: PCI INT A -> Link[LMAD] -> GSI 21 (level, low) -> IRQ 21
[   14.277201] forcedeth 0000:00:09.0: setting latency timer to 64
[   14.277248] nv_probe: set workaround bit for reversed mac addr
[   14.278296] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 3, addr 00:21:28:00:1a:f7
[   14.278299] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   14.278840] ACPI: PCI Interrupt Link [IIM0] enabled at IRQ 44
[   14.278850] forcedeth 0000:80:08.0: PCI INT A -> Link[IIM0] -> GSI 44 (level, low) -> IRQ 44
[   14.278853] forcedeth 0000:80:08.0: setting latency timer to 64
[   14.278895] nv_probe: set workaround bit for reversed mac addr
[   14.279935] forcedeth 0000:80:08.0: ifname eth2, PHY OUI 0x5043 @ 2, addr 00:21:28:00:1a:f8
[   14.279938] forcedeth 0000:80:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   14.280441] ACPI: PCI Interrupt Link [IIM1] enabled at IRQ 47
[   14.280443] forcedeth 0000:80:09.0: PCI INT A -> Link[IIM1] -> GSI 47 (level, low) -> IRQ 47
[   14.280447] forcedeth 0000:80:09.0: setting latency timer to 64
[   14.280494] nv_probe: set workaround bit for reversed mac addr
[   14.281011] Adaptec aacraid driver 1.1-5[2456]-ms
[   14.281604] forcedeth 0000:80:09.0: ifname eth3, PHY OUI 0x5043 @ 3, addr 00:21:28:00:1a:f9
[   14.281607] forcedeth 0000:80:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   14.281771] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
[   14.281790] aacraid 0000:04:00.0: PCI INT A -> Link[LNEB] -> GSI 19 (level, low) -> IRQ 19
[   14.281799] aacraid 0000:04:00.0: setting latency timer to 64
[   14.403816] usb 1-1: configuration #1 chosen from 1 choice
[   14.407889] Initializing USB Mass Storage driver...
[   14.408067] scsi13 : SCSI emulation for USB Mass Storage devices
[   14.408194] usb-storage: device found at 2
[   14.408197] usb-storage: waiting for device to settle before scanning
[   14.408205] usbcore: registered new interface driver usb-storage
[   14.408208] USB Mass Storage support registered.
[   14.540317] AAC0: kernel 5.2-0[15825] Jun 28 2008
[   14.540321] AAC0: monitor 5.2-0[15825]
[   14.540323] AAC0: bios 5.2-0[15825]
[   14.540326] AAC0: serial 00909AA0727
[   14.540328] AAC0: Non-DASD support enabled.
[   14.540329] AAC0: 64bit support enabled.
[   14.540333] AAC0: 64 Bit DAC enabled
[   14.547436] scsi12 : aacraid
[   14.547774] scsi 12:0:0:0: Direct-Access     Sun      WEBAPPS          V1.0 PQ: 0 ANSI: 2
[   14.558976] scsi 12:1:0:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
[   14.560964] scsi 12:1:1:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
[   14.562660] scsi 12:1:2:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
[   14.564414] scsi 12:1:3:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
[   14.566165] scsi 12:1:4:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
[   14.567885] scsi 12:1:5:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
[   14.569637] scsi 12:1:6:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
[   14.571359] scsi 12:1:7:0: Direct-Access     HITACHI  H101414SCSUN146G SA25 PQ: 0 ANSI: 5
[   14.673777] scsi 12:3:0:0: Enclosure         ADAPTEC  Virtual SGPIO  0 0001 PQ: 0 ANSI: 5
[   14.700022] usb 1-6: new high speed USB device using ehci_hcd and address 5
[   14.765395] scsi 12:3:1:0: Enclosure         ADAPTEC  Virtual SGPIO  1 0001 PQ: 0 ANSI: 5
[   14.820870] sd 12:0:0:0: [sda] 2005585920 512-byte hardware sectors: (1.02 TB/956 GiB)
[   14.820891] sd 12:0:0:0: [sda] Write Protect is off
[   14.820894] sd 12:0:0:0: [sda] Mode Sense: 06 00 10 00
[   14.820928] sd 12:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
[   14.821050] sd 12:0:0:0: [sda] 2005585920 512-byte hardware sectors: (1.02 TB/956 GiB)
[   14.821067] sd 12:0:0:0: [sda] Write Protect is off
[   14.821069] sd 12:0:0:0: [sda] Mode Sense: 06 00 10 00
[   14.821099] sd 12:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
[   14.821104]  sda: sda1 sda2 < sda5 >
[   14.827776] sd 12:0:0:0: [sda] Attached SCSI removable disk
[   14.827854] sd 12:0:0:0: Attached scsi generic sg0 type 0
[   14.827931] scsi 12:1:0:0: Attached scsi generic sg1 type 0
[   14.828004] scsi 12:1:1:0: Attached scsi generic sg2 type 0
[   14.828116] scsi 12:1:2:0: Attached scsi generic sg3 type 0
[   14.828234] scsi 12:1:3:0: Attached scsi generic sg4 type 0
[   14.828325] scsi 12:1:4:0: Attached scsi generic sg5 type 0
[   14.828397] scsi 12:1:5:0: Attached scsi generic sg6 type 0
[   14.828471] scsi 12:1:6:0: Attached scsi generic sg7 type 0
[   14.828563] scsi 12:1:7:0: Attached scsi generic sg8 type 0
[   14.828654] scsi 12:3:0:0: Attached scsi generic sg9 type 13
[   14.828763] scsi 12:3:1:0: Attached scsi generic sg10 type 13
[   14.851140] usb 1-6: configuration #1 chosen from 1 choice
[   14.851333] hub 1-6:1.0: USB hub found
[   14.851426] hub 1-6:1.0: 4 ports detected
[   14.860834] Driver 'ses' needs updating - please use bus_type methods
[   14.860865] ses 12:3:0:0: Attached Enclosure device
[   14.860872] ses 12:3:1:0: Attached Enclosure device
[   15.050725] PM: Starting manual resume from disk
[   15.050729] PM: Resume from partition 252:1
[   15.050731] PM: Checking hibernation image.
[   15.051059] PM: Resume from disk failed.
[   15.080770] kjournald starting.  Commit interval 5 seconds
[   15.080782] EXT3-fs: mounted filesystem with ordered data mode.
[   15.190045] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   15.430324] usb 2-2: configuration #1 chosen from 1 choice
[   15.780061] usb 2-5: new low speed USB device using ohci_hcd and address 3
[   16.012786] usb 2-5: configuration #1 chosen from 1 choice
[   16.657579] udev: starting version 141
[   16.825805] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xed00
[   16.825832] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xee00
[   16.825908] i2c-adapter i2c-2: nForce2 SMBus adapter at 0x8800
[   16.825923] i2c-adapter i2c-3: nForce2 SMBus adapter at 0x8480
[   16.862468] usbcore: registered new interface driver hiddev
[   16.866547] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   16.872813] input: RU RU-CIM as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input4
[   16.889917] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[   16.890046] resource map sanity check conflict: 0xff000000 0xffffffff 0xff700000 0xffffffff reserved
[   16.890058] ------------[ cut here ]------------
[   16.890061] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
[   16.890064] Modules linked in: ck804xrom(+) mtd chipreg map_funcs pcspkr(+) usbhid(+) i2c_nforce2 ses enclosure usb_storage aacraid forcedeth fbcon tileblit font bitblit softcursor
[   16.890078] Pid: 1391, comm: modprobe Not tainted 2.6.28-11-server #42-Ubuntu
[   16.890081] Call Trace:
[   16.890089]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
[   16.890094]  [<ffffffff80257686>] ? iomem_map_sanity_check+0x46/0xd0
[   16.890098]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
[   16.890103]  [<ffffffffa00bc2db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[   16.890107]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
[   16.890111]  [<ffffffffa00bc2db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[   16.890115]  [<ffffffffa00c2041>] init_ck804xrom+0x41/0x59 [ck804xrom]
[   16.890119]  [<ffffffffa00c2000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
[   16.890123]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
[   16.890129]  [<ffffffff8041b919>] ? rb_insert_color+0x109/0x140
[   16.890135]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0
[   16.890138]  [<ffffffff8024870b>] ? enqueue_task_fair+0x7b/0x80
[   16.890142]  [<ffffffff8023e6a0>] ? enqueue_task+0x50/0x60
[   16.890145]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0
[   16.890152]  [<ffffffff8027eecd>] sys_init_module+0xad/0x1e0
[   16.890155]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[   16.890158] ---[ end trace 2df41ba1dd6e3af1 ]---
[   17.090134] generic-usb 0003:14DD:1005.0001: input,hidraw0: USB HID v1.11 Keyboard [RU RU-CIM] on usb-0000:00:02.0-2/input0
[   17.098851] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input5
[   17.200139] generic-usb 0003:046B:FF10.0002: input,hidraw1: USB HID v1.10 Keyboard [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:02.0-5/input0
[   17.208911] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.1/input/input6
[   17.310070] generic-usb 0003:046B:FF10.0003: input,hidraw2: USB HID v1.10 Mouse [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:02.0-5/input1
[   17.310095] usbcore: registered new interface driver usbhid
[   17.310099] usbhid: v2.6:USB HID core driver
[   17.423827] lp: driver loaded but no devices found
[   17.639511] Adding 39526392k swap on /dev/mapper/webapps-swap_1.  Priority:-1 extents:1 across:39526392k
[   18.181298] EXT3 FS on dm-0, internal journal
[   19.400513] usb-storage: device scan complete
[   19.435017] scsi 13:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-T632A SR03 PQ: 0 ANSI: 0
[   19.452742] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   19.452746] Uniform CD-ROM driver Revision: 3.20
[   19.452855] sr 13:0:0:0: Attached scsi CD-ROM sr0
[   19.452923] sr 13:0:0:0: Attached scsi generic sg11 type 5
```

---

### Post by x33a on 2009-09-15
please embed the output in
```
code
```

---

### Post by dkurtz on 2009-09-15
Sorry about that. It should be ready for you... :)

---

### Post by x33a on 2009-09-15
try adding gateway to the virtual ip.

---

### Post by dkurtz on 2009-09-15
I tried that yesterday and still got the same result. I also tried commenting out the virtual adapter assignment and restarting, but the box still got hung. 

Would it be possible avahi-daemon is causing this problem? This box is running NFS, Samba and Winbind. I have a feeling there's a service trying to start before the network adapter can be configured, or that there's a competition for a resource and the box just dies, but this is just a guess. I let it sit for as long as 10 minutes yesterday while it was Configuring Network Interfaces, but it never did anything until I broke the process with Ctrl+Alt+Del.

---

### Post by x33a on 2009-09-15
well, i have no experience with servers or nfs, winbind etc, so just doing guesswork. but, it seems that the machine is trying to mount some network drive, and that is causing it to hang.

maybe someone else could enlighten us.

---

### Post by dkurtz on 2009-09-15
I personally don't have any experience with NFS either, so I am going into this problem rather blind, but I agree with your theory from other forum threads I've read, or similar problems. Is there a way to have the boot more verbose to possibly figure out what the conflict is?

---

### Post by x33a on 2009-09-15
well any conflicts should be logged into the log files, so even if you miss out the error during booting, logs should still record that error.

try looking at log files of samba, winbind etc., if any.

---

