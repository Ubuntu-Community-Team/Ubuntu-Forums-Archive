---
title: "Dell Studio 15 Hardy Heron wirelss stopped working"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by wonderbriefs on 2008-12-11
I have a Dell Studio 1535 with Hardy Heron preinstalled. WThe wireless network worked fine when I got it. I even brought it to other locations and successfully connected to other wifi networks.

Today while at home, my cable dropped out, then came back. Every other computer in the house recovered their connections but my Dell laptop.

When I click on the wireless network icon, it can see my network but will not connect. I type my password, it tries to connect, and fails.

I click on "restricted hardware" and it claims that the Broadcom driver isn't enabled. I click to enable it, but the box will never check. I get prompted to reboot, without the box having a check mark. I reboot, and have the same issue. Sometimes while trying to connect, the laptop freezes all together with the caps lock key blinking.

I run lspci and get this...
Network Controller: Broadcom Corporation BCM4312 802.11/g
I run iwconfig and get this...
"no wireless extensions"

What's going on?

---

### Post by wonderbriefs on 2008-12-11
I believe this had the "wl" driver before, I don't know why it's now showing up as broadcom.

Can anyone tell me how to get it back to the wl driver?

---

### Post by Ayuthia on 2008-12-11
The wl module is the Broadcom wireless module.  You might try the following and see if you can connect:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```

If that works and then you lose it again when you reboot, please post the results of:
```
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e wl
cat /etc/modules|grep -e b43 -e ssb -e wl
```This will help us see what needs to be added.  My guess is that the wl module is just not being loaded and just needs to be added to /etc/modules so that it will load.

---

### Post by wonderbriefs on 2008-12-11
that didn't work. It still finds my network, prompts for password, and fails to connect, in an endless loop until I hit cancel.

Output of ```
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e wl
```
returns "#replaced by b43 and ssb"
Command ```
cat /etc/modules|grep -e b43 -e ssb -e wl
``` renders no output at all.

---

### Post by Ayuthia on 2008-12-11
You might try to reset the modem and possibly change the channel.  If you don't mind, can you also post the results of:
```
sudo iwlist scan
```
If the only thing that has changed recently is the cable going out, hopefully that will fix the problem.

However, the flashing caps lock light is a kernel panic.  If that happens, please go into Ubuntu (after you reboot) and either attach the /var/log/dmesg.0 file or take a look at the file and see what error message came up for the kernel panic.  It might provide some clues that might help.

Can you also post your uname -a info?  I just want to see which kernel version you are using.

---

### Post by wonderbriefs on 2008-12-11
```
chris@dell-desktop:~$ sudo iwlist scan
[sudo] password for chris: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:2F:08:08:64
                    ESSID:"superhappyfuntime"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-35 dBm  Noise level:-21 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

