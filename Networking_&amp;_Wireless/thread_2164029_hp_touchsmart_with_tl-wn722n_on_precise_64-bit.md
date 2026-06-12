---
title: "hp touchsmart with tl-wn722n on precise 64-bit"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by jaing on 2013-07-20
After failing to get the wna3100 adapter working, I purchased the TP-LINK WN722N wireless adapter because of this [guide]("http://www.linuxplained.com/linux-compatible-usb-wireless-adapters-2012/"). After searching I tried to install several different drivers, to no avail.

dmesg shows that the wusb is connected, with no complaints about driver errors, but when i type ipconfig, it only show auth0 and lo.

On the same partition I tried 13.04, but because of display and performance issues i decided to use 12.04 instead.

I have no internet connectivity in ubuntu.

---

### Post by jaing on 2013-07-20
More info:

Hp touchsmart Pc iq770
Ubuntu 12.04.2 LTS
Kernel: 3.8.0-19-generic x86_64


from lsusb:


```

Bus 001 Device 012: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n

```





interfaces:


```


jaing@minion-of-jaing:~$ ifconfig
eth0
      Link encap:Ethernet  HWaddr 00:1a:92:eb:b6:3b
  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


          RX packets:0 errors:0 dropped:0 overruns:0 frame:0


          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0


          collisions:0 txqueuelen:1000
 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo
        Link encap:Local Loopback
  
          inet addr:127.0.0.1  Mask:255.0.0.0


          inet6 addr: ::1/128 Scope:Host


          UP LOOPBACK RUNNING  MTU:65536
  Metric:1
          RX packets:816 errors:0 dropped:0 overruns:0 frame:0


          TX packets:816 errors:0 dropped:0 overruns:0 carrier:0


          collisions:0 txqueuelen:0
 
          RX bytes:62352 (62.3 KB)
  TX bytes:62352 (62.3 KB)




jaing@minion-of-jaing:~$ iwconfig


eth0
      no wireless extensions.




lo
        no wireless extensions.





```



lsmod:


```


Module
                  Size  Used by


hid_generic            12540  0 


usbhid                 47074  0 


hid                   101002  2 
hid_generic,usbhid
usb_storage            57204  0 


pata_acpi              13038  0 


firewire_ohci          40103  0 


forcedeth              66977  0 


firewire_core          64508  1 
firewire_ohci
crc_itu_t              12707  1 
firewire_core
sata_nv                31812  4 


pata_amd               14129  0 







```

