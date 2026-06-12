---
title: "Help for Micromax CDMA 2000 HSIA modem"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by drpjkurian on 2010-10-12
My dear friends
I badly require help for configuring my colleague's Micromax CDMA 2000 HSIA modem. He is using Ubuntu Jaunty jackalope
I did the following procedures

1.I installed modeswitch
2. I installed udev packages
3. I installed Wvdial
4. I installed gnome ppp
My terminal output are as follows
```
repertory@repertory-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05c6:2001 Qualcomm, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
repertory@repertory-desktop:~$ dmesg | grep -e "modem" -e "tty"
[    0.004000] console [tty0] enabled
[    1.597190] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.597615] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

Wvdial cof is as follows
```
[Dialer Defaults]
Modem Type = Analog Modem
Phone = *99***1#	
Username = ""
Password = ""
Modem = /dev/ttyS0
Init1 = ATZ
Init2 = at+cgdcont=1,"ip","bsnlnet"
Stupid Mode = 1
```

With regards
Dr Kurian

---

### Post by dineshs on 2010-10-12
pl edit grub as follows```
sudo gedit /boot/grub/menu.lst
```
add the line marked blue as shown
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid        51b2f214-7a9d-47e5-b654-f45edbea0504 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=51b2f214-7a9d-47e5-b654-f45edbea0504 ro quiet splash [COLOR="Blue"]usbserial.vendor=0x05c6 usbserial.product=0x2001 [/COLOR]
initrd        /boot/initrd.img-2.6.28-11-generic 
quiet
```restart and post the output of
```
dmesg | grep -e "modem" -e "tty"
```

---

### Post by drpjkurian on 2010-10-15
Hi dinesh
Sorry for the delay. Well I tried the above mentioned step, But was unsuccessful. the output of the bash script is as follows
```
repertory@repertory-desktop:~$ dmesg | grep -e "modem" -e "tty"
[    0.004000] console [tty0] enabled
[    1.590805] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.591226] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```

I think I may have to ask my colleague to forget about Linux. Well He was a recent convert from Windows....

---

### Post by drpjkurian on 2010-10-15
Hi Dinesh
I tried this bash command ```
dmesg
``` and i got this output 
```
[    8.497815] usb-storage: device scan complete
[    8.500794] scsi 2:0:0:0: CD-ROM            CDMA2000 Modem            2.31 PQ
```

and ```
[  612.568964] usbserial: `0×05c6' invalid for parameter `vendor'
[  624.775282] usbserial: `0×05c6' invalid for parameter `vendor'
```

will it help you solve the issue?

---

### Post by dineshs on 2010-10-15
> [  624.775282] usbserial: `0×05c6' invalid for parameter `vendor'Can you copy the lines?I doubt this character × (it is a lowercase x)

---

