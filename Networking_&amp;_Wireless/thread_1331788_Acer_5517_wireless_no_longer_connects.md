---
title: "Acer 5517 wireless no longer connects"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by jeannacav on 2009-11-19
I just started to use the acer 5517.

I wiped the windoze7 off and partitioned the whole drive into 3 parts (not Gallia)

When I was doing the forced recover stuff that acer somehow imposes, the wireless was working fine.
Once the jaunty was complete the wireless no longer worked at all.

I read the solved link and installed a stable backports thingy. and it worked.
but the wired connection did not work.

Using the wireless I ran the updates manager and installed 228MB of additions, which needed a reboot to finish.

When that was finished, the wireless no longer worked, but the wired does.
The wireless can see that my modem is there and displays its name, but there is no (is it called?) handshake.

**SO,**

I read the how to post a wireless help request and I have some pertinent information about the parts and status.
Here goes:

=============terminal response========

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
        Subsystem: Acer Incorporated [ALI] Device 028d
        Flags: bus master, 66MHz, medium devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: 92100000-922fffff
        Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
        I/O behind bridge: 00003000-00006fff
        Memory behind bridge: 91100000-920fffff
        Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
        Capabilities: <access denied>
:

=================list devices==========

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
08:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

===========ifconfig and iwconfig========

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:5b:c7:d4  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe5b:c7d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5363 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:9782810 (9.7 MB)  TX bytes:672640 (672.6 KB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


[and then]

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

====================

So, I hope this will allow someone to help me.
If you need more info please be specific. (I am new enough to need that)

And,
thank you

OH BTW
there are a few terminal instructions that return a request for my sudo password.
I am unable to use the keyboard from then on.
So, I can neither supply my password nor type anything else.

thank you,

jeanna

---

### Post by jeannacav on 2009-11-19
I think I got around the sudo thing. Here is more information.

=====results from lshw network to the end of instructions========

~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:5b:c7:d4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=192.168.1.64 latency=0 module=atl1c multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:ef:f1:1c:80:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').


$ lsb_release -d
Description:	Ubuntu 9.04


$ uname -mr
2.6.28-16-generic i686


============ results dmesg===========




[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 9169920 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1790596k/1833984k available (4116k kernel code, 39292k reserved, 2199k data, 532k init, 926148k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc050520d - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc050520d   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.64 BogoMIPS (lpj=6383296)
[    0.004031] Security Framework initialized
[    0.004039] SELinux:  Disabled at boot.
[    0.004056] AppArmor: AppArmor initialized
[    0.004065] Mount-cache hash table entries: 512
[    0.004203] Initializing cgroup subsys ns
[    0.004207] Initializing cgroup subsys cpuacct
[    0.004210] Initializing cgroup subsys memory
[    0.004215] Initializing cgroup subsys freezer
[    0.004228] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004231] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004235] using C1E aware idle routine
[    0.004245] Checking 'hlt' instruction... OK.
[    0.020601] SMP alternatives: switching to UP code
[    0.170483] ACPI: Core revision 20080926
[    0.174279] ACPI: Checking initramfs for custom DSDT
[    0.532499] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.575260] CPU0: AMD Athlon(tm) Processor TF-20 stepping 02
[    0.576002] Brought up 1 CPUs
[    0.576002] Total of 1 processors activated (3191.64 BogoMIPS).
[    0.576002] CPU0 attaching NULL sched-domain.
[    0.576002] net_namespace: 776 bytes
[    0.576002] Booting paravirtualized kernel on bare hardware
[    0.576002] Time: 20:45:25  Date: 11/19/09
[    0.576002] regulator: core version 0.5
[    0.576002] NET: Registered protocol family 16
[    0.576002] EISA bus registered
[    0.576002] ACPI: bus type pci registered
[    0.576002] PCI: MCFG configuration 0: base f7000000 segment 0 buses 0 - 15
[    0.576002] PCI: MCFG area at f7000000 reserved in E820
[    0.576002] PCI: Using MMCONFIG for extended config space
[    0.576002] PCI: Using configuration type 1 for base access
[    0.576002] ACPI: EC: Look up EC in DSDT
[    0.581500] ACPI: BIOS _OSI(Linux) query ignored
[    0.586510] ACPI: Interpreter enabled
[    0.586514] ACPI: (supports S0 S1 S3 S4 S5)
[    0.586544] ACPI: Using IOAPIC for interrupt routing
[    0.595653] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.595815] System has AMD C1E enabled
[    0.595815] Switch to broadcast mode on CPU0
[    1.092006] ACPI: EC: missing confirmations, switch off interrupt mode.
[    1.220398] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    1.220400] ACPI: EC: driver started in poll mode
[    1.220629] ACPI: No dock devices found.
[    1.220645] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.220790] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.220794] pci 0000:00:04.0: PME# disabled
[    1.220826] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.220829] pci 0000:00:05.0: PME# disabled
[    1.220894] pci 0000:00:11.0: reg 10 io port: [0x8038-0x803f]
[    1.220903] pci 0000:00:11.0: reg 14 io port: [0x804c-0x804f]
[    1.220911] pci 0000:00:11.0: reg 18 io port: [0x8030-0x8037]
[    1.220919] pci 0000:00:11.0: reg 1c io port: [0x8048-0x804b]
[    1.220927] pci 0000:00:11.0: reg 20 io port: [0x8010-0x801f]
[    1.220936] pci 0000:00:11.0: reg 24 32bit mmio: [0x92306000-0x923063ff]
[    1.220983] pci 0000:00:12.0: reg 10 32bit mmio: [0x92305000-0x92305fff]
[    1.221044] pci 0000:00:12.1: reg 10 32bit mmio: [0x92304000-0x92304fff]
[    1.221125] pci 0000:00:12.2: reg 10 32bit mmio: [0x92306400-0x923064ff]
[    1.221169] pci 0000:00:12.2: supports D1 D2
[    1.221172] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.221177] pci 0000:00:12.2: PME# disabled
[    1.221309] pci 0000:00:14.2: reg 10 64bit mmio: [0x92300000-0x92303fff]
[    1.221348] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.221353] pci 0000:00:14.2: PME# disabled
[    1.221588] pci 0000:01:05.0: reg 10 32bit mmio: [0x80000000-0x8fffffff]
[    1.221593] pci 0000:01:05.0: reg 14 io port: [0x7000-0x70ff]
[    1.221598] pci 0000:01:05.0: reg 18 32bit mmio: [0x92200000-0x9220ffff]
[    1.221608] pci 0000:01:05.0: reg 24 32bit mmio: [0x92100000-0x921fffff]
[    1.221617] pci 0000:01:05.0: supports D1 D2
[    1.221700] pci 0000:00:01.0: bridge io port: [0x7000-0x7fff]
[    1.221704] pci 0000:00:01.0: bridge 32bit mmio: [0x92100000-0x922fffff]
[    1.221709] pci 0000:00:01.0: bridge 64bit mmio pref: [0x80000000-0x8fffffff]
[    1.221757] pci 0000:02:00.0: reg 10 64bit mmio: [0x91100000-0x9110ffff]
[    1.221794] pci 0000:02:00.0: supports D1
[    1.221796] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    1.221801] pci 0000:02:00.0: PME# disabled
[    1.221867] pci 0000:00:04.0: bridge io port: [0x3000-0x6fff]
[    1.221871] pci 0000:00:04.0: bridge 32bit mmio: [0x91100000-0x920fffff]
[    1.221876] pci 0000:00:04.0: bridge 64bit mmio pref: [0x90000000-0x90ffffff]
[    1.221928] pci 0000:08:00.0: reg 10 64bit mmio: [0x91000000-0x9103ffff]
[    1.221937] pci 0000:08:00.0: reg 18 io port: [0x2000-0x207f]
[    1.221973] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.221979] pci 0000:08:00.0: PME# disabled
[    1.222042] pci 0000:00:05.0: bridge io port: [0x2000-0x2fff]
[    1.222047] pci 0000:00:05.0: bridge 32bit mmio: [0x91000000-0x910fffff]
[    1.222113] pci 0000:00:14.4: transparent bridge
[    1.222118] pci 0000:00:14.4: bridge io port: [0x1000-0x1fff]
[    1.222141] bus 00 -> node 0
[    1.222154] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.222478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    1.222681] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    1.222901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    1.223183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.233577] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.233876] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.234166] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.234453] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.234739] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.235026] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.235311] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.235597] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.235918] ACPI: WMI: Mapper loaded
[    1.236112] SCSI subsystem initialized
[    1.236154] libata version 3.00 loaded.
[    1.236201] usbcore: registered new interface driver usbfs
[    1.236219] usbcore: registered new interface driver hub
[    1.236246] usbcore: registered new device driver usb
[    1.236371] PCI: Using ACPI for IRQ routing
[    1.236502] Bluetooth: Core ver 2.13
[    1.236502] NET: Registered protocol family 31
[    1.236502] Bluetooth: HCI device and connection manager initialized
[    1.236502] Bluetooth: HCI socket layer initialized
[    1.236502] NET: Registered protocol family 8
[    1.236502] NET: Registered protocol family 20
[    1.236502] NetLabel: Initializing
[    1.236502] NetLabel:  domain hash size = 128
[    1.236502] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.236502] NetLabel:  unlabeled traffic allowed by default
[    1.236502] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 2303, 0
[    1.236502] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    1.240024] hpet: hpet2 irq 2303 for MSI
[    1.240100] AppArmor: AppArmor Filesystem Enabled
[    1.240106] pnp: PnP ACPI init
[    1.240106] ACPI: bus type pnp registered
[    1.244027] Switched to high resolution mode on CPU 0
[    1.312099] pnp: PnP ACPI: found 10 devices
[    1.312101] ACPI: ACPI bus type pnp unregistered
[    1.312105] PnPBIOS: Disabled by ACPI PNP
[    1.312116] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.312120] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.312123] system 00:01: iomem range 0xf7000000-0xf7ffffff has been reserved
[    1.312132] system 00:08: ioport range 0x400-0x4cf has been reserved
[    1.312135] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.312139] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    1.312142] system 00:08: ioport range 0x680-0x6ff has been reserved
[    1.312145] system 00:08: ioport range 0x77a-0x77a has been reserved
[    1.312148] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    1.312151] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    1.312155] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    1.312158] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    1.312161] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    1.312164] system 00:08: ioport range 0xcd0-0xcdb has been reserved
[    1.312168] system 00:08: ioport range 0xfd60-0xfd63 has been reserved
[    1.312174] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    1.312178] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    1.347161] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.347165] pci 0000:00:01.0:   IO window: 0x7000-0x7fff
[    1.347170] pci 0000:00:01.0:   MEM window: 0x92100000-0x922fffff
[    1.347174] pci 0000:00:01.0:   PREFETCH window: 0x00000080000000-0x0000008fffffff
[    1.347180] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    1.347183] pci 0000:00:04.0:   IO window: 0x3000-0x6fff
[    1.347187] pci 0000:00:04.0:   MEM window: 0x91100000-0x920fffff
[    1.347191] pci 0000:00:04.0:   PREFETCH window: 0x00000090000000-0x00000090ffffff
[    1.347196] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    1.347199] pci 0000:00:05.0:   IO window: 0x2000-0x2fff
[    1.347204] pci 0000:00:05.0:   MEM window: 0x91000000-0x910fffff
[    1.347207] pci 0000:00:05.0:   PREFETCH window: disabled
[    1.347212] pci 0000:00:14.4: PCI bridge, secondary bus 0000:09
[    1.347249] pci 0000:00:14.4:   IO window: 0x1000-0x1fff
[    1.347255] pci 0000:00:14.4:   MEM window: disabled
[    1.347260] pci 0000:00:14.4:   PREFETCH window: disabled
[    1.347273] pci 0000:00:01.0: setting latency timer to 64
[    1.347283] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.347287] pci 0000:00:04.0: setting latency timer to 64
[    1.347294] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.347298] pci 0000:00:05.0: setting latency timer to 64
[    1.347306] bus: 00 index 0 io port: [0x00-0xffff]
[    1.347309] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.347312] bus: 01 index 0 io port: [0x7000-0x7fff]
[    1.347314] bus: 01 index 1 mmio: [0x92100000-0x922fffff]
[    1.347317] bus: 01 index 2 mmio: [0x80000000-0x8fffffff]
[    1.347319] bus: 01 index 3 mmio: [0x0-0x0]
[    1.347322] bus: 02 index 0 io port: [0x3000-0x6fff]
[    1.347324] bus: 02 index 1 mmio: [0x91100000-0x920fffff]
[    1.347327] bus: 02 index 2 mmio: [0x90000000-0x90ffffff]
[    1.347329] bus: 02 index 3 mmio: [0x0-0x0]
[    1.347332] bus: 08 index 0 io port: [0x2000-0x2fff]
[    1.347334] bus: 08 index 1 mmio: [0x91000000-0x910fffff]
[    1.347337] bus: 08 index 2 mmio: [0x0-0x0]
[    1.347339] bus: 08 index 3 mmio: [0x0-0x0]
[    1.347341] bus: 09 index 0 io port: [0x1000-0x1fff]
[    1.347344] bus: 09 index 1 mmio: [0x0-0x0]
[    1.347346] bus: 09 index 2 mmio: [0x0-0x0]
[    1.347348] bus: 09 index 3 io port: [0x00-0xffff]
[    1.347351] bus: 09 index 4 mmio: [0x000000-0xffffffff]
[    1.347361] NET: Registered protocol family 2
[    1.347551] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.347869] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.348607] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.348963] TCP: Hash tables configured (established 131072 bind 65536)
[    1.348966] TCP reno registered
[    1.349093] NET: Registered protocol family 1
[    1.349237] checking if image is initramfs... it is
[    2.071165] Freeing initrd memory: 7382k freed
[    2.071233] Simple Boot Flag at 0x44 set to 0x1
[    2.071307] cpufreq: No nForce2 chipset.
[    2.071442] audit: initializing netlink socket (disabled)
[    2.071458] type=2000 audit(1258663526.068:1): initialized
[    2.081194] highmem bounce pool size: 64 pages
[    2.081199] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.082578] VFS: Disk quotas dquot_6.5.1
[    2.082637] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.083305] fuse init (API version 7.10)
[    2.083392] msgmni has been set to 1704
[    2.083635] alg: No test for stdrng (krng)
[    2.083647] io scheduler noop registered
[    2.083649] io scheduler anticipatory registered
[    2.083651] io scheduler deadline registered
[    2.083668] io scheduler cfq registered (default)
[    2.172079] pci 0000:01:05.0: Boot video device
[    2.308221] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.308252] pcieport-driver 0000:00:04.0: found MSI capability
[    2.308276] pcieport-driver 0000:00:04.0: irq 2302 for MSI/MSI-X
[    2.308287] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.308303] pci_express 0000:00:04.0:pcie02: allocate port service
[    2.308316] pci_express 0000:00:04.0:pcie03: allocate port service
[    2.308361] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.308391] pcieport-driver 0000:00:05.0: found MSI capability
[    2.308410] pcieport-driver 0000:00:05.0: irq 2301 for MSI/MSI-X
[    2.308420] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.308437] pci_express 0000:00:05.0:pcie03: allocate port service
[    2.308495] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.308552] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.315399] ACPI: AC Adapter [ACAD] (on-line)
[    2.948192] ACPI: Battery Slot [BAT1] (battery present)
[    2.948297] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.948300] ACPI: Power Button (FF) [PWRF]
[    2.948343] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.948346] ACPI: Power Button (CM) [PWRB]
[    2.948389] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.948392] ACPI: Sleep Button (CM) [SLPB]
[    2.948446] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0D:00/input/input3
[    3.056229] ACPI: Lid Switch [LID]
[    3.056550] ACPI: processor limited to max C-state 1
[    3.056563] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.056588] processor ACPI_CPU:00: registered as cooling_device0
[    3.056592] ACPI: Processor [C000] (supports 8 throttling states)
[    3.134867] thermal LNXTHERM:01: registered as thermal_zone0
[    3.146134] ACPI: Thermal Zone [THRM] (23 C)
[    3.146179] isapnp: Scanning for PnP cards...
[    3.530470] isapnp: No Plug & Play device found
[    3.531751] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.532771] brd: module loaded
[    3.533089] loop: module loaded
[    3.533160] Fixed MDIO Bus: probed
[    3.533167] PPP generic driver version 2.4.2
[    3.533230] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    3.533257] Driver 'sd' needs updating - please use bus_type methods
[    3.533267] Driver 'sr' needs updating - please use bus_type methods
[    3.533306] ahci 0000:00:11.0: version 3.0
[    3.533355] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.533409] ahci 0000:00:11.0: irq 2300 for MSI/MSI-X
[    3.533594] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    3.533598] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    3.534621] scsi0 : ahci
[    3.534774] scsi1 : ahci
[    3.534865] scsi2 : ahci
[    3.534954] scsi3 : ahci
[    3.535047] scsi4 : ahci
[    3.535136] scsi5 : ahci
[    3.535313] ata1: SATA max UDMA/133 abar m1024@0x92306000 port 0x92306100 irq 2300
[    3.535317] ata2: SATA max UDMA/133 abar m1024@0x92306000 port 0x92306180 irq 2300
[    3.535322] ata3: SATA max UDMA/133 abar m1024@0x92306000 port 0x92306200 irq 2300
[    3.535326] ata4: SATA max UDMA/133 abar m1024@0x92306000 port 0x92306280 irq 2300
[    3.535330] ata5: SATA max UDMA/133 abar m1024@0x92306000 port 0x92306300 irq 2300
[    3.535335] ata6: SATA max UDMA/133 abar m1024@0x92306000 port 0x92306380 irq 2300
[    4.016075] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.057101] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    4.057105] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.058536] ata1.00: configured for UDMA/133
[    4.392079] ata2: SATA link down (SStatus 0 SControl 300)
[    4.892076] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.895259] ata3.00: ATAPI: Slimtype DVD A  DS8A4SH, CA11, max UDMA/100, ATAPI AN
[    4.897211] ata3.00: configured for UDMA/100
[    5.232079] ata4: SATA link down (SStatus 0 SControl 300)
[    5.568078] ata5: SATA link down (SStatus 0 SControl 300)
[    5.904079] ata6: SATA link down (SStatus 0 SControl 300)
[    5.920169] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    5.920268] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    5.920285] sd 0:0:0:0: [sda] Write Protect is off
[    5.920288] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.920314] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.920382] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    5.920396] sd 0:0:0:0: [sda] Write Protect is off
[    5.920399] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.920423] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.920427]  sda: sda1 sda2 sda3
[    5.991293] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.991345] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.998268] scsi 2:0:0:0: CD-ROM            Slimtype DVD A  DS8A4SH   CA11 PQ: 0 ANSI: 5
[    6.008007] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    6.008025] Uniform CD-ROM driver Revision: 3.20
[    6.008113] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    6.008154] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    6.008822] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.008880] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.008903] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    6.008907] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    6.008969] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    6.009045] ehci_hcd 0000:00:12.2: debug port 1
[    6.009065] ehci_hcd 0000:00:12.2: irq 17, io mem 0x92306400
[    6.020065] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    6.020131] usb usb1: configuration #1 chosen from 1 choice
[    6.020163] hub 1-0:1.0: USB hub found
[    6.020173] hub 1-0:1.0: 6 ports detected
[    6.020317] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.020366] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.020380] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    6.020384] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    6.020428] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 2
[    6.020490] ohci_hcd 0000:00:12.0: irq 16, io mem 0x92305000
[    6.080105] usb usb2: configuration #1 chosen from 1 choice
[    6.080131] hub 2-0:1.0: USB hub found
[    6.080176] hub 2-0:1.0: 3 ports detected
[    6.080302] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.080315] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    6.080319] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    6.080361] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 3
[    6.080414] ohci_hcd 0000:00:12.1: irq 16, io mem 0x92304000
[    6.140095] usb usb3: configuration #1 chosen from 1 choice
[    6.140122] hub 3-0:1.0: USB hub found
[    6.140167] hub 3-0:1.0: 3 ports detected
[    6.140295] uhci_hcd: USB Universal Host Controller Interface driver
[    6.140373] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    6.161471] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.161476] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.161634] mice: PS/2 mouse device common for all mice
[    6.161951] rtc_cmos 00:04: RTC can wake from S4
[    6.161988] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    6.162060] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    6.162121] device-mapper: uevent: version 1.0.3
[    6.162270] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    6.162353] device-mapper: multipath: version 1.0.5 loaded
[    6.162359] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.162469] EISA: Probing bus 0 at eisa.0
[    6.162515] Cannot allocate resource for EISA slot 1
[    6.162518] Cannot allocate resource for EISA slot 2
[    6.162520] Cannot allocate resource for EISA slot 3
[    6.162523] Cannot allocate resource for EISA slot 4
[    6.162525] Cannot allocate resource for EISA slot 5
[    6.162528] Cannot allocate resource for EISA slot 6
[    6.162530] Cannot allocate resource for EISA slot 7
[    6.162532] Cannot allocate resource for EISA slot 8
[    6.162535] EISA: Detected 0 cards.
[    6.162582] cpuidle: using governor ladder
[    6.162616] cpuidle: using governor menu
[    6.163168] TCP cubic registered
[    6.163272] NET: Registered protocol family 10
[    6.163714] lo: Disabled Privacy Extensions
[    6.164082] NET: Registered protocol family 17
[    6.164099] Bluetooth: L2CAP ver 2.11
[    6.164101] Bluetooth: L2CAP socket layer initialized
[    6.164105] Bluetooth: SCO (Voice Link) ver 0.6
[    6.164106] Bluetooth: SCO socket layer initialized
[    6.164133] Bluetooth: RFCOMM socket layer initialized
[    6.164141] Bluetooth: RFCOMM TTY layer initialized
[    6.164143] Bluetooth: RFCOMM ver 1.10
[    6.164167] powernow-k8: Found 1 AMD Athlon(tm) Processor TF-20 processors (1 cpu cores) (version 2.20.00)
[    6.164212] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x16
[    6.164215] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
[    6.164254] Using IPI No-Shortcut mode
[    6.164332] registered taskstats version 1
[    6.164452]   Magic number: 1:816:801
[    6.164584] rtc_cmos 00:04: setting system clock to 2009-11-19 20:45:31 UTC (1258663531)
[    6.164587] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.164589] EDD information not available.
[    6.164979] Freeing unused kernel memory: 532k freed
[    6.165131] Write protecting the kernel text: 4120k
[    6.165183] Write protecting the kernel read-only data: 1524k
[    6.199206] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    7.159977] PM: Starting manual resume from disk
[    7.159981] PM: Resume from partition 8:3
[    7.159983] PM: Checking hibernation image.
[    7.160227] PM: Resume from disk failed.
[    7.195969] kjournald starting.  Commit interval 5 seconds
[    7.195980] EXT3-fs: mounted filesystem with ordered data mode.
[   12.227642] udev: starting version 141
[   12.399111] acpi device:04: registered as cooling_device1
[   12.399566] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[   12.406358] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.625005] atl1c 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.625018] atl1c 0000:08:00.0: setting latency timer to 64
[   12.647105] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   12.647111] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   12.716942] atl1c 0000:08:00.0: version 1.0.0.1-NAPI
[   12.717123] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.717145] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.783842] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   12.989673] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.056990] acer-wmi: Acer Laptop ACPI-WMI Extras
[   13.062354] acer-wmi: Unable to detect available WMID devices
[   13.139911] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.140091] HDA Intel 0000:00:14.2: setting latency timer to 64
[   13.173864] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   13.457689] lp: driver loaded but no devices found
[   13.559143] Adding 3903784k swap on /dev/sda3.  Priority:-1 extents:1 across:3903784k
[   13.752144] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   13.788127] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   14.105111] EXT3 FS on sda1, internal journal
[   14.993139] kjournald starting.  Commit interval 5 seconds
[   14.993560] EXT3 FS on sda2, internal journal
[   14.993566] EXT3-fs: mounted filesystem with ordered data mode.
[   15.304250] type=1505 audit(1258663540.639:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1898
[   15.371815] type=1505 audit(1258663540.703:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1902
[   15.371971] type=1505 audit(1258663540.703:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1902
[   15.372030] type=1505 audit(1258663540.703:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1902
[   15.372114] type=1505 audit(1258663540.707:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1902
[   15.558205] type=1505 audit(1258663540.891:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1907
[   15.558434] type=1505 audit(1258663540.891:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1907
[   15.597674] type=1505 audit(1258663540.931:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1911
[   18.057117] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.057121] Bluetooth: BNEP filters: protocol multicast
[   18.076696] Bridge firewalling registered
[   19.116523] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.272000] Linux agpgart interface v0.103
[   19.304660] [drm] Initialized drm 1.1.0 20060810
[   19.368475] pci 0000:01:05.0: setting latency timer to 64
[   19.368681] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   19.537985] ppdev: user-space parallel port driver
[   20.478521] [drm] Setting GART location based on new memory map
[   20.495812] [drm] Loading RS780 CP Microcode
[   20.496949] [drm] Loading RS780 PFP Microcode
[   20.512007] [drm] Resetting GPU
[   20.512069] [drm] writeback test succeeded in 1 usecs
[   23.665906] atl1c 0000:08:00.0: irq 2299 for MSI/MSI-X
[   23.666022] atl1c 0000:08:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   33.856055] eth0: no IPv6 routers present
[   81.000066] Clocksource tsc unstable (delta = -91876296 ns)
[  115.479484] CPU0 attaching NULL sched-domain.
[  115.497339] CPU0 attaching NULL sched-domain.


=====
Wow... lots of stuff. I hope a brain can figure what I need.

thanks,

jeanna

---

### Post by jeannacav on 2009-11-19
One more thing occurred to me this morning.

Since I was unable to use the internet to get the backports drill, I used a flashdrive on my working acer 5515, then copied it to the desktop of this acer 5517.

That is how I got the wireless to work.

It is still on the desktop and I bet it is supposed to be in some folder where the computer can find it on bootup and use it.

If that is so,
Please someone tell me where. I will drop it into the right place.

thank you,

jeanna

---

### Post by premjan on 2010-01-07
So wait - your wireless lan is working now?  I am unclear on what you did with backports to make it happen.  I am having trouble with my Acer 5517 WLAN connection - it doesn't let me sudo modprobe acer_wmi for some reason.  The wired LAN works OK.  Post more details of what step made it work please?

---

### Post by jeannacav on 2010-01-07
> **premjan said:**
> So wait - your wireless lan is working now?  I am unclear on what you did with backports to make it happen.  I am having trouble with my Acer 5517 WLAN connection - it doesn't let me sudo modprobe acer_wmi for some reason.  The wired LAN works OK.  Post more details of what step made it work please?

The sudo thing was strange.
When you are asked for your password, just ignore the fact that nothing is being typed and put in your password and return then it should do it.



OK,
So in the end I changed channels on my router.
I had as many as 7 neighbors and whenever one of them joined or left the neighborhood my connection went south.
Some of them are stronger than my own router right here 2 feet away.

But I found that synaptic could install the backports, so I let it do that. However that did not work very well once it was installed.


Coffeecat gave me the help I needed in the end with changing the channel.
(I will look for c cats instructions and copy them here soon.)

I am a really new ubuntu user so I cannot go into much detail here.

Please let me know what you have done, then maybe someone else can help if/when I cannot.

jeanna

---

### Post by jeannacav on 2010-01-07
Here is coffeecat's instrux on changing the channel
cc is in the uk.
I am in the us and I can only use 1,6,11, I think. I changed from 11 to 6 and it is much better, although not yet rock solid. I am sure glad I can use the eth cord.


> You need to log into the web configuration interface of your router to be able to change the wireless channel. Have a look in your router manual to get the specifics. But in general terms, connect to the router with an ethernet cable - always do this if you are going to change wireless settings. Open Firefox (or any web browser), and type the IP address of your router in the address bar. This is usually 192.168.1.1 or 192.168.0.1 or 10.0.0.1 depending on the make of your router. Your manual should tell you the actual address for your device, or you could right-click on network manager and click on 'Connection Information'. The address is the one listed as 'Default Route'.

Once you've entered the router IP address and pressed enter, you'll be prompted for the admin username and password. If you haven't set these yourself the defaults will be in the manual - often something as obvious as 'admin' and 'admin'. Once you've logged in you'll be in the configuration interface. Look under 'wireless' and you should be able to find where to change the channel. All changes have to be saved otherwise they'll be lost when you power down the router.


[for cc's other replies]("http://ubuntuforums.org/showthread.php?p=8585785#post8585785")

jeanna

---

### Post by premjan on 2010-01-07
Hmmm, I didn't have a problem with running sudo.  The problem I had was similar to [this]("http://code.google.com/p/aceracpi/issues/detail?id=42#c6"), although I have acer_wmi available on my laptop in /sys/modules/acer_wmi, it has not created a folder /sys/devices/platform/acer-wmi for some reason.  Also when I press my WLAN button on my laptop it does not light up.  Maybe I screwed up something in my kubuntu install?

I'm also not sure why I need to change the channel - windows 7 works fine with the settings I have.  Kubuntu only seems to work with the wired interface.

---

### Post by jeannacav on 2010-01-07
> **premjan said:**
> 


I'm also not sure why I need to change the channel - windows 7 works fine with the settings I have.  Kubuntu only seems to work with the wired interface.
Yes, be glad you have the wired. Some folks do not even have that!

The button went on for me after I got the right backports from synaptic. but since it is a toggle, I cannot say much, but it is always on now.

I really don't know why you must change the channel either, but the expl that cc gave seemed reasonable.
And, changing the channel was easy.
I think the problem lies with ubuntu and the atheros card. Somehow it is flaky.
I also had no problem with the windoz7 but I have no interest in using windoz so I wiped it off the acer, which means I cannot tell you what is happening by comparison.

I do not know what acer-wmi means so maybe someone else can help you... sorry.
If you did get the backports from synaptic and you have tried the channel change and those don't help, I am sorry but I am not able to help more than that.

---

