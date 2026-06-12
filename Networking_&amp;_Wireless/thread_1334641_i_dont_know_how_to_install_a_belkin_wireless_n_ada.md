---
title: "i dont know how to install a belkin wireless n adapter"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by scooba61709 on 2009-11-22
i am new to ubuntu and lunix. i am having trouble figureing out how to get the windows drivers to work on ubunto 9.4 i dont know any thing bout it so any thing would help please let me know

---

### Post by coffeeaddict22 on 2009-11-22
Hi Scoob,
Welcome to Ubuntu!  We all learnt the hard way, so welcome to the club.
Your question is a bit of an oxymoron.  Windows drivers tell a piece of hardware how to communicate with... windows.  You presumably want the hardware to play nicely with Linux, so you need a Linux driver.

First up, plug in the adapter.  Linux should recognise it; if it's new, I'd strongly recommend upgrading to 9.10, as wireless drivers have been getting a lot of work put into them, so running an older kernel is less helpful.

Once you've done that, look in System/Administration/Hardware Drivers, and if the card is recognised you may be offered the chance to add a proprietary driver.  If offered, take it.

If not, post back the output of the following terminal (look in Applications/Accessories/Terminal) commands: 
```
lsusb
lshw -C network
ifconfig
``` and that should give us something to go on.  if the card is not a USB adapter, type in "lspci" instead of "lsusb"

---

### Post by scooba61709 on 2009-11-22
ok it is a usb and i will be getting 9.10 in the mail some time soon lol and i am also getting kubuntu will that be the same in a way? thawnxs also for the information

---

### Post by coffeeaddict22 on 2009-11-22
If you're on the net (and reading this...) it's just as quick to download your distro of choice.

Kubuntu is KDE based.  Linux is the operating system; at it's base that's a collection of programs that tell bits of hardware (the processor, memory, video card, etc) how to talk to each other.  The interface you use to talk to the system is usually mostly pictures- a Graphical User Interface, or GUI.  There's more than one way of putting pictures on a page, and so there are different Window managers.  KDE is one, Ubuntu is based on Gnome, which is another.  There's other's too- XFCE is a window manager that takes up less memory, for instance.

The other issue with window managers is sometimes the interface is different; for instance, I think Kubuntu uses wicd as its network manager instead of (surprise) Gnome-network-manager.

---

### Post by scooba61709 on 2009-11-22
this is what it said when i looked it up n it wants me to use it as a super-user? ya i dont understand that but what else do i do now 
 
 
 
 
 
 
 *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 3
       bus info: [EMAIL="pci@0000:00:03.0"]pci@0000:00:03.0[/EMAIL]
       logical name: eth0
       version: 90
       serial: 00:0a:e6:64:ba:c8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:61:6c:dc:44:7a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[EMAIL="steven@steven:~$"]steven@steven:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:64:ba:c8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xd400 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[EMAIL="steven@steven:~$"]steven@steven:~$[/EMAIL]

---

### Post by coffeeaddict22 on 2009-11-22
OK.
There's no wireless in that.  That's the output from lshw -C network; what does lsusb return?

---

### Post by scooba61709 on 2009-11-22
Bus 001 Device 002: ID 050d:815c Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by coffeeaddict22 on 2009-11-22
OK.  Line 1 is the adapter showing up, so it is recognised there.  What does ```
hciconfig
``` return?

---

### Post by scooba61709 on 2009-11-22
nothing

---

### Post by coffeeaddict22 on 2009-11-22
OK.  try the output of ```
 cat /var/log/dmesg | grep Blue*
```

---