### Post by drpjkurian on 2010-10-16
Hi dinesh
I am attaching herewith the copy of the whole dmseg command. Astonished to inform you that the lines ```
[  612.568964] usbserial: `0×05c6' invalid for parameter `vendor'
[  624.775282] usbserial: `0×05c6' invalid for parameter `vendor'
``` are missing

dmseg output is as follows
```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-19-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #65-Ubuntu SMP Thu Sep 16 14:14:28 UTC 2010 (Ubuntu 2.6.28-19.65-generic)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe40000 (usable)
[    0.000000]  BIOS-e820: 000000001fe40000 - 000000001fe50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fe50000 - 000000001ff00000 (ACPI NVS)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x1fe40 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fe40000 (usable)
[    0.000000]  modified: 000000001fe40000 - 000000001fe50000 (ACPI data)
[    0.000000]  modified: 000000001fe50000 - 000000001ff00000 (ACPI NVS)
[    0.000000] kernel direct mapping tables up to 1fe40000 @ 10000-16000
[    0.000000] RAMDISK: 1f6fa000 - 1fe2f39c
[    0.000000] ACPI: RSDP 000F77A0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FE40000, 0030 (r1 INTEL  D845GVS1 20050316 MSFT       97)
[    0.000000] ACPI: FACP 1FE40200, 0074 (r1 INTEL  D845GVS1 20050316 MSFT       97)
[    0.000000] ACPI: DSDT 1FE40370, 415D (r1 INTEL  D845GVS1      10A MSFT  100000D)
[    0.000000] ACPI: FACS 1FE50000, 0040
[    0.000000] ACPI: APIC 1FE40300, 0068 (r1 INTEL  D845GVS1 20050316 MSFT       97)
[    0.000000] ACPI: ASF! 1FE444D0, 0084 (r16 AMIASF I845GASF        1 MSFT  100000D)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fe40000
[    0.000000]   low ram: 00000000 - 1fe40000
[    0.000000]   bootmap 00012000 - 00015fc8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fe40000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [001f6fa000 - 001fe2f39c]          RAMDISK ==> [001f6fa000 - 001fe2f39c]
[    0.000000]   #5 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fe40
[    0.000000]   HighMem  0x0001fe40 -> 0x0001fe40
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0001fe40
[    0.000000] On node 0 totalpages: 130501
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125539 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:e0100000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129480
[    0.000000] Kernel command line: root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro quiet splash usbserial.vendor=0x05c6 usbserial.product=0x2001 
[    0.000000] Unknown boot option `usbserial.vendor=0x05c6': ignoring
[    0.000000] Unknown boot option `usbserial.product=0x2001': ignoring
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2800.079 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2612480 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 499576k/522496k available (4116k kernel code, 22236k reserved, 2199k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe0640000 - 0xff3fe000   ( 493 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdfe40000   ( 510 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05051d1 - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05051d1   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.15 BogoMIPS (lpj=11200316)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: Hyper-Threading is disabled
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016941] SMP alternatives: switching to UP code
[    0.152034] ACPI: Core revision 20080926
[    0.157839] ACPI: Checking initramfs for custom DSDT
[    0.467920] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.507613] CPU0: Intel(R) Celeron(R) CPU 2.80GHz stepping 09
[    0.508002] Brought up 1 CPUs
[    0.508002] Total of 1 processors activated (5600.15 BogoMIPS).
[    0.508002] CPU0 attaching NULL sched-domain.
[    0.508002] net_namespace: 776 bytes
[    0.508002] Booting paravirtualized kernel on bare hardware
[    0.508002] Time:  4:12:19  Date: 10/16/10
[    0.508002] regulator: core version 0.5
[    0.508002] NET: Registered protocol family 16
[    0.508002] EISA bus registered
[    0.508002] ACPI: bus type pci registered
[    0.508002] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.508002] PCI: Using configuration type 1 for base access
[    0.508002] ACPI: EC: Look up EC in DSDT
[    0.515571] ACPI: Interpreter enabled
[    0.515580] ACPI: (supports S0 S1 S4 S5)
[    0.515604] ACPI: Using IOAPIC for interrupt routing
[    0.522776] ACPI: No dock devices found.
[    0.522793] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.522870] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.522940] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.522947] pci 0000:00:02.0: reg 14 32bit mmio: [0xffa80000-0xffafffff]
[    0.523052] pci 0000:00:1d.0: reg 20 io port: [0xe800-0xe81f]
[    0.523106] pci 0000:00:1d.1: reg 20 io port: [0xe880-0xe89f]
[    0.523159] pci 0000:00:1d.2: reg 20 io port: [0xec00-0xec1f]
[    0.523222] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa7fc00-0xffa7ffff]
[    0.523267] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.523273] pci 0000:00:1d.7: PME# disabled
[    0.523325] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.523326] * this clock source is slow. If you are sure your timer does not have
[    0.523327] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.523369] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.523377] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.523381] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.523402] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.523410] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.523417] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.523424] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.523431] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.523439] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.523490] pci 0000:00:1f.3: reg 20 io port: [0xe000-0xe01f]
[    0.523534] pci 0000:00:1f.5: reg 10 io port: [0xe400-0xe4ff]
[    0.523541] pci 0000:00:1f.5: reg 14 io port: [0xe080-0xe0bf]
[    0.523548] pci 0000:00:1f.5: reg 18 32bit mmio: [0xffa7f800-0xffa7f9ff]
[    0.523555] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xffa7f400-0xffa7f4ff]
[    0.523578] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.523583] pci 0000:00:1f.5: PME# disabled
[    0.523633] pci 0000:01:08.0: reg 10 32bit mmio: [0xff8ff000-0xff8fffff]
[    0.523640] pci 0000:01:08.0: reg 14 io port: [0xdc00-0xdc3f]
[    0.523672] pci 0000:01:08.0: supports D1 D2
[    0.523674] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.523679] pci 0000:01:08.0: PME# disabled
[    0.523713] pci 0000:00:1e.0: transparent bridge
[    0.523718] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.523723] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff8fffff]
[    0.523728] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe6a00000-0xe6afffff]
[    0.523738] bus 00 -> node 0
[    0.523748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.523947] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.525518] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.525733] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.525943] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.526151] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.526358] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.526567] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.526776] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.526984] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.527148] ACPI: Power Resource [URP1] (off)
[    0.527198] ACPI: Power Resource [URP2] (off)
[    0.527246] ACPI: Power Resource [FDDP] (off)
[    0.527299] ACPI: Power Resource [LPTP] (off)
[    0.527446] ACPI: WMI: Mapper loaded
[    0.527760] SCSI subsystem initialized
[    0.527840] libata version 3.00 loaded.
[    0.527925] usbcore: registered new interface driver usbfs
[    0.527952] usbcore: registered new interface driver hub
[    0.528036] usbcore: registered new device driver usb
[    0.528235] PCI: Using ACPI for IRQ routing
[    0.528349] Bluetooth: Core ver 2.13
[    0.528349] NET: Registered protocol family 31
[    0.528349] Bluetooth: HCI device and connection manager initialized
[    0.528349] Bluetooth: HCI socket layer initialized
[    0.528349] NET: Registered protocol family 8
[    0.528349] NET: Registered protocol family 20
[    0.528349] NetLabel: Initializing
[    0.528349] NetLabel:  domain hash size = 128
[    0.528349] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.528349] NetLabel:  unlabeled traffic allowed by default
[    0.528349] AppArmor: AppArmor Filesystem Enabled
[    0.528349] pnp: PnP ACPI init
[    0.528349] ACPI: bus type pnp registered
[    0.533729] pnp: PnP ACPI: found 12 devices
[    0.533733] ACPI: ACPI bus type pnp unregistered
[    0.533739] PnPBIOS: Disabled by ACPI PNP
[    0.533761] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.533770] system 00:0a: ioport range 0x400-0x47f has been reserved
[    0.533773] system 00:0a: ioport range 0x680-0x6ff has been reserved
[    0.533776] system 00:0a: ioport range 0x480-0x4bf has been reserved
[    0.533780] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.533783] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.533791] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.533794] system 00:0b: iomem range 0xc0000-0xdffff could not be reserved
[    0.533797] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.533800] system 00:0b: iomem range 0x100000-0x1fefffff could not be reserved
[    0.568598] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.568604] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.568610] pci 0000:00:1e.0:   MEM window: 0xff800000-0xff8fffff
[    0.568615] pci 0000:00:1e.0:   PREFETCH window: 0x000000e6a00000-0x000000e6afffff
[    0.568633] pci 0000:00:1e.0: setting latency timer to 64
[    0.568638] bus: 00 index 0 io port: [0x00-0xffff]
[    0.568641] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.568643] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.568646] bus: 01 index 1 mmio: [0xff800000-0xff8fffff]
[    0.568648] bus: 01 index 2 mmio: [0xe6a00000-0xe6afffff]
[    0.568651] bus: 01 index 3 io port: [0x00-0xffff]
[    0.568653] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.568667] NET: Registered protocol family 2
[    0.568847] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.569174] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.569271] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.569373] TCP: Hash tables configured (established 16384 bind 16384)
[    0.569376] TCP reno registered
[    0.569603] NET: Registered protocol family 1
[    0.569785] checking if image is initramfs... it is
[    1.072050] Switched to high resolution mode on CPU 0
[    1.215176] Freeing initrd memory: 7380k freed
[    1.215316] cpufreq: No nForce2 chipset.
[    1.215523] audit: initializing netlink socket (disabled)
[    1.215549] type=2000 audit(1287202339.212:1): initialized
[    1.223952] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.225418] VFS: Disk quotas dquot_6.5.1
[    1.225511] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.226368] fuse init (API version 7.10)
[    1.226495] msgmni has been set to 990
[    1.226809] alg: No test for stdrng (krng)
[    1.226836] io scheduler noop registered
[    1.226839] io scheduler anticipatory registered
[    1.226841] io scheduler deadline registered
[    1.226878] io scheduler cfq registered (default)
[    1.226899] pci 0000:00:02.0: Boot video device
[    1.226992] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    1.230639] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.230652] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.230823] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.230827] ACPI: Power Button (FF) [PWRF]
[    1.230893] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.230902] ACPI: Sleep Button (CM) [SLPB]
[    1.231125] processor ACPI_CPU:00: registered as cooling_device0
[    1.231130] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.233521] isapnp: Scanning for PnP cards...
[    1.585214] isapnp: No Plug & Play device found
[    1.586950] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.587051] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.587474] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.588524] brd: module loaded
[    1.588955] loop: module loaded
[    1.589110] Fixed MDIO Bus: probed
[    1.589118] PPP generic driver version 2.4.2
[    1.589198] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.589250] Driver 'sd' needs updating - please use bus_type methods
[    1.589263] Driver 'sr' needs updating - please use bus_type methods
[    1.589358] ata_piix 0000:00:1f.1: version 2.12
[    1.589374] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.589391] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.589452] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.589612] scsi0 : ata_piix
[    1.589776] scsi1 : ata_piix
[    1.591572] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.591577] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.752427] ata1.00: ATA-6: WDC WD400BB-22JHC0, 05.01C05, max UDMA/100
[    1.752431] ata1.00: 78165360 sectors, multi 16: LBA 
[    1.760377] ata1.00: configured for UDMA/100
[    2.108302] ata2.01: ATAPI: LITE-ON CD-RW SOHR-5239V, 2$0B, max UDMA/33
[    2.140260] ata2.01: configured for UDMA/33
[    2.140927] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-22JH 05.0 PQ: 0 ANSI: 5
[    2.141102] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.141127] sd 0:0:0:0: [sda] Write Protect is off
[    2.141130] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.141166] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.141283] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.141305] sd 0:0:0:0: [sda] Write Protect is off
[    2.141308] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.141343] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.141349]  sda: sda1 sda2 < sda5 >
[    2.171023] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.171105] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.172085] scsi 1:0:1:0: CD-ROM            LITE-ON  CD-RW SOHR-5239V 2$0B PQ: 0 ANSI: 5
[    2.177362] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    2.177369] Uniform CD-ROM driver Revision: 3.20
[    2.177524] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    2.177606] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    2.178327] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.178369] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.178401] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.178406] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.178521] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.182446] ehci_hcd 0000:00:1d.7: debug port 1
[    2.182454] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.182475] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa7fc00
[    2.196011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.196129] usb usb1: configuration #1 chosen from 1 choice
[    2.196168] hub 1-0:1.0: USB hub found
[    2.196183] hub 1-0:1.0: 6 ports detected
[    2.196357] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.196387] uhci_hcd: USB Universal Host Controller Interface driver
[    2.196451] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.196463] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.196466] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.196551] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.196592] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[    2.196707] usb usb2: configuration #1 chosen from 1 choice
[    2.196744] hub 2-0:1.0: USB hub found
[    2.196758] hub 2-0:1.0: 2 ports detected
[    2.196890] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.196901] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.196905] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.196980] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.197017] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
[    2.197121] usb usb3: configuration #1 chosen from 1 choice
[    2.197155] hub 3-0:1.0: USB hub found
[    2.197167] hub 3-0:1.0: 2 ports detected
[    2.197295] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.197306] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.197310] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.197386] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.197422] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[    2.197537] usb usb4: configuration #1 chosen from 1 choice
[    2.197583] hub 4-0:1.0: USB hub found
[    2.197595] hub 4-0:1.0: 2 ports detected
[    2.197798] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.197802] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.198545] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.198757] mice: PS/2 mouse device common for all mice
[    2.198950] rtc_cmos 00:02: RTC can wake from S4
[    2.199004] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.199037] rtc0: alarms up to one month, 114 bytes nvram
[    2.199146] device-mapper: uevent: version 1.0.3
[    2.199341] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.199447] device-mapper: multipath: version 1.0.5 loaded
[    2.199451] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.199602] EISA: Probing bus 0 at eisa.0
[    2.199642] EISA: Detected 0 cards.
[    2.199697] cpuidle: using governor ladder
[    2.199700] cpuidle: using governor menu
[    2.200439] TCP cubic registered
[    2.200549] NET: Registered protocol family 10
[    2.201117] lo: Disabled Privacy Extensions
[    2.201539] NET: Registered protocol family 17
[    2.201580] Bluetooth: L2CAP ver 2.11
[    2.201582] Bluetooth: L2CAP socket layer initialized
[    2.201585] Bluetooth: SCO (Voice Link) ver 0.6
[    2.201587] Bluetooth: SCO socket layer initialized
[    2.201661] Bluetooth: RFCOMM socket layer initialized
[    2.201675] Bluetooth: RFCOMM TTY layer initialized
[    2.201677] Bluetooth: RFCOMM ver 1.10
[    2.201768] Using IPI No-Shortcut mode
[    2.201921] registered taskstats version 1
[    2.202026]   Magic number: 14:814:211
[    2.202117] rtc_cmos 00:02: setting system clock to 2010-10-16 04:12:21 UTC (1287202341)
[    2.202121] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.202123] EDD information not available.
[    2.202857] Freeing unused kernel memory: 532k freed
[    2.202992] Write protecting the kernel text: 4120k
[    2.203035] Write protecting the kernel read-only data: 1524k
[    2.248375] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.873974] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    2.874095] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    2.874099] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.874161] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.893851] e100 0000:01:08.0: PME# disabled
[    2.902700] e100: eth0: e100_probe: addr 0xff8ff000, irq 20, MAC addr 00:16:76:26:66:9c
[    3.066642] usb 2-2: configuration #1 chosen from 1 choice
[    3.431596] usbcore: registered new interface driver hiddev
[    3.444962] input: USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
[    3.445570] generic-usb 0003:1267:0201.0001: input,hidraw0: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:1d.0-2/input0
[    3.445598] usbcore: registered new interface driver usbhid
[    3.445603] usbhid: v2.6:USB HID core driver
[    3.545352] PM: Starting manual resume from disk
[    3.545358] PM: Resume from partition 8:5
[    3.545360] PM: Checking hibernation image.
[    3.545602] PM: Resume from disk failed.
[    3.549510] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.549516] EXT3-fs: write access will be enabled during recovery.
[    4.028722] kjournald starting.  Commit interval 5 seconds
[    4.028748] EXT3-fs: sda1: orphan cleanup on readonly fs
[    4.028756] ext3_orphan_cleanup: deleting unreferenced inode 1508380
[    4.028790] EXT3-fs: sda1: 1 orphan inode deleted
[    4.028793] EXT3-fs: recovery complete.
[    4.064753] EXT3-fs: mounted filesystem with ordered data mode.
[    9.605493] udev: starting version 141
[    9.848340] parport_pc 00:08: reported by Plug and Play ACPI
[    9.848422] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    9.923118] Linux agpgart interface v0.103
[    9.986431] intel_rng: Firmware space is locked read-only. If you can't or
[    9.986434] intel_rng: don't want to disable this in firmware setup, and if
[    9.986436] intel_rng: you are certain that your system has a functional
[    9.986437] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    9.997467] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    9.997703] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[   10.000173] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   10.014106] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.322703] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.400961] iTCO_vendor_support: vendor-support=0
[   10.403230] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.403425] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   10.403570] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.619463] ppdev: user-space parallel port driver
[   10.854339] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.854519] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   11.176016] intel8x0_measure_ac97_clock: measured 55104 usecs
[   11.176021] intel8x0: clocking to 48000
[   11.369296] lp0: using parport0 (interrupt-driven).
[   11.495941] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k
[   12.066353] EXT3 FS on sda1, internal journal
[   13.160763] type=1505 audit(1287202352.457:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1831
[   13.224215] type=1505 audit(1287202352.521:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1835
[   13.224474] type=1505 audit(1287202352.521:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1835
[   13.224584] type=1505 audit(1287202352.521:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1835
[   13.224660] type=1505 audit(1287202352.521:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1835
[   13.398643] type=1505 audit(1287202352.693:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1840
[   13.398996] type=1505 audit(1287202352.693:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1840
[   13.438384] type=1505 audit(1287202352.733:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1844
[   16.028380] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.028385] Bluetooth: BNEP filters: protocol multicast
[   16.053277] Bridge firewalling registered
[   17.895472] [drm] Initialized drm 1.1.0 20060810
[   17.947270] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.947279] pci 0000:00:02.0: setting latency timer to 64
[   17.947536] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   17.952660] [drm:i915_setparam] *ERROR* unknown parameter 4
[   17.952706] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   18.600525] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   20.720952] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.724136] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   20.725118] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.056034] eth0: no IPv6 routers present
[ 1847.972761] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 1848.139747] usb 4-2: configuration #1 chosen from 1 choice
[ 1848.667521] Initializing USB Mass Storage driver...
[ 1848.669764] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1848.670242] usbcore: registered new interface driver usb-storage
[ 1848.670249] USB Mass Storage support registered.
[ 1848.673713] usb-storage: device found at 2
[ 1848.673718] usb-storage: waiting for device to settle before scanning
[ 1853.673620] usb-storage: device scan complete
[ 1853.676633] scsi 2:0:0:0: CD-ROM            CDMA2000 Modem            2.31 PQ: 0 ANSI: 2
[ 1853.735605] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 1853.735787] sr 2:0:0:0: Attached scsi CD-ROM sr1
[ 1853.735917] sr 2:0:0:0: Attached scsi generic sg2 type 5
[ 1853.901571] sr 2:0:0:0: ioctl_internal_command return code = 8000002
[ 1853.901576]    : Sense Key : No Sense [current] 
[ 1853.901581]    : Add. Sense: No additional sense information
[ 1853.908576] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1853.908592] sr: Sense Key : No Sense [current] 
[ 1853.908597] sr: Add. Sense: No additional sense information
[ 1854.268500] sr 2:0:0:0: ioctl_internal_command return code = 8000002
[ 1854.268505]    : Sense Key : No Sense [current] 
[ 1854.268510]    : Add. Sense: No additional sense information
[ 1854.275499] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1854.275516] sr: Sense Key : No Sense [current] 
[ 1854.275520] sr: Add. Sense: No additional sense information
[ 1856.833083] sr 2:0:0:0: ioctl_internal_command return code = 8000002
[ 1856.833088]    : Sense Key : No Sense [current] 
[ 1856.833093]    : Add. Sense: No additional sense information
[ 1856.843387] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1856.843405] sr: Sense Key : No Sense [current] 
[ 1856.843410] sr: Add. Sense: No additional sense information
[ 1857.866925] sr 2:0:0:0: ioctl_internal_command return code = 8000002
[ 1857.866931]    : Sense Key : No Sense [current] 
[ 1857.866935]    : Add. Sense: No additional sense information
[ 1857.873919] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1857.873935] sr: Sense Key : No Sense [current] 
[ 1857.873939] sr: Add. Sense: No additional sense information
[ 1857.880917] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 28 00 00 00 00 10 00
[ 1857.880932] sr: Sense Key : No Sense [current] 
[ 1857.880937] sr: Add. Sense: No additional sense information
[ 1857.887918] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 20 00 00 00 00 18 00
[ 1857.887934] sr: Sense Key : No Sense [current] 
[ 1857.887939] sr: Add. Sense: No additional sense information
[ 1857.904890] sr 2:0:0:0: ioctl_internal_command return code = 8000002
[ 1857.904895]    : Sense Key : No Sense [current] 
[ 1857.904900]    : Add. Sense: No additional sense information
[ 1857.911912] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1857.911928] sr: Sense Key : No Sense [current] 
[ 1857.911932] sr: Add. Sense: No additional sense information
[ 1857.932930] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1857.936922] ISOFS: changing to secondary root
```

---

### Post by dineshs on 2010-10-17
> **dineshs said:**
> pl edit grub as follows```
sudo gedit /boot/grub/menu.lst
```
add the line marked blue as shown
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid        51b2f214-7a9d-47e5-b654-f45edbea0504 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=51b2f214-7a9d-47e5-b654-f45edbea0504 ro quiet splash [COLOR="Blue"]usbserial.vendor=0x05c6 usbserial.product=0x2001 [/COLOR]
initrd        /boot/initrd.img-2.6.28-11-generic 
quiet
```restart and post the output of
```
dmesg | grep -e "modem" -e "tty"
```
What I suggest is run *sudo gedit /boot/grub/menu.lst* then copy the blue portion from above and paste it in your menu.lst in correct place so that it looks similar above
The character x shold be a lowercase x and not ×
Also please post the result of ```
usb-devices
```
Sorry for the delay.I was out of station