dmesg:
```


[    0.000000] Initializing cgroup subsys cpuset


[    0.000000] Initializing cgroup subsys cpu


[    0.000000] Linux version 3.8.0-19-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 (Ubuntu 3.8.0-19.29-generic 3.8.8)


[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=22411724-ce26-4d19-a103-e49bd29242de ro quiet splash vt.handoff=7


[    0.000000] KERNEL supported cpus:


[    0.000000]   Intel GenuineIntel


[    0.000000]   AMD AuthenticAMD


[    0.000000]   Centaur CentaurHauls


[    0.000000] e820: BIOS-provided physical RAM map:


[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable


[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved


[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved


[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffcffff] usable


[    0.000000] BIOS-e820: [mem 0x000000007ffd0000-0x000000007ffddfff] ACPI data


[    0.000000] BIOS-e820: [mem 0x000000007ffde000-0x000000007fffffff] ACPI NVS


[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved


[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved


[    0.000000] BIOS-e820: [mem 0x00000000ff700000-0x00000000ffffffff] reserved


[    0.000000] NX (Execute Disable) protection: active


[    0.000000] SMBIOS 2.4 present.


[    0.000000] DMI: HP-Pavilion RN635AA-ABA IQ770/PHOENIX, BIOS 5.15    11/26/2007


[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved


[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable


[    0.000000] No AGP bridge found


[    0.000000] e820: last_pfn = 0x7ffd0 max_arch_pfn = 0x400000000


[    0.000000] MTRR default type: uncachable


[    0.000000] MTRR fixed ranges enabled:


[    0.000000]   00000-9FFFF write-back


[    0.000000]   A0000-EFFFF uncachable


[    0.000000]   F0000-FFFFF write-protect


[    0.000000] MTRR variable ranges enabled:


[    0.000000]   0 base 0000000000 mask FF80000000 write-back


[    0.000000]   1 disabled


[    0.000000]   2 disabled


[    0.000000]   3 disabled


[    0.000000]   4 base 00000FC000 mask 0FFFFFE000 write-protect


[    0.000000]   5 base 00000DC000 mask 0FFFFFE000 write-back


[    0.000000]   6 disabled


[    0.000000]   7 disabled


[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106


[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.


[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.


[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.


[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.


[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]


[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]


[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576


[    0.000000] init_memory_mapping: [mem 0x00000000-0x7ffcffff]


[    0.000000]  [mem 0x00000000-0x7fdfffff] page 2M


[    0.000000]  [mem 0x7fe00000-0x7ffcffff] page 4k


[    0.000000] kernel direct mapping tables up to 0x7ffcffff @ [mem 0x1fffc000-0x1fffffff]


[    0.000000] RAMDISK: [mem 0x36122000-0x37088fff]


[    0.000000] ACPI: RSDP 00000000000fc560 00014 (v00 HPQOEM)


[    0.000000] ACPI: RSDT 000000007ffd0000 00040 (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: FACP 000000007ffd0200 00084 (v02 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: DSDT 000000007ffd05c0 04B50 (v01 HPQOEM SLIC-CPC 00000000 INTL 20060210)


[    0.000000] ACPI: FACS 000000007ffde000 00040


[    0.000000] ACPI: APIC 000000007ffd0390 00070 (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: MCFG 000000007ffd0400 0003C (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: SLIC 000000007ffd0440 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)


[    0.000000] ACPI: OEMB 000000007ffde040 00063 (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: HPET 000000007ffd5110 00038 (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: SSDT 000000007ffd5150 00182 (v01 A M I  POWERNOW 00000001 AMD  00000001)


[    0.000000] ACPI: Local APIC address 0xfee00000


[    0.000000] Scanning NUMA topology in Northbridge 24


[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007ffcffff]


[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7ffcffff]


[    0.000000]   NODE_DATA [mem 0x7ffcb000-0x7ffcffff]


[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007d600000-ffff88007f5fffff] on node 0


[    0.000000] Zone ranges:


[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]


[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]


[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node


[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]


[    0.000000]   node   0: [mem 0x00100000-0x7ffcffff]


[    0.000000] On node 0 totalpages: 524127


[    0.000000]   DMA zone: 64 pages used for memmap


[    0.000000]   DMA zone: 6 pages reserved


[    0.000000]   DMA zone: 3913 pages, LIFO batch:0


[    0.000000]   DMA32 zone: 8128 pages used for memmap


[    0.000000]   DMA32 zone: 512016 pages, LIFO batch:31


[    0.000000] Detected use of extended apic ids on hypertransport bus


[    0.000000] ACPI: PM-Timer IO Port: 0x4008


[    0.000000] ACPI: Local APIC address 0xfee00000


[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)


[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)


[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])


[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23


[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)


[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)


[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)


[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)


[    0.000000] ACPI: IRQ0 used by override.


[    0.000000] ACPI: IRQ2 used by override.


[    0.000000] ACPI: IRQ9 used by override.


[    0.000000] ACPI: IRQ14 used by override.


[    0.000000] ACPI: IRQ15 used by override.


[    0.000000] Using ACPI (MADT) for SMP configuration information


[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000


[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs


[    0.000000] nr_irqs_gsi: 40


[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000


[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000


[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000


[    0.000000] e820: [mem 0x80000000-0xfebfffff] available for PCI devices


[    0.000000] Booting paravirtualized kernel on bare hardware


[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1


[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s85056 r8192 d21440 u1048576


[    0.000000] pcpu-alloc: s85056 r8192 d21440 u1048576 alloc=1*2097152


[    0.000000] pcpu-alloc: [0] 0 1 


[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515929


[    0.000000] Policy zone: DMA32


[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=22411724-ce26-4d19-a103-e49bd29242de ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Memory: 2031916k/2096960k available (7006k kernel code, 452k absent, 64592k reserved, 6238k data, 992k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25


[    0.000000] console [tty0] enabled


[    0.000000] allocated 8388608 bytes of page_cgroup


[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups


[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT


[    0.000000] tsc: Detected 1607.547 MHz processor


[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized


[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3215.09 BogoMIPS (lpj=6430188)


[    0.004011] pid_max: default: 32768 minimum: 301


[    0.004057] Security Framework initialized


[    0.004078] AppArmor: AppArmor initialized


[    0.004080] Yama: becoming mindful.


[    0.004423] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)


[    0.009041] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)


[    0.009615] Mount-cache hash table entries: 256


[    0.009913] Initializing cgroup subsys cpuacct


[    0.009917] Initializing cgroup subsys memory


[    0.009930] Initializing cgroup subsys devices


[    0.009933] Initializing cgroup subsys freezer


[    0.009936] Initializing cgroup subsys blkio


[    0.009938] Initializing cgroup subsys perf_event


[    0.009943] Initializing cgroup subsys hugetlb


[    0.009976] tseg: 0000000000


[    0.010006] CPU: Physical Processor ID: 0


[    0.010008] CPU: Processor Core ID: 0


[    0.010011] mce: CPU supports 5 MCE banks


[    0.010020] LVT offset 0 assigned for vector 0xf9


[    0.010028] process: using AMD E400 aware idle routine


[    0.010033] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4


[    0.010033] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4


[    0.010033] tlb_flushall_shift: 4


[    0.010209] Freeing SMP alternatives: 24k freed


[    0.012493] ACPI: Core revision 20121018


[    0.017087] ftrace: allocating 26689 entries in 105 pages


[    0.036496] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1


[    0.076205] smpboot: CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-52 (fam: 0f, model: 48, stepping: 02)


[    0.080000] Performance Events: AMD PMU driver.


[    0.080000] ... version:                0


[    0.080000] ... bit width:              48


[    0.080000] ... generic registers:      4


[    0.080000] ... value mask:             0000ffffffffffff


[    0.080000] ... max period:             00007fffffffffff


[    0.080000] ... fixed-purpose events:   0


[    0.080000] ... event mask:             000000000000000f


[    0.080000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.


[    0.080000] smpboot: Booting Node   0, Processors  #1 OK


[    0.168116] Brought up 2 CPUs


[    0.168120] smpboot: Total of 2 processors activated (6429.88 BogoMIPS)


[    0.168738] devtmpfs: initialized
[    0.170424] EVM: security.selinux


[    0.170427] EVM: security.SMACK64
[    0.170430] EVM: security.capability


[    0.170454] PM: Registering ACPI NVS region [mem 0x7ffde000-0x7fffffff] (139264 bytes)


[    0.173334] regulator-dummy: no parameters


[    0.173418] NET: Registered protocol family 16


[    0.173606] node 0 link 0: io port [1000, ffffff]


[    0.173610] TOM: 0000000080000000 aka 2048M


[    0.173614] node 0 link 0: mmio [e0000000, efffffff]


[    0.173619] node 0 link 0: mmio [a0000, bffff]


[    0.173622] node 0 link 0: mmio [80000000, fe0bffff]


[    0.173626] bus: [bus 00-ff] on node 0 link 0


[    0.173629] bus: 00 [io  0x0000-0xffff]


[    0.173631] bus: 00 [mem 0x80000000-0xfcffffffff]


[    0.173634] bus: 00 [mem 0x000a0000-0x000bffff]


[    0.173718] ACPI: bus type pci registered


[    0.173805] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)


[    0.173809] PCI: not using MMCONFIG


[    0.173812] PCI: Using configuration type 1 for base access


[    0.175194] bio: create slab <bio-0> at 0


[    0.175194] ACPI: Added _OSI(Module Device)


[    0.175194] ACPI: Added _OSI(Processor Device)


[    0.175194] ACPI: Added _OSI(3.0 _SCP Extensions)


[    0.175194] ACPI: Added _OSI(Processor Aggregator Device)


[    0.177089] ACPI: EC: Look up EC in DSDT


[    0.178322] ACPI: Executed 1 blocks of module-level executable AML code


[    0.220111] ACPI BIOS Bug: Warning: Incorrect checksum in table [OEMB] - 0xCE, should be 0xC1 (20121018/tbutils-324)


[    0.220346] ACPI: Interpreter enabled


[    0.220353] ACPI: (supports S0 S1 S3 S4 S5)


[    0.220385] ACPI: Using IOAPIC for interrupt routing


[    0.220428] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)


[    0.221433] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources


[    0.241376] ACPI: No dock devices found.


[    0.241386] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug


[    0.241481] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])


[    0.241485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]


[    0.241788] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)


[    0.241792] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)


[    0.241797] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)


[    0.241801] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)


[    0.241805] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xff6fffff] (ignored)


[    0.241809] PCI: root bus 00: hardware-probed resources


[    0.241852] PCI host bridge to bus 0000:00


[    0.241857] pci_bus 0000:00: root bus resource [bus 00-ff]


[    0.241861] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]


[    0.241866] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfcffffffff]


[    0.241870] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]


[    0.241885] pci 0000:00:00.0: [10de:02f3] type 00 class 0x050000


[    0.241945] pci 0000:00:00.1: [10de:02fa] type 00 class 0x050000
[    0.241985] pci 0000:00:00.2: [10de:02fe] type 00 class 0x050000


[    0.242032] pci 0000:00:00.3: [10de:02f8] type 00 class 0x050000


[    0.242078] pci 0000:00:00.4: [10de:02f9] type 00 class 0x050000


[    0.242125] pci 0000:00:00.5: [10de:02ff] type 00 class 0x050000


[    0.242176] pci 0000:00:00.6: [10de:027f] type 00 class 0x050000


[    0.242213] pci 0000:00:00.7: [10de:027e] type 00 class 0x050000


[    0.242264] pci 0000:00:02.0: [10de:02fc] type 01 class 0x060400


[    0.242302] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.242323] pci 0000:00:03.0: [10de:02fd] type 01 class 0x060400


[    0.242359] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.242380] pci 0000:00:04.0: [10de:02fb] type 01 class 0x060400


[    0.242416] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.242454] pci 0000:00:09.0: [10de:0270] type 00 class 0x050000


[    0.242662] pci 0000:00:0a.0: [10de:0260] type 00 class 0x060100


[    0.242722] pci 0000:00:0a.1: [10de:0264] type 00 class 0x0c0500


[    0.242762] pci 0000:00:0a.1: reg 20: [io  0x5000-0x503f]


[    0.242772] pci 0000:00:0a.1: reg 24: [io  0x6000-0x603f]


[    0.242814] pci 0000:00:0a.1: PME# supported from D3hot D3cold


[    0.242843] pci 0000:00:0b.0: [10de:026d] type 00 class 0x0c0310


[    0.242857] pci 0000:00:0b.0: reg 10: [mem 0xf5ebe000-0xf5ebefff]


[    0.242910] pci 0000:00:0b.0: supports D1 D2


[    0.242914] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.242934] pci 0000:00:0b.1: [10de:026e] type 00 class 0x0c0320


[    0.242948] pci 0000:00:0b.1: reg 10: [mem 0xf5ebfc00-0xf5ebfcff]


[    0.243004] pci 0000:00:0b.1: supports D1 D2


[    0.243008] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold


[    0.243035] pci 0000:00:0d.0: [10de:0265] type 00 class 0x01018a


[    0.243064] pci 0000:00:0d.0: reg 20: [io  0xffa0-0xffaf]


[    0.243109] pci 0000:00:0e.0: [10de:0266] type 00 class 0x010185


[    0.243124] pci 0000:00:0e.0: reg 10: [io  0xd800-0xd807]


[    0.243133] pci 0000:00:0e.0: reg 14: [io  0xd480-0xd483]


[    0.243141] pci 0000:00:0e.0: reg 18: [io  0xd400-0xd407]


[    0.243150] pci 0000:00:0e.0: reg 1c: [io  0xd080-0xd083]


[    0.243158] pci 0000:00:0e.0: reg 20: [io  0xd000-0xd00f]


[    0.243167] pci 0000:00:0e.0: reg 24: [mem 0xf5ebd000-0xf5ebdfff]


[    0.243221] pci 0000:00:10.0: [10de:026f] type 01 class 0x060401


[    0.243281] pci 0000:00:10.1: [10de:026c] type 00 class 0x040300


[    0.243297] pci 0000:00:10.1: reg 10: [mem 0xf5eb8000-0xf5ebbfff]


[    0.243360] pci 0000:00:10.1: PME# supported from D3hot D3cold


[    0.243392] pci 0000:00:14.0: [10de:0269] type 00 class 0x068000


[    0.243405] pci 0000:00:14.0: reg 10: [mem 0xf5ebc000-0xf5ebcfff]


[    0.243414] pci 0000:00:14.0: reg 14: [io  0xcc00-0xcc07]


[    0.243456] pci 0000:00:14.0: supports D1 D2


[    0.243460] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.243478] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000


[    0.243507] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000


[    0.243530] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000


[    0.243554] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000


[    0.243615] pci 0000:00:02.0: PCI bridge to [bus 01]


[    0.243647] pci 0000:00:03.0: PCI bridge to [bus 02]


[    0.243687] pci 0000:03:00.0: [10de:0398] type 00 class 0x030000


[    0.243698] pci 0000:03:00.0: reg 10: [mem 0xf7000000-0xf7ffffff]


[    0.243709] pci 0000:03:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]


[    0.243720] pci 0000:03:00.0: reg 1c: [mem 0xf6000000-0xf6ffffff 64bit]


[    0.243728] pci 0000:03:00.0: reg 24: [io  0xec00-0xec7f]


[    0.243737] pci 0000:03:00.0: reg 30: [mem 0xf5fe0000-0xf5ffffff pref]


[    0.243773] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'


[    0.243782] pci 0000:00:04.0: PCI bridge to [bus 03]


[    0.243788] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]


[    0.243793] pci 0000:00:04.0:   bridge window [mem 0xf5f00000-0xf7ffffff]


[    0.243798] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]


[    0.243835] pci 0000:04:00.0: [14f1:5b7a] type 00 class 0x040000


[    0.243853] pci 0000:04:00.0: reg 10: [mem 0xf8000000-0xfbffffff]


[    0.243938] pci 0000:04:01.0: [11c1:5811] type 00 class 0x0c0010


[    0.243955] pci 0000:04:01.0: reg 10: [mem 0xfebff000-0xfebfffff]


[    0.244035] pci 0000:04:01.0: supports D1 D2


[    0.244039] pci 0000:04:01.0: PME# supported from D0 D1 D2 D3hot


[    0.244081] pci 0000:00:10.0: PCI bridge to [bus 04] (subtractive decode)


[    0.244087] pci 0000:00:10.0:   bridge window [mem 0xf8000000-0xfebfffff]


[    0.244093] pci 0000:00:10.0:   bridge window [io  0x0000-0xffff] (subtractive decode)


[    0.244097] pci 0000:00:10.0:   bridge window [mem 0x80000000-0xfcffffffff] (subtractive decode)


[    0.244101] pci 0000:00:10.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)


[    0.244129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]


[    0.244182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]


[    0.244227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]


[    0.244316] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]


[    0.244382]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM


[    0.244385]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)


[    0.246391] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *15


[    0.246503] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.


[    0.246611] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.


[    0.246717] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *10


[    0.246822] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10


[    0.246929] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.


[    0.247034] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.


[    0.247140] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.


[    0.247247] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *7


[    0.247353] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15


[    0.247459] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5


[    0.247565] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11


[    0.247671] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.


[    0.247777] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.


[    0.247884] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5


[    0.248007] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11


[    0.248129] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10


[    0.248245] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.


[    0.248375] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.


[    0.248524] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none


[    0.248524] vgaarb: loaded
[    0.248524] vgaarb: bridge control possible 0000:03:00.0


[    0.248524] SCSI subsystem initialized
[    0.248524] ACPI: bus type scsi registered


[    0.248524] libata version 3.00 loaded.


[    0.248524] ACPI: bus type usb registered


[    0.248524] usbcore: registered new interface driver usbfs


[    0.248524] usbcore: registered new interface driver hub


[    0.248524] usbcore: registered new device driver usb


[    0.248524] PCI: Using ACPI for IRQ routing


[    0.256818] PCI: pci_cache_line_size set to 64 bytes


[    0.256902] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]


[    0.256906] e820: reserve RAM buffer [mem 0x7ffd0000-0x7fffffff]


[    0.257056] NetLabel: Initializing


[    0.257059] NetLabel:  domain hash size = 128


[    0.257061] NetLabel:  protocols = UNLABELED CIPSOv4


[    0.257078] NetLabel:  unlabeled traffic allowed by default


[    0.257099] HPET: 3 timers in total, 0 timers will be used for per-cpu timer


[    0.257099] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31


[    0.257099] hpet0: 3 comparators, 32-bit 25.000000 MHz counter


[    0.258118] Switching to clocksource hpet


[    0.266326] AppArmor: AppArmor Filesystem Enabled


[    0.266374] pnp: PnP ACPI init


[    0.266396] ACPI: bus type pnp registered


[    0.266470] pnp 00:00: [dma 4]


[    0.266507] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)


[    0.266566] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)


[    0.266632] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)


[    0.266678] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)


[    0.266840] system 00:04: [io  0x0295-0x02a4] has been reserved


[    0.266847] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.266945] system 00:05: [mem 0xfefe0000-0xfefe01ff] has been reserved


[    0.266950] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.267435] system 00:06: [io  0x04d0-0x04d1] has been reserved


[    0.267440] system 00:06: [io  0x0800-0x080f] has been reserved


[    0.267444] system 00:06: [io  0x4000-0x407f] has been reserved


[    0.267449] system 00:06: [io  0x4080-0x40ff] has been reserved


[    0.267453] system 00:06: [io  0x4400-0x447f] has been reserved


[    0.267458] system 00:06: [io  0x4480-0x44ff] has been reserved


[    0.267462] system 00:06: [io  0x4800-0x487f] has been reserved


[    0.267467] system 00:06: [io  0x4880-0x48ff] has been reserved


[    0.267471] system 00:06: [io  0x2000-0x207f] has been reserved


[    0.267480] system 00:06: [io  0x2080-0x20ff] has been reserved


[    0.267485] system 00:06: [mem 0x000d0000-0x000d3fff window] has been reserved


[    0.267490] system 00:06: [mem 0x000d4000-0x000d7fff window] has been reserved


[    0.267495] system 00:06: [mem 0x000de000-0x000dffff window] has been reserved


[    0.267500] system 00:06: [mem 0xf5ec0000-0xf5efffff] has been reserved


[    0.267505] system 00:06: [mem 0xfee01000-0xfeefffff] has been reserved


[    0.267510] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.267618] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)


[    0.267727] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved


[    0.267732] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved


[    0.267737] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.267842] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved


[    0.267847] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.268161] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved


[    0.268166] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved


[    0.268171] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved


[    0.268176] system 00:0a: [mem 0x00100000-0x7fffffff] could not be reserved


[    0.268181] system 00:0a: [mem 0xff700000-0xffffffff] has been reserved


[    0.268186] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)


[    0.268616] pnp: PnP ACPI: found 11 devices


[    0.268618] ACPI: ACPI bus type pnp unregistered


[    0.276576] pci 0000:00:02.0: PCI bridge to [bus 01]


[    0.276586] pci 0000:00:03.0: PCI bridge to [bus 02]


[    0.276594] pci 0000:00:04.0: PCI bridge to [bus 03]


[    0.276598] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]


[    0.276604] pci 0000:00:04.0:   bridge window [mem 0xf5f00000-0xf7ffffff]


[    0.276609] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]


[    0.276615] pci 0000:00:10.0: PCI bridge to [bus 04]


[    0.276621] pci 0000:00:10.0:   bridge window [mem 0xf8000000-0xfebfffff]


[    0.276640] pci 0000:00:10.0: setting latency timer to 64


[    0.276646] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]


[    0.276650] pci_bus 0000:00: resource 5 [mem 0x80000000-0xfcffffffff]


[    0.276654] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]


[    0.276658] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]


[    0.276662] pci_bus 0000:03: resource 1 [mem 0xf5f00000-0xf7ffffff]


[    0.276667] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.276671] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xfebfffff]
[    0.276675] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    0.276679] pci_bus 0000:04: resource 5 [mem 0x80000000-0xfcffffffff]
[    0.276683] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.276742] NET: Registered protocol family 2
[    0.276971] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.277146] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.277287] TCP: Hash tables configured (established 16384 bind 16384)
[    0.277379] TCP: reno registered
[    0.277388] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.277423] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.277546] NET: Registered protocol family 1
[    0.277620] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.277648] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.277682] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.277942] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    0.756195] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.756279] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.756336] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.756396] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.756426] pci 0000:03:00.0: Boot video device
[    0.756436] PCI: CLS 64 bytes, default 64
[    0.756511] Trying to unpack rootfs image as initramfs...
[    1.217581] Freeing initrd memory: 15772k freed
[    1.227496] Initialise module verification
[    1.227572] audit: initializing netlink socket (disabled)
[    1.227591] type=2000 audit(1374323506.224:1): initialized
[    1.273418] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.276182] VFS: Disk quotas dquot_6.5.2
[    1.276264] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.277178] fuse init (API version 7.20)
[    1.277334] msgmni has been set to 3999
[    1.278143] Key type asymmetric registered
[    1.278147] Asymmetric key parser 'x509' registered
[    1.278205] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.278260] io scheduler noop registered
[    1.278264] io scheduler deadline registered (default)
[    1.278274] io scheduler cfq registered
[    1.278495] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.278590] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    1.278680] pcieport 0000:00:04.0: irq 42 for MSI/MSI-X
[    1.278768] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.278793] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.278980] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.278987] ACPI: Power Button [PWRB]
[    1.279056] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.279060] ACPI: Power Button [PWRF]
[    1.279149] ACPI: acpi_idle registered with cpuidle
[    1.283273] GHES: HEST is not enabled!
[    1.283425] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.285910] Linux agpgart interface v0.103
[    1.288176] brd: module loaded
[    1.289456] loop: module loaded
[    1.290122] libphy: Fixed MDIO Bus: probed
[    1.290233] tun: Universal TUN/TAP device driver, 1.6
[    1.290235] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.290304] PPP generic driver version 2.4.2
[    1.290376] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.290379] ehci-pci: EHCI PCI platform driver
[    1.290437] ehci-pci 0000:00:0b.1: setting latency timer to 64
[    1.290442] ehci-pci 0000:00:0b.1: EHCI Host Controller
[    1.290452] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    1.290466] ehci-pci 0000:00:0b.1: debug port 1
[    1.290497] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
[    1.290532] ehci-pci 0000:00:0b.1: irq 22, io mem 0xf5ebfc00
[    1.300036] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    1.300070] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.300075] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.300079] usb usb1: Product: EHCI Host Controller
[    1.300083] usb usb1: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    1.300087] usb usb1: SerialNumber: 0000:00:0b.1
[    1.300246] hub 1-0:1.0: USB hub found
[    1.300253] hub 1-0:1.0: 8 ports detected
[    1.300480] ehci-platform: EHCI generic platform driver
[    1.300497] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.300552] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    1.300557] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    1.300569] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    1.300606] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xf5ebe000
[    1.358030] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.358035] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.358038] usb usb2: Product: OHCI Host Controller
[    1.358042] usb usb2: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    1.358046] usb usb2: SerialNumber: 0000:00:0b.0
[    1.358198] hub 2-0:1.0: USB hub found
[    1.358206] hub 2-0:1.0: 8 ports detected
[    1.358422] uhci_hcd: USB Universal Host Controller Interface driver
[    1.358525] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.358968] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.358977] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.359173] mousedev: PS/2 mouse device common for all mice
[    1.359367] rtc_cmos 00:01: RTC can wake from S4
[    1.359537] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.359580] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.359725] device-mapper: uevent: version 1.0.3
[    1.359822] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.359848] cpuidle: using governor ladder
[    1.359874] cpuidle: using governor menu
[    1.359878] ledtrig-cpu: registered to indicate activity on CPUs
[    1.359881] EFI Variables Facility v0.08 2004-May-17
[    1.360260] ashmem: initialized


[    1.360439] TCP: cubic registered


[    1.360615] NET: Registered protocol family 10


[    1.360890] NET: Registered protocol family 17


[    1.360906] Key type dns_resolver registered


[    1.361267] Loading module verification certificates


[    1.362973] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'


[    1.362991] registered taskstats version 1


[    1.366912] Key type trusted registered


[    1.370610] Key type encrypted registered


[    1.374659] rtc_cmos 00:01: setting system clock to 2013-07-20 12:31:47 UTC (1374323507)


[    1.374802] powernow-k8: fid 0x8 (1600 MHz), vid 0x13


[    1.374808] powernow-k8: fid 0x0 (800 MHz), vid 0x1e


[    1.374847] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52 (2 cpu cores) (version 2.20.00)


[    1.374870] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found


[    1.374872] EDD information not available.


[    1.377606] Freeing unused kernel memory: 992k freed


[    1.378152] Write protecting the kernel read-only data: 12288k


[    1.384067] Freeing unused kernel memory: 1176k freed


[    1.389984] Freeing unused kernel memory: 1080k freed


[    1.413816] udevd[94]: starting version 175


[    1.544554] pata_amd 0000:00:0d.0: version 0.4.1


[    1.544611] pata_amd 0000:00:0d.0: setting latency timer to 64


[    1.548572] scsi0 : pata_amd
[    1.562326] Disabling lock debugging due to kernel taint


[    1.607095] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19


[    1.612035] usb 1-2: new high-speed USB device number 2 using ehci-pci


[    1.632829] scsi1 : pata_amd
[    1.633715] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14


[    1.633719] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15


[    1.633808] sata_nv 0000:00:0e.0: version 3.5


[    1.634047] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21


[    1.634070] sata_nv 0000:00:0e.0: Using SWNCQ mode


[    1.634125] sata_nv 0000:00:0e.0: setting latency timer to 64


[    1.634547] scsi2 : sata_nv
[    1.635110] scsi3 : sata_nv


[    1.635633] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 21


[    1.635637] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 21


[    1.635741] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.


[    1.635944] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20


[    1.635970] forcedeth 0000:00:14.0: setting latency timer to 64


[    1.660113] firewire_ohci 0000:04:01.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0


[    1.746685] usb 1-2: New USB device found, idVendor=0846, idProduct=9020


[    1.746693] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3


[    1.746697] usb 1-2: Product: Remote Download Wireless Adapter


[    1.746701] usb 1-2: Manufacturer: Broadcom


[    1.746705] usb 1-2: SerialNumber: 113


[    1.812357] ata1.00: ATAPI: TSSTcorpDVDR/RW TS-T632L, 1117, max UDMA/33


[    1.812370] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:900:0x11)


[    1.844271] ata1.00: configured for UDMA/33


[    1.856023] usb 1-5: new high-speed USB device number 3 using ehci-pci


[    1.868522] scsi 0:0:0:0: CD-ROM            TSSTcorp DVDR/RW TS-T632L 1117 PQ: 0 ANSI: 5


[    1.900765] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray


[    1.900768] cdrom: Uniform CD-ROM driver Revision: 3.20


[    1.900946] sr 0:0:0:0: Attached scsi CD-ROM sr0


[    1.901153] sr 0:0:0:0: Attached scsi generic sg0 type 5


[    1.901285] ata2: port disabled--ignoring


[    1.989808] usb 1-5: New USB device found, idVendor=058f, idProduct=6361


[    1.989813] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3


[    1.989816] usb 1-5: Product: USB Reader


[    1.989820] usb 1-5: Manufacturer:  


[    1.989824] usb 1-5: SerialNumber: 058F12M111B


[    2.100046] usb 1-6: new high-speed USB device number 4 using ehci-pci


[    2.100049] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)


[    2.108219] ata3.00: ATA-7: ST3320820AS, 3.AHG, max UDMA/100


[    2.108223] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)


[    2.124209] ata3.00: configured for UDMA/100


[    2.124386] scsi 2:0:0:0: Direct-Access     ATA      ST3320820AS      3.AH PQ: 0 ANSI: 5


[    2.124577] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)


[    2.124628] sd 2:0:0:0: Attached scsi generic sg1 type 0


[    2.124649] sd 2:0:0:0: [sda] Write Protect is off


[    2.124654] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00


[    2.124685] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


[    2.160116] firewire_core 0000:04:01.0: created device fw0: GUID 0011d8000140a3bd, S400


[    2.160615] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1a:92:eb:b6:3b


[    2.160623] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3


[    2.192998]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >


[    2.193751] sd 2:0:0:0: [sda] Attached SCSI disk


[    2.232442] usb 1-6: New USB device found, idVendor=0424, idProduct=2507


[    2.232449] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0


[    2.232729] hub 1-6:1.0: USB hub found


[    2.232809] hub 1-6:1.0: 7 ports detected


[    2.436028] ata4: SATA link down (SStatus 0 SControl 300)


[    2.604033] usb 1-8: new high-speed USB device number 6 using ehci-pci


[    2.736316] usb 1-8: New USB device found, idVendor=0424, idProduct=2507


[    2.736323] usb 1-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0


[    2.736608] hub 1-8:1.0: USB hub found


[    2.736683] hub 1-8:1.0: 7 ports detected


[    2.869301] Initializing USB Mass Storage driver...


[    2.869503] scsi4 : usb-storage 1-5:1.0


[    2.869642] usbcore: registered new interface driver usb-storage


[    2.869645] USB Mass Storage support registered.


[    2.936198] usb 1-6.1: new full-speed USB device number 7 using ehci-pci


[    3.034308] usb 1-6.1: New USB device found, idVendor=0471, idProduct=060f


[    3.034313] usb 1-6.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3


[    3.034317] usb 1-6.1: Product: BB+ Module(e.d)


[    3.034321] usb 1-6.1: Manufacturer:  


[    3.034325] usb 1-6.1: SerialNumber: NCLJ


[    3.120065] usb 1-6.3: new low-speed USB device number 8 using ehci-pci


[    3.218933] usb 1-6.3: New USB device found, idVendor=03f0, idProduct=100c


[    3.218938] usb 1-6.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0


[    3.218942] usb 1-6.3: Product: USB Multimedia Cordless Kit


[    3.218945] usb 1-6.3: Manufacturer: BTC


[    3.238752] usbcore: registered new interface driver usbhid


[    3.238757] usbhid: USB HID core driver


[    3.244057] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:0b.1/usb1/1-6/1-6.3/1-6.3:1.0/input/input2


[    3.244343] hid-generic 0003:03F0:100C.0001: input,hidraw0: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Kit] on usb-0000:00:0b.1-6.3/input0


[    3.245247] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:0b.1/usb1/1-6/1-6.3/1-6.3:1.1/input/input3


[    3.249059] hid-generic 0003:03F0:100C.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Kit] on usb-0000:00:0b.1-6.3/input1


[    3.292195] usb 1-6.7: new full-speed USB device number 9 using ehci-pci


[    3.412812] usb 1-6.7: New USB device found, idVendor=03f0, idProduct=171d


[    3.412817] usb 1-6.7: New USB device strings: Mfr=1, Product=2, SerialNumber=0


[    3.412821] usb 1-6.7: Product: HP Integrated Module


[    3.412825] usb 1-6.7: Manufacturer: Broadcom Corp


[    3.588034] usb 2-7: new full-speed USB device number 2 using ohci_hcd


[    3.800066] usb 2-7: New USB device found, idVendor=1926, idProduct=0001


[    3.800073] usb 2-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0


[    3.800077] usb 2-7: Product: Touchscreen


[    3.800081] usb 2-7: Manufacturer: Nextwindow


[    3.815135] input: Nextwindow Touchscreen as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.0/input/input4


[    3.815477] hid-generic 0003:1926:0001.0003: input,hidraw2: USB HID v1.00 Mouse [Nextwindow Touchscreen] on usb-0000:00:0b.0-7/input0


[    3.827221] hid-generic 0003:1926:0001.0004: hiddev0,hidraw3: USB HID v1.00 Device [Nextwindow Touchscreen] on usb-0000:00:0b.0-7/input1


[    3.839137] input: Nextwindow Touchscreen as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.2/input/input5


[    3.839276] hid-generic 0003:1926:0001.0005: input,hidraw4: USB HID v1.00 Keyboard [Nextwindow Touchscreen] on usb-0000:00:0b.0-7/input2


[    3.870844] scsi 4:0:0:0: Direct-Access     Generic  CF Reader        1.01 PQ: 0 ANSI: 0


[    3.871578] scsi 4:0:0:1: Direct-Access     Generic  SM/SD/MS Reader  1.00 PQ: 0 ANSI: 0


[    3.872609] sd 4:0:0:0: Attached scsi generic sg2 type 0


[    3.872853] sd 4:0:0:1: Attached scsi generic sg3 type 0


[    3.875707] sd 4:0:0:0: [sdb] Attached SCSI removable disk


[    3.876344] sd 4:0:0:1: [sdc] Attached SCSI removable disk


[    3.924694] usb 1-8.2: new high-speed USB device number 10 using ehci-pci


[    3.935716] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)


[    4.033310] usb 1-8.2: New USB device found, idVendor=0ace, idProduct=b215


[    4.033318] usb 1-8.2: New USB device strings: Mfr=16, Product=32, SerialNumber=0


[    4.033322] usb 1-8.2: Product: USB2.0 WLAN
[    4.033325] usb 1-8.2: Manufacturer: ZyDAS


[    4.120075] usb 1-8.3: new high-speed USB device number 11 using ehci-pci


[    4.221689] usb 1-8.3: New USB device found, idVendor=0c45, idProduct=62c0


[    4.221696] usb 1-8.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3


[    4.221700] usb 1-8.3: Product: USB 2.0 Camera


[    4.221703] usb 1-8.3: Manufacturer: Sonix Technology Co., Ltd.


[    4.221706] usb 1-8.3: SerialNumber: SN0001


[    4.967571] init: ureadahead main process (287) terminated with status 5


[    6.062623] Adding 19530748k swap on /dev/sda6.  Priority:-1 extents:1 across:19530748k 


[    7.182670] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready


[    7.340550] udevd[359]: starting version 175


[    8.561900] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro


[    9.502924] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)


[   10.849158] type=1400 audit(1374345116.970:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=627 comm="apparmor_parser"


[   10.849447] type=1400 audit(1374345116.970:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=626 comm="apparmor_parser"


[   10.849880] type=1400 audit(1374345116.970:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=627 comm="apparmor_parser"


[   10.850186] type=1400 audit(1374345116.970:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=626 comm="apparmor_parser"


[   10.850289] type=1400 audit(1374345116.970:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=627 comm="apparmor_parser"


[   10.850603] type=1400 audit(1374345116.970:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=626 comm="apparmor_parser"


[   11.441898] init: failsafe main process (685) killed by TERM signal
[   12.907283] type=1400 audit(1374345119.026:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=801 comm="apparmor_parser"


[   12.908139] type=1400 audit(1374345119.030:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=801 comm="apparmor_parser"


[   12.908907] type=1400 audit(1374345119.030:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=801 comm="apparmor_parser"


[   13.399778] type=1400 audit(1374345119.518:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=800 comm="apparmor_parser"


[   13.863369] init: bluetooth main process (812) terminated with status 1


[   13.863415] init: bluetooth main process ended, respawning


[   14.006937] init: bluetooth main process (847) terminated with status 1


[   14.006990] init: bluetooth main process ended, respawning


[   14.044140] init: bluetooth main process (870) terminated with status 1


[   14.044193] init: bluetooth main process ended, respawning


[   14.081230] init: bluetooth main process (893) terminated with status 1


[   14.081280] init: bluetooth main process ended, respawning


[   14.123780] init: bluetooth main process (916) terminated with status 1


[   14.123831] init: bluetooth main process ended, respawning


[   14.161868] init: bluetooth main process (939) terminated with status 1


[   14.161919] init: bluetooth main process ended, respawning


[   14.199413] init: bluetooth main process (962) terminated with status 1


[   14.199466] init: bluetooth main process ended, respawning


[   14.237638] init: bluetooth main process (985) terminated with status 1


[   14.237689] init: bluetooth main process ended, respawning


[   14.273543] init: bluetooth main process (1008) terminated with status 1


[   14.273597] init: bluetooth main process ended, respawning


[   14.310664] init: bluetooth main process (1031) terminated with status 1


[   14.310714] init: bluetooth main process ended, respawning


[   14.380137] init: bluetooth main process (1054) terminated with status 1


[   14.380192] init: bluetooth respawning too fast, stopped


[   16.990607] init: udev-fallback-graphics main process (1182) terminated with status 1


[   19.700870] forcedeth 0000:00:14.0 eth0: no link during initialization


[   19.701267] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready


[   19.701697] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready


[   60.093084] audit_printk_skb: 45 callbacks suppressed


[   60.093091] type=1400 audit(1374345166.214:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2108 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


[  223.188218] usb 1-6.6: new high-speed USB device number 12 using ehci-pci


[  223.312954] usb 1-6.6: New USB device found, idVendor=0cf3, idProduct=9271


[  223.312968] usb 1-6.6: New USB device strings: Mfr=16, Product=32, SerialNumber=48


[  223.312977] usb 1-6.6: Product: USB2.0 WLAN


[  223.312985] usb 1-6.6: Manufacturer: ATHEROS


[  223.312992] usb 1-6.6: SerialNumber: 12345


[  333.813326] type=1400 audit(1374345439.934:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=822 comm="cupsd" pid=822 comm="cupsd" capability=36  capname="block_suspend"


Hp touchsmart Pc iq770


Ubuntu 12.04.2 LTS


Kernel: 3.8.0-19-generic x86_64






from lsusb:




Bus 001 Device 012: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n






interfaces:




jaing@minion-of-jaing:~$ ifconfig
eth0
      Link encap:Ethernet  HWaddr 00:1a:92:eb:b6:3b
  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


          RX packets:0 errors:0 dropped:0 overruns:0 frame:0


          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0


          collisions:0 txqueuelen:1000
 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo
        Link encap:Local Loopback
  
          inet addr:127.0.0.1  Mask:255.0.0.0


          inet6 addr: ::1/128 Scope:Host


          UP LOOPBACK RUNNING  MTU:65536
  Metric:1
          RX packets:816 errors:0 dropped:0 overruns:0 frame:0


          TX packets:816 errors:0 dropped:0 overruns:0 carrier:0


          collisions:0 txqueuelen:0
 
          RX bytes:62352 (62.3 KB)
  TX bytes:62352 (62.3 KB)




jaing@minion-of-jaing:~$ iwconfig


eth0
      no wireless extensions.




lo
        no wireless extensions.








lsmod:




Module
                  Size  Used by


hid_generic            12540  0 


usbhid                 47074  0 


hid                   101002  2 
hid_generic,usbhid
usb_storage            57204  0 


pata_acpi              13038  0 


firewire_ohci          40103  0 


forcedeth              66977  0 


firewire_core          64508  1 
firewire_ohci
crc_itu_t              12707  1 
firewire_core
sata_nv                31812  4 


pata_amd               14129  0 








dmesg:








[    0.000000] Initializing cgroup subsys cpuset


[    0.000000] Initializing cgroup subsys cpu


[    0.000000] Linux version 3.8.0-19-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 (Ubuntu 3.8.0-19.29-generic 3.8.8)


[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=22411724-ce26-4d19-a103-e49bd29242de ro quiet splash vt.handoff=7


[    0.000000] KERNEL supported cpus:


[    0.000000]   Intel GenuineIntel


[    0.000000]   AMD AuthenticAMD


[    0.000000]   Centaur CentaurHauls


[    0.000000] e820: BIOS-provided physical RAM map:


[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable


[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved


[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved


[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffcffff] usable


[    0.000000] BIOS-e820: [mem 0x000000007ffd0000-0x000000007ffddfff] ACPI data


[    0.000000] BIOS-e820: [mem 0x000000007ffde000-0x000000007fffffff] ACPI NVS


[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved


[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved


[    0.000000] BIOS-e820: [mem 0x00000000ff700000-0x00000000ffffffff] reserved


[    0.000000] NX (Execute Disable) protection: active


[    0.000000] SMBIOS 2.4 present.


[    0.000000] DMI: HP-Pavilion RN635AA-ABA IQ770/PHOENIX, BIOS 5.15    11/26/2007


[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved


[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable


[    0.000000] No AGP bridge found


[    0.000000] e820: last_pfn = 0x7ffd0 max_arch_pfn = 0x400000000


[    0.000000] MTRR default type: uncachable


[    0.000000] MTRR fixed ranges enabled:


[    0.000000]   00000-9FFFF write-back


[    0.000000]   A0000-EFFFF uncachable


[    0.000000]   F0000-FFFFF write-protect


[    0.000000] MTRR variable ranges enabled:


[    0.000000]   0 base 0000000000 mask FF80000000 write-back


[    0.000000]   1 disabled


[    0.000000]   2 disabled


[    0.000000]   3 disabled


[    0.000000]   4 base 00000FC000 mask 0FFFFFE000 write-protect


[    0.000000]   5 base 00000DC000 mask 0FFFFFE000 write-back


[    0.000000]   6 disabled


[    0.000000]   7 disabled


[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106


[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.


[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.


[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.


[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.


[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]


[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]


[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576


[    0.000000] init_memory_mapping: [mem 0x00000000-0x7ffcffff]


[    0.000000]  [mem 0x00000000-0x7fdfffff] page 2M


[    0.000000]  [mem 0x7fe00000-0x7ffcffff] page 4k


[    0.000000] kernel direct mapping tables up to 0x7ffcffff @ [mem 0x1fffc000-0x1fffffff]


[    0.000000] RAMDISK: [mem 0x36122000-0x37088fff]


[    0.000000] ACPI: RSDP 00000000000fc560 00014 (v00 HPQOEM)


[    0.000000] ACPI: RSDT 000000007ffd0000 00040 (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: FACP 000000007ffd0200 00084 (v02 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: DSDT 000000007ffd05c0 04B50 (v01 HPQOEM SLIC-CPC 00000000 INTL 20060210)


[    0.000000] ACPI: FACS 000000007ffde000 00040


[    0.000000] ACPI: APIC 000000007ffd0390 00070 (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: MCFG 000000007ffd0400 0003C (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: SLIC 000000007ffd0440 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)


[    0.000000] ACPI: OEMB 000000007ffde040 00063 (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: HPET 000000007ffd5110 00038 (v01 HPQOEM SLIC-CPC 11000726 MSFT 00000097)


[    0.000000] ACPI: SSDT 000000007ffd5150 00182 (v01 A M I  POWERNOW 00000001 AMD  00000001)


[    0.000000] ACPI: Local APIC address 0xfee00000


[    0.000000] Scanning NUMA topology in Northbridge 24


[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007ffcffff]


[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7ffcffff]


[    0.000000]   NODE_DATA [mem 0x7ffcb000-0x7ffcffff]


[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007d600000-ffff88007f5fffff] on node 0


[    0.000000] Zone ranges:


[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]


[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]


[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node


[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]


[    0.000000]   node   0: [mem 0x00100000-0x7ffcffff]


[    0.000000] On node 0 totalpages: 524127


[    0.000000]   DMA zone: 64 pages used for memmap


[    0.000000]   DMA zone: 6 pages reserved


[    0.000000]   DMA zone: 3913 pages, LIFO batch:0


[    0.000000]   DMA32 zone: 8128 pages used for memmap


[    0.000000]   DMA32 zone: 512016 pages, LIFO batch:31


[    0.000000] Detected use of extended apic ids on hypertransport bus


[    0.000000] ACPI: PM-Timer IO Port: 0x4008


[    0.000000] ACPI: Local APIC address 0xfee00000


[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)


[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)


[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])


[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23


[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)


[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)


[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)


[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)


[    0.000000] ACPI: IRQ0 used by override.


[    0.000000] ACPI: IRQ2 used by override.


[    0.000000] ACPI: IRQ9 used by override.


[    0.000000] ACPI: IRQ14 used by override.


[    0.000000] ACPI: IRQ15 used by override.


[    0.000000] Using ACPI (MADT) for SMP configuration information


[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000


[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs


[    0.000000] nr_irqs_gsi: 40


[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000


[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000


[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000


[    0.000000] e820: [mem 0x80000000-0xfebfffff] available for PCI devices


[    0.000000] Booting paravirtualized kernel on bare hardware


[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1


[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s85056 r8192 d21440 u1048576


[    0.000000] pcpu-alloc: s85056 r8192 d21440 u1048576 alloc=1*2097152


[    0.000000] pcpu-alloc: [0] 0 1 


[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515929


[    0.000000] Policy zone: DMA32


[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=22411724-ce26-4d19-a103-e49bd29242de ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Memory: 2031916k/2096960k available (7006k kernel code, 452k absent, 64592k reserved, 6238k data, 992k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25


[    0.000000] console [tty0] enabled


[    0.000000] allocated 8388608 bytes of page_cgroup


[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups


[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT


[    0.000000] tsc: Detected 1607.547 MHz processor


[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized


[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3215.09 BogoMIPS (lpj=6430188)


[    0.004011] pid_max: default: 32768 minimum: 301


[    0.004057] Security Framework initialized


[    0.004078] AppArmor: AppArmor initialized


[    0.004080] Yama: becoming mindful.


[    0.004423] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)


[    0.009041] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)


[    0.009615] Mount-cache hash table entries: 256


[    0.009913] Initializing cgroup subsys cpuacct


[    0.009917] Initializing cgroup subsys memory


[    0.009930] Initializing cgroup subsys devices


[    0.009933] Initializing cgroup subsys freezer


[    0.009936] Initializing cgroup subsys blkio


[    0.009938] Initializing cgroup subsys perf_event


[    0.009943] Initializing cgroup subsys hugetlb


[    0.009976] tseg: 0000000000


[    0.010006] CPU: Physical Processor ID: 0


[    0.010008] CPU: Processor Core ID: 0


[    0.010011] mce: CPU supports 5 MCE banks


[    0.010020] LVT offset 0 assigned for vector 0xf9


[    0.010028] process: using AMD E400 aware idle routine


[    0.010033] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4


[    0.010033] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4


[    0.010033] tlb_flushall_shift: 4


[    0.010209] Freeing SMP alternatives: 24k freed


[    0.012493] ACPI: Core revision 20121018


[    0.017087] ftrace: allocating 26689 entries in 105 pages


[    0.036496] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1


[    0.076205] smpboot: CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-52 (fam: 0f, model: 48, stepping: 02)


[    0.080000] Performance Events: AMD PMU driver.


[    0.080000] ... version:                0


[    0.080000] ... bit width:              48


[    0.080000] ... generic registers:      4


[    0.080000] ... value mask:             0000ffffffffffff


[    0.080000] ... max period:             00007fffffffffff


[    0.080000] ... fixed-purpose events:   0


[    0.080000] ... event mask:             000000000000000f


[    0.080000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.


[    0.080000] smpboot: Booting Node   0, Processors  #1 OK


[    0.168116] Brought up 2 CPUs


[    0.168120] smpboot: Total of 2 processors activated (6429.88 BogoMIPS)


[    0.168738] devtmpfs: initialized
[    0.170424] EVM: security.selinux


[    0.170427] EVM: security.SMACK64
[    0.170430] EVM: security.capability


[    0.170454] PM: Registering ACPI NVS region [mem 0x7ffde000-0x7fffffff] (139264 bytes)


[    0.173334] regulator-dummy: no parameters


[    0.173418] NET: Registered protocol family 16


[    0.173606] node 0 link 0: io port [1000, ffffff]


[    0.173610] TOM: 0000000080000000 aka 2048M


[    0.173614] node 0 link 0: mmio [e0000000, efffffff]


[    0.173619] node 0 link 0: mmio [a0000, bffff]


[    0.173622] node 0 link 0: mmio [80000000, fe0bffff]


[    0.173626] bus: [bus 00-ff] on node 0 link 0


[    0.173629] bus: 00 [io  0x0000-0xffff]


[    0.173631] bus: 00 [mem 0x80000000-0xfcffffffff]


[    0.173634] bus: 00 [mem 0x000a0000-0x000bffff]


[    0.173718] ACPI: bus type pci registered


[    0.173805] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)


[    0.173809] PCI: not using MMCONFIG


[    0.173812] PCI: Using configuration type 1 for base access


[    0.175194] bio: create slab <bio-0> at 0


[    0.175194] ACPI: Added _OSI(Module Device)


[    0.175194] ACPI: Added _OSI(Processor Device)


[    0.175194] ACPI: Added _OSI(3.0 _SCP Extensions)


[    0.175194] ACPI: Added _OSI(Processor Aggregator Device)


[    0.177089] ACPI: EC: Look up EC in DSDT


[    0.178322] ACPI: Executed 1 blocks of module-level executable AML code


[    0.220111] ACPI BIOS Bug: Warning: Incorrect checksum in table [OEMB] - 0xCE, should be 0xC1 (20121018/tbutils-324)


[    0.220346] ACPI: Interpreter enabled


[    0.220353] ACPI: (supports S0 S1 S3 S4 S5)


[    0.220385] ACPI: Using IOAPIC for interrupt routing


[    0.220428] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)


[    0.221433] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources


[    0.241376] ACPI: No dock devices found.


[    0.241386] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug


[    0.241481] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])


[    0.241485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]


[    0.241788] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)


[    0.241792] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)


[    0.241797] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)


[    0.241801] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)


[    0.241805] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xff6fffff] (ignored)


[    0.241809] PCI: root bus 00: hardware-probed resources


[    0.241852] PCI host bridge to bus 0000:00


[    0.241857] pci_bus 0000:00: root bus resource [bus 00-ff]


[    0.241861] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]


[    0.241866] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfcffffffff]


[    0.241870] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]


[    0.241885] pci 0000:00:00.0: [10de:02f3] type 00 class 0x050000


[    0.241945] pci 0000:00:00.1: [10de:02fa] type 00 class 0x050000
[    0.241985] pci 0000:00:00.2: [10de:02fe] type 00 class 0x050000


[    0.242032] pci 0000:00:00.3: [10de:02f8] type 00 class 0x050000


[    0.242078] pci 0000:00:00.4: [10de:02f9] type 00 class 0x050000


[    0.242125] pci 0000:00:00.5: [10de:02ff] type 00 class 0x050000


[    0.242176] pci 0000:00:00.6: [10de:027f] type 00 class 0x050000


[    0.242213] pci 0000:00:00.7: [10de:027e] type 00 class 0x050000


[    0.242264] pci 0000:00:02.0: [10de:02fc] type 01 class 0x060400


[    0.242302] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.242323] pci 0000:00:03.0: [10de:02fd] type 01 class 0x060400


[    0.242359] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.242380] pci 0000:00:04.0: [10de:02fb] type 01 class 0x060400


[    0.242416] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.242454] pci 0000:00:09.0: [10de:0270] type 00 class 0x050000


[    0.242662] pci 0000:00:0a.0: [10de:0260] type 00 class 0x060100


[    0.242722] pci 0000:00:0a.1: [10de:0264] type 00 class 0x0c0500


[    0.242762] pci 0000:00:0a.1: reg 20: [io  0x5000-0x503f]


[    0.242772] pci 0000:00:0a.1: reg 24: [io  0x6000-0x603f]


[    0.242814] pci 0000:00:0a.1: PME# supported from D3hot D3cold


[    0.242843] pci 0000:00:0b.0: [10de:026d] type 00 class 0x0c0310


[    0.242857] pci 0000:00:0b.0: reg 10: [mem 0xf5ebe000-0xf5ebefff]


[    0.242910] pci 0000:00:0b.0: supports D1 D2


[    0.242914] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.242934] pci 0000:00:0b.1: [10de:026e] type 00 class 0x0c0320


[    0.242948] pci 0000:00:0b.1: reg 10: [mem 0xf5ebfc00-0xf5ebfcff]


[    0.243004] pci 0000:00:0b.1: supports D1 D2


[    0.243008] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold


[    0.243035] pci 0000:00:0d.0: [10de:0265] type 00 class 0x01018a


[    0.243064] pci 0000:00:0d.0: reg 20: [io  0xffa0-0xffaf]


[    0.243109] pci 0000:00:0e.0: [10de:0266] type 00 class 0x010185


[    0.243124] pci 0000:00:0e.0: reg 10: [io  0xd800-0xd807]


[    0.243133] pci 0000:00:0e.0: reg 14: [io  0xd480-0xd483]


[    0.243141] pci 0000:00:0e.0: reg 18: [io  0xd400-0xd407]


[    0.243150] pci 0000:00:0e.0: reg 1c: [io  0xd080-0xd083]


[    0.243158] pci 0000:00:0e.0: reg 20: [io  0xd000-0xd00f]


[    0.243167] pci 0000:00:0e.0: reg 24: [mem 0xf5ebd000-0xf5ebdfff]


[    0.243221] pci 0000:00:10.0: [10de:026f] type 01 class 0x060401


[    0.243281] pci 0000:00:10.1: [10de:026c] type 00 class 0x040300


[    0.243297] pci 0000:00:10.1: reg 10: [mem 0xf5eb8000-0xf5ebbfff]


[    0.243360] pci 0000:00:10.1: PME# supported from D3hot D3cold


[    0.243392] pci 0000:00:14.0: [10de:0269] type 00 class 0x068000


[    0.243405] pci 0000:00:14.0: reg 10: [mem 0xf5ebc000-0xf5ebcfff]


[    0.243414] pci 0000:00:14.0: reg 14: [io  0xcc00-0xcc07]


[    0.243456] pci 0000:00:14.0: supports D1 D2


[    0.243460] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold


[    0.243478] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000


[    0.243507] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000


[    0.243530] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000


[    0.243554] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000


[    0.243615] pci 0000:00:02.0: PCI bridge to [bus 01]


[    0.243647] pci 0000:00:03.0: PCI bridge to [bus 02]


[    0.243687] pci 0000:03:00.0: [10de:0398] type 00 class 0x030000


[    0.243698] pci 0000:03:00.0: reg 10: [mem 0xf7000000-0xf7ffffff]


[    0.243709] pci 0000:03:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]


[    0.243720] pci 0000:03:00.0: reg 1c: [mem 0xf6000000-0xf6ffffff 64bit]


[    0.243728] pci 0000:03:00.0: reg 24: [io  0xec00-0xec7f]


[    0.243737] pci 0000:03:00.0: reg 30: [mem 0xf5fe0000-0xf5ffffff pref]


[    0.243773] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'


[    0.243782] pci 0000:00:04.0: PCI bridge to [bus 03]


[    0.243788] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]


[    0.243793] pci 0000:00:04.0:   bridge window [mem 0xf5f00000-0xf7ffffff]


[    0.243798] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]


[    0.243835] pci 0000:04:00.0: [14f1:5b7a] type 00 class 0x040000


[    0.243853] pci 0000:04:00.0: reg 10: [mem 0xf8000000-0xfbffffff]


[    0.243938] pci 0000:04:01.0: [11c1:5811] type 00 class 0x0c0010


[    0.243955] pci 0000:04:01.0: reg 10: [mem 0xfebff000-0xfebfffff]


[    0.244035] pci 0000:04:01.0: supports D1 D2


[    0.244039] pci 0000:04:01.0: PME# supported from D0 D1 D2 D3hot


[    0.244081] pci 0000:00:10.0: PCI bridge to [bus 04] (subtractive decode)


[    0.244087] pci 0000:00:10.0:   bridge window [mem 0xf8000000-0xfebfffff]


[    0.244093] pci 0000:00:10.0:   bridge window [io  0x0000-0xffff] (subtractive decode)


[    0.244097] pci 0000:00:10.0:   bridge window [mem 0x80000000-0xfcffffffff] (subtractive decode)


[    0.244101] pci 0000:00:10.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)


[    0.244129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]


[    0.244182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]


[    0.244227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]


[    0.244316] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]


[    0.244382]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM


[    0.244385]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)


[    0.246391] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *15


[    0.246503] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.


[    0.246611] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.


[    0.246717] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *10


[    0.246822] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10


[    0.246929] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.


[    0.247034] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.


[    0.247140] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.


[    0.247247] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *7


[    0.247353] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15


[    0.247459] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5


[    0.247565] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11


[    0.247671] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.


[    0.247777] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.


[    0.247884] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5


[    0.248007] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11


[    0.248129] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10


[    0.248245] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.


[    0.248375] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.


[    0.248524] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none


[    0.248524] vgaarb: loaded
[    0.248524] vgaarb: bridge control possible 0000:03:00.0


[    0.248524] SCSI subsystem initialized
[    0.248524] ACPI: bus type scsi registered


[    0.248524] libata version 3.00 loaded.


[    0.248524] ACPI: bus type usb registered


[    0.248524] usbcore: registered new interface driver usbfs


[    0.248524] usbcore: registered new interface driver hub


[    0.248524] usbcore: registered new device driver usb


[    0.248524] PCI: Using ACPI for IRQ routing


[    0.256818] PCI: pci_cache_line_size set to 64 bytes


[    0.256902] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]


[    0.256906] e820: reserve RAM buffer [mem 0x7ffd0000-0x7fffffff]


[    0.257056] NetLabel: Initializing


[    0.257059] NetLabel:  domain hash size = 128


[    0.257061] NetLabel:  protocols = UNLABELED CIPSOv4


[    0.257078] NetLabel:  unlabeled traffic allowed by default


[    0.257099] HPET: 3 timers in total, 0 timers will be used for per-cpu timer


[    0.257099] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31


[    0.257099] hpet0: 3 comparators, 32-bit 25.000000 MHz counter


[    0.258118] Switching to clocksource hpet


[    0.266326] AppArmor: AppArmor Filesystem Enabled


[    0.266374] pnp: PnP ACPI init


[    0.266396] ACPI: bus type pnp registered


[    0.266470] pnp 00:00: [dma 4]


[    0.266507] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)


[    0.266566] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)


[    0.266632] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)


[    0.266678] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)


[    0.266840] system 00:04: [io  0x0295-0x02a4] has been reserved


[    0.266847] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.266945] system 00:05: [mem 0xfefe0000-0xfefe01ff] has been reserved


[    0.266950] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.267435] system 00:06: [io  0x04d0-0x04d1] has been reserved


[    0.267440] system 00:06: [io  0x0800-0x080f] has been reserved


[    0.267444] system 00:06: [io  0x4000-0x407f] has been reserved


[    0.267449] system 00:06: [io  0x4080-0x40ff] has been reserved


[    0.267453] system 00:06: [io  0x4400-0x447f] has been reserved


[    0.267458] system 00:06: [io  0x4480-0x44ff] has been reserved


[    0.267462] system 00:06: [io  0x4800-0x487f] has been reserved


[    0.267467] system 00:06: [io  0x4880-0x48ff] has been reserved


[    0.267471] system 00:06: [io  0x2000-0x207f] has been reserved


[    0.267480] system 00:06: [io  0x2080-0x20ff] has been reserved


[    0.267485] system 00:06: [mem 0x000d0000-0x000d3fff window] has been reserved


[    0.267490] system 00:06: [mem 0x000d4000-0x000d7fff window] has been reserved


[    0.267495] system 00:06: [mem 0x000de000-0x000dffff window] has been reserved


[    0.267500] system 00:06: [mem 0xf5ec0000-0xf5efffff] has been reserved


[    0.267505] system 00:06: [mem 0xfee01000-0xfeefffff] has been reserved


[    0.267510] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.267618] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)


[    0.267727] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved


[    0.267732] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved


[    0.267737] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.267842] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved


[    0.267847] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)


[    0.268161] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved


[    0.268166] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved


[    0.268171] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved


[    0.268176] system 00:0a: [mem 0x00100000-0x7fffffff] could not be reserved


[    0.268181] system 00:0a: [mem 0xff700000-0xffffffff] has been reserved


[    0.268186] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)


[    0.268616] pnp: PnP ACPI: found 11 devices


[    0.268618] ACPI: ACPI bus type pnp unregistered


[    0.276576] pci 0000:00:02.0: PCI bridge to [bus 01]


[    0.276586] pci 0000:00:03.0: PCI bridge to [bus 02]


[    0.276594] pci 0000:00:04.0: PCI bridge to [bus 03]


[    0.276598] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]


[    0.276604] pci 0000:00:04.0:   bridge window [mem 0xf5f00000-0xf7ffffff]


[    0.276609] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]


[    0.276615] pci 0000:00:10.0: PCI bridge to [bus 04]


[    0.276621] pci 0000:00:10.0:   bridge window [mem 0xf8000000-0xfebfffff]


[    0.276640] pci 0000:00:10.0: setting latency timer to 64


[    0.276646] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]


[    0.276650] pci_bus 0000:00: resource 5 [mem 0x80000000-0xfcffffffff]


[    0.276654] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]


[    0.276658] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]


[    0.276662] pci_bus 0000:03: resource 1 [mem 0xf5f00000-0xf7ffffff]


[    0.276667] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.276671] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xfebfffff]
[    0.276675] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    0.276679] pci_bus 0000:04: resource 5 [mem 0x80000000-0xfcffffffff]
[    0.276683] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.276742] NET: Registered protocol family 2
[    0.276971] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.277146] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.277287] TCP: Hash tables configured (established 16384 bind 16384)
[    0.277379] TCP: reno registered
[    0.277388] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.277423] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.277546] NET: Registered protocol family 1
[    0.277620] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.277648] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.277682] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.277942] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    0.756195] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.756279] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.756336] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.756396] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.756426] pci 0000:03:00.0: Boot video device
[    0.756436] PCI: CLS 64 bytes, default 64
[    0.756511] Trying to unpack rootfs image as initramfs...
[    1.217581] Freeing initrd memory: 15772k freed
[    1.227496] Initialise module verification
[    1.227572] audit: initializing netlink socket (disabled)
[    1.227591] type=2000 audit(1374323506.224:1): initialized
[    1.273418] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.276182] VFS: Disk quotas dquot_6.5.2
[    1.276264] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.277178] fuse init (API version 7.20)
[    1.277334] msgmni has been set to 3999
[    1.278143] Key type asymmetric registered
[    1.278147] Asymmetric key parser 'x509' registered
[    1.278205] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.278260] io scheduler noop registered
[    1.278264] io scheduler deadline registered (default)
[    1.278274] io scheduler cfq registered
[    1.278495] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.278590] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    1.278680] pcieport 0000:00:04.0: irq 42 for MSI/MSI-X
[    1.278768] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.278793] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.278980] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.278987] ACPI: Power Button [PWRB]
[    1.279056] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.279060] ACPI: Power Button [PWRF]
[    1.279149] ACPI: acpi_idle registered with cpuidle
[    1.283273] GHES: HEST is not enabled!
[    1.283425] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.285910] Linux agpgart interface v0.103
[    1.288176] brd: module loaded
[    1.289456] loop: module loaded
[    1.290122] libphy: Fixed MDIO Bus: probed
[    1.290233] tun: Universal TUN/TAP device driver, 1.6
[    1.290235] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.290304] PPP generic driver version 2.4.2
[    1.290376] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.290379] ehci-pci: EHCI PCI platform driver
[    1.290437] ehci-pci 0000:00:0b.1: setting latency timer to 64
[    1.290442] ehci-pci 0000:00:0b.1: EHCI Host Controller
[    1.290452] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    1.290466] ehci-pci 0000:00:0b.1: debug port 1
[    1.290497] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
[    1.290532] ehci-pci 0000:00:0b.1: irq 22, io mem 0xf5ebfc00
[    1.300036] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    1.300070] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.300075] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.300079] usb usb1: Product: EHCI Host Controller
[    1.300083] usb usb1: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    1.300087] usb usb1: SerialNumber: 0000:00:0b.1
[    1.300246] hub 1-0:1.0: USB hub found
[    1.300253] hub 1-0:1.0: 8 ports detected
[    1.300480] ehci-platform: EHCI generic platform driver
[    1.300497] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.300552] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    1.300557] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    1.300569] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    1.300606] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xf5ebe000
[    1.358030] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.358035] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.358038] usb usb2: Product: OHCI Host Controller
[    1.358042] usb usb2: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    1.358046] usb usb2: SerialNumber: 0000:00:0b.0
[    1.358198] hub 2-0:1.0: USB hub found
[    1.358206] hub 2-0:1.0: 8 ports detected
[    1.358422] uhci_hcd: USB Universal Host Controller Interface driver
[    1.358525] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.358968] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.358977] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.359173] mousedev: PS/2 mouse device common for all mice
[    1.359367] rtc_cmos 00:01: RTC can wake from S4
[    1.359537] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.359580] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.359725] device-mapper: uevent: version 1.0.3
[    1.359822] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.359848] cpuidle: using governor ladder
[    1.359874] cpuidle: using governor menu
[    1.359878] ledtrig-cpu: registered to indicate activity on CPUs
[    1.359881] EFI Variables Facility v0.08 2004-May-17
[    1.360260] ashmem: initialized


[    1.360439] TCP: cubic registered


[    1.360615] NET: Registered protocol family 10


[    1.360890] NET: Registered protocol family 17


[    1.360906] Key type dns_resolver registered


[    1.361267] Loading module verification certificates


[    1.362973] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'


[    1.362991] registered taskstats version 1


[    1.366912] Key type trusted registered


[    1.370610] Key type encrypted registered


[    1.374659] rtc_cmos 00:01: setting system clock to 2013-07-20 12:31:47 UTC (1374323507)


[    1.374802] powernow-k8: fid 0x8 (1600 MHz), vid 0x13


[    1.374808] powernow-k8: fid 0x0 (800 MHz), vid 0x1e


[    1.374847] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52 (2 cpu cores) (version 2.20.00)


[    1.374870] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found


[    1.374872] EDD information not available.


[    1.377606] Freeing unused kernel memory: 992k freed


[    1.378152] Write protecting the kernel read-only data: 12288k


[    1.384067] Freeing unused kernel memory: 1176k freed


[    1.389984] Freeing unused kernel memory: 1080k freed


[    1.413816] udevd[94]: starting version 175


[    1.544554] pata_amd 0000:00:0d.0: version 0.4.1


[    1.544611] pata_amd 0000:00:0d.0: setting latency timer to 64


[    1.548572] scsi0 : pata_amd
[    1.562326] Disabling lock debugging due to kernel taint


[    1.607095] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19


[    1.612035] usb 1-2: new high-speed USB device number 2 using ehci-pci


[    1.632829] scsi1 : pata_amd
[    1.633715] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14


[    1.633719] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15


[    1.633808] sata_nv 0000:00:0e.0: version 3.5


[    1.634047] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21


[    1.634070] sata_nv 0000:00:0e.0: Using SWNCQ mode


[    1.634125] sata_nv 0000:00:0e.0: setting latency timer to 64


[    1.634547] scsi2 : sata_nv
[    1.635110] scsi3 : sata_nv


[    1.635633] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 21


[    1.635637] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 21


[    1.635741] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.


[    1.635944] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20


[    1.635970] forcedeth 0000:00:14.0: setting latency timer to 64


[    1.660113] firewire_ohci 0000:04:01.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0


[    1.746685] usb 1-2: New USB device found, idVendor=0846, idProduct=9020


[    1.746693] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3


[    1.746697] usb 1-2: Product: Remote Download Wireless Adapter


[    1.746701] usb 1-2: Manufacturer: Broadcom


[    1.746705] usb 1-2: SerialNumber: 113


[    1.812357] ata1.00: ATAPI: TSSTcorpDVDR/RW TS-T632L, 1117, max UDMA/33


[    1.812370] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:900:0x11)


[    1.844271] ata1.00: configured for UDMA/33


[    1.856023] usb 1-5: new high-speed USB device number 3 using ehci-pci


[    1.868522] scsi 0:0:0:0: CD-ROM            TSSTcorp DVDR/RW TS-T632L 1117 PQ: 0 ANSI: 5


[    1.900765] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray


[    1.900768] cdrom: Uniform CD-ROM driver Revision: 3.20


[    1.900946] sr 0:0:0:0: Attached scsi CD-ROM sr0


[    1.901153] sr 0:0:0:0: Attached scsi generic sg0 type 5


[    1.901285] ata2: port disabled--ignoring


[    1.989808] usb 1-5: New USB device found, idVendor=058f, idProduct=6361


[    1.989813] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3


[    1.989816] usb 1-5: Product: USB Reader


[    1.989820] usb 1-5: Manufacturer:  


[    1.989824] usb 1-5: SerialNumber: 058F12M111B


[    2.100046] usb 1-6: new high-speed USB device number 4 using ehci-pci


[    2.100049] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)


[    2.108219] ata3.00: ATA-7: ST3320820AS, 3.AHG, max UDMA/100


[    2.108223] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)


[    2.124209] ata3.00: configured for UDMA/100


[    2.124386] scsi 2:0:0:0: Direct-Access     ATA      ST3320820AS      3.AH PQ: 0 ANSI: 5


[    2.124577] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)


[    2.124628] sd 2:0:0:0: Attached scsi generic sg1 type 0


[    2.124649] sd 2:0:0:0: [sda] Write Protect is off


[    2.124654] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00


[    2.124685] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


[    2.160116] firewire_core 0000:04:01.0: created device fw0: GUID 0011d8000140a3bd, S400


[    2.160615] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1a:92:eb:b6:3b


[    2.160623] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3


[    2.192998]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >


[    2.193751] sd 2:0:0:0: [sda] Attached SCSI disk


[    2.232442] usb 1-6: New USB device found, idVendor=0424, idProduct=2507


[    2.232449] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0


[    2.232729] hub 1-6:1.0: USB hub found


[    2.232809] hub 1-6:1.0: 7 ports detected


[    2.436028] ata4: SATA link down (SStatus 0 SControl 300)


[    2.604033] usb 1-8: new high-speed USB device number 6 using ehci-pci


[    2.736316] usb 1-8: New USB device found, idVendor=0424, idProduct=2507


[    2.736323] usb 1-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0


[    2.736608] hub 1-8:1.0: USB hub found


[    2.736683] hub 1-8:1.0: 7 ports detected


[    2.869301] Initializing USB Mass Storage driver...


[    2.869503] scsi4 : usb-storage 1-5:1.0


[    2.869642] usbcore: registered new interface driver usb-storage


[    2.869645] USB Mass Storage support registered.


[    2.936198] usb 1-6.1: new full-speed USB device number 7 using ehci-pci


[    3.034308] usb 1-6.1: New USB device found, idVendor=0471, idProduct=060f


[    3.034313] usb 1-6.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3


[    3.034317] usb 1-6.1: Product: BB+ Module(e.d)


[    3.034321] usb 1-6.1: Manufacturer:  


[    3.034325] usb 1-6.1: SerialNumber: NCLJ


[    3.120065] usb 1-6.3: new low-speed USB device number 8 using ehci-pci


[    3.218933] usb 1-6.3: New USB device found, idVendor=03f0, idProduct=100c


[    3.218938] usb 1-6.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0


[    3.218942] usb 1-6.3: Product: USB Multimedia Cordless Kit


[    3.218945] usb 1-6.3: Manufacturer: BTC


[    3.238752] usbcore: registered new interface driver usbhid


[    3.238757] usbhid: USB HID core driver


[    3.244057] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:0b.1/usb1/1-6/1-6.3/1-6.3:1.0/input/input2


[    3.244343] hid-generic 0003:03F0:100C.0001: input,hidraw0: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Kit] on usb-0000:00:0b.1-6.3/input0


[    3.245247] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:0b.1/usb1/1-6/1-6.3/1-6.3:1.1/input/input3


[    3.249059] hid-generic 0003:03F0:100C.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Kit] on usb-0000:00:0b.1-6.3/input1


[    3.292195] usb 1-6.7: new full-speed USB device number 9 using ehci-pci


[    3.412812] usb 1-6.7: New USB device found, idVendor=03f0, idProduct=171d


[    3.412817] usb 1-6.7: New USB device strings: Mfr=1, Product=2, SerialNumber=0


[    3.412821] usb 1-6.7: Product: HP Integrated Module


[    3.412825] usb 1-6.7: Manufacturer: Broadcom Corp


[    3.588034] usb 2-7: new full-speed USB device number 2 using ohci_hcd


[    3.800066] usb 2-7: New USB device found, idVendor=1926, idProduct=0001


[    3.800073] usb 2-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0


[    3.800077] usb 2-7: Product: Touchscreen


[    3.800081] usb 2-7: Manufacturer: Nextwindow


[    3.815135] input: Nextwindow Touchscreen as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.0/input/input4


[    3.815477] hid-generic 0003:1926:0001.0003: input,hidraw2: USB HID v1.00 Mouse [Nextwindow Touchscreen] on usb-0000:00:0b.0-7/input0


[    3.827221] hid-generic 0003:1926:0001.0004: hiddev0,hidraw3: USB HID v1.00 Device [Nextwindow Touchscreen] on usb-0000:00:0b.0-7/input1


[    3.839137] input: Nextwindow Touchscreen as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.2/input/input5


[    3.839276] hid-generic 0003:1926:0001.0005: input,hidraw4: USB HID v1.00 Keyboard [Nextwindow Touchscreen] on usb-0000:00:0b.0-7/input2


[    3.870844] scsi 4:0:0:0: Direct-Access     Generic  CF Reader        1.01 PQ: 0 ANSI: 0


[    3.871578] scsi 4:0:0:1: Direct-Access     Generic  SM/SD/MS Reader  1.00 PQ: 0 ANSI: 0


[    3.872609] sd 4:0:0:0: Attached scsi generic sg2 type 0


[    3.872853] sd 4:0:0:1: Attached scsi generic sg3 type 0


[    3.875707] sd 4:0:0:0: [sdb] Attached SCSI removable disk


[    3.876344] sd 4:0:0:1: [sdc] Attached SCSI removable disk


[    3.924694] usb 1-8.2: new high-speed USB device number 10 using ehci-pci


[    3.935716] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)


[    4.033310] usb 1-8.2: New USB device found, idVendor=0ace, idProduct=b215


[    4.033318] usb 1-8.2: New USB device strings: Mfr=16, Product=32, SerialNumber=0


[    4.033322] usb 1-8.2: Product: USB2.0 WLAN
[    4.033325] usb 1-8.2: Manufacturer: ZyDAS
[    4.120075] usb 1-8.3: new high-speed USB device number 11 using ehci-pci


[    4.221689] usb 1-8.3: New USB device found, idVendor=0c45, idProduct=62c0
[    4.221696] usb 1-8.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    4.221700] usb 1-8.3: Product: USB 2.0 Camera
[    4.221703] usb 1-8.3: Manufacturer: Sonix Technology Co., Ltd.
[    4.221706] usb 1-8.3: SerialNumber: SN0001
[    4.967571] init: ureadahead main process (287) terminated with status 5
[    6.062623] Adding 19530748k swap on /dev/sda6.  Priority:-1 extents:1 across:19530748k 
[    7.182670] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.340550] udevd[359]: starting version 175
[    8.561900] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[    9.502924] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   10.849158] type=1400 audit(1374345116.970:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=627 comm="apparmor_parser"
[   10.849447] type=1400 audit(1374345116.970:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=626 comm="apparmor_parser"
[   10.849880] type=1400 audit(1374345116.970:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=627 comm="apparmor_parser"
[   10.850186] type=1400 audit(1374345116.970:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=626 comm="apparmor_parser"
[   10.850289] type=1400 audit(1374345116.970:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=627 comm="apparmor_parser"
[   10.850603] type=1400 audit(1374345116.970:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=626 comm="apparmor_parser"
[   11.441898] init: failsafe main process (685) killed by TERM signal
[   12.907283] type=1400 audit(1374345119.026:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=801 comm="apparmor_parser"
[   12.908139] type=1400 audit(1374345119.030:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=801 comm="apparmor_parser"
[   12.908907] type=1400 audit(1374345119.030:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=801 comm="apparmor_parser"
[   13.399778] type=1400 audit(1374345119.518:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=800 comm="apparmor_parser"
[   13.863369] init: bluetooth main process (812) terminated with status 1
[   13.863415] init: bluetooth main process ended, respawning
[   14.006937] init: bluetooth main process (847) terminated with status 1
[   14.006990] init: bluetooth main process ended, respawning
[   14.044140] init: bluetooth main process (870) terminated with status 1
[   14.044193] init: bluetooth main process ended, respawning
[   14.081230] init: bluetooth main process (893) terminated with status 1
[   14.081280] init: bluetooth main process ended, respawning
[   14.123780] init: bluetooth main process (916) terminated with status 1
[   14.123831] init: bluetooth main process ended, respawning
[   14.161868] init: bluetooth main process (939) terminated with status 1
[   14.161919] init: bluetooth main process ended, respawning
[   14.199413] init: bluetooth main process (962) terminated with status 1
[   14.199466] init: bluetooth main process ended, respawning
[   14.237638] init: bluetooth main process (985) terminated with status 1
[   14.237689] init: bluetooth main process ended, respawning
[   14.273543] init: bluetooth main process (1008) terminated with status 1
[   14.273597] init: bluetooth main process ended, respawning
[   14.310664] init: bluetooth main process (1031) terminated with status 1
[   14.310714] init: bluetooth main process ended, respawning
[   14.380137] init: bluetooth main process (1054) terminated with status 1
[   14.380192] init: bluetooth respawning too fast, stopped
[   16.990607] init: udev-fallback-graphics main process (1182) terminated with status 1
[   19.700870] forcedeth 0000:00:14.0 eth0: no link during initialization
[   19.701267] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.701697] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.093084] audit_printk_skb: 45 callbacks suppressed
[   60.093091] type=1400 audit(1374345166.214:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2108 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  223.188218] usb 1-6.6: new high-speed USB device number 12 using ehci-pci
[  223.312954] usb 1-6.6: New USB device found, idVendor=0cf3, idProduct=9271
[  223.312968] usb 1-6.6: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[  223.312977] usb 1-6.6: Product: USB2.0 WLAN
[  223.312985] usb 1-6.6: Manufacturer: ATHEROS
[  223.312992] usb 1-6.6: SerialNumber: 12345
[  333.813326] type=1400 audit(1374345439.934:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=822 comm="cupsd" pid=822 comm="cupsd" capability=36  capname="block_suspend"




```

---