### Post by scooba61709 on 2009-11-22
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bd000 - 37fef3a1
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb33a1
[    0.000000] Move RAMDISK from 00000000378bd000 - 0000000037fef3a0 to 00881000 - 00fb33a0
[    0.000000] ACPI: RSDP 000FA340, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 4FFF0000, 0028 (r1 AMIINT SiS735XX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 4FFF0030, 0074 (r1 AMIINT SiS735XX     1000 MSFT  100000B)
[    0.000000] ACPI: DSDT 4FFF0100, 33C2 (r1    SiS      735      100 MSFT  100000D)
[    0.000000] ACPI: FACS 4FFF8000, 0040
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
[    0.000000]   #7 [0000881000 - 0000fb33a1]      NEW RAMDISK ==> [0000881000 - 0000fb33a1]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0004fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004fff0
[    0.000000] On node 0 totalpages: 327551
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 792 pages used for memmap
[    0.000000]   HighMem zone: 100570 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324991
[    0.000000] Kernel command line: root=UUID=41bcbfbb-55e2-4d3b-a9f5-a8d18c5370a1 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1244.629 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 6552960 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1276752k/1310656k available (4126k kernel code, 32588k reserved, 2208k data, 532k init, 405448k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004028] Calibrating delay loop (skipped), value calculated using timer frequency.. 2489.25 BogoMIPS (lpj=4978516)
[    0.004079] Security Framework initialized
[    0.004101] SELinux:  Disabled at boot.
[    0.004164] AppArmor: AppArmor initialized
[    0.004184] Mount-cache hash table entries: 512
[    0.004538] Initializing cgroup subsys ns
[    0.004548] Initializing cgroup subsys cpuacct
[    0.004552] Initializing cgroup subsys memory
[    0.004562] Initializing cgroup subsys freezer
[    0.004592] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004597] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004638] Checking 'hlt' instruction... OK.
[    0.020839] SMP alternatives: switching to UP code
[    0.265028] Freeing SMP alternatives: 18k freed
[    0.265039] ACPI: Core revision 20080926
[    0.267563] ACPI: Checking initramfs for custom DSDT
[    0.735247] ACPI: setting ELCR to 0200 (from 0820)
[    0.736144] weird, boot CPU (#0) not listedby the BIOS.
[    0.736149] SMP motherboard not detected.
[    0.736155] Local APIC not detected. Using dummy APIC emulation.
[    0.736158] SMP disabled
[    0.736767] Brought up 1 CPUs
[    0.736773] Total of 1 processors activated (2489.25 BogoMIPS).
[    0.736802] CPU0 attaching NULL sched-domain.
[    0.737490] net_namespace: 776 bytes
[    0.737519] Booting paravirtualized kernel on bare hardware
[    0.737959] Time: 14:24:33  Date: 11/22/09
[    0.737972] regulator: core version 0.5
[    0.738061] NET: Registered protocol family 16
[    0.738332] EISA bus registered
[    0.738360] ACPI: bus type pci registered
[    0.741784] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[    0.741788] PCI: Using configuration type 1 for base access
[    0.744188] ACPI: EC: Look up EC in DSDT
[    0.752587] ACPI: Interpreter enabled
[    0.752598] ACPI: (supports S0 S1 S4 S5)
[    0.752627] ACPI: Using PIC for interrupt routing
[    0.760662] ACPI: No dock devices found.
[    0.760681] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.760767] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xd3ffffff]
[    0.760908] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.760956] pci 0000:00:02.1: reg 20 io port: [0xc00-0xc1f]
[    0.760993] pci 0000:00:02.2: reg 10 32bit mmio: [0xcfffe000-0xcfffefff]
[    0.761047] pci 0000:00:02.3: reg 10 32bit mmio: [0xcffff000-0xcfffffff]
[    0.761121] pci 0000:00:02.5: reg 20 io port: [0xff00-0xff0f]
[    0.761176] pci 0000:00:02.7: reg 10 io port: [0xdc00-0xdcff]
[    0.761185] pci 0000:00:02.7: reg 14 io port: [0xd800-0xd83f]
[    0.761223] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.761229] pci 0000:00:02.7: PME# disabled
[    0.761266] pci 0000:00:03.0: reg 10 io port: [0xd400-0xd4ff]
[    0.761275] pci 0000:00:03.0: reg 14 32bit mmio: [0xcffcd000-0xcffcdfff]
[    0.761304] pci 0000:00:03.0: reg 30 32bit mmio: [0xcffa0000-0xcffbffff]
[    0.761316] pci 0000:00:03.0: supports D1 D2
[    0.761319] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.761325] pci 0000:00:03.0: PME# disabled
[    0.761399] pci 0000:00:13.0: reg 20 io port: [0xcc00-0xcc1f]
[    0.761420] pci 0000:00:13.0: PME# supported from D0 D3hot D3cold
[    0.761426] pci 0000:00:13.0: PME# disabled
[    0.761481] pci 0000:00:13.1: reg 20 io port: [0xd000-0xd01f]
[    0.761502] pci 0000:00:13.1: PME# supported from D0 D3hot D3cold
[    0.761507] pci 0000:00:13.1: PME# disabled
[    0.761543] pci 0000:00:13.2: reg 10 32bit mmio: [0xcfffdf00-0xcfffdfff]
[    0.761583] pci 0000:00:13.2: PME# supported from D0 D3hot D3cold
[    0.761589] pci 0000:00:13.2: PME# disabled
[    0.761663] pci 0000:01:00.0: reg 10 32bit mmio: [0xc8000000-0xcbffffff]
[    0.761673] pci 0000:01:00.0: reg 14 io port: [0xa800-0xa8ff]
[    0.761681] pci 0000:01:00.0: reg 18 32bit mmio: [0xcfefc000-0xcfefffff]
[    0.761705] pci 0000:01:00.0: reg 30 32bit mmio: [0xcfec0000-0xcfedffff]
[    0.761719] pci 0000:01:00.0: supports D1
[    0.761766] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.761772] pci 0000:00:01.0: bridge 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.761779] pci 0000:00:01.0: bridge 32bit mmio pref: [0xc7c00000-0xcfcfffff]
[    0.761790] bus 00 -> node 0
[    0.761801] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.763812] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.764035] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[    0.764242] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 12 14 15)
[    0.764450] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 12 14 15)
[    0.764655] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[    0.764862] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[    0.765068] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 12 14 15)
[    0.765274] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 12 14 15)
[    0.765416] ACPI: Power Resource [URP1] (off)
[    0.765472] ACPI: Power Resource [URP2] (off)
[    0.765544] ACPI: Power Resource [FDDP] (off)
[    0.765599] ACPI: Power Resource [LPTP] (off)
[    0.765712] ACPI: WMI: Mapper loaded
[    0.766168] SCSI subsystem initialized
[    0.766266] libata version 3.00 loaded.
[    0.766370] usbcore: registered new interface driver usbfs
[    0.766405] usbcore: registered new interface driver hub
[    0.766464] usbcore: registered new device driver usb
[    0.766714] PCI: Using ACPI for IRQ routing
[    0.766881] Bluetooth: Core ver 2.13
[    0.766881] NET: Registered protocol family 31
[    0.766881] Bluetooth: HCI device and connection manager initialized
[    0.766881] Bluetooth: HCI socket layer initialized
[    0.766881] NET: Registered protocol family 8
[    0.766881] NET: Registered protocol family 20
[    0.766881] NetLabel: Initializing
[    0.766881] NetLabel:  domain hash size = 128
[    0.766881] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.766881] NetLabel:  unlabeled traffic allowed by default
[    0.766881] AppArmor: AppArmor Filesystem Enabled
[    0.766881] pnp: PnP ACPI init
[    0.766881] ACPI: bus type pnp registered
[    0.774281] pnp: PnP ACPI: found 13 devices
[    0.774286] ACPI: ACPI bus type pnp unregistered
[    0.774295] PnPBIOS: Disabled by ACPI PNP
[    0.809181] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.809187] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.809196] pci 0000:00:01.0:   MEM window: 0xcfe00000-0xcfefffff
[    0.809203] pci 0000:00:01.0:   PREFETCH window: 0x000000c7c00000-0x000000cfcfffff
[    0.809227] bus: 00 index 0 io port: [0x00-0xffff]
[    0.809231] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.809235] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.809238] bus: 01 index 1 mmio: [0xcfe00000-0xcfefffff]
[    0.809242] bus: 01 index 2 mmio: [0xc7c00000-0xcfcfffff]
[    0.809245] bus: 01 index 3 mmio: [0x0-0x0]
[    0.809270] NET: Registered protocol family 2
[    0.809507] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.810226] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.812953] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.814242] TCP: Hash tables configured (established 131072 bind 65536)
[    0.814250] TCP reno registered
[    0.814530] NET: Registered protocol family 1
[    0.814801] checking if image is initramfs... it is
[    1.312097] Switched to high resolution mode on CPU 0
[    1.855278] Freeing initrd memory: 7368k freed
[    1.855487] cpufreq: No nForce2 chipset.
[    1.855760] audit: initializing netlink socket (disabled)
[    1.855806] type=2000 audit(1258899873.852:1): initialized
[    1.868512] highmem bounce pool size: 64 pages
[    1.868525] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.870780] VFS: Disk quotas dquot_6.5.1
[    1.870881] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.871928] fuse init (API version 7.10)
[    1.872135] msgmni has been set to 1717
[    1.872542] alg: No test for stdrng (krng)
[    1.872566] io scheduler noop registered
[    1.872570] io scheduler anticipatory registered
[    1.872574] io scheduler deadline registered
[    1.872603] io scheduler cfq registered (default)
[    1.872759] pci 0000:01:00.0: Boot video device
[    1.879101] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.879118] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.879360] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.879365] ACPI: Power Button (FF) [PWRF]
[    1.879452] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.879462] ACPI: Sleep Button (CM) [SLPB]
[    1.879690] processor ACPI_CPU:00: registered as cooling_device0
[    1.883123] isapnp: Scanning for PnP cards...
[    2.236546] isapnp: No Plug & Play device found
[    2.238879] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.239035] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.239160] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.239586] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.239760] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.241133] brd: module loaded
[    2.241699] loop: module loaded
[    2.241883] Fixed MDIO Bus: probed
[    2.241895] PPP generic driver version 2.4.2
[    2.242014] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.242081] Driver 'sd' needs updating - please use bus_type methods
[    2.242097] Driver 'sr' needs updating - please use bus_type methods
[    2.242991] pata_sis 0000:00:02.5: version 0.5.2
[    2.243391] scsi0 : pata_sis
[    2.243600] scsi1 : pata_sis
[    2.245115] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.245121] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.408587] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    2.408592] ata1.00: 160086528 sectors, multi 16: LBA 
[    2.424418] ata1.00: configured for UDMA/100
[    2.596384] ata2.00: ATAPI: LITE-ON LTR-48125W, VS04, max UDMA/33
[    2.596432] ata2.01: ATAPI: SAMSUNG CD-ROM  SC-148C, B104, max UDMA/33
[    2.612278] ata2.00: configured for UDMA/33
[    2.628282] ata2.01: configured for UDMA/33
[    2.649591] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    2.649792] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors: (81.9 GB/76.3 GiB)
[    2.649828] sd 0:0:0:0: [sda] Write Protect is off
[    2.649833] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.649885] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.650032] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors: (81.9 GB/76.3 GiB)
[    2.650061] sd 0:0:0:0: [sda] Write Protect is off
[    2.650065] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.650113] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.650122]  sda: sda1 sda2 < sda5 >
[    2.711756] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.711862] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.716627] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-48125W       VS04 PQ: 0 ANSI: 5
[    2.765262] sr0: scsi3-mmc drive: 75x/48x writer cd/rw xa/form2 cdda tray
[    2.765269] Uniform CD-ROM driver Revision: 3.20
[    2.765475] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.765547] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.765833] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   B104 PQ: 0 ANSI: 5
[    2.768631] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    2.768742] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    2.768801] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    2.769068] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.769484] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[    2.769491] PCI: setting IRQ 5 as level-triggered
[    2.769498] ehci_hcd 0000:00:13.2: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    2.769561] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.769686] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.769770] ehci_hcd 0000:00:13.2: irq 5, io mem 0xcfffdf00
[    2.780056] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 0.95
[    2.780191] usb usb1: configuration #1 chosen from 1 choice
[    2.780243] hub 1-0:1.0: USB hub found
[    2.780266] hub 1-0:1.0: 4 ports detected
[    2.780455] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.780760] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[    2.780768] ohci_hcd 0000:00:02.2: PCI INT D -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
[    2.780796] ohci_hcd 0000:00:02.2: OHCI Host Controller
[    2.780875] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 2
[    2.780904] ohci_hcd 0000:00:02.2: irq 5, io mem 0xcfffe000
[    2.838116] usb usb2: configuration #1 chosen from 1 choice
[    2.838161] hub 2-0:1.0: USB hub found
[    2.838183] hub 2-0:1.0: 3 ports detected
[    2.838578] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[    2.838585] ohci_hcd 0000:00:02.3: PCI INT A -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
[    2.838606] ohci_hcd 0000:00:02.3: OHCI Host Controller
[    2.838698] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 3
[    2.838724] ohci_hcd 0000:00:02.3: irq 5, io mem 0xcffff000
[    2.894097] usb usb3: configuration #1 chosen from 1 choice
[    2.894140] hub 3-0:1.0: USB hub found
[    2.894159] hub 3-0:1.0: 3 ports detected
[    2.894308] uhci_hcd: USB Universal Host Controller Interface driver
[    2.894707] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    2.894713] PCI: setting IRQ 11 as level-triggered
[    2.894719] uhci_hcd 0000:00:13.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.894733] uhci_hcd 0000:00:13.0: UHCI Host Controller
[    2.894828] uhci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    2.894864] uhci_hcd 0000:00:13.0: irq 11, io base 0x0000cc00
[    2.895005] usb usb4: configuration #1 chosen from 1 choice
[    2.895059] hub 4-0:1.0: USB hub found
[    2.895080] hub 4-0:1.0: 2 ports detected
[    2.895453] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    2.895459] uhci_hcd 0000:00:13.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.895468] uhci_hcd 0000:00:13.1: UHCI Host Controller
[    2.895585] uhci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 5
[    2.895610] uhci_hcd 0000:00:13.1: irq 11, io base 0x0000d000
[    2.895758] usb usb5: configuration #1 chosen from 1 choice
[    2.895800] hub 5-0:1.0: USB hub found
[    2.895817] hub 5-0:1.0: 2 ports detected
[    2.896092] usbcore: registered new interface driver libusual
[    2.896170] usbcore: registered new interface driver usbserial
[    2.896190] USB Serial support registered for generic
[    2.896213] usbcore: registered new interface driver usbserial_generic
[    2.896217] usbserial: USB Serial Driver core
[    2.896300] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.896602] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.896623] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.896858] mice: PS/2 mouse device common for all mice
[    2.897155] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.897182] rtc0: alarms up to one month, 114 bytes nvram
[    2.897339] device-mapper: uevent: version 1.0.3
[    2.897569] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.897684] device-mapper: multipath: version 1.0.5 loaded
[    2.897690] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.897870] EISA: Probing bus 0 at eisa.0
[    2.897915] EISA: Detected 0 cards.
[    2.897975] cpuidle: using governor ladder
[    2.897979] cpuidle: using governor menu
[    2.898890] TCP cubic registered
[    2.899054] NET: Registered protocol family 10
[    2.899790] lo: Disabled Privacy Extensions
[    2.900409] NET: Registered protocol family 17
[    2.900448] Bluetooth: L2CAP ver 2.11
[    2.900452] Bluetooth: L2CAP socket layer initialized
[    2.900457] Bluetooth: SCO (Voice Link) ver 0.6
[    2.900460] Bluetooth: SCO socket layer initialized
[    2.900538] Bluetooth: RFCOMM socket layer initialized
[    2.900557] Bluetooth: RFCOMM TTY layer initialized
[    2.900560] Bluetooth: RFCOMM ver 1.10
[    2.900601] powernow-k8: Processor cpuid 680 not supported
[    2.900648] IO APIC resources could be not be allocated.
[    2.900703] Using IPI No-Shortcut mode
[    2.900898] registered taskstats version 1
[    2.901115]   Magic number: 1:543:435
[    2.901307] rtc_cmos 00:02: setting system clock to 2009-11-22 14:24:35 UTC (1258899875)
[    2.901313] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.901317] EDD information not available.
[    2.902788] Freeing unused kernel memory: 532k freed
[    2.903010] Write protecting the kernel text: 4128k
[    2.903077] Write protecting the kernel read-only data: 1532k
[    2.936315] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.093404] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    3.453352] FDC 0 is a post-1991 82077
[    3.492242] usb 1-3: configuration #1 chosen from 1 choice
[    3.510247] Initializing USB Mass Storage driver...
[    3.516865] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.517832] usbcore: registered new interface driver usb-storage
[    3.517843] USB Mass Storage support registered.
[    3.518063] usb-storage: device found at 2
[    3.518066] usb-storage: waiting for device to settle before scanning
[    3.614250] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    3.645778] sis900.c: v1.08.10 Apr. 2 2006
[    3.646273] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
[    3.646282] sis900 0000:00:03.0: PCI INT A -> Link[LNKG] -> GSI 5 (level, low) -> IRQ 5
[    3.647282] 0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
[    3.657597] 0000:00:03.0: Using transceiver found at address 1 as default
[    3.661579] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 5, 00:0a:e6:64:ba:c8
[    3.777835] usb 1-4: configuration #1 chosen from 1 choice
[    4.526306] PM: Starting manual resume from disk
[    4.526316] PM: Resume from partition 8:5
[    4.526319] PM: Checking hibernation image.
[    4.526664] PM: Resume from disk failed.
[    4.587342] kjournald starting.  Commit interval 5 seconds
[    4.587373] EXT3-fs: mounted filesystem with ordered data mode.
[    8.516357] usb-storage: device scan complete
[    8.517151] scsi 2:0:0:0: Direct-Access     FLASH    Drive AU_USB20   8.07 PQ: 0 ANSI: 2
[    8.518997] sd 2:0:0:0: [sdb] 4104192 512-byte hardware sectors: (2.10 GB/1.95 GiB)
[    8.519489] sd 2:0:0:0: [sdb] Write Protect is off
[    8.519495] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    8.519500] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.521116] sd 2:0:0:0: [sdb] 4104192 512-byte hardware sectors: (2.10 GB/1.95 GiB)
[    8.521613] sd 2:0:0:0: [sdb] Write Protect is off
[    8.521618] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    8.521622] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.521630]  sdb:
[    8.602408] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    8.602561] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   10.407404] udev: starting version 141
[   10.669124] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.699009] Linux agpgart interface v0.103
[   10.776442] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[   10.779034] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   10.779049] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
[   10.779053] ACPI: Device needs an ACPI driver
[   10.787842] parport_pc 00:0a: reported by Plug and Play ACPI
[   10.787915] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.804080] agpgart-sis 0000:00:00.0: SiS chipset [1039/0735]
[   10.810754] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   11.114294] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   11.290601] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.789398] psmouse serio1: ID: 10 00 64<6>Intel ICH 0000:00:02.7: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   12.204122] intel8x0_measure_ac97_clock: measured 55693 usecs
[   12.204132] intel8x0: clocking to 48000
[   12.246022] ppdev: user-space parallel port driver
[   12.351367] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   12.688088] lp0: using parport0 (interrupt-driven).
[   12.892379] Adding 3301316k swap on /dev/sda5.  Priority:-1 extents:1 across:3301316k
[   13.488596] EXT3 FS on sda1, internal journal
[   14.969934] type=1505 audit(1258899887.566:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1902
[   15.083362] type=1505 audit(1258899887.678:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1906
[   15.083877] type=1505 audit(1258899887.678:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1906
[   15.084097] type=1505 audit(1258899887.682:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1906
[   15.084237] type=1505 audit(1258899887.682:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1906
[   15.399165] type=1505 audit(1258899887.994:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1911
[   15.399800] type=1505 audit(1258899887.994:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1911
[   15.468296] type=1505 audit(1258899888.066:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1915
[   18.969303] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.969311] Bluetooth: BNEP filters: protocol multicast
[   19.035967] Bridge firewalling registered
[   20.621263] mtrr: no MTRR for c8000000,2000000 found
[   20.936361] [drm] Initialized drm 1.1.0 20060810
[   21.021597] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   21.021832] [drm] Initialized r128 2.5.0 20030725 on minor 0
[   21.203412] agpgart-sis 0000:00:00.0: AGP 2.0 bridge
[   21.203453] agpgart-sis 0000:00:00.0: putting AGP V2 device into 1x mode
[   21.203505] pci 0000:01:00.0: putting AGP V2 device into 1x mode
cat: 1: No such file or directory
cat: grep: No such file or directory
cat: blue*: No such file or directory
[EMAIL="steven@steven:~$"]steven@steven:~$[/EMAIL]

---

### Post by coffeeaddict22 on 2009-11-23
OK.  Sorry, the "Blue*" bit was a brain fart.  However, there doesn't appear to be a lot in the dmesg log about the USB adapter.  Can you try ```
cat /var/log/messages | grep usb
```?

Couple of points.  In Linux, the middle mouse button is usually set up so most of the time you can highlight a piece of text, move to where you want it, and a middle mouse click will paste it there.

Second, that earlier comment about becoming superuser.  The "superuser", or "root" is the admin login that gives you the ability to alter the system any way you want.  Without it, you're a user but can't access any of the sensitive stuff, and most definitely can't modify it.  It's the source of a lot of Linux's security, particularly compared to other operating systems.  Some Linux distributions allow you to log in to the root account; Ubuntu explicitly stops you from doing that (yes, you can change that if you try hard enough, but it defeats the purpose of running Ubuntu).
To "elevate your priviledges" to superuser, enter the relevant command with the word sudo in front of it- eg sudo lshw.  But, be careful.  If you don't understand a command, don't run it with sudo in front of it.  There have been cases of idiots leaving commands around that would fry your system; as a rule if it's on these forums you should be OK, because they're moderated in the main, but not in real time, so that doesn't excuse you from both learning and using your common sense.

Final tip.  If you run a command, then realise you needed root priviledges to do that successfully, just type "sudo !!" and the previous command is repeated with superuser priviledges.

---

### Post by scooba61709 on 2009-11-23
first what is it u are looking for n here is what i got from the last command i put in n 
 
[    1.870275] io scheduler cfq registered (default)
[    1.870436] pci 0000:01:00.0: Boot video device
[    1.876829] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.876846] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.877091] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.877098] ACPI: Power Button (FF) [PWRF]
[    1.877185] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.877197] ACPI: Sleep Button (CM) [SLPB]
[    1.877441] processor ACPI_CPU:00: registered as cooling_device0
[    1.880917] isapnp: Scanning for PnP cards...
[    2.234347] isapnp: No Plug & Play device found
[    2.236786] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.236944] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.237070] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.237509] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.237686] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.239100] brd: module loaded
[    2.239687] loop: module loaded
[    2.239873] Fixed MDIO Bus: probed
[    2.239886] PPP generic driver version 2.4.2
[    2.240076] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.240143] Driver 'sd' needs updating - please use bus_type methods
[    2.240159] Driver 'sr' needs updating - please use bus_type methods
[    2.241097] pata_sis 0000:00:02.5: version 0.5.2
[    2.241501] scsi0 : pata_sis
[    2.241721] scsi1 : pata_sis
[    2.243192] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.243198] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.404588] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    2.404593] ata1.00: 160086528 sectors, multi 16: LBA 
[    2.420425] ata1.00: configured for UDMA/100
[    2.592384] ata2.00: ATAPI: LITE-ON LTR-48125W, VS04, max UDMA/33
[    2.592431] ata2.01: ATAPI: SAMSUNG CD-ROM  SC-148C, B104, max UDMA/33
[    2.608279] ata2.00: configured for UDMA/33
[    2.624282] ata2.01: configured for UDMA/33
[    2.645468] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    2.645675] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors: (81.9 GB/76.3 GiB)
[    2.645712] sd 0:0:0:0: [sda] Write Protect is off
[    2.645717] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.645770] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.645921] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors: (81.9 GB/76.3 GiB)
[    2.645949] sd 0:0:0:0: [sda] Write Protect is off
[    2.645954] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.646004] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.646013]  sda: sda1 sda2 < sda5 >
[    2.713273] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.713384] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.718143] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-48125W       VS04 PQ: 0 ANSI: 5
[    2.767612] sr0: scsi3-mmc drive: 67x/48x writer cd/rw xa/form2 cdda tray
[    2.767620] Uniform CD-ROM driver Revision: 3.20
[    2.767840] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.767914] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.768220] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   B104 PQ: 0 ANSI: 5
[    2.771057] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    2.771176] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    2.771238] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    2.771511] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.771938] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[    2.771945] PCI: setting IRQ 5 as level-triggered
[    2.771952] ehci_hcd 0000:00:13.2: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    2.772056] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.772186] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.772272] ehci_hcd 0000:00:13.2: irq 5, io mem 0xcfffdf00
[    2.784035] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 0.95
[    2.784174] usb usb1: configuration #1 chosen from 1 choice
[    2.784227] hub 1-0:1.0: USB hub found
[    2.784250] hub 1-0:1.0: 4 ports detected
[    2.784445] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.784758] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[    2.784766] ohci_hcd 0000:00:02.2: PCI INT D -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
[    2.784793] ohci_hcd 0000:00:02.2: OHCI Host Controller
[    2.784874] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 2
[    2.784904] ohci_hcd 0000:00:02.2: irq 5, io mem 0xcfffe000
[    2.842120] usb usb2: configuration #1 chosen from 1 choice
[    2.842165] hub 2-0:1.0: USB hub found
[    2.842187] hub 2-0:1.0: 3 ports detected
[    2.842600] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[    2.842607] ohci_hcd 0000:00:02.3: PCI INT A -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
[    2.842630] ohci_hcd 0000:00:02.3: OHCI Host Controller
[    2.842725] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 3
[    2.842754] ohci_hcd 0000:00:02.3: irq 5, io mem 0xcffff000
[    2.898101] usb usb3: configuration #1 chosen from 1 choice
[    2.898143] hub 3-0:1.0: USB hub found
[    2.898163] hub 3-0:1.0: 3 ports detected
[    2.898317] uhci_hcd: USB Universal Host Controller Interface driver
[    2.898728] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    2.898734] PCI: setting IRQ 11 as level-triggered
[    2.898741] uhci_hcd 0000:00:13.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.898755] uhci_hcd 0000:00:13.0: UHCI Host Controller
[    2.898856] uhci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    2.898893] uhci_hcd 0000:00:13.0: irq 11, io base 0x0000cc00
[    2.899037] usb usb4: configuration #1 chosen from 1 choice
[    2.899092] hub 4-0:1.0: USB hub found
[    2.899113] hub 4-0:1.0: 2 ports detected
[    2.899489] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    2.899495] uhci_hcd 0000:00:13.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.899505] uhci_hcd 0000:00:13.1: UHCI Host Controller
[    2.899611] uhci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 5
[    2.899636] uhci_hcd 0000:00:13.1: irq 11, io base 0x0000d000
[    2.899797] usb usb5: configuration #1 chosen from 1 choice
[    2.899838] hub 5-0:1.0: USB hub found
[    2.899856] hub 5-0:1.0: 2 ports detected
[    2.900135] usbcore: registered new interface driver libusual
[    2.900215] usbcore: registered new interface driver usbserial
[    2.900236] USB Serial support registered for generic
[    2.900260] usbcore: registered new interface driver usbserial_generic
[    2.900264] usbserial: USB Serial Driver core
[    2.900348] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.900653] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.900676] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.900917] mice: PS/2 mouse device common for all mice
[    2.901218] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.901245] rtc0: alarms up to one month, 114 bytes nvram
[    2.901408] device-mapper: uevent: version 1.0.3
[    2.901640] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.901759] device-mapper: multipath: version 1.0.5 loaded
[    2.901765] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.901952] EISA: Probing bus 0 at eisa.0
[    2.901997] EISA: Detected 0 cards.
[    2.902059] cpuidle: using governor ladder
[    2.902063] cpuidle: using governor menu
[    2.902981] TCP cubic registered
[    2.903148] NET: Registered protocol family 10
[    2.903927] lo: Disabled Privacy Extensions
[    2.904531] NET: Registered protocol family 17
[    2.904571] Bluetooth: L2CAP ver 2.11
[    2.904574] Bluetooth: L2CAP socket layer initialized
[    2.904580] Bluetooth: SCO (Voice Link) ver 0.6
[    2.904583] Bluetooth: SCO socket layer initialized
[    2.904663] Bluetooth: RFCOMM socket layer initialized
[    2.904682] Bluetooth: RFCOMM TTY layer initialized
[    2.904685] Bluetooth: RFCOMM ver 1.10
[    2.904725] powernow-k8: Processor cpuid 680 not supported
[    2.904786] IO APIC resources could be not be allocated.
[    2.904840] Using IPI No-Shortcut mode
[    2.905047] registered taskstats version 1
[    2.905256]   Magic number: 1:755:439
[    2.905456] rtc_cmos 00:02: setting system clock to 2009-11-22 16:24:30 UTC (1258907070)
[    2.905462] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.905466] EDD information not available.
[    2.906920] Freeing unused kernel memory: 532k freed
[    2.907142] Write protecting the kernel text: 4128k
[    2.907209] Write protecting the kernel read-only data: 1532k
[    2.940314] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.096887] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    3.254213] usb 1-4: configuration #1 chosen from 1 choice
[    3.448506] FDC 0 is a post-1991 82077
[    3.626146] sis900.c: v1.08.10 Apr. 2 2006
[    3.626761] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
[    3.626771] sis900 0000:00:03.0: PCI INT A -> Link[LNKG] -> GSI 5 (level, low) -> IRQ 5
[    3.627721] 0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
[    3.637501] 0000:00:03.0: Using transceiver found at address 1 as default
[    3.642657] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 5, 00:0a:e6:64:ba:c8
[    4.529998] PM: Starting manual resume from disk
[    4.530009] PM: Resume from partition 8:5
[    4.530012] PM: Checking hibernation image.
[    4.530362] PM: Resume from disk failed.
[    4.597227] kjournald starting.  Commit interval 5 seconds
[    4.597258] EXT3-fs: mounted filesystem with ordered data mode.
[   10.442465] udev: starting version 141
[   10.646777] Linux agpgart interface v0.103
[   10.664248] agpgart-sis 0000:00:00.0: SiS chipset [1039/0735]
[   10.670814] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   10.737494] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.825039] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[   10.858209] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   10.858223] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
[   10.858227] ACPI: Device needs an ACPI driver
[   11.000159] parport_pc 00:0a: reported by Plug and Play ACPI
[   11.000228] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.190942] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   11.280938] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.804518] psmouse serio1: ID: 10 00 64<6>Intel ICH 0000:00:02.7: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   12.188146] intel8x0_measure_ac97_clock: measured 55683 usecs
[   12.188156] intel8x0: clocking to 48000
[   12.214498] ppdev: user-space parallel port driver
[   12.376305] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   12.648233] lp0: using parport0 (interrupt-driven).
[   12.847858] Adding 3301316k swap on /dev/sda5.  Priority:-1 extents:1 across:3301316k
[   13.441577] EXT3 FS on sda1, internal journal
[   14.880426] type=1505 audit(1258907082.474:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1857
[   14.993245] type=1505 audit(1258907082.586:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1861
[   14.993805] type=1505 audit(1258907082.586:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1861
[   14.993970] type=1505 audit(1258907082.586:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1861
[   14.994100] type=1505 audit(1258907082.586:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1861
[   15.316469] type=1505 audit(1258907082.910:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1866
[   15.317185] type=1505 audit(1258907082.910:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1866
[   15.386689] type=1505 audit(1258907082.978:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1870
[   18.746475] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.746484] Bluetooth: BNEP filters: protocol multicast
[   18.813106] Bridge firewalling registered
[   20.481750] mtrr: no MTRR for c8000000,2000000 found
[   20.902161] [drm] Initialized drm 1.1.0 20060810
[   20.993145] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   20.993376] [drm] Initialized r128 2.5.0 20030725 on minor 0
[   21.164391] agpgart-sis 0000:00:00.0: AGP 2.0 bridge
[   21.164431] agpgart-sis 0000:00:00.0: putting AGP V2 device into 1x mode
[   21.164483] pci 0000:01:00.0: putting AGP V2 device into 1x mode
cat: 1: No such file or directory
cat: grep: No such file or directory
cat: usb: No such file or directory

---

### Post by scooba61709 on 2009-11-23
oops i put the wrong thingin be back on in a few have to set up the other puter lol

---

### Post by scooba61709 on 2009-11-23
Nov 22 09:52:04 steven kernel: [    0.268051] ACPI: Checking initramfs for custom DSDT
Nov 22 09:52:04 steven kernel: [    0.735715] ACPI: setting ELCR to 0200 (from 0820)
Nov 22 09:52:04 steven kernel: [    0.736140] weird, boot CPU (#0) not listedby the BIOS.
Nov 22 09:52:04 steven kernel: [    0.736146] SMP motherboard not detected.
Nov 22 09:52:04 steven kernel: [    0.736151] Local APIC not detected. Using dummy APIC emulation.
Nov 22 09:52:04 steven kernel: [    0.736155] SMP disabled
Nov 22 09:52:04 steven kernel: [    0.736766] Brought up 1 CPUs
Nov 22 09:52:04 steven kernel: [    0.736771] Total of 1 processors activated (2489.22 BogoMIPS).
Nov 22 09:52:04 steven kernel: [    0.737512] net_namespace: 776 bytes
Nov 22 09:52:04 steven kernel: [    0.737540] Booting paravirtualized kernel on bare hardware
Nov 22 09:52:04 steven kernel: [    0.737988] Time: 16:51:48  Date: 11/22/09
Nov 22 09:52:04 steven kernel: [    0.738001] regulator: core version 0.5
Nov 22 09:52:04 steven kernel: [    0.738091] NET: Registered protocol family 16
Nov 22 09:52:04 steven kernel: [    0.738368] EISA bus registered
Nov 22 09:52:04 steven kernel: [    0.738397] ACPI: bus type pci registered
Nov 22 09:52:04 steven kernel: [    0.742055] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
Nov 22 09:52:04 steven kernel: [    0.742060] PCI: Using configuration type 1 for base access
Nov 22 09:52:04 steven kernel: [    0.752879] ACPI: Interpreter enabled
Nov 22 09:52:04 steven kernel: [    0.752890] ACPI: (supports S0 S1 S4 S5)
Nov 22 09:52:04 steven kernel: [    0.752921] ACPI: Using PIC for interrupt routing
Nov 22 09:52:04 steven kernel: [    0.760925] ACPI: No dock devices found.
Nov 22 09:52:04 steven kernel: [    0.760944] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 22 09:52:04 steven kernel: [    0.761171] pci 0000:00:02.0: Enabling SiS 96x SMBus
Nov 22 09:52:04 steven kernel: [    0.761486] pci 0000:00:02.7: PME# supported from D3hot D3cold
Nov 22 09:52:04 steven kernel: [    0.761493] pci 0000:00:02.7: PME# disabled
Nov 22 09:52:04 steven kernel: [    0.761583] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 22 09:52:04 steven kernel: [    0.761589] pci 0000:00:03.0: PME# disabled
Nov 22 09:52:04 steven kernel: [    0.761684] pci 0000:00:13.0: PME# supported from D0 D3hot D3cold
Nov 22 09:52:04 steven kernel: [    0.761689] pci 0000:00:13.0: PME# disabled
Nov 22 09:52:04 steven kernel: [    0.761765] pci 0000:00:13.1: PME# supported from D0 D3hot D3cold
Nov 22 09:52:04 steven kernel: [    0.761770] pci 0000:00:13.1: PME# disabled
Nov 22 09:52:04 steven kernel: [    0.761846] pci 0000:00:13.2: PME# supported from D0 D3hot D3cold
Nov 22 09:52:04 steven kernel: [    0.761852] pci 0000:00:13.2: PME# disabled
Nov 22 09:52:04 steven kernel: [    0.764106] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
Nov 22 09:52:04 steven kernel: [    0.764314] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
Nov 22 09:52:04 steven kernel: [    0.764517] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 12 14 15)
Nov 22 09:52:04 steven kernel: [    0.764723] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 12 14 15)
Nov 22 09:52:04 steven kernel: [    0.764928] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
Nov 22 09:52:04 steven kernel: [    0.765134] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
Nov 22 09:52:04 steven kernel: [    0.765340] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 12 14 15)
Nov 22 09:52:04 steven kernel: [    0.765545] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 12 14 15)
Nov 22 09:52:04 steven kernel: [    0.765688] ACPI: Power Resource [URP1] (off)
Nov 22 09:52:04 steven kernel: [    0.765744] ACPI: Power Resource [URP2] (off)
Nov 22 09:52:04 steven kernel: [    0.765821] ACPI: Power Resource [FDDP] (off)
Nov 22 09:52:04 steven kernel: [    0.765877] ACPI: Power Resource [LPTP] (off)
Nov 22 09:52:04 steven kernel: [    0.765993] ACPI: WMI: Mapper loaded
Nov 22 09:52:04 steven kernel: [    0.766464] SCSI subsystem initialized
Nov 22 09:52:04 steven kernel: [    0.766674] usbcore: registered new interface driver usbfs
Nov 22 09:52:04 steven kernel: [    0.766709] usbcore: registered new interface driver hub
Nov 22 09:52:04 steven kernel: [    0.766769] usbcore: registered new device driver usb
Nov 22 09:52:04 steven kernel: [    0.767025] PCI: Using ACPI for IRQ routing
Nov 22 09:52:04 steven kernel: [    0.767202] Bluetooth: Core ver 2.13
Nov 22 09:52:04 steven kernel: [    0.767202] NET: Registered protocol family 31
Nov 22 09:52:04 steven kernel: [    0.767202] Bluetooth: HCI device and connection manager initialized
Nov 22 09:52:04 steven kernel: [    0.767202] Bluetooth: HCI socket layer initialized
Nov 22 09:52:04 steven kernel: [    0.767202] NET: Registered protocol family 8
Nov 22 09:52:04 steven kernel: [    0.767202] NET: Registered protocol family 20
Nov 22 09:52:04 steven kernel: [    0.767202] NetLabel: Initializing
Nov 22 09:52:04 steven kernel: [    0.767202] NetLabel:  domain hash size = 128
Nov 22 09:52:04 steven kernel: [    0.767202] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 22 09:52:04 steven kernel: [    0.767202] NetLabel:  unlabeled traffic allowed by default
Nov 22 09:52:04 steven kernel: [    0.767202] AppArmor: AppArmor Filesystem Enabled
Nov 22 09:52:04 steven kernel: [    0.767202] pnp: PnP ACPI init
Nov 22 09:52:04 steven kernel: [    0.767202] ACPI: bus type pnp registered
Nov 22 09:52:04 steven kernel: [    0.774572] pnp: PnP ACPI: found 13 devices
Nov 22 09:52:04 steven kernel: [    0.774576] ACPI: ACPI bus type pnp unregistered
Nov 22 09:52:04 steven kernel: [    0.774585] PnPBIOS: Disabled by ACPI PNP
Nov 22 09:52:04 steven kernel: [    0.809473] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Nov 22 09:52:04 steven kernel: [    0.809479] pci 0000:00:01.0:   IO window: 0xa000-0xafff
Nov 22 09:52:04 steven kernel: [    0.809488] pci 0000:00:01.0:   MEM window: 0xcfe00000-0xcfefffff
Nov 22 09:52:04 steven kernel: [    0.809495] pci 0000:00:01.0:   PREFETCH window: 0x000000c7c00000-0x000000cfcfffff
Nov 22 09:52:04 steven kernel: [    0.809519] bus: 00 index 0 io port: [0x00-0xffff]
Nov 22 09:52:04 steven kernel: [    0.809523] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Nov 22 09:52:04 steven kernel: [    0.809527] bus: 01 index 0 io port: [0xa000-0xafff]
Nov 22 09:52:04 steven kernel: [    0.809530] bus: 01 index 1 mmio: [0xcfe00000-0xcfefffff]
Nov 22 09:52:04 steven kernel: [    0.809534] bus: 01 index 2 mmio: [0xc7c00000-0xcfcfffff]
Nov 22 09:52:04 steven kernel: [    0.809537] bus: 01 index 3 mmio: [0x0-0x0]
Nov 22 09:52:04 steven kernel: [    0.809561] NET: Registered protocol family 2
Nov 22 09:52:04 steven kernel: [    0.809795] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Nov 22 09:52:04 steven kernel: [    0.810252] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Nov 22 09:52:04 steven kernel: [    0.810446] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Nov 22 09:52:04 steven kernel: [    0.810626] TCP: Hash tables configured (established 8192 bind 8192)
Nov 22 09:52:04 steven kernel: [    0.810631] TCP reno registered
Nov 22 09:52:04 steven kernel: [    0.810786] NET: Registered protocol family 1
Nov 22 09:52:04 steven kernel: [    0.811034] checking if image is initramfs... it is
Nov 22 09:52:04 steven kernel: [    1.853520] Freeing initrd memory: 7368k freed
Nov 22 09:52:04 steven kernel: [    1.853733] cpufreq: No nForce2 chipset.
Nov 22 09:52:04 steven kernel: [    1.854008] audit: initializing netlink socket (disabled)
Nov 22 09:52:04 steven kernel: [    1.854053] type=2000 audit(1258908708.852:1): initialized
Nov 22 09:52:04 steven kernel: [    1.866653] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov 22 09:52:04 steven kernel: [    1.868954] VFS: Disk quotas dquot_6.5.1
Nov 22 09:52:04 steven kernel: [    1.869056] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 22 09:52:04 steven kernel: [    1.870134] fuse init (API version 7.10)
Nov 22 09:52:04 steven kernel: [    1.870295] msgmni has been set to 488
Nov 22 09:52:04 steven kernel: [    1.870695] alg: No test for stdrng (krng)
Nov 22 09:52:04 steven kernel: [    1.870722] io scheduler noop registered
Nov 22 09:52:04 steven kernel: [    1.870726] io scheduler anticipatory registered
Nov 22 09:52:04 steven kernel: [    1.870730] io scheduler deadline registered
Nov 22 09:52:04 steven kernel: [    1.870758] io scheduler cfq registered (default)
Nov 22 09:52:04 steven kernel: [    1.877325] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 22 09:52:04 steven kernel: [    1.877342] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 22 09:52:04 steven kernel: [    1.877587] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Nov 22 09:52:04 steven kernel: [    1.877594] ACPI: Power Button (FF) [PWRF]
Nov 22 09:52:04 steven kernel: [    1.877682] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Nov 22 09:52:04 steven kernel: [    1.877694] ACPI: Sleep Button (CM) [SLPB]
Nov 22 09:52:04 steven kernel: [    1.877936] processor ACPI_CPU:00: registered as cooling_device0
Nov 22 09:52:04 steven kernel: [    1.881408] isapnp: Scanning for PnP cards...
Nov 22 09:52:04 steven kernel: [    2.234836] isapnp: No Plug & Play device found
Nov 22 09:52:04 steven kernel: [    2.237270] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Nov 22 09:52:04 steven kernel: [    2.237430] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 22 09:52:04 steven kernel: [    2.237555] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 22 09:52:04 steven kernel: [    2.237992] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 22 09:52:04 steven kernel: [    2.238169] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 22 09:52:04 steven kernel: [    2.239580] brd: module loaded
Nov 22 09:52:04 steven kernel: [    2.240232] loop: module loaded
Nov 22 09:52:04 steven kernel: [    2.240423] Fixed MDIO Bus: probed
Nov 22 09:52:04 steven kernel: [    2.240435] PPP generic driver version 2.4.2
Nov 22 09:52:04 steven kernel: [    2.240557] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Nov 22 09:52:04 steven kernel: [    2.240625] Driver 'sd' needs updating - please use bus_type methods
Nov 22 09:52:04 steven kernel: [    2.240641] Driver 'sr' needs updating - please use bus_type methods
Nov 22 09:52:04 steven kernel: [    2.241991] scsi0 : pata_sis
Nov 22 09:52:04 steven kernel: [    2.242211] scsi1 : pata_sis
Nov 22 09:52:04 steven kernel: [    2.243684] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Nov 22 09:52:04 steven kernel: [    2.243690] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Nov 22 09:52:04 steven kernel: [    2.404588] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
Nov 22 09:52:04 steven kernel: [    2.404594] ata1.00: 160086528 sectors, multi 16: LBA 
Nov 22 09:52:04 steven kernel: [    2.420401] ata1.00: configured for UDMA/100
Nov 22 09:52:04 steven kernel: [    2.592383] ata2.00: ATAPI: LITE-ON LTR-48125W, VS04, max UDMA/33
Nov 22 09:52:04 steven kernel: [    2.592431] ata2.01: ATAPI: SAMSUNG CD-ROM  SC-148C, B104, max UDMA/33
Nov 22 09:52:04 steven kernel: [    2.608279] ata2.00: configured for UDMA/33
Nov 22 09:52:04 steven kernel: [    2.624282] ata2.01: configured for UDMA/33
Nov 22 09:52:04 steven kernel: [    2.645501] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
Nov 22 09:52:04 steven kernel: [    2.645708] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors: (81.9 GB/76.3 GiB)
Nov 22 09:52:04 steven kernel: [    2.645746] sd 0:0:0:0: [sda] Write Protect is off
Nov 22 09:52:04 steven kernel: [    2.645804] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 22 09:52:04 steven kernel: [    2.645955] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors: (81.9 GB/76.3 GiB)
Nov 22 09:52:04 steven kernel: [    2.645984] sd 0:0:0:0: [sda] Write Protect is off
Nov 22 09:52:04 steven kernel: [    2.646038] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 22 09:52:04 steven kernel: [    2.646047]  sda: sda1 sda2 < sda5 >
Nov 22 09:52:04 steven kernel: [    2.712799] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 22 09:52:04 steven kernel: [    2.712910] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 22 09:52:04 steven kernel: [    2.717680] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-48125W       VS04 PQ: 0 ANSI: 5
Nov 22 09:52:04 steven kernel: [    2.767167] sr0: scsi3-mmc drive: 75x/48x writer cd/rw xa/form2 cdda tray
Nov 22 09:52:04 steven kernel: [    2.767174] Uniform CD-ROM driver Revision: 3.20
Nov 22 09:52:04 steven kernel: [    2.767464] sr 1:0:0:0: Attached scsi generic sg1 type 5
Nov 22 09:52:04 steven kernel: [    2.767751] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   B104 PQ: 0 ANSI: 5
Nov 22 09:52:04 steven kernel: [    2.770603] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
Nov 22 09:52:04 steven kernel: [    2.770783] sr 1:0:1:0: Attached scsi generic sg2 type 5
Nov 22 09:52:04 steven kernel: [    2.771056] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 22 09:52:04 steven kernel: [    2.771481] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
Nov 22 09:52:04 steven kernel: [    2.771495] ehci_hcd 0000:00:13.2: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
Nov 22 09:52:04 steven kernel: [    2.771560] ehci_hcd 0000:00:13.2: EHCI Host Controller
Nov 22 09:52:04 steven kernel: [    2.771688] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
Nov 22 09:52:04 steven kernel: [    2.771775] ehci_hcd 0000:00:13.2: irq 5, io mem 0xcfffdf00
Nov 22 09:52:04 steven kernel: [    2.780057] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 0.95
Nov 22 09:52:04 steven kernel: [    2.780196] usb usb1: configuration #1 chosen from 1 choice
Nov 22 09:52:04 steven kernel: [    2.780249] hub 1-0:1.0: USB hub found
Nov 22 09:52:04 steven kernel: [    2.780273] hub 1-0:1.0: 4 ports detected
Nov 22 09:52:04 steven kernel: [    2.780468] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 22 09:52:04 steven kernel: [    2.780779] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
Nov 22 09:52:04 steven kernel: [    2.780787] ohci_hcd 0000:00:02.2: PCI INT D -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
Nov 22 09:52:04 steven kernel: [    2.780815] ohci_hcd 0000:00:02.2: OHCI Host Controller
Nov 22 09:52:04 steven kernel: [    2.780896] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 2
Nov 22 09:52:04 steven kernel: [    2.780926] ohci_hcd 0000:00:02.2: irq 5, io mem 0xcfffe000
Nov 22 09:52:04 steven kernel: [    2.838119] usb usb2: configuration #1 chosen from 1 choice
Nov 22 09:52:04 steven kernel: [    2.838165] hub 2-0:1.0: USB hub found
Nov 22 09:52:04 steven kernel: [    2.838187] hub 2-0:1.0: 3 ports detected
Nov 22 09:52:04 steven kernel: [    2.838600] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
Nov 22 09:52:04 steven kernel: [    2.838607] ohci_hcd 0000:00:02.3: PCI INT A -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
Nov 22 09:52:04 steven kernel: [    2.838629] ohci_hcd 0000:00:02.3: OHCI Host Controller
Nov 22 09:52:04 steven kernel: [    2.838725] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 3
Nov 22 09:52:04 steven kernel: [    2.838753] ohci_hcd 0000:00:02.3: irq 5, io mem 0xcffff000
Nov 22 09:52:04 steven kernel: [    2.894099] usb usb3: configuration #1 chosen from 1 choice
Nov 22 09:52:04 steven kernel: [    2.894142] hub 3-0:1.0: USB hub found
Nov 22 09:52:04 steven kernel: [    2.894162] hub 3-0:1.0: 3 ports detected
Nov 22 09:52:04 steven kernel: [    2.894316] uhci_hcd: USB Universal Host Controller Interface driver
Nov 22 09:52:04 steven kernel: [    2.894727] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Nov 22 09:52:04 steven kernel: [    2.894739] uhci_hcd 0000:00:13.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Nov 22 09:52:04 steven kernel: [    2.894752] uhci_hcd 0000:00:13.0: UHCI Host Controller
Nov 22 09:52:04 steven kernel: [    2.894853] uhci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
Nov 22 09:52:04 steven kernel: [    2.894890] uhci_hcd 0000:00:13.0: irq 11, io base 0x0000cc00
Nov 22 09:52:04 steven kernel: [    2.895035] usb usb4: configuration #1 chosen from 1 choice
Nov 22 09:52:04 steven kernel: [    2.895092] hub 4-0:1.0: USB hub found
Nov 22 09:52:04 steven kernel: [    2.895113] hub 4-0:1.0: 2 ports detected
Nov 22 09:52:04 steven kernel: [    2.895488] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Nov 22 09:52:04 steven kernel: [    2.895495] uhci_hcd 0000:00:13.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Nov 22 09:52:04 steven kernel: [    2.895504] uhci_hcd 0000:00:13.1: UHCI Host Controller
Nov 22 09:52:04 steven kernel: [    2.895609] uhci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 5
Nov 22 09:52:04 steven kernel: [    2.895634] uhci_hcd 0000:00:13.1: irq 11, io base 0x0000d000
Nov 22 09:52:04 steven kernel: [    2.895794] usb usb5: configuration #1 chosen from 1 choice
Nov 22 09:52:04 steven kernel: [    2.895836] hub 5-0:1.0: USB hub found
Nov 22 09:52:04 steven kernel: [    2.895854] hub 5-0:1.0: 2 ports detected
Nov 22 09:52:04 steven kernel: [    2.896130] usbcore: registered new interface driver libusual
Nov 22 09:52:04 steven kernel: [    2.896210] usbcore: registered new interface driver usbserial
Nov 22 09:52:04 steven kernel: [    2.896231] USB Serial support registered for generic
Nov 22 09:52:04 steven kernel: [    2.896254] usbcore: registered new interface driver usbserial_generic
Nov 22 09:52:04 steven kernel: [    2.896259] usbserial: USB Serial Driver core
Nov 22 09:52:04 steven kernel: [    2.896344] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 22 09:52:04 steven kernel: [    2.896647] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 22 09:52:04 steven kernel: [    2.896671] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 22 09:52:04 steven kernel: [    2.896914] mice: PS/2 mouse device common for all mice
Nov 22 09:52:04 steven kernel: [    2.897215] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Nov 22 09:52:04 steven kernel: [    2.897242] rtc0: alarms up to one month, 114 bytes nvram
Nov 22 09:52:04 steven kernel: [    2.897406] device-mapper: uevent: version 1.0.3
Nov 22 09:52:04 steven kernel: [    2.897640] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Nov 22 09:52:04 steven kernel: [    2.897758] device-mapper: multipath: version 1.0.5 loaded
Nov 22 09:52:04 steven kernel: [    2.897764] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 22 09:52:04 steven kernel: [    2.897951] EISA: Probing bus 0 at eisa.0
Nov 22 09:52:04 steven kernel: [    2.897996] EISA: Detected 0 cards.
Nov 22 09:52:04 steven kernel: [    2.898059] cpuidle: using governor ladder
Nov 22 09:52:04 steven kernel: [    2.898064] cpuidle: using governor menu
Nov 22 09:52:04 steven kernel: [    2.898981] TCP cubic registered
Nov 22 09:52:04 steven kernel: [    2.899146] NET: Registered protocol family 10
Nov 22 09:52:04 steven kernel: [    2.899894] lo: Disabled Privacy Extensions
Nov 22 09:52:04 steven kernel: [    2.900516] NET: Registered protocol family 17
Nov 22 09:52:04 steven kernel: [    2.900555] Bluetooth: L2CAP ver 2.11
Nov 22 09:52:04 steven kernel: [    2.900559] Bluetooth: L2CAP socket layer initialized
Nov 22 09:52:04 steven kernel: [    2.900564] Bluetooth: SCO (Voice Link) ver 0.6
Nov 22 09:52:04 steven kernel: [    2.900567] Bluetooth: SCO socket layer initialized
Nov 22 09:52:04 steven kernel: [    2.900649] Bluetooth: RFCOMM socket layer initialized
Nov 22 09:52:04 steven kernel: [    2.900668] Bluetooth: RFCOMM TTY layer initialized
Nov 22 09:52:04 steven kernel: [    2.900671] Bluetooth: RFCOMM ver 1.10
Nov 22 09:52:04 steven kernel: [    2.900712] powernow-k8: Processor cpuid 680 not supported
Nov 22 09:52:04 steven kernel: [    2.900817] Using IPI No-Shortcut mode
Nov 22 09:52:04 steven kernel: [    2.901021] registered taskstats version 1
Nov 22 09:52:04 steven kernel: [    2.901231]   Magic number: 1:720:894
Nov 22 09:52:04 steven kernel: [    2.901450] rtc_cmos 00:02: setting system clock to 2009-11-22 16:51:50 UTC (1258908710)
Nov 22 09:52:04 steven kernel: [    2.901456] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 22 09:52:04 steven kernel: [    2.901460] EDD information not available.
Nov 22 09:52:04 steven kernel: [    2.902939] Freeing unused kernel memory: 532k freed
Nov 22 09:52:04 steven kernel: [    2.903162] Write protecting the kernel text: 4128k
Nov 22 09:52:04 steven kernel: [    2.903229] Write protecting the kernel read-only data: 1532k
Nov 22 09:52:04 steven kernel: [    2.939132] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Nov 22 09:52:04 steven kernel: [    3.092115] usb 1-3: new high speed USB device using ehci_hcd and address 2
Nov 22 09:52:04 steven kernel: [    3.452701] FDC 0 is a post-1991 82077
Nov 22 09:52:04 steven kernel: [    3.460419] usb 1-3: configuration #1 chosen from 1 choice
Nov 22 09:52:04 steven kernel: [    3.472104] Initializing USB Mass Storage driver...
Nov 22 09:52:04 steven kernel: [    3.508066] scsi2 : SCSI emulation for USB Mass Storage devices
Nov 22 09:52:04 steven kernel: [    3.511074] usbcore: registered new interface driver usb-storage
Nov 22 09:52:04 steven kernel: [    3.511087] USB Mass Storage support registered.
Nov 22 09:52:04 steven kernel: [    3.572166] usb 1-4: new high speed USB device using ehci_hcd and address 3
Nov 22 09:52:04 steven kernel: [    3.642089] sis900.c: v1.08.10 Apr. 2 2006
Nov 22 09:52:04 steven kernel: [    3.642718] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
Nov 22 09:52:04 steven kernel: [    3.642729] sis900 0000:00:03.0: PCI INT A -> Link[LNKG] -> GSI 5 (level, low) -> IRQ 5
Nov 22 09:52:04 steven kernel: [    3.643682] 0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
Nov 22 09:52:04 steven kernel: [    3.653462] 0000:00:03.0: Using transceiver found at address 1 as default
Nov 22 09:52:04 steven kernel: [    3.658626] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 5, 00:0a:e6:64:ba:c8
Nov 22 09:52:04 steven kernel: [    3.747098] usb 1-4: configuration #1 chosen from 1 choice
Nov 22 09:52:04 steven kernel: [    4.485768] PM: Starting manual resume from disk
Nov 22 09:52:04 steven kernel: [    4.521768] kjournald starting.  Commit interval 5 seconds
Nov 22 09:52:04 steven kernel: [    4.521801] EXT3-fs: mounted filesystem with ordered data mode.
Nov 22 09:52:04 steven kernel: [    8.509114] scsi 2:0:0:0: Direct-Access     FLASH    Drive AU_USB20   8.07 PQ: 0 ANSI: 2
Nov 22 09:52:04 steven kernel: [    8.510946] sd 2:0:0:0: [sdb] 4104192 512-byte hardware sectors: (2.10 GB/1.95 GiB)
Nov 22 09:52:04 steven kernel: [    8.511571] sd 2:0:0:0: [sdb] Write Protect is off
Nov 22 09:52:04 steven kernel: [    8.513710] sd 2:0:0:0: [sdb] 4104192 512-byte hardware sectors: (2.10 GB/1.95 GiB)
Nov 22 09:52:04 steven kernel: [    8.514324] sd 2:0:0:0: [sdb] Write Protect is off
Nov 22 09:52:04 steven kernel: [    8.514342]  sdb:
Nov 22 09:52:04 steven kernel: [    8.734047] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Nov 22 09:52:04 steven kernel: [    8.734219] sd 2:0:0:0: Attached scsi generic sg3 type 0
Nov 22 09:52:04 steven kernel: [   10.391820] udev: starting version 141
Nov 22 09:52:04 steven kernel: [   10.581612] Linux agpgart interface v0.103
Nov 22 09:52:04 steven kernel: [   10.655314] agpgart-sis 0000:00:00.0: SiS chipset [1039/0735]
Nov 22 09:52:04 steven kernel: [   10.661903] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
Nov 22 09:52:04 steven kernel: [   10.670255] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 22 09:52:04 steven kernel: [   10.695817] parport_pc 00:0a: reported by Plug and Play ACPI
Nov 22 09:52:04 steven kernel: [   10.695889] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov 22 09:52:04 steven kernel: [   10.760363] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
Nov 22 09:52:04 steven kernel: [   10.760378] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
Nov 22 09:52:04 steven kernel: [   10.760382] ACPI: Device needs an ACPI driver
Nov 22 09:52:04 steven kernel: [   11.115136] input: PC Speaker as /devices/platform/pcspkr/input/input4
Nov 22 09:52:04 steven kernel: [   11.298375] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Nov 22 09:52:04 steven kernel: [   12.180131] intel8x0_measure_ac97_clock: measured 55677 usecs
Nov 22 09:52:04 steven kernel: [   12.180141] intel8x0: clocking to 48000
Nov 22 09:52:04 steven kernel: [   12.238742] ppdev: user-space parallel port driver
Nov 22 09:52:04 steven kernel: [   12.362334] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Nov 22 09:52:04 steven kernel: [   12.664085] lp0: using parport0 (interrupt-driven).
Nov 22 09:52:04 steven kernel: [   12.864812] Adding 3301316k swap on /dev/sda5.  Priority:-1 extents:1 across:3301316k
Nov 22 09:52:04 steven kernel: [   13.459856] EXT3 FS on sda1, internal journal
Nov 22 09:52:04 steven kernel: [   14.921136] type=1505 audit(1258908722.518:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1905
Nov 22 09:52:04 steven kernel: [   15.035865] type=1505 audit(1258908722.630:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1909
Nov 22 09:52:04 steven kernel: [   15.036492] type=1505 audit(1258908722.634:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1909
Nov 22 09:52:04 steven kernel: [   15.036665] type=1505 audit(1258908722.634:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1909
Nov 22 09:52:04 steven kernel: [   15.036794] type=1505 audit(1258908722.634:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1909
Nov 22 09:52:04 steven kernel: [   15.357002] type=1505 audit(1258908722.954:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1914
Nov 22 09:52:04 steven kernel: [   15.357684] type=1505 audit(1258908722.954:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1914
Nov 22 09:52:04 steven kernel: [   15.427027] type=1505 audit(1258908723.022:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1918
Nov 22 09:52:06 steven kernel: [   18.936940] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 22 09:52:06 steven kernel: [   18.936948] Bluetooth: BNEP filters: protocol multicast
Nov 22 09:52:06 steven kernel: [   19.011893] Bridge firewalling registered
Nov 22 09:52:08 steven kernel: [   21.294920] [drm] Initialized drm 1.1.0 20060810
Nov 22 09:52:08 steven kernel: [   21.334464] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Nov 22 09:52:08 steven kernel: [   21.334699] [drm] Initialized r128 2.5.0 20030725 on minor 0
Nov 22 09:52:09 steven kernel: [   21.469808] agpgart-sis 0000:00:00.0: AGP 2.0 bridge
Nov 22 09:52:09 steven kernel: [   21.469850] agpgart-sis 0000:00:00.0: putting AGP V2 device into 1x mode
Nov 22 09:52:09 steven kernel: [   21.469901] pci 0000:01:00.0: putting AGP V2 device into 1x mode
Nov 22 09:52:12 steven kernel: [   24.404547] eth0: Media Link Off
Nov 22 09:52:12 steven kernel: [   24.404698] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 22 09:52:14 steven pulseaudio[2866]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov 22 09:52:14 steven pulseaudio[2866]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
cat: 1: No such file or directory
cat: grep: No such file or directory
cat: usb: No such file or directory
[EMAIL="steven@steven:~$"]steven@steven:~$[/EMAIL] 
 
 
this is what i got

---

### Post by coffeeaddict22 on 2009-11-23
OK.  Just realised what you're doing.  The "|" in cat /var/log/messages | grep usb isn't a number 1; its the pipe- a vertical line, {SHIFT} + just above the Enter key on all my keyboards.  It sends the output from the first command to the second; grep just picks out the bits of interest.  One of the very nice tricks you get to use in Linux.

Second, when you're posting lots of output, put them in code tags: its the # icon at the top of the box.

Having said that, the adapter still isn't showing up as being even attempted in the message log.

Looking around, it appears there's a bit of an issue with the Belkin.  Have a look at this [post]("http://blog.delgurth.com/tag/ubuntu/").  You may have to scroll down to the instructions on how to make it work.  Essentially, you're going to have to get the driver to be recognised by the operating system.

---

### Post by scooba61709 on 2009-11-24
just down loaded 9.10 it showes that the wireless usb is there but it wont connect to any of them

---

### Post by coffeeaddict22 on 2009-11-24
Sorry, not sure what you mean by "shows the wireless USB is there".  Where are you looking?

---

### Post by scooba61709 on 2009-11-24
ok when 9.10 boots it showes different wireless networks that i can connect to n when i try to connect it doesnt connect even though there are many to choose from

---

### Post by coffeeaddict22 on 2009-11-24
OK.  Open a terminal, type in ```
nm-tool
``` and post back the output.

---

### Post by utvolfan67 on 2009-11-25
coffeeaddict22:
 
I am also having a problem with Ubuntu connecting to wireless.  Mine actually sees the wlan0 interface, assigns it an IP (192.168.1.101) but I can't ping the Linksys router (192.168.1.1) or my XP machine (192.168.1.102).  I am totally baffled as to how the router could assign my Ubuntu machine an IP but I can't ping anything on the network.  Any ideas?  I have a post out already but have only gotten 2 replies that were of no help.

---

### Post by coffeeaddict22 on 2009-11-25
Hi utvolfan67,
Assuming you're running vanilla Ubuntu, once you've got a driver working, ```
nm-tool
``` (as in the post above) gives maximum diagnostic information.
Just to make it easy for me, can you also do ```
lshw -C network
``` in the terminal and post that back?  Much of the information is a copy, but it makes it easy to confirm the basics.

---

### Post by scooba61709 on 2009-11-25
NetworkManager Tool 


State: disconnected 


- Device: eth0 ----------------------------------------------------------------- 
Type: Wired 
Driver: sis900 
State: unavailable 
Default: no 
HW Address: 00:0A:E6:64:BA:C8 


Capabilities: 
Carrier Detect: yes 
Speed: 10 Mb/s 


Wired Properties 
Carrier: off 




- Device: wlan0 ---------------------------------------------------------------- 
Type: 802.11 WiFi 
Driver: rt2800usb 
State: disconnected 
Default: no 
HW Address: 00:1C:DF:31:77:DA 


Capabilities: 


Wireless Properties 
WEP Encryption: yes 
WPA Encryption: yes 
WPA2 Encryption: yes 


Wireless Access Points 
myqwest5761: Infra, 00:1E:A7:9B:1E:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP 
amra: Infra, 00:23:69:EF:30:F5, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 
linksys: Infra, 00:18:F8:C1:D4:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 
linksys: Infra, 00:18:39:97:72:F7, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 
linksys_SES_29862: Infra, 00:14:BF:F4:8A:84, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA 
Schaaby2: Infra, 00:11:24:90:32:8F, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 




steven@ubuntu:~$

---

### Post by coffeeaddict22 on 2009-11-25
OK, it all looks good on that.  All you need to do is connect to one of them.  Which one are you planning on connecting to?  The only reason to ask is the encryptation may be an issue, although that's less likely.
On the top panel you'll have a network icon- looks like 4 steps.  Right click, choose edit connections, and then in the box you get, select wireless connections.  Add the connection of your choice, including it's security requirements.  Post back if you run into trouble.

Sorry, another addit.  If you look at that scan, 5 of the 6 networks in range are on the same frequency, which is only good for hair loss (caused by tearing it out).  If you aren't trying to get on the Schaaby2 network, change your channel on the router.  You don't have to do anything for your PC to recognise the change.

---

### Post by utvolfan67 on 2009-11-25
> **coffeeaddict22 said:**
> Hi utvolfan67,
Assuming you're running vanilla Ubuntu, once you've got a driver working, ```
nm-tool
``` (as in the post above) gives maximum diagnostic information.
Just to make it easy for me, can you also do ```
lshw -C network
``` in the terminal and post that back? Much of the information is a copy, but it makes it easy to confirm the basics.
 
Coffeeaddict22,
 
Thanks for the response.  I wasn't familiar with nm-tool but once I ran it I realized it probably has something to do with the default driver I'm using.  Here are the results:
 
```

NetworkManager Tool
State: connected
- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: e1000
State: unavailable
Default: no
HW Address: 00:0B:DB:C9:2F:B4
Capabilities:
Carrier Detect: yes
Wired Properties
Carrier: off
 
- Device: wlan0 [titannet] ----------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8187
State: connected
Default: yes
HW Address: 00:17:3F:34:9B:E6
Capabilities:
Speed: 1 Mb/s
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points (* = current AP)
*titannet: Infra, 00:13:10:3C:66:94, Freq 2437 MHz, Rate 54 Mb/s, Strength 36 WPA
IPv4 Settings:
Address: 192.168.1.101
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1
DNS: 68.87.68.166
DNS: 68.87.74.166
 
 
 

``` 
 
and the lshw -C network
 
```

randy@titan3:~$ sudo lshw -C network
[sudo] password for randy: 
*-network 
description: Ethernet interface
product: 82545EM Gigabit Ethernet Controller (Copper)
vendor: Intel Corporation
physical id: e
bus info: pci@0000:03:0e.0
logical name: eth0
version: 01
serial: 00:0b:db:c9:2f:b4
capacity: 1GB/s
width: 64 bits
clock: 66MHz
capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
*-network:0
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:17:3f:34:9b:e6
capabilities: ethernet physical wireless
configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 3e:d9:bb:93:03:aa
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
 

```
 
Thanks in advance for any assistance you can provide.

---

### Post by coffeeaddict22 on 2009-11-25
Utvol,
what does ```
route -n
``` return?  It looks like a working interface.

---

### Post by utvolfan67 on 2009-11-25
> **coffeeaddict22 said:**
> Utvol,
what does ```
route -n
``` return? It looks like a working interface.
 
coffee,
 
Here is what I got back.  I also tried to ping the router as well.
 
```

randy@titan3:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 2 0 0 wlan0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlan0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 wlan0
randy@titan3:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable
From 192.168.1.101 icmp_seq=4 Destination Host Unreachable
From 192.168.1.101 icmp_seq=5 Destination Host Unreachable
From 192.168.1.101 icmp_seq=6 Destination Host Unreachable
From 192.168.1.101 icmp_seq=7 Destination Host Unreachable

```

---

### Post by scooba61709 on 2009-11-25
wow i am so lost but i am trying to connect to the linksyes but i dont have access to the routter lol

---

### Post by coffeeaddict22 on 2009-11-25
utvolfan,
Your card is working.  You've got a network glitch.  If I had to guess, you need the network password.  You're trying to get access to a network with the SSID of titannet, and it's got WPA encryptation.  Make sure you've got the right password, and try again.

---

### Post by coffeeaddict22 on 2009-11-25
> **scooba61709 said:**
> NetworkManager Tool 


Wireless Access Points 
myqwest5761: Infra, 00:1E:A7:9B:1E:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP 
amra: Infra, 00:23:69:EF:30:F5, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 
linksys: Infra, 00:18:F8:C1:D4:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 
linksys: Infra, 00:18:39:97:72:F7, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 
linksys_SES_29862: Infra, 00:14:BF:F4:8A:84, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA 
Schaaby2: Infra, 00:11:24:90:32:8F, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 




steven@ubuntu:~$

scoob,
As you can see in the list above, there's two networks with the name linksys, both on the same frequency, which sounds like sanity- destroying material, and will probably mean you're going to get network disconnects/ hangups at random.  Changing the channel is too easy, and changing the SSID (name) is about as basic as it gets, so whoever owns those networks needs to be told to join the 21st century.  Neither appear to be encrypted, so I hope you aren't too fussed if someone listens in on you... and yes, if you know what to do it's not too difficult.  I saw a script a while back that you could run on your server to turn all the pictures upside down for someone accessing through it.

More importantly, your card is able to scan and is picking the networks up OK.  So the problem is now how to connect.  What is the output of ```
route -n
```

---

### Post by scooba61709 on 2009-11-26
Kernel IP routing table 
Destination Gateway Genmask Flags Metric Ref Use Iface 
 
that is what is said

---

### Post by coffeeaddict22 on 2009-11-26
So what happens when you try to add the network?  Click on the network manager icon on the top panel, and then the network you want to connect to.  If you like, right click and set it up as a default.  If it doesn't work, why not?

---