---

### Post by Prince.Paul.K on 2010-10-18
Hi,

I do had the same problem, but at last I succeeded in connecting the Modem.

Your Modem is identified.
> Bus 003 Device 002: ID 05c6:2001 Qualcomm, Inc.

Update the usb-modeswitch-data. You can get the new version from here [http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20100826.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20100826.tar.bz2")

If not kindly 
```

sudo gedit /etc/usb_modeswitch.d/05c6:2001

```

Paste the following as the content
```

########################################################
# D-Link DWM-162-U5, Micromax MMX 300c

DefaultVendor= 0x05c6
DefaultProduct=0x2001

TargetVendor=  0x1e0e
TargetProductList="ce16,cefe"

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

```

Then do a restart.

I am pasting my .wvdial.conf of my system for your easy reference.

```

[Dialer Defaults]
Modem = /dev/gsmmodem
ISDN = off
Modem Type = USB Modem
Baud = 115200
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = 
Init4 = 
Init5 = 
Init6 = 
Init7 = 
Init8 = 
Init9 = 
Phone = #777
Phone1 = 
Phone2 = 
Phone3 = 
Phone4 = 
Dial Prefix = 
Dial Attempts = 1
Dial Command = ATM0L0DT
Ask Password = off
Password = 91********
Username = 91********
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on
;Minimize = on
;Dock = on
# Do NOT edit this file by hand!

```

Please ensure you modem is /dev/gsmmodem not /dev/ttyUSB0 1/2

For the details visit the link here for the installation of usb-modeswitch [http://www.draisberghof.de/usb_modeswitch/]("http://www.draisberghof.de/usb_modeswitch/")

---

### Post by drpjkurian on 2010-10-20
Hi Paul
I was really overjoyed to see your response, and I tried it immediately but to utter dismay I was not able to make that modem working by following your instruction.

---

### Post by drpjkurian on 2010-10-20
Dear Dinesh

I followed your instruction and pasted only the blue words. 
the command ```
usb devices
``` gave an ouput of command not found

---

### Post by dineshs on 2010-10-20
> **drpjkurian said:**
> Dear Dinesh

```
usb devices
``` 
The command is ```
usb-devices
```
Also post the output of```
sudo gedit /boot/grub/menu.lst
```

---

### Post by drpjkurian on 2010-10-29
Hi Dinesh
Sorry for the delay in response..
Well the output of the following commands are
```
usb devices
```
Please see the attachment

the output of the command```
sudo gedit /boot/grub/menu.lst
``` is as follows

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7bde9647-8f07-4b3d-a629-cfd6c2d28f87

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-19-generic
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro quiet splash usbserial.vendor=0x05c6 usbserial.product=0x2001   
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bde9647-8f07-4b3d-a629-cfd6c2d28f87 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7bde9647-8f07-4b3d-a629-cfd6c2d28f87
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by dineshs on 2010-10-30
Now try ```
 dmesg | grep -e "modem" -e "tty"

```
You should get something like [COLOR="Blue"]converter now attached to ttyUSB0[/COLOR]
If not 
Edit your grub  ```
sudo gedit /boot/grub/menu.lst
``` Delete what we added[COLOR="Blue"] usbserial.vendor=0x05c6 usbserial.product=0x2001[/COLOR]
Then run ```
sudo modprobe usbserial vendor=0x05c6 product=0x2001
```
Restart and see if dmesg | grep -e "modem" -e "tty" shows the result

---

### Post by parkarvv on 2010-11-14
Pl help me to connect to net using a Micromax MMX 200c USB cdma modem on Ubuntu 10.04.

The O/Ps of the commands are

vishal@VP:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- ATQ0 V1 E1 S0=0 &C1
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &D2 -- ATQ0 V1 E1 S0=0 &D2
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: AnyDATA.NET Inc.
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 +FCLASS=0"



vishal@VP:~$ sudo cat /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Password = <Your Password>
; Username = <Your Login Name>
Modem = /dev/ttyUSB0
Baud = 9600

[Dialer bsnl]
Init1 = ATZ
Stupid Mode = 1
Phone = #777
PPPD Options = lock noauth refuse-eap refuse-chap refuse-mschap
Modem = /dev/ttyUSB1
Username = cdma
Dial Command = ATDT
Password = cdma


vishal@VP:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 +FCLASS=0
ATQ0 V1 E1 S0=0 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.



vishal@VP:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    4.769007] USB Serial support registered for GSM modem (1-port)
[    4.769166] option 6-1:1.0: GSM modem (1-port) converter detected
[    4.769391] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
[    4.769410] option 6-1:1.1: GSM modem (1-port) converter detected
[    4.769584] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
[    4.769601] option 6-1:1.2: GSM modem (1-port) converter detected
[    4.769771] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2
[    4.769795] option: v0.7.2:USB Driver for GSM modems
[   34.348428] usb 6-2: PocketPC PDA converter now attached to ttyUSB3
[  134.764168] ipaq ttyUSB3: ipaq_open - failed submitting read urb, error -19
[  134.764648] ipaq ttyUSB3: PocketPC PDA converter now disconnected from ttyUSB3
vishal@VP:~$ 


Pl help.

---

### Post by alexfish on 2010-11-14
Hi

the wvdial command "sudo wvdial" only dials up the default

therfore remove the " ; " highlighted, then  after the = edit details for your connection

Code:

sudo gedit /etc/wvdial.conf


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 +FCLASS=0
Modem Type = Analog Modem
[COLOR=Blue];[/COLOR] Phone = [COLOR=Blue]<Target Phone Number>[/COLOR]
ISDN = 0
[COLOR=Blue];[/COLOR] Password = [COLOR=Blue]<Your Password>[/COLOR]
[COLOR=Blue]; [/COLOR]Username = [COLOR=Blue]<Your Login Name>[/COLOR]
Modem = /dev/ttyUSB0
Baud = 9600

the normal baud rate for cdma "Baud = 460800"

the [Dialer Defaults] can be changed to suit IE [Dialer [COLOR=Blue]myconnection[/COLOR]]

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Example:

[Dialer [COLOR=Black]myconnection[/COLOR]]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 +FCLASS=0
Modem Type = Analog Modem
Phone = [COLOR=Blue]1234[/COLOR]
ISDN = 0
Password = [COLOR=Blue]mypassword[/COLOR]
Username = [COLOR=Blue]username[/COLOR]
Modem = /dev/ttyUSB0
Baud = [COLOR=Blue]460800[/COLOR]



then called

sudo wvdial [COLOR=Blue]myconnection

[COLOR=Black]Note if there is a pin number then add

AT+CPIN=<pinnumber> 

use at intit1 or init2

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Example:
[/COLOR][/COLOR]
[Dialer [COLOR=Black]myconnection[/COLOR]]
Init1 = ATZ
[COLOR=Blue]Init2 = AT+CPIN=1234[/COLOR]
Init3 = ATQ0 V1 E1 S0=0 +FCLASS=0
Modem Type = Analog Modem
Phone = [COLOR=Blue]1234[/COLOR]
ISDN = 0
Password = [COLOR=Blue]mypassword[/COLOR]
Username = [COLOR=Blue]username[/COLOR]
Modem = /dev/ttyUSB0
Baud = [COLOR=Blue]460800[/COLOR]
[COLOR=Blue][COLOR=Black]

Also if problem connecting can add this line to the wvdial.conf
[COLOR=Blue]
[/COLOR][/COLOR]Stupid Mode = 1[/COLOR]

---

