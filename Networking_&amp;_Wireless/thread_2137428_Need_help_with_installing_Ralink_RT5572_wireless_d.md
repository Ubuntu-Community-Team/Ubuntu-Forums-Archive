---
title: "Need help with installing Ralink RT5572 wireless driver"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by cardu on 2013-04-20
Hi,

My Ubuntu is 12.10 x64. 
My wireless card is TP-LINK TL-WDN3200. 
I've downloaded my driver from here: [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5032](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5032). 
I've followed the 16-step compilation-installation guide from here: [http://www.ctheroux.com/2012/09/ralink-rt5572-based-wifi-usb-dongle-setup-on-ubuntu-12-04/](http://www.ctheroux.com/2012/09/ralink-rt5572-based-wifi-usb-dongle-setup-on-ubuntu-12-04/). 
I can see the driver being installed in the directory: /etc/Wireless/RT2870STA
But when I run iwconfig or ifconfig, I don't see my wireless interface. It is not recognized when I plug it and unplug it. 
When I run sudo modprobe rt2879sta, it says "module not found".
When I run lsusb, I see the device: Bus 001 Device 012: ID 148f:5572 Ralink Technology, Corp. 
What could be the problem?

Thanks

---

### Post by chili555 on 2013-04-20
The module it builds is called rt5572sta. What happens when you do:```
sudo modprobe rt5572sta
dmesg | grep rt5
iwconfig
```> I can see the driver being installed in the directory: /etc/Wireless/RT2870STADrivers are installed in /lib/modules/some_such. /etc is where configuration files are placed.

---

### Post by ahallubuntu on 2013-04-20
~

---

### Post by cardu on 2013-04-21
> **chili555 said:**
> The module it builds is called rt5572sta. What happens when you do:```
sudo modprobe rt5572sta
dmesg | grep rt5
iwconfig
```

Ok, sudo modprobe rt5572sta worked. But my adapter is still not working. This is the output from my iwconfig: 

```

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
eth0      no wireless extensions.
lo        no wireless extensions.

```

Also, after restart the ra0 entry disappears. Any other ideas?

---

### Post by chili555 on 2013-04-21
Let's get rt5572sta to load automagically:```
sudo su
modprobe rt5572sta
echo rt5572sta >> /etc/modules
exit
```Let's see what ra0 is doing behind the scenes:```
sudo iwlist ra0 scan
dmesg | grep -e rt5 -e ra0
```

---

### Post by cardu on 2013-04-21
Hi, 

Thank you for your support. Here is the output from your commands: 

```

$ sudo su
# modprobe rt5572sta
# echo rt5572sta >> /etc/modules 
# exit
$ sudo iwlist ra0 scan
ra0       Interface doesn't support scanning.
$ dmesg | grep -e rt5 -e ra0
$ 