```

I'm not sure what I'm looking for in my dmesg.o file so here's the entire thing. Maybe something jumps out at you.
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-22-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 18:32:42 UTC 2008 (Ubuntu 2.6.24-22.45-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f65c800 (usable)
[    0.000000]  BIOS-e820: 000000007f65c800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 521820) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521820
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521820
[    0.000000] On node 0 totalpages: 521820
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290160 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBAF0 checksum 0
[    0.000000] ACPI: RSDP 000FBAF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7F65E200, 0064 (r1 DELL    M09     27D8071E ASL        61)
[    0.000000] ACPI: FACP 7F65E09C, 00F4 (r4 DELL    M09     27D8071E ASL        61)
[    0.000000] ACPI: DSDT 7F65E800, 521C (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7F66D000, 0040
[    0.000000] ACPI: HPET 7F65E300, 0038 (r1 DELL    M09            1 ASL        61)
[    0.000000] ACPI: APIC 7F65E400, 0068 (r1 DELL    M09     27D8071E ASL        47)
[    0.000000] ACPI: MCFG 7F65E3C0, 003E (r16 DELL    M09     27D8071E ASL        61)
[    0.000000] ACPI: SLIC 7F65E49C, 0024 (r1 DELL    M09     27D8071E ASL        61)
[    0.000000] ACPI: OSFR 7F65DA00, 0086 (r1 DELL    M09     27D8071E ASL        61)
[    0.000000] ACPI: BOOT 7F65DFC0, 0028 (r1 DELL    M09     27D8071E ASL        61)
[    0.000000] ACPI: SSDT 7F65C9FA, 04D4 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517744
[    0.000000] Kernel command line: root=UUID=b84a9588-c175-41e8-b18c-587a158ee251 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.262 MHz processor.
[    8.799011] Console: colour VGA+ 80x25
[    8.799014] console [tty0] enabled
[    8.799308] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.799589] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.878642] Memory: 2057396k/2087280k available (2177k kernel code, 28644k reserved, 1005k data, 368k init, 1169776k highmem)
[    8.878648] virtual kernel memory layout:
[    8.878649]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.878650]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.878651]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.878652]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.878652]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.878653]       .data : 0xc0320704 - 0xc041bdc4   (1005 kB)
[    8.878654]       .text : 0xc0100000 - 0xc0320704   (2177 kB)
[    8.878657] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.878695] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    8.878828] hpet clockevent registered
[    8.958798] Calibrating delay using timer specific routine.. 3995.06 BogoMIPS (lpj=7990138)
[    8.958817] Security Framework initialized
[    8.958823] SELinux:  Disabled at boot.
[    8.958836] AppArmor: AppArmor initialized
[    8.958839] Failure registering capabilities with primary security module.
[    8.958846] Mount-cache hash table entries: 512
[    8.958960] Initializing cgroup subsys ns
[    8.958964] Initializing cgroup subsys cpuacct
[    8.958974] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[    8.958980] monitor/mwait feature present.
[    8.958981] using mwait in idle threads.
[    8.958985] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.958987] CPU: L2 cache: 2048K
[    8.958990] CPU: Physical Processor ID: 0
[    8.958991] CPU: Processor Core ID: 0
[    8.958993] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[    8.959001] Compat vDSO mapped to ffffe000.
[    8.959012] Checking 'hlt' instruction... OK.
[    8.975135] SMP alternatives: switching to UP code
[    8.976558] Early unpacking initramfs... done
[    9.264338] ACPI: Core revision 20070126
[    9.264375] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.306923] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    9.306937] SMP alternatives: switching to SMP code
[    9.307556] Booting processor 1/1 eip 3000
[    9.317763] Initializing CPU#1
[    9.394598] Calibrating delay using timer specific routine.. 3990.49 BogoMIPS (lpj=7980980)
[    9.394603] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[    9.394608] monitor/mwait feature present.
[    9.394611] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.394612] CPU: L2 cache: 2048K
[    9.394614] CPU: Physical Processor ID: 0
[    9.394615] CPU: Processor Core ID: 1
[    9.394616] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[    9.395082] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    9.395102] Total of 2 processors activated (7985.55 BogoMIPS).
[    9.395303] ENABLING IO-APIC IRQs
[    9.395491] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.542629] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    9.562632] Brought up 2 CPUs
[    9.562654] CPU0 attaching sched-domain:
[    9.562656]  domain 0: span 03
[    9.562658]   groups: 01 02
[    9.562660] CPU1 attaching sched-domain:
[    9.562662]  domain 0: span 03
[    9.562663]   groups: 02 01
[    9.562848] net_namespace: 64 bytes
[    9.562858] Booting paravirtualized kernel on bare hardware
[    9.563251] Time: 22:43:39  Date: 12/11/08
[    9.563275] NET: Registered protocol family 16
[    9.563428] EISA bus registered
[    9.563431] ACPI: bus type pci registered
[    9.574041] PCI: PCI BIOS revision 2.10 entry at 0xfac86, last bus=14
[    9.574043] PCI: Using configuration type 1
[    9.574056] Setting up standard PCI resources
[    9.581430] ACPI: EC: Look up EC in DSDT
[    9.645136] ACPI: SSDT 7F66D080, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    9.645286] ACPI: Interpreter enabled
[    9.645289] ACPI: (supports S0 S3 S4 S5)
[    9.645300] ACPI: Using IOAPIC for interrupt routing
[    9.664520] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.665564] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.665568] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    9.667078] PCI: Transparent bridge - 0000:00:1e.0
[    9.667129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.667531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    9.667670] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.667775] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.667879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    9.667983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    9.677415] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    9.677516] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    9.677615] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *3
[    9.677705] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11) *0, disabled.
[    9.677805] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    9.677906] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    9.678006] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    9.678097] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    9.678221] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.678244] pnp: PnP ACPI init
[    9.678251] ACPI: bus type pnp registered
[    9.714747] pnpacpi: exceeded the max number of mem resources: 12
[    9.714927] pnp: PnP ACPI: found 13 devices
[    9.714929] ACPI: ACPI bus type pnp unregistered
[    9.714932] PnPBIOS: Disabled by ACPI PNP
[    9.715108] PCI: Using ACPI for IRQ routing
[    9.715111] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.810419] NET: Registered protocol family 8
[    9.810421] NET: Registered protocol family 20
[    9.810448] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.810452] hpet0: 3 64-bit timers, 14318180 Hz
[    9.811483] AppArmor: AppArmor Filesystem Enabled
[    9.814412] Time: tsc clocksource has been installed.
[    9.814419] Switched to high resolution mode on CPU 0
[    9.814511] Switched to high resolution mode on CPU 1
[    9.830392] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    9.830399] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    9.830403] system 00:0a: ioport range 0x900-0x97f has been reserved
[    9.830406] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    9.830408] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[    9.830410] system 00:0a: ioport range 0x1008-0x100f has been reserved
[    9.830415] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    9.830417] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[    9.830419] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[    9.830421] system 00:0b: ioport range 0x1060-0x107f has been reserved
[    9.830424] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    9.830426] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    9.830428] system 00:0b: ioport range 0x1010-0x102f has been reserved
[    9.830430] system 00:0b: ioport range 0x809-0x809 has been reserved
[    9.830435] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    9.830437] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    9.830440] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    9.830442] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    9.830444] system 00:0c: iomem range 0x100000-0x7f65c7ff could not be reserved
[    9.830447] system 00:0c: iomem range 0x7f65c800-0x7f6fffff could not be reserved
[    9.830449] system 00:0c: iomem range 0x7f700000-0x7f7fffff could not be reserved
[    9.830451] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    9.830454] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    9.830456] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    9.830459] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    9.830461] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    9.860804] PCI: Bridge: 0000:00:1c.0
[    9.860805]   IO window: disabled.
[    9.860811]   MEM window: disabled.
[    9.860815]   PREFETCH window: disabled.
[    9.860821] PCI: Bridge: 0000:00:1c.1
[    9.860822]   IO window: disabled.
[    9.860828]   MEM window: f6c00000-f6cfffff
[    9.860833]   PREFETCH window: disabled.
[    9.860839] PCI: Bridge: 0000:00:1c.3
[    9.860841]   IO window: d000-dfff
[    9.860847]   MEM window: f6a00000-f6bfffff
[    9.860852]   PREFETCH window: f0000000-f01fffff
[    9.860858] PCI: Bridge: 0000:00:1c.5
[    9.860859]   IO window: disabled.
[    9.860864]   MEM window: f6900000-f69fffff
[    9.860869]   PREFETCH window: disabled.
[    9.860875] PCI: Bridge: 0000:00:1e.0
[    9.860876]   IO window: disabled.
[    9.860882]   MEM window: f6800000-f68fffff
[    9.860886]   PREFETCH window: disabled.
[    9.860917] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.860924] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.860949] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    9.860954] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.860979] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[    9.860985] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    9.861009] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[    9.861014] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    9.861029] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.861038] NET: Registered protocol family 2
[    9.898378] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.898570] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.898953] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.899157] TCP: Hash tables configured (established 131072 bind 65536)
[    9.899159] TCP reno registered
[    9.910441] checking if image is initramfs... it is
[   10.475751] Freeing initrd memory: 7324k freed
[   10.475887] Simple Boot Flag at 0x79 set to 0x1
[   10.476402] audit: initializing netlink socket (disabled)
[   10.476415] audit(1229035419.429:1): initialized
[   10.476595] highmem bounce pool size: 64 pages
[   10.478194] VFS: Disk quotas dquot_6.5.1
[   10.478256] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.478375] io scheduler noop registered
[   10.478377] io scheduler anticipatory registered
[   10.478378] io scheduler deadline registered
[   10.478387] io scheduler cfq registered (default)
[   10.478398] Boot video device is 0000:00:02.0
[   10.478622] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.478683] assign_interrupt_mode Found MSI capability
[   10.478734] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.478761] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.478857] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.478918] assign_interrupt_mode Found MSI capability
[   10.478966] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.478990] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.479087] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   10.479147] assign_interrupt_mode Found MSI capability
[   10.479196] Allocate Port Service[0000:00:1c.3:pcie00]
[   10.479221] Allocate Port Service[0000:00:1c.3:pcie02]
[   10.479318] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   10.479379] assign_interrupt_mode Found MSI capability
[   10.479427] Allocate Port Service[0000:00:1c.5:pcie00]
[   10.479452] Allocate Port Service[0000:00:1c.5:pcie02]
[   10.479676] isapnp: Scanning for PnP cards...
[   10.833934] isapnp: No Plug & Play device found
[   10.854103] Real Time Clock Driver v1.12ac
[   10.854228] hpet_resources: 0xfed00000 is busy
[   10.854282] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.855540] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.855593] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.855670] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.863128] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.863131] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.893938] mice: PS/2 mouse device common for all mice
[   10.894028] EISA: Probing bus 0 at eisa.0
[   10.894036] Cannot allocate resource for EISA slot 1
[   10.894066] EISA: Detected 0 cards.
[   10.894068] cpuidle: using governor ladder
[   10.894070] cpuidle: using governor menu
[   10.894141] NET: Registered protocol family 1
[   10.894164] Using IPI No-Shortcut mode
[   10.894190] registered taskstats version 1
[   10.894302]   Magic number: 4:881:754
[   10.894368] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.894370] EDD information not available.
[   10.894552] Freeing unused kernel memory: 368k freed
[   10.894573] Write protecting the kernel read-only data: 801k
[   10.898275] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.071462] fuse init (API version 7.9)
[   12.087708] ACPI: SSDT 7F65D538, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   12.087886] ACPI: SSDT 7F65CECE, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   12.088373] Monitor-Mwait will be used to enter C-1 state
[   12.088375] Monitor-Mwait will be used to enter C-2 state
[   12.088377] Monitor-Mwait will be used to enter C-3 state
[   12.088479] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.088483] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.088667] ACPI: SSDT 7F65D77C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   12.088827] ACPI: SSDT 7F65D4B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   12.089521] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   12.089526] ACPI: Processor [CPU1] (supports 8 throttling states)
[   12.101407] ACPI: Thermal Zone [THM] (41 C)
[   12.214677] usbcore: registered new interface driver usbfs
[   12.214697] usbcore: registered new interface driver hub
[   12.214719] usbcore: registered new device driver usb
[   12.215941] USB Universal Host Controller Interface driver v3.0
[   12.215988] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
[   12.215999] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   12.216003] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   12.216212] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   12.216246] uhci_hcd 0000:00:1a.0: irq 19, io base 0x00006f60
[   12.216361] usb usb1: configuration #1 chosen from 1 choice
[   12.216381] hub 1-0:1.0: USB hub found
[   12.216385] hub 1-0:1.0: 2 ports detected
[   12.319061] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[   12.319073] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   12.319077] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   12.319097] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   12.319128] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00006f80
[   12.319225] usb usb2: configuration #1 chosen from 1 choice
[   12.319245] hub 2-0:1.0: USB hub found
[   12.319251] hub 2-0:1.0: 2 ports detected
[   12.415070] SCSI subsystem initialized
[   12.425259] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[   12.425271] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.425275] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.425295] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   12.425323] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00006f00
[   12.425424] usb usb3: configuration #1 chosen from 1 choice
[   12.425445] hub 3-0:1.0: USB hub found
[   12.425449] hub 3-0:1.0: 2 ports detected
[   12.430721] libata version 3.00 loaded.
[   12.529218] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[   12.529229] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.529233] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.529253] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   12.529282] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00006f20
[   12.529384] usb usb4: configuration #1 chosen from 1 choice
[   12.529404] hub 4-0:1.0: USB hub found
[   12.529408] hub 4-0:1.0: 2 ports detected
[   12.561113] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   12.633154] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[   12.633165] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.633170] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.633192] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   12.633223] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006f40
[   12.633322] usb usb5: configuration #1 chosen from 1 choice
[   12.633342] hub 5-0:1.0: USB hub found
[   12.633346] hub 5-0:1.0: 2 ports detected
[   12.730149] usb 1-1: configuration #1 chosen from 1 choice
[   12.732088] hub 1-1:1.0: USB hub found
[   12.734064] hub 1-1:1.0: 3 ports detected
[   12.737212] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
[   12.737226] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   12.737229] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   12.737254] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   12.741168] ehci_hcd 0000:00:1a.7: debug port 1
[   12.741175] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   12.741180] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xfed1c400
[   12.756999] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.757105] usb usb6: configuration #1 chosen from 1 choice
[   12.757126] hub 6-0:1.0: USB hub found
[   12.757131] hub 6-0:1.0: 4 ports detected
[   12.857176] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   12.909974] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f68ff800-f68fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   12.914059] ahci 0000:00:1f.2: version 3.0
[   12.914081] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   13.044878] Clocksource tsc unstable (delta = -2410085310 ns)
[   13.049178] Time: hpet clocksource has been installed.
[   13.050472] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   13.062770] usb 5-1: not running at top speed; connect to a high speed hub
[   13.071643] usb 5-1: configuration #1 chosen from 1 choice
[   13.077647] hub 1-1:1.0: hub_port_status failed (err = -71)
[   13.078644] hub 1-1:1.0: hub_port_status failed (err = -71)
[   13.079632] hub 1-1:1.0: hub_port_status failed (err = -71)
[   13.109469] usb 1-1: USB disconnect, address 2
[   13.133581] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   13.152858] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   13.152865] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   13.152874] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.153161] scsi0 : ahci
[   13.153351] scsi1 : ahci
[   13.153481] scsi2 : ahci
[   13.153709] ata1: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb900 irq 219
[   13.153713] ata2: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb980 irq 219
[   13.153716] ata3: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfba00 irq 219
[   13.154474] usb 1-1: configuration #1 chosen from 1 choice
[   13.155720] hub 1-1:1.0: USB hub found
[   13.157661] hub 1-1:1.0: 3 ports detected
[   13.264966] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00021a45de1]
[   13.272158] usb 1-1.1: new full speed USB device using uhci_hcd and address 4
[   13.332339] usb 1-1.1: configuration #1 chosen from 1 choice
[   13.355280] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   13.356204] ata1.00: ATA-8: Hitachi HTS543225L9A300, FBEOC40C, max UDMA/133
[   13.356209] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   13.357384] ata1.00: configured for UDMA/133
[   13.422789] usb 1-1.2: new full speed USB device using uhci_hcd and address 5
[   13.472133] usb 1-1.2: configuration #1 chosen from 1 choice
[   13.476334] usbcore: registered new interface driver hiddev
[   13.479506] input: HID 413c:8157 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2
[   13.489959] input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8157] on usb-0000:00:1a.0-1.1
[   13.494560] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input3
[   13.505767] input,hidraw1: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2
[   13.505787] usbcore: registered new interface driver usbhid
[   13.505792] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   13.530086] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   13.558699] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633A, D300, max UDMA/100
[   13.558704] ata2.00: applying bridge limits
[   13.587706] ata2.00: configured for UDMA/100
[   13.612420] ata3: SATA link down (SStatus 0 SControl 300)
[   13.612677] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
[   13.615016] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A D300 PQ: 0 ANSI: 5
[   13.615375] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[   13.615387] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.615391] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.615415] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   13.619323] ehci_hcd 0000:00:1d.7: debug port 1
[   13.619330] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.619335] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfed1c000
[   13.625938] Driver 'sd' needs updating - please use bus_type methods
[   13.629241] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   13.629252] sd 0:0:0:0: [sda] Write Protect is off
[   13.629254] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.629269] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.629315] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   13.629324] sd 0:0:0:0: [sda] Write Protect is off
[   13.629325] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.629339] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.629342]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   13.636228] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.636405] usb usb7: configuration #1 chosen from 1 choice
[   13.636449] hub 7-0:1.0: USB hub found
[   13.636455] hub 7-0:1.0: 6 ports detected
[   13.651670]  sda1 sda2 sda3 sda4 < sda5 >
[   13.678378] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.681632] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.681647] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.691507] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   13.691512] Uniform CD-ROM driver Revision: 3.20
[   13.691553] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   13.736474] tg3.c:v3.86 (November 9, 2007)
[   13.736515] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   13.736529] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   13.926166] usb 7-5: new high speed USB device using ehci_hcd and address 2
[   14.065770] usb 7-5: configuration #1 chosen from 1 choice
[   14.066299] usb 5-1: USB disconnect, address 2
[   14.214697] eth0: Tigon3 [partno(BCM95784M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:21:70:85:f4:e6
[   14.214703] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   14.214705] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   14.248143] Attempting manual resume
[   14.248145] swsusp: Resume From Partition 8:5
[   14.248147] PM: Checking swsusp image.
[   14.248289] PM: Resume from disk failed.
[   14.260910] EXT3-fs: INFO: recovery required on readonly filesystem.
[   14.260914] EXT3-fs: write access will be enabled during recovery.
[   14.431461] kjournald starting.  Commit interval 5 seconds
[   14.431493] EXT3-fs: sda3: orphan cleanup on readonly fs
[   14.431499] ext3_orphan_cleanup: deleting unreferenced inode 2369488
[   14.431517] EXT3-fs: sda3: 1 orphan inode deleted
[   14.431518] EXT3-fs: recovery complete.
[   14.434464] EXT3-fs: mounted filesystem with ordered data mode.
[   22.982081] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   23.076866] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.104953] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.227375] iTCO_vendor_support: vendor-support=0
[   23.325724] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   23.359912] input: PS/2 Mouse as /devices/virtual/input/input5
[   23.416967] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[   23.482399] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   23.482439] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.482473] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   23.517080] Linux agpgart interface v0.102
[   23.688058] ACPI: Battery Slot [BAT0] (battery present)
[   23.749524] ieee80211_crypt: registered algorithm 'NULL'
[   23.765699] ACPI: AC Adapter [AC] (on-line)
[   23.793644] input: Lid Switch as /devices/virtual/input/input7
[   23.817671] ACPI: Lid Switch [LID]
[   23.817733] input: Power Button (CM) as /devices/virtual/input/input8
[   23.844506] ricoh-mmc: Ricoh MMC Controller disabling driver
[   23.844509] ricoh-mmc: Copyright(c) Philip Langdale
[   23.844551] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   23.844563] ricoh-mmc: Controller is now disabled.
[   23.852612] sdhci: Secure Digital Host Controller Interface driver
[   23.852615] sdhci: Copyright(c) Pierre Ossman
[   23.852654] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   23.852677] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
[   23.852737] mmc0: SDHCI at 0xf68ff400 irq 22 DMA
[   23.877456] ACPI: Power Button (CM) [PBTN]
[   23.877515] input: Sleep Button (CM) as /devices/virtual/input/input9
[   23.902707] wl: module license 'MIXED/Proprietary' taints kernel.
[   23.907390] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   23.907406] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   23.949418] ACPI: Sleep Button (CM) [SBTN]
[   23.950705] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/LNXVIDEO:00/input/input10
[   23.994918] agpgart: Detected an Intel 965GM Chipset.
[   23.995809] agpgart: Detected 7676K stolen memory.
[   24.009213] agpgart: AGP aperture is 256M @ 0xe0000000
[   24.021373] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   24.021439] ACPI: WMI-Acer: Mapper loaded
[   24.022001] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11
[   24.026898] Linux video capture interface: v2.00
[   24.061835] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:18a0)
[   24.062805] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb7/7-5/7-5:1.0/input/input12
[   24.081382] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   24.081524] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input13
[   24.083816] ieee80211_crypt: registered algorithm 'TKIP'
[   24.083963] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.6
[   24.104398] usbcore: registered new interface driver uvcvideo
[   24.104403] USB Video Class driver (SVN r217)
[   24.153308] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   24.329683] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   24.329706] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   24.925797] lp: driver loaded but no devices found
[   25.005208] vloopback: Video4linux loopback driver v1.1.5
[   25.005249] vloopback: Loopback 0 registered, input: video2, output: video1
[   25.057098] Adding 2016116k swap on /dev/sda5.  Priority:-1 extents:1 across:2016116k
[   25.541897] EXT3 FS on sda3, internal journal
[   26.147509] ip_tables: (C) 2000-2006 Netfilter Core Team
```

Here's my uname -a info
```
Linux dell-desktop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

---

### Post by wonderbriefs on 2008-12-11
Not sure if this is significant or not, but I noticed my dmesg.0 is reporting a different version than lspci
```
[   24.083963] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.6

```

---

### Post by Ayuthia on 2008-12-11
Everything looks fine.  You might want to see if you can just connect to an unencrypted site.  By any chance, did you run any updates lately?  If so, can you try and see if you can connect with the previous kernel (possibly 2.6.24-21)?  It might be possible that the kernel change might have affected your wireless.  I know that the 4315 chipset has some issues with WEP/WPA.

By the way, the test without encryption is just a test.  I am not recommending that you should change your wireless to not be encrypted.  We just need to see if you are able to connect.  If we can get a connection, we can then see what is causing your WPA connection to not work.

The card is generally listed as a 4312 card since 8.04.1 (It was listed as a 4310 card prior to 8.04.1).  However the pciid is always listed as 14e4:4315.  That is why you see two different numbers.

---

### Post by wonderbriefs on 2008-12-11
I've tried on kernal 2.6.24-16 but have the same effect.

One thing has changed since then. I right clicked on my network, and selected "Edit Wireless Networks" then copied the password just to make absolutely sure I was entering it correctly. 

Now instead of prompting me for a password, it just cycles endlessly trying to connect to no avail.

There are no unsecured networks in my neighborhood. I'll have to try on an unsecured network later.

---

### Post by wonderbriefs on 2008-12-11
I've manually reconfigured the network, and it finally worked again.

I'm up and running, but take note that this is still very buggy.

---

### Post by mikewhatever on 2008-12-11
> **wonderbriefs said:**
> I've manually reconfigured the network, and it finally worked again.

I'm up and running, but take note that this is still very buggy.

Glad it finally worked. May I point out that the majority of ubuntuforums' members are not developers, but rather simple users volunteering to help others with problems. Us taking notes is not going to fix bugs, but you filing bug reports may. [http://ubuntuforums.org/showthread.php?t=734460](http://ubuntuforums.org/showthread.php?t=734460)

---