```

So the last command did not returned any result. Any other ideas? 

Thank you very much.

---

### Post by chili555 on 2013-04-21
After you loaded rt5572sta, did the wireless interface ra0 show up?```
iwconfig
```Please reboot so we have a clean slate, with the device inserted and run:```
dmesg > cardu.txt
```Find the file cardu.txt in your user directory and copy and paste it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/) 

Give us the link so we can try to see what's going wrong.

Referring to the instructions you linked, can you confirm that you did this step?> 9. Edit the file os/linux/config.mk.  Set to y the two variables HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT.  Your file shall shows

```
# Support Wpa_Supplicant
# i.e. wpa_supplicant -Dralink
HAS_WPA_SUPPLICANT=[COLOR="#FF0000"]y[/COLOR]
# Support Native WpaSupplicant for Network Maganger
# i.e. wpa_supplicant -Dwext
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="#FF0000"]y[/COLOR]
```Would you please double-check the file?

---

### Post by cardu on 2013-04-21
Hi, 

I've rebooted many times. 
I confirm I've executed step #9. I've checked the file. Both are set to "y".
Here is the output to your commands:

iwconfig
ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


eth0      no wireless extensions.


lo        no wireless extensions.

I cannot attach to paste url because of this error:
An error has occurred in the Pastebin software. Please notify the administrators.

I could not attach it so I paste it here (sorry): 
 

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-27-generic (buildd@lamiak) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #46-Ubuntu SMP Mon Mar 25 19:58:17 UTC 2013 (Ubuntu 3.5.0-27.46-generic 3.5.7.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-27-generic root=UUID=3812f7df-8eb8-4c63-9e4b-7818cd182193 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000de31afff] usable
[    0.000000] BIOS-e820: [mem 0x00000000de31b000-0x00000000de892fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000de893000-0x00000000deb12fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000deb13000-0x00000000deb17fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000deb18000-0x00000000deb5afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000deb5b000-0x00000000df456fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000df457000-0x00000000df7f1fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df7f2000-0x00000000df7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./P67 Pro3, BIOS P3.20 05/11/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x21f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EBFFF uncachable
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FF0000000 write-back
[    0.000000]   2 base 210000000 mask FF8000000 write-back
[    0.000000]   3 base 218000000 mask FFC000000 write-back
[    0.000000]   4 base 21C000000 mask FFE000000 write-back
[    0.000000]   5 base 21E000000 mask FFF000000 write-back
[    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 256MB, type WB
[    0.000000] reg 2, base: 8448MB, range: 128MB, type WB
[    0.000000] reg 3, base: 8576MB, range: 64MB, type WB
[    0.000000] reg 4, base: 8640MB, range: 32MB, type WB
[    0.000000] reg 5, base: 8672MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 8176M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 6      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 512MB, type WB
[    0.000000] reg 5, base: 8688MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcd30-0x000fcd3f] mapped at [ffff8800000fcd30]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdf7fffff]
[    0.000000]  [mem 0x00000000-0xdf7fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xdf7fffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21effffff]
[    0.000000]  [mem 0x100000000-0x21effffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x21effffff @ [mem 0xdf7fa000-0xdf7fffff]
[    0.000000] RAMDISK: [mem 0x362ba000-0x37154fff]
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000deafa080 0007C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000deb03960 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000deafa190 097D0 (v02 ALASKA    A M I 00000014 INTL 20051117)
[    0.000000] ACPI: FACS 00000000deb11f80 00040
[    0.000000] ACPI: APIC 00000000deb03a58 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: ASF! 00000000deb03ad0 000A5 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: MCFG 00000000deb03b78 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000deb03bb8 004A6 (v01 Intel_ AoacTabl 00001000 INTL 20091112)
[    0.000000] ACPI: AAFT 00000000deb04060 000C2 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000deb04128 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000deb04160 00460 (v01 IdeRef IdeTable 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000deb045c0 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000deb04f70 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: BGRT 00000000deb05a08 0003C (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21effffff]
[    0.000000]   NODE_DATA [mem 0x21effc000-0x21effffff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216600000-ffff88021e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x21effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xde31afff]
[    0.000000]   node   0: [mem 0xdeb5b000-0xdf456fff]
[    0.000000]   node   0: [mem 0xdf7f2000-0xdf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x21effffff]
[    0.000000] On node 0 totalpages: 2087859
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 892005 pages, LIFO batch:31
[    0.000000]   Normal zone: 18368 pages used for memmap
[    0.000000]   Normal zone: 1157184 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000de31b000 - 00000000de893000
[    0.000000] PM: Registered nosave memory: 00000000de893000 - 00000000deb13000
[    0.000000] PM: Registered nosave memory: 00000000deb13000 - 00000000deb18000
[    0.000000] PM: Registered nosave memory: 00000000deb18000 - 00000000deb5b000
[    0.000000] PM: Registered nosave memory: 00000000df457000 - 00000000df7f2000
[    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] e820: [mem 0xdf800000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021ec00000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2053101
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-27-generic root=UUID=3812f7df-8eb8-4c63-9e4b-7818cd182193 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8123036k/8896512k available (6710k kernel code, 545076k absent, 228400k reserved, 6455k data, 932k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3292.612 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6585.22 BogoMIPS (lpj=13170448)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000019] Security Framework initialized
[    0.000027] AppArmor: AppArmor initialized
[    0.000028] Yama: becoming mindful.
[    0.000405] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001600] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002099] Mount-cache hash table entries: 256
[    0.002211] Initializing cgroup subsys cpuacct
[    0.002213] Initializing cgroup subsys memory
[    0.002219] Initializing cgroup subsys devices
[    0.002220] Initializing cgroup subsys freezer
[    0.002221] Initializing cgroup subsys blkio
[    0.002222] Initializing cgroup subsys perf_event
[    0.002239] CPU: Physical Processor ID: 0
[    0.002240] CPU: Processor Core ID: 0
[    0.002243] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002243] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002245] mce: CPU supports 9 MCE banks
[    0.002255] CPU0: Thermal monitoring enabled (TM1)
[    0.002260] using mwait in idle threads.
[    0.004071] ACPI: Core revision 20120320
[    0.012454] ftrace: allocating 25104 entries in 99 pages
[    0.021880] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.061437] CPU0: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz stepping 07
[    0.168462] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.168466] PEBS disabled due to CPU errata.
[    0.168467] ... version:                3
[    0.168468] ... bit width:              48
[    0.168469] ... generic registers:      8
[    0.168470] ... value mask:             0000ffffffffffff
[    0.168470] ... max period:             000000007fffffff
[    0.168471] ... fixed-purpose events:   3
[    0.168472] ... event mask:             00000007000000ff
[    0.168558] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.168604] Booting Node   0, Processors  #1 #2 #3 Ok.
[    0.208025] Brought up 4 CPUs
[    0.208027] Total of 4 processors activated (26340.89 BogoMIPS).
[    0.210539] devtmpfs: initialized
[    0.211297] EVM: security.selinux
[    0.211298] EVM: security.SMACK64
[    0.211299] EVM: security.capability
[    0.211325] PM: Registering ACPI NVS region [mem 0xde893000-0xdeb12fff] (2621440 bytes)
[    0.211352] PM: Registering ACPI NVS region [mem 0xdeb18000-0xdeb5afff] (274432 bytes)
[    0.211840] dummy: 
[    0.211868] RTC time: 16:48:38, date: 04/21/13
[    0.211891] NET: Registered protocol family 16
[    0.211948] Trying to unpack rootfs image as initramfs...
[    0.211991] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.211992] ACPI: bus type pci registered
[    0.212028] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.212030] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.216385] PCI: Using configuration type 1 for base access
[    0.216951] bio: create slab <bio-0> at 0
[    0.217000] ACPI: Added _OSI(Module Device)
[    0.217001] ACPI: Added _OSI(Processor Device)
[    0.217002] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.217003] ACPI: Added _OSI(Processor Aggregator Device)
[    0.218051] ACPI: EC: Look up EC in DSDT
[    0.219158] ACPI: Executed 1 blocks of module-level executable AML code
[    0.240530] ACPI: SSDT 00000000de844018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.240795] ACPI: Dynamic OEM Table Load:
[    0.240797] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.268322] ACPI: SSDT 00000000de845a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.268606] ACPI: Dynamic OEM Table Load:
[    0.268608] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.304110] ACPI: SSDT 00000000de843d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.304370] ACPI: Dynamic OEM Table Load:
[    0.304371] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.308369] ACPI: Interpreter enabled
[    0.308372] ACPI: (supports S0 S1 S3 S4 S5)
[    0.308389] ACPI: Using IOAPIC for interrupt routing
[    0.312281] ACPI: No dock devices found.
[    0.312284] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.312480] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.312742] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.312743] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.312745] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.312746] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.312748] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.312749] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.312750] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.312751] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.312752] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.312754] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.312755] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xfeafffff]
[    0.312773] PCI host bridge to bus 0000:00
[    0.312775] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.312776] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.312778] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.312779] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.312780] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.312781] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.312783] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.312784] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.312785] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.312786] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.312788] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
[    0.312794] pci 0000:00:00.0: [8086:0100] type 00 class 0x060000
[    0.312821] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.312845] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.312884] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.312906] pci 0000:00:16.0: reg 10: [mem 0xf620a000-0xf620a00f 64bit]
[    0.312977] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.313008] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.313027] pci 0000:00:1a.0: reg 10: [mem 0xf6207000-0xf62073ff]
[    0.313112] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.313137] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.313151] pci 0000:00:1b.0: reg 10: [mem 0xf6200000-0xf6203fff 64bit]
[    0.313215] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.313242] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.313372] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.313409] pci 0000:00:1c.4: [8086:1c18] type 01 class 0x060400
[    0.313484] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.313508] pci 0000:00:1c.5: [8086:1c1a] type 01 class 0x060400
[    0.313582] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.313606] pci 0000:00:1c.7: [8086:1c1e] type 01 class 0x060400
[    0.313681] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.313709] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.313728] pci 0000:00:1d.0: reg 10: [mem 0xf6206000-0xf62063ff]
[    0.313813] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.313837] pci 0000:00:1f.0: [8086:1c46] type 00 class 0x060100
[    0.313953] pci 0000:00:1f.2: [8086:1c00] type 00 class 0x01018f
[    0.313967] pci 0000:00:1f.2: reg 10: [io  0xf0d0-0xf0d7]
[    0.313975] pci 0000:00:1f.2: reg 14: [io  0xf0c0-0xf0c3]
[    0.313982] pci 0000:00:1f.2: reg 18: [io  0xf0b0-0xf0b7]
[    0.313990] pci 0000:00:1f.2: reg 1c: [io  0xf0a0-0xf0a3]
[    0.313997] pci 0000:00:1f.2: reg 20: [io  0xf090-0xf09f]
[    0.314005] pci 0000:00:1f.2: reg 24: [io  0xf080-0xf08f]
[    0.314048] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.314062] pci 0000:00:1f.3: reg 10: [mem 0xf6205000-0xf62050ff 64bit]
[    0.314081] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.314113] pci 0000:00:1f.5: [8086:1c08] type 00 class 0x010185
[    0.314127] pci 0000:00:1f.5: reg 10: [io  0xf070-0xf077]
[    0.314134] pci 0000:00:1f.5: reg 14: [io  0xf060-0xf063]
[    0.314142] pci 0000:00:1f.5: reg 18: [io  0xf050-0xf057]
[    0.314149] pci 0000:00:1f.5: reg 1c: [io  0xf040-0xf043]
[    0.314157] pci 0000:00:1f.5: reg 20: [io  0xf030-0xf03f]
[    0.314163] pci 0000:00:1f.5: reg 24: [io  0xf020-0xf02f]
[    0.314225] pci 0000:01:00.0: [10de:1201] type 00 class 0x030000
[    0.314233] pci 0000:01:00.0: reg 10: [mem 0xf4000000-0xf5ffffff]
[    0.314241] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xe7ffffff 64bit pref]
[    0.314249] pci 0000:01:00.0: reg 1c: [mem 0xe8000000-0xebffffff 64bit pref]
[    0.314255] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.314261] pci 0000:01:00.0: reg 30: [mem 0xf6000000-0xf607ffff pref]
[    0.314305] pci 0000:01:00.1: [10de:0e0c] type 00 class 0x040300
[    0.314313] pci 0000:01:00.1: reg 10: [mem 0xf6080000-0xf6083fff]
[    0.319978] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.319981] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.319983] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf60fffff]
[    0.319986] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xebffffff 64bit pref]
[    0.320055] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.320132] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.320151] pci 0000:03:00.0: reg 10: [io  0xd000-0xd0ff]
[    0.320184] pci 0000:03:00.0: reg 18: [mem 0xec104000-0xec104fff 64bit pref]
[    0.320205] pci 0000:03:00.0: reg 20: [mem 0xec100000-0xec103fff 64bit pref]
[    0.320294] pci 0000:03:00.0: supports D1 D2
[    0.320295] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.327959] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.327963] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.327971] pci 0000:00:1c.4:   bridge window [mem 0xec100000-0xec1fffff 64bit pref]
[    0.328037] pci 0000:04:00.0: [1b6f:7023] type 00 class 0x0c0330
[    0.328064] pci 0000:04:00.0: reg 10: [mem 0xf6100000-0xf6107fff 64bit]
[    0.328189] pci 0000:04:00.0: supports D1 D2
[    0.328190] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.335933] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.335940] pci 0000:00:1c.5:   bridge window [mem 0xf6100000-0xf61fffff]
[    0.336003] pci 0000:05:00.0: [1b21:1080] type 01 class 0x060401
[    0.336149] pci 0000:00:1c.7: PCI bridge to [bus 05-06]
[    0.336292] pci 0000:05:00.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.336318] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.336320] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.336321] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.336322] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.336360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.336461] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.336484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.336502] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.336521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    0.336540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08.BR40._PRT]
[    0.336570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.336661]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.336781]  pci0000:00: ACPI _OSC control (0x1c) granted
[    0.339531] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.339563] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.339593] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.339625] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.339655] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.339685] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.339715] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.339746] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.339808] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.339810] vgaarb: loaded
[    0.339811] vgaarb: bridge control possible 0000:01:00.0
[    0.339909] SCSI subsystem initialized
[    0.339938] libata version 3.00 loaded.
[    0.339951] ACPI: bus type usb registered
[    0.339962] usbcore: registered new interface driver usbfs
[    0.339967] usbcore: registered new interface driver hub
[    0.339977] usbcore: registered new device driver usb
[    0.340016] PCI: Using ACPI for IRQ routing
[    0.341406] PCI: pci_cache_line_size set to 64 bytes
[    0.341473] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
[    0.341474] e820: reserve RAM buffer [mem 0xde31b000-0xdfffffff]
[    0.341476] e820: reserve RAM buffer [mem 0xdf457000-0xdfffffff]
[    0.341477] e820: reserve RAM buffer [mem 0xdf800000-0xdfffffff]
[    0.341478] e820: reserve RAM buffer [mem 0x21f000000-0x21fffffff]
[    0.341533] NetLabel: Initializing
[    0.341534] NetLabel:  domain hash size = 128
[    0.341535] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.341542] NetLabel:  unlabeled traffic allowed by default
[    0.341576] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.341580] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.343584] Switching to clocksource hpet
[    0.347324] AppArmor: AppArmor Filesystem Enabled
[    0.347340] pnp: PnP ACPI init
[    0.347350] ACPI: bus type pnp registered
[    0.347521] pnp 00:00: [bus 00-3e]
[    0.347523] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.347524] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.347526] pnp 00:00: [io  0x0d00-0xffff window]
[    0.347527] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.347528] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.347530] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.347531] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.347532] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.347533] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.347535] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.347537] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.347538] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.347539] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.347541] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.347542] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.347543] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.347544] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.347546] pnp 00:00: [mem 0xe0000000-0xfeafffff window]
[    0.347547] pnp 00:00: [mem 0x00010000-0x0001ffff window]
[    0.347593] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.347608] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.347633] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.347636] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.347644] pnp 00:02: [io  0x0000-0x001f]
[    0.347645] pnp 00:02: [io  0x0081-0x0091]
[    0.347646] pnp 00:02: [io  0x0093-0x009f]
[    0.347655] pnp 00:02: [io  0x00c0-0x00df]
[    0.347657] pnp 00:02: [dma 4]
[    0.347667] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.347672] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.347683] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.347732] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.347744] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.347753] pnp 00:05: [io  0x002e-0x002f]
[    0.347754] pnp 00:05: [io  0x004e-0x004f]
[    0.347756] pnp 00:05: [io  0x0061]
[    0.347757] pnp 00:05: [io  0x0063]
[    0.347758] pnp 00:05: [io  0x0065]
[    0.347759] pnp 00:05: [io  0x0067]
[    0.347760] pnp 00:05: [io  0x0070]
[    0.347761] pnp 00:05: [io  0x0080]
[    0.347762] pnp 00:05: [io  0x0092]
[    0.347763] pnp 00:05: [io  0x00b2-0x00b3]
[    0.347764] pnp 00:05: [io  0x0680-0x069f]
[    0.347765] pnp 00:05: [io  0x0200-0x020f]
[    0.347767] pnp 00:05: [io  0xffff]
[    0.347768] pnp 00:05: [io  0xffff]
[    0.347769] pnp 00:05: [io  0x0400-0x0453]
[    0.347770] pnp 00:05: [io  0x0458-0x047f]
[    0.347771] pnp 00:05: [io  0x0500-0x057f]
[    0.347772] pnp 00:05: [io  0x164e-0x164f]
[    0.347797] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.347799] system 00:05: [io  0x0200-0x020f] has been reserved
[    0.347800] system 00:05: [io  0xffff] has been reserved
[    0.347802] system 00:05: [io  0xffff] has been reserved
[    0.347803] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.347804] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.347806] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.347807] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.347809] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.347814] pnp 00:06: [io  0x0070-0x0077]
[    0.347821] pnp 00:06: [irq 8]
[    0.347832] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.347848] pnp 00:07: [io  0x0454-0x0457]
[    0.347867] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.347869] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.347901] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.347903] pnp 00:08: [io  0x0290-0x029f]
[    0.347904] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.347923] system 00:08: [io  0x0290-0x029f] has been reserved
[    0.347925] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.348065] pnp 00:09: [io  0x0010-0x001f]
[    0.348067] pnp 00:09: [io  0x0022-0x003f]
[    0.348068] pnp 00:09: [io  0x0044-0x005f]
[    0.348069] pnp 00:09: [io  0x0062-0x0063]
[    0.348071] pnp 00:09: [io  0x0065-0x006f]
[    0.348072] pnp 00:09: [io  0x0072-0x007f]
[    0.348073] pnp 00:09: [io  0x0080]
[    0.348074] pnp 00:09: [io  0x0084-0x0086]
[    0.348075] pnp 00:09: [io  0x0088]
[    0.348076] pnp 00:09: [io  0x008c-0x008e]
[    0.348077] pnp 00:09: [io  0x0090-0x009f]
[    0.348078] pnp 00:09: [io  0x00a2-0x00bf]
[    0.348079] pnp 00:09: [io  0x00e0-0x00ef]
[    0.348081] pnp 00:09: [io  0x04d0-0x04d1]
[    0.348103] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.348105] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.348109] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.348114] pnp 00:0a: [irq 13]
[    0.348126] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.348281] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.348285] pnp 00:0b: [irq 4]
[    0.348286] pnp 00:0b: [dma 0 disabled]
[    0.348319] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.348457] pnp 00:0c: [mem 0xfed1c000-0xfed1ffff]
[    0.348458] pnp 00:0c: [mem 0xfed10000-0xfed17fff]
[    0.348459] pnp 00:0c: [mem 0xfed18000-0xfed18fff]
[    0.348460] pnp 00:0c: [mem 0xfed19000-0xfed19fff]
[    0.348462] pnp 00:0c: [mem 0xf8000000-0xfbffffff]
[    0.348463] pnp 00:0c: [mem 0xfed20000-0xfed3ffff]
[    0.348464] pnp 00:0c: [mem 0xfed90000-0xfed93fff]
[    0.348465] pnp 00:0c: [mem 0xfed45000-0xfed8ffff]
[    0.348466] pnp 00:0c: [mem 0xff000000-0xffffffff]
[    0.348469] pnp 00:0c: [mem 0xfee00000-0xfeefffff]
[    0.348470] pnp 00:0c: [mem 0xec200000-0xec200fff]
[    0.348502] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.348504] system 00:0c: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.348505] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.348506] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.348508] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.348509] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.348511] system 00:0c: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.348512] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.348513] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.348515] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.348516] system 00:0c: [mem 0xec200000-0xec200fff] has been reserved
[    0.348518] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.348611] pnp: PnP ACPI: found 13 devices
[    0.348612] ACPI: ACPI bus type pnp unregistered
[    0.354308] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02-02] add_size 1000
[    0.354311] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02-02] add_size 200000
[    0.354312] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02-02] add_size 200000
[    0.354351] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.354353] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.354354] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.354358] pci 0000:00:1c.0: BAR 14: assigned [mem 0xec300000-0xec4fffff]
[    0.354361] pci 0000:00:1c.0: BAR 15: assigned [mem 0xec500000-0xec6fffff 64bit pref]
[    0.354362] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.354364] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.354366] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.354368] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf60fffff]
[    0.354370] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xebffffff 64bit pref]
[    0.354373] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.354376] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.354383] pci 0000:00:1c.0:   bridge window [mem 0xec300000-0xec4fffff]
[    0.354387] pci 0000:00:1c.0:   bridge window [mem 0xec500000-0xec6fffff 64bit pref]
[    0.354395] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.354398] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.354404] pci 0000:00:1c.4:   bridge window [mem 0xec100000-0xec1fffff 64bit pref]
[    0.354409] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.354414] pci 0000:00:1c.5:   bridge window [mem 0xf6100000-0xf61fffff]
[    0.354422] pci 0000:05:00.0: PCI bridge to [bus 06-06]
[    0.354445] pci 0000:00:1c.7: PCI bridge to [bus 05-06]
[    0.354494] pci 0000:05:00.0: setting latency timer to 64
[    0.354499] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.354500] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.354502] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.354503] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.354504] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.354505] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.354507] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.354508] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.354509] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.354510] pci_bus 0000:00: resource 13 [mem 0x000e8000-0x000ebfff]
[    0.354512] pci_bus 0000:00: resource 14 [mem 0xe0000000-0xfeafffff]
[    0.354513] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.354514] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf60fffff]
[    0.354516] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xebffffff 64bit pref]
[    0.354517] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.354519] pci_bus 0000:02: resource 1 [mem 0xec300000-0xec4fffff]
[    0.354520] pci_bus 0000:02: resource 2 [mem 0xec500000-0xec6fffff 64bit pref]
[    0.354521] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.354522] pci_bus 0000:03: resource 2 [mem 0xec100000-0xec1fffff 64bit pref]
[    0.354524] pci_bus 0000:04: resource 1 [mem 0xf6100000-0xf61fffff]
[    0.354544] NET: Registered protocol family 2
[    0.354656] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.355121] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.356063] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.356180] TCP: Hash tables configured (established 524288 bind 65536)
[    0.356182] TCP: reno registered
[    0.356190] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.356212] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.356272] NET: Registered protocol family 1
[    0.387312] Freeing initrd memory: 14956k freed
[    0.395570] pci 0000:01:00.0: Boot video device
[    0.395634] PCI: CLS 64 bytes, default 64
[    0.395635] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.395637] software IO TLB [mem 0xda31b000-0xde31afff] (64MB) mapped at [ffff8800da31b000-ffff8800de31afff]
[    0.395961] audit: initializing netlink socket (disabled)
[    0.395973] type=2000 audit(1366562918.284:1): initialized
[    0.410972] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.412087] VFS: Disk quotas dquot_6.5.2
[    0.412110] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.412378] fuse init (API version 7.19)
[    0.412423] msgmni has been set to 15894
[    0.412643] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.412661] io scheduler noop registered
[    0.412662] io scheduler deadline registered (default)
[    0.412676] io scheduler cfq registered
[    0.412744] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.412844] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.412961] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.413050] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.413138] pcieport 0000:00:1c.7: irq 44 for MSI/MSI-X
[    0.413203] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.413204] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.413206] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    0.413207] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.413226] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.413231] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.413245] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.413246] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.413250] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.413264] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.413265] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.413269] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.413283] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
[    0.413284] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    0.413288] pcie_pme 0000:00:1c.7:pcie01: service driver pcie_pme loaded
[    0.413296] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.413304] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.413329] intel_idle: MWAIT substates: 0x1120
[    0.413330] intel_idle: v0.4 model 0x2A
[    0.413331] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.413381] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.413384] ACPI: Power Button [PWRB]
[    0.413405] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.413407] ACPI: Power Button [PWRF]
[    0.413471] ACPI: Requesting acpi_cpufreq
[    0.415924] ioremap: invalid physical address a0a601800000001
[    0.415926] ------------[ cut here ]------------
[    0.415929] WARNING: at /build/buildd/linux-3.5.0/arch/x86/mm/ioremap.c:83 __ioremap_caller+0x372/0x380()
[    0.415929] Hardware name: To Be Filled By O.E.M.
[    0.415930] Modules linked in:
[    0.415932] Pid: 1, comm: swapper/0 Not tainted 3.5.0-27-generic #46-Ubuntu
[    0.415933] Call Trace:
[    0.415937]  [<ffffffff81051bef>] warn_slowpath_common+0x7f/0xc0
[    0.415939]  [<ffffffff81051c4a>] warn_slowpath_null+0x1a/0x20
[    0.415941]  [<ffffffff81043492>] __ioremap_caller+0x372/0x380
[    0.415943]  [<ffffffff81d24a67>] ? bgrt_init+0x47/0x126
[    0.415946]  [<ffffffff813b4490>] ? acpi_get_table_with_size+0x5f/0xbe
[    0.415948]  [<ffffffff81d24a20>] ? acpi_hed_init+0x30/0x30
[    0.415950]  [<ffffffff810434f7>] ioremap_nocache+0x17/0x20
[    0.415951]  [<ffffffff81d24a67>] bgrt_init+0x47/0x126
[    0.415954]  [<ffffffff8100212a>] do_one_initcall+0x12a/0x180
[    0.415956]  [<ffffffff81cf2d44>] kernel_init+0x140/0x1c9
[    0.415958]  [<ffffffff81cf2588>] ? loglevel+0x31/0x31
[    0.415960]  [<ffffffff8168ad64>] kernel_thread_helper+0x4/0x10
[    0.415962]  [<ffffffff81cf2c04>] ? start_kernel+0x3dc/0x3dc
[    0.415963]  [<ffffffff8168ad60>] ? gs_change+0x13/0x13
[    0.415966] ---[ end trace 041b699bcaadf75a ]---
[    0.415967] GHES: HEST is not enabled!
[    0.416002] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.436370] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.457346] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.457500] Linux agpgart interface v0.103
[    0.458195] brd: module loaded
[    0.458559] loop: module loaded
[    0.458616] ata_piix 0000:00:1f.2: version 2.13
[    0.458629] ata_piix 0000:00:1f.2: MAP [
[    0.458630]  P0 P2 P1 P3 ]
[    0.458658] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.458793] scsi0 : ata_piix
[    0.458835] scsi1 : ata_piix
[    0.458933] ata1: SATA max UDMA/133 cmd 0xf0d0 ctl 0xf0c0 bmdma 0xf090 irq 19
[    0.458938] ata2: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf098 irq 19
[    0.458953] ata_piix 0000:00:1f.5: MAP [
[    0.458954]  P0 -- P1 -- ]
[    0.458982] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.459077] scsi2 : ata_piix
[    0.459108] scsi3 : ata_piix
[    0.459155] ata3: SATA max UDMA/133 cmd 0xf070 ctl 0xf060 bmdma 0xf030 irq 19
[    0.459159] ata4: SATA max UDMA/133 cmd 0xf050 ctl 0xf040 bmdma 0xf038 irq 19
[    0.459311] Fixed MDIO Bus: probed
[    0.459334] tun: Universal TUN/TAP device driver, 1.6
[    0.459335] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.459359] PPP generic driver version 2.4.2
[    0.459384] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.459411] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.459414] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.459418] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.459437] ehci_hcd 0000:00:1a.0: debug port 2
[    0.463307] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.463318] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf6207000
[    0.475250] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.475282] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.475285] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.475287] usb usb1: Product: EHCI Host Controller
[    0.475290] usb usb1: Manufacturer: Linux 3.5.0-27-generic ehci_hcd
[    0.475292] usb usb1: SerialNumber: 0000:00:1a.0
[    0.475362] hub 1-0:1.0: USB hub found
[    0.475364] hub 1-0:1.0: 2 ports detected
[    0.475407] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.475410] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.475413] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.475431] ehci_hcd 0000:00:1d.0: debug port 2
[    0.479302] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.479312] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf6206000
[    0.491200] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.491223] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.491226] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.491229] usb usb2: Product: EHCI Host Controller
[    0.491232] usb usb2: Manufacturer: Linux 3.5.0-27-generic ehci_hcd
[    0.491234] usb usb2: SerialNumber: 0000:00:1d.0
[    0.491299] hub 2-0:1.0: USB hub found
[    0.491301] hub 2-0:1.0: 2 ports detected
[    0.491332] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.491341] uhci_hcd: USB Universal Host Controller Interface driver
[    0.491368] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.491372] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    0.491492] xhci_hcd 0000:04:00.0: irq 17, io mem 0xf6100000
[    0.491561] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
[    0.491617] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.491618] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.491619] usb usb3: Product: xHCI Host Controller
[    0.491620] usb usb3: Manufacturer: Linux 3.5.0-27-generic xhci_hcd
[    0.491622] usb usb3: SerialNumber: 0000:04:00.0
[    0.491658] xHCI xhci_add_endpoint called for root hub
[    0.491659] xHCI xhci_check_bandwidth called for root hub
[    0.491670] hub 3-0:1.0: USB hub found
[    0.491678] hub 3-0:1.0: 2 ports detected
[    0.491714] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.491717] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    0.491736] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.491738] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.491739] usb usb4: Product: xHCI Host Controller
[    0.491740] usb usb4: Manufacturer: Linux 3.5.0-27-generic xhci_hcd
[    0.491741] usb usb4: SerialNumber: 0000:04:00.0
[    0.491772] xHCI xhci_add_endpoint called for root hub
[    0.491773] xHCI xhci_check_bandwidth called for root hub
[    0.491784] hub 4-0:1.0: USB hub found
[    0.491790] hub 4-0:1.0: 2 ports detected
[    0.491866] usbcore: registered new interface driver libusual
[    0.491882] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.494572] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.494576] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.494633] mousedev: PS/2 mouse device common for all mice
[    0.494705] rtc_cmos 00:06: RTC can wake from S4
[    0.494804] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.494830] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.494871] device-mapper: uevent: version 1.0.3
[    0.494905] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.494942] cpuidle: using governor ladder
[    0.494989] cpuidle: using governor menu
[    0.494990] EFI Variables Facility v0.08 2004-May-17
[    0.495109] ashmem: initialized
[    0.495182] TCP: cubic registered
[    0.495238] NET: Registered protocol family 10
[    0.495347] NET: Registered protocol family 17
[    0.495353] Key type dns_resolver registered
[    0.495487] PM: Hibernation image not present or could not be loaded.
[    0.495493] registered taskstats version 1
[    0.497645] Key type trusted registered
[    0.499217] Key type encrypted registered
[    0.501266]   Magic number: 9:51:844
[    0.501269]   hash matches /build/buildd/linux-3.5.0/drivers/base/power/main.c:428
[    0.501369] rtc_cmos 00:06: setting system clock to 2013-04-21 16:48:38 UTC (1366562918)
[    0.501931] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.501932] EDD information not available.
[    0.785704] ata4: SATA link down (SStatus 0 SControl 330)
[    0.797120] ata3: SATA link down (SStatus 0 SControl 330)
[    0.797140] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    0.926152] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    0.926157] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.926422] hub 1-1:1.0: USB hub found
[    0.926509] hub 1-1:1.0: 6 ports detected
[    1.037440] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.169357] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.169362] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.169626] hub 2-1:1.0: USB hub found
[    1.169717] hub 2-1:1.0: 8 ports detected
[    1.240857] usb 1-1.3: new high-speed USB device number 3 using ehci_hcd
[    1.248806] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 330)
[    1.248819] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[    1.248939] ata1.00: SATA link up 6.0 Gbps (SStatus 133 SControl 330)
[    1.248951] ata1.01: SATA link down (SStatus 0 SControl 330)
[    1.264938] ata2.00: ATAPI: HL-DT-ST DVDRAM GH20NS10, EL00, max UDMA/100
[    1.273270] ata1.00: ATA-8: Corsair Force 3 SSD, 5.02, max UDMA/133
[    1.273274] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.305223] ata1.00: configured for UDMA/133
[    1.305473] scsi 0:0:0:0: Direct-Access     ATA      Corsair Force 3  5.02 PQ: 0 ANSI: 5
[    1.305602] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.305648] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.305945] sd 0:0:0:0: [sda] Write Protect is off
[    1.305947] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.306035] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.307154]  sda: sda1 sda2 < sda5 >
[    1.307807] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.310835] ata2.01: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[    1.310839] ata2.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.324748] ata2.00: configured for UDMA/100
[    1.385576] ata2.01: configured for UDMA/133
[    1.392282] Refined TSC clocksource calibration: 3292.520 MHz.
[    1.392288] Switching to clocksource tsc
[    1.422278] usb 1-1.3: New USB device found, idVendor=0cf3, idProduct=1002
[    1.422283] usb 1-1.3: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[    1.422286] usb 1-1.3: Product: USB2.0 WLAN
[    1.422289] usb 1-1.3: Manufacturer: ATHER
[    1.422291] usb 1-1.3: SerialNumber: 12345
[    1.492038] usb 1-1.4: new high-speed USB device number 4 using ehci_hcd
[    1.499901] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL00 PQ: 0 ANSI: 5
[    1.600198] usb 1-1.4: New USB device found, idVendor=148f, idProduct=5572
[    1.600203] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.600206] usb 1-1.4: Product: 802.11 n WLAN
[    1.600208] usb 1-1.4: Manufacturer: Ralink
[    1.600211] usb 1-1.4: SerialNumber: 1.0
[    1.610124] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.610128] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.610276] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.610397] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.616851] scsi 1:0:1:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    1.616953] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    1.617022] sd 1:0:1:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.617235] sd 1:0:1:0: [sdb] Write Protect is off
[    1.617237] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.617306] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.669532]  sdb: sdb1 sdb2 < sdb5 sdb6 > sdb3
[    1.669991] sd 1:0:1:0: [sdb] Attached SCSI disk
[    1.670926] Freeing unused kernel memory: 932k freed
[    1.671004] Write protecting the kernel read-only data: 12288k
[    1.671449] usb 2-1.2: new high-speed USB device number 3 using ehci_hcd
[    1.673659] Freeing unused kernel memory: 1472k freed
[    1.675752] Freeing unused kernel memory: 1136k freed
[    1.685696] udevd[109]: starting version 175
[    1.702897] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.702998] r8169 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.703104] r8169 0000:03:00.0: eth0: RTL8168e/8111e at 0xffffc9000578c000, bc:5f:f4:65:2f:8a, XID 0c200000 IRQ 46
[    1.703106] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.761341] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    1.761344] EXT4-fs (sda5): write access will be enabled during recovery
[    1.764624] usb 2-1.2: New USB device found, idVendor=05e3, idProduct=0607
[    1.764629] usb 2-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.764632] usb 2-1.2: Product: USB2.0 Hub
[    1.765090] hub 2-1.2:1.0: USB hub found
[    1.765362] hub 2-1.2:1.0: 4 ports detected
[    1.796170] EXT4-fs (sda5): recovery complete
[    1.796692] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    1.838917] usb 2-1.8: new full-speed USB device number 4 using ehci_hcd
[    1.932949] usb 2-1.8: New USB device found, idVendor=1532, idProduct=0015
[    1.932954] usb 2-1.8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.932957] usb 2-1.8: Product: Razer Naga
[    1.932960] usb 2-1.8: Manufacturer: Razer
[    2.038517] usb 2-1.2.1: new low-speed USB device number 5 using ehci_hcd
[    2.136910] usb 2-1.2.1: New USB device found, idVendor=046d, idProduct=c22b
[    2.136915] usb 2-1.2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.136918] usb 2-1.2.1: Product: G110 G-keys
[    2.136921] usb 2-1.2.1: Manufacturer: LOGITECH
[    2.209923] usb 2-1.2.3: new low-speed USB device number 6 using ehci_hcd
[    2.307225] usb 2-1.2.3: New USB device found, idVendor=046d, idProduct=c22a
[    2.307228] usb 2-1.2.3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.307230] usb 2-1.2.3: Product: Gaming Keyboard G110
[    2.335112] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.350665] udevd[404]: starting version 175
[    2.431630] lp: driver loaded but no devices found
[    2.432522] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    2.432527] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.432528] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    2.432530] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    2.432533] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.432535] ACPI Warning: 0x0000000000000500-0x000000000000057f SystemIO conflicts with Region \GPR2 1 (20120320/utaddress-251)
[    2.432537] ACPI Warning: 0x0000000000000500-0x000000000000057f SystemIO conflicts with Region \GPIO 2 (20120320/utaddress-251)
[    2.432539] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.432540] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    2.456237] type=1400 audit(1366552120.454:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=691 comm="apparmor_parser"
[    2.456243] type=1400 audit(1366552120.454:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=583 comm="apparmor_parser"
[    2.456465] type=1400 audit(1366552120.454:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=691 comm="apparmor_parser"
[    2.456473] type=1400 audit(1366552120.454:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=583 comm="apparmor_parser"
[    2.456594] type=1400 audit(1366552120.454:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=691 comm="apparmor_parser"
[    2.456603] type=1400 audit(1366552120.454:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=583 comm="apparmor_parser"
[    2.457878] wmi: Mapper loaded
[    2.464368] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x25
[    2.467554] mei 0000:00:16.0: setting latency timer to 64
[    2.467603] mei 0000:00:16.0: irq 47 for MSI/MSI-X
[    2.471277] Compat-wireless backport release: compat-wireless-v3.6.2-1-snpc
[    2.471279] Backport based on linux-stable.git v3.6.2
[    2.471280] compat.git: linux-stable.git
[    2.475081] mei 0000:00:16.0: wd: failed to find the client
[    2.479003] usbhid 2-1.2.1:1.1: couldn't find an input interrupt endpoint
[    2.484462] cfg80211: Calling CRDA to update world regulatory domain
[    2.485176] usbcore: registered new interface driver usbhid
[    2.485177] usbhid: USB HID core driver
[    2.506526] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x25
[    2.507506] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x25
[    2.508188] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x25
[    2.508913] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.528988] input: Razer Razer Naga as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/input/input2
[    2.529047] hid-generic 0003:1532:0015.0001: input,hidraw0: USB HID v1.11 Mouse [Razer Razer Naga] on usb-0000:00:1d.0-1.8/input0
[    2.529336] input: Razer Razer Naga as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.1/input/input3
[    2.529460] hid-generic 0003:1532:0015.0002: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer Naga] on usb-0000:00:1d.0-1.8/input1
[    2.529564] input: LOGITECH G110 G-keys as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.0/input/input4
[    2.529631] hid-generic 0003:046D:C22B.0003: input,hiddev0,hidraw2: USB HID v1.00 Keypad [LOGITECH G110 G-keys] on usb-0000:00:1d.0-1.2.1/input0
[    2.529711] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.3/2-1.2.3:1.0/input/input5
[    2.529749] hid-generic 0003:046D:C22A.0004: input,hidraw3: USB HID v1.10 Keyboard [Gaming Keyboard G110] on usb-0000:00:1d.0-1.2.3/input0
[    2.530980] rtusb init rt2870 --->
[    2.531038] 
[    2.531038] 
[    2.531038] === pAd = ffffc9000581c000, size = 598032 ===
[    2.531038] 
[    2.531065] <-- RTMPAllocAdapterBlock, Status=0
[    2.531489] NVM is EFUSE
[    2.531607] usbcore: registered new interface driver rt2870
[    2.532217] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.3/2-1.2.3:1.1/input/input6
[    2.532355] hid-generic 0003:046D:C22A.0005: input,hiddev0,hidraw4: USB HID v1.10 Device [Gaming Keyboard G110] on usb-0000:00:1d.0-1.2.3/input1
[    2.553792] [drm] Initialized drm 1.1.0 20060810
[    2.618159] cfg80211: World regulatory domain updated:
[    2.618162] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    2.618163] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.618164] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.618165] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.618166] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.618167] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.624329] usb 1-1.3: reset high-speed USB device number 3 using ehci_hcd
[    2.650337] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[    2.676905] [drm] nouveau 0000:01:00.0: Detected an NVc0 generation card (0x0ce080a1)
[    2.682383] [drm] nouveau 0000:01:00.0: Checking PRAMIN for VBIOS
[    2.704957] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    2.704998] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    2.705028] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    2.705058] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    2.705087] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    2.705116] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    2.705144] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    2.705174] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    2.782252] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    2.782255] [drm] nouveau 0000:01:00.0: Using VBIOS from PRAMIN
[    2.782256] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    2.782258] [drm] nouveau 0000:01:00.0: Bios version 70.24.2e.00
[    2.782260] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[    2.782424] [drm] nouveau 0000:01:00.0: MXM: no VBIOS data, nothing to do
[    2.782425] [drm] nouveau 0000:01:00.0: DCB version 4.0
[    2.782426] [drm] nouveau 0000:01:00.0: DCB outp 00: 04000310 00000000
[    2.782428] [drm] nouveau 0000:01:00.0: DCB outp 01: 02011300 00000000
[    2.782429] [drm] nouveau 0000:01:00.0: DCB outp 02: 01011302 00020030
[    2.782430] [drm] nouveau 0000:01:00.0: DCB outp 03: 02022362 00020010
[    2.782430] [drm] nouveau 0000:01:00.0: DCB outp 04: 08033382 00020030
[    2.782431] [drm] nouveau 0000:01:00.0: DCB conn 00: 00000000
[    2.782433] [drm] nouveau 0000:01:00.0: DCB conn 01: 00001130
[    2.782434] [drm] nouveau 0000:01:00.0: DCB conn 02: 00002261
[    2.782435] [drm] nouveau 0000:01:00.0: DCB conn 03: 00010330
[    2.782438] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x6EB0
[    2.785221] usbcore: registered new interface driver carl9170
[    2.802349] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x75B0
[    2.836668] usb 1-1.3: driver   API: 1.9.6 2012-07-07 [1-1]
[    2.836672] usb 1-1.3: firmware API: 1.9.4 2011-06-30
[    2.836674] usb 1-1.3: Unprotected firmware image.
[    2.932256] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x8C88
[    2.932259] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x8C92
[    2.932316] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x8E71
[    2.932317] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0x8ED6
[    2.952099] [drm] nouveau 0000:01:00.0: 0x8ED6: Condition still not met after 20ms, skipping following opcodes
[    2.955049] [TTM] Zone  kernel: Available graphics memory: 4070766 kiB
[    2.955051] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    2.955052] [TTM] Initializing pool allocator
[    2.955055] [TTM] Initializing DMA pool allocator
[    2.955061] [drm] nouveau 0000:01:00.0: Detected 2048MiB VRAM (GDDR5)
[    2.956896] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    2.961568] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.961569] [drm] No driver support for vblank timestamp query.
[    3.184125] ath: EEPROM regdomain: 0x809c
[    3.184128] ath: EEPROM indicates we should expect a country code
[    3.184129] ath: doing EEPROM country->regdmn map search
[    3.184130] ath: country maps to regdmn code: 0x52
[    3.184131] ath: Country alpha2 being used: CN
[    3.184132] ath: Regpair used: 0x52
[    3.184133] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.184135] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184136] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.184137] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184138] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.184139] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184140] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.184141] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184142] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.184143] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184144] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.184145] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184145] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.184146] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184147] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.184148] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184149] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.184150] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184151] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.184152] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184153] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.184154] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.184155] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    3.184156] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    3.184157] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    3.184188] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.184189] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184190] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.184191] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184192] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.184193] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184194] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.184195] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184196] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.184197] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184205] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.184206] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184207] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.184208] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184209] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.184210] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184211] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.184212] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184213] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.184214] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184215] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.184216] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.184217] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.184218] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.184219] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.184220] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.184221] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    3.184222] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.187828] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    3.188003] cfg80211: Calling CRDA for country: CN
[    3.188998] Registered led device: carl9170-phy0::tx
[    3.189023] input: phy0 WPS Button as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/ieee80211/phy0/input15
[    3.190153] usb 1-1.3: Atheros AR9170 is registered as 'phy0'
[    3.190473] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.190475] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190476] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.190477] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190478] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.190479] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190480] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.190481] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190482] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.190483] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190484] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.190485] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190486] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.190487] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190488] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.190489] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190490] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.190491] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190492] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.190493] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190494] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.190495] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190496] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.190497] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190498] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.190499] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.190500] cfg80211: Disabling freq 2484 MHz
[    3.190502] cfg80211: Regulatory domain changed to country: CN
[    3.190502] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.190503] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    3.190504] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[    3.278255] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[    3.278259] [drm] nouveau 0000:01:00.0: 0: core 50MHz shader 101MHz memory 135MHz voltage 875mV
[    3.278261] [drm] nouveau 0000:01:00.0: 1: core 405MHz shader 810MHz memory 324MHz voltage 912mV
[    3.278263] [drm] nouveau 0000:01:00.0: 3: core 810MHz shader 1620MHz memory 2004MHz voltage 962mV-1075mV
[    3.278264] [drm] nouveau 0000:01:00.0: c: core 50MHz shader 101MHz memory 135MHz voltage 950mV fanspeed 40%
[    3.282102] [drm] nouveau 0000:01:00.0: MM: using COPY0 for buffer copies
[    3.449384] [drm] nouveau 0000:01:00.0: allocated 1680x1050 fb: 0x140000, bo ffff880212c5d000
[    3.449447] fbcon: nouveaufb (fb0) is primary device
[    3.449507] Console: switching to colour frame buffer device 210x65
[    3.449525] fb0: nouveaufb frame buffer device
[    3.449526] drm: registered panic notifier
[    3.449530] [drm] Initialized nouveau 1.0.0 20120316 for 0000:01:00.0 on minor 0
[    3.449558] hda_intel: Disabling MSI
[    3.449573] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[    4.334785] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    4.334858] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[    4.334973] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[    4.335093] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[    4.563004] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    4.600524] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[    4.614420] init: failsafe main process (983) killed by TERM signal
[    4.629679] ppdev: user-space parallel port driver
[    4.631902] Bluetooth: Core ver 2.16
[    4.631912] NET: Registered protocol family 31
[    4.631913] Bluetooth: HCI device and connection manager initialized
[    4.631914] Bluetooth: HCI socket layer initialized
[    4.631915] Bluetooth: L2CAP socket layer initialized
[    4.631917] Bluetooth: SCO socket layer initialized
[    4.633411] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.633413] Bluetooth: BNEP filters: protocol multicast
[    4.635663] Bluetooth: RFCOMM TTY layer initialized
[    4.635666] Bluetooth: RFCOMM socket layer initialized
[    4.635667] Bluetooth: RFCOMM ver 1.11
[    4.643913] type=1400 audit(1366552122.650:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1087 comm="apparmor_parser"
[    4.644217] type=1400 audit(1366552122.650:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1087 comm="apparmor_parser"
[    4.659517] type=1400 audit(1366552122.666:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1122 comm="apparmor_parser"
[    4.876120] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.876312] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.012364] [drm] nouveau 0000:01:00.0: 906e not supported yet
[    5.032100] r8169 0000:03:00.0: eth0: link down
[    5.032523] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.046471] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.385213] wlan0: authenticate with 58:6d:8f:82:cd:6f
[    7.469976] wlan0: send auth to 58:6d:8f:82:cd:6f (try 1/3)
[    7.471678] wlan0: authenticated
[    7.560223] wlan0: associate with 58:6d:8f:82:cd:6f (try 1/3)
[    7.563877] wlan0: RX AssocResp from 58:6d:8f:82:cd:6f (capab=0x11 status=0 aid=7)
[    7.568346] wlan0: associated
[    7.568763] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  524.772093] [drm] nouveau 0000:01:00.0: PFIFO: unknown status 0x40000000
[  911.926586] usb 1-1.3: USB disconnect, device number 3
[  911.931780] wlan0: deauthenticating from 58:6d:8f:82:cd:6f by local choice (reason=3)
[  911.935725] ieee80211 phy0: writing reg 0x1c36f0 (val 0x5000) failed (-5)
[  911.935733] ieee80211 phy0: writing reg 0x1c36f0 (val 0x5000) failed (-5)
[  911.939707] cfg80211: All devices are disconnected, going to restore regulatory settings
[  911.939713] cfg80211: Restoring regulatory settings
[  911.939717] cfg80211: Calling CRDA to update world regulatory domain
[  911.972683] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  911.972688] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972691] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  911.972693] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972695] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  911.972697] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972700] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  911.972702] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972704] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  911.972706] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972708] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  911.972710] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972712] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  911.972715] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972717] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  911.972719] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972721] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  911.972723] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972725] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  911.972727] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972729] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  911.972732] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972734] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  911.972736] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972738] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  911.972740] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  911.972742] cfg80211: Disabling freq 2484 MHz
[  911.972746] cfg80211: World regulatory domain updated:
[  911.972747] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  911.972749] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  911.972752] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  911.972754] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  911.972756] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  911.972758] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  912.437086] usb 1-1.4: USB disconnect, device number 4
[  912.437173] rtusb_disconnect: unregister usbnet usb-0000:00:1a.0-1.4
[  912.437177] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
[  912.442021]  RTUSB disconnect successfully
[ 1331.308115] usb 1-1.4: new high-speed USB device number 5 using ehci_hcd
[ 1331.416140] usb 1-1.4: New USB device found, idVendor=148f, idProduct=5572
[ 1331.416145] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1331.416148] usb 1-1.4: Product: 802.11 n WLAN
[ 1331.416151] usb 1-1.4: Manufacturer: Ralink
[ 1331.416153] usb 1-1.4: SerialNumber: 1.0
[ 1331.417888] 
[ 1331.417888] 
[ 1331.417888] === pAd = ffffc9000a901000, size = 598032 ===
[ 1331.417888] 
[ 1331.417950] <-- RTMPAllocAdapterBlock, Status=0
[ 1331.418479] NVM is EFUSE

---

### Post by chili555 on 2013-04-21
> [ 7.385213][COLOR="#FF0000"] wlan0[/COLOR]: authenticate with 58:6d:8f:82:cd:6f
[ 7.469976] wlan0: send auth to 58:6d:8f:82:cd:6f (try 1/3)
[ 7.471678] wlan0: authenticated
[ 7.560223] wlan0: associate with 58:6d:8f:82:cd:6f (try 1/3)
[ 7.563877] wlan0: RX AssocResp from 58:6d:8f:82:cd:6f (capab=0x11 status=0 aid=7)
[ 7.568346] wlan0: associated
[ 7.568763] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes readyWhat explains this? Do you have an internal wireless device that's connected just perfectly? Isn't your wireless interface ra0?

:confused:

---

### Post by cardu on 2013-04-25
I've used my neighbour wireless USB stick to post here. But all configurations were done without it, only with mine. Anyway, I gave up and installed back my Windows. It is too hard. Will wait for better days for Linux to come. It should be far easier to install a driver.

---

### Post by kevron2 on 2013-09-05
It appears RT5572 doesn't work with 13.04.  I can install the driver and get ra0 to appear, and I can even scan for networks.  But I timeout while trying to get a IP over DHCP.

---

### Post by chili555 on 2013-09-05
> **kevron2 said:**
> It appears RT5572 doesn't work with 13.04.  I can install the driver and get ra0 to appear, and I can even scan for networks.  But I timeout while trying to get a IP over DHCP.May we see: ```
lsusb
lsmod | grep -e rt2 -e rt5
```Thanks.

---

### Post by kevron2 on 2013-09-06
```

kev@powerpatch:~$ lsusb
lsBus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
...
Bus 001 Device 056: ID 148f:5572 Ralink Technology, Corp. 
...
kev@powerpatch:~$ lsmod | grep -e rt2 -e rt5
rt5572sta             810831  1 



```

---

### Post by chili555 on 2013-09-06
When you built the driver for 13.04, was it from the same files you previously used to build for a previous version? If so, did you precede the 'make' command with 'make clean'? Did you make the needed changes to os/linux/config.mk?

I wonder if we wouldn't be better off to go straight to backports. In kernel 3.10 and later, your device is covered by rt2800usb. I suggest you 'sudo make uninstall' on rt5572sta and then I suggest you download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:
```
cd Desktop/backports-3.11-rc3-1/
make defconfig-wifi
make
sudo make install
sudo modprobe -r rt5572sta
sudo modprobe rt2800usb

```Any improvement?

---

### Post by kevron2 on 2013-09-06
rt2800usb works.  Thanks!

---

