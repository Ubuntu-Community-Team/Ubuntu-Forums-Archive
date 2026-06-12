---
title: "[SOLVED] configure wireless BCM4306 better"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by joejoe148 on 2009-01-01
I cant seem to figure out how to get my wireless to be all it can be.

I currently am connected at 1Mbps and every configuration attempt fails

In system>administration>network I am only able to connect in roaming mode.  If I try to manually configure it never works.

In "network tools" wlan0 shows up  and that is where I get the 1Mbps figure from but if I select Wlan0 and try to click configure i get and error message that the interface doesnt exist

Any help would be appreciated.  the specks from the sticky follow. I hope it isnt too long.



These are the specs:
Gateway laptop 200 ARC

02:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

wlan0     IEEE 802.11g  ESSID:"tweed"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:46:86:FA:3A   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=131/100  Signal level=-30 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[B]searching for modules brought up these that may be useful.  Tis is the only section with something that looked wireless
[/B]
b43legacy             127776  0 
mac80211              165652  1 b43legacy
evdev                  13056  7 
cfg80211               15112  1 mac80211

**ok, looking for messages with dmesg brought up a lot of stuff.  this is what looked right.**

[  602.548513] b43legacy-phy0 debug: Using software based encryption for mac: ff:ff:ff:ff:ff:ff
[  602.549868] wlan0: Initial auth_alg=0
[  602.549874] wlan0: authenticate with AP 00:13:46:86:fa:3a
[  602.551381] wlan0: RX authentication from 00:13:46:86:fa:3a (alg=0 transaction=2 status=0)
[  602.551388] wlan0: authenticated
[  602.551392] wlan0: associate with AP 00:13:46:86:fa:3a
[  602.554841] wlan0: RX AssocResp from 00:13:46:86:fa:3a (capab=0x431 status=0 aid=2)
[  602.554846] wlan0: associated
[  602.554850] wlan0: CTS protection enabled (BSSID=00:13:46:86:fa:3a)
[  602.554854] wlan0: switched to short barker preamble (BSSID=00:13:46:86:fa:3a)
[  602.555140] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1413.256079] wlan0: no IPv6 routers present
[ 1423.568533] wlan0: no IPv6 routers present

**OK here is the network configuration**

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:00:00:60:32:f4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:2d:00:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.103 multicast=yes wireless=IEEE 802.11g

Ubuntu version is 8.04.1
kernal/architecture is 2.6.24-22-generic i686

---

### Post by joejoe148 on 2009-01-03
I was looking through the required stuff for posting and found a lot more wireless info in the messages section.  here is the complete dmesg.

[    0.000000]   HighMem    128736 ->   128736
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7C90 checksum 0
[    0.000000] ACPI: RSDP 000F7C90, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1F6E7D3F, 0034 (r1 PTLTD  Montara   6040000  LTP        0)
[    0.000000] ACPI: FACP 1F6EBED2, 0074 (r1 INTEL  MONTARA   6040000 PTL        50)
[    0.000000] ACPI: DSDT 1F6E82B1, 3C21 (r1 INTEL  MONTARAG  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1F6FCFC0, 0040
[    0.000000] ACPI: BOOT 1F6EBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 1F6E8188, 0121 (r1 INTEL  CPU0CST         1 INTL 20020725)
[    0.000000] ACPI: SSDT 1F6E7D73, 0248 (r1  INTEL  EISTRef     2000 INTL  2012044)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000d8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d8000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127731
[    0.000000] Kernel command line: root=UUID=23d1de38-9e22-4919-9111-6280937439cc ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (013fd000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1395.493 MHz processor.
[    8.695431] Console: colour VGA+ 80x25
[    8.695437] console [tty0] enabled
[    8.695639] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.695899] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.714053] Memory: 498436k/514944k available (2177k kernel code, 15900k reserved, 1005k data, 368k init, 0k highmem)
[    8.714063] virtual kernel memory layout:
[    8.714064]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.714066]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.714068]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    8.714069]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[    8.714071]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.714072]       .data : 0xc0320704 - 0xc041bdc4   (1005 kB)
[    8.714074]       .text : 0xc0100000 - 0xc0320704   (2177 kB)
[    8.714078] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.714125] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.794064] Calibrating delay using timer specific routine.. 2793.00 BogoMIPS (lpj=5586009)
[    8.794096] Security Framework initialized
[    8.794104] SELinux:  Disabled at boot.
[    8.794124] AppArmor: AppArmor initialized
[    8.794129] Failure registering capabilities with primary security module.
[    8.794140] Mount-cache hash table entries: 512
[    8.794291] Initializing cgroup subsys ns
[    8.794297] Initializing cgroup subsys cpuacct
[    8.794310] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    8.794324] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.794327] CPU: L2 cache: 1024K
[    8.794331] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00042040 00000180 00000000 00000000 00000000
[    8.794342] Compat vDSO mapped to ffffe000.
[    8.794356] Checking 'hlt' instruction... OK.
[    8.810520] SMP alternatives: switching to UP code
[    8.812737] Freeing SMP alternatives: 11k freed
[    8.812871] Early unpacking initramfs... done
[    9.256875] ACPI: Core revision 20070126
[    9.256959] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.258914] ACPI: setting ELCR to 0200 (from 0c20)
[    9.317474] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
[    9.317481] SMP motherboard not detected.
[    9.317484] Local APIC not detected. Using dummy APIC emulation.
[    9.317548] Brought up 1 CPUs
[    9.317568] CPU0 attaching sched-domain:
[    9.317572]  domain 0: span 01
[    9.317574]   groups: 01
[    9.317788] net_namespace: 64 bytes
[    9.317799] Booting paravirtualized kernel on bare hardware
[    9.318518] Time: 13:02:44  Date: 01/03/09
[    9.318549] NET: Registered protocol family 16
[    9.318782] EISA bus registered
[    9.318796] ACPI: bus type pci registered
[    9.325812] PCI: PCI BIOS revision 2.10 entry at 0xfd9b2, last bus=2
[    9.325815] PCI: Using configuration type 1
[    9.325827] Setting up standard PCI resources
[    9.337074] ACPI: EC: Look up EC in DSDT
[    9.339717] ACPI: Interpreter enabled
[    9.339721] ACPI: (supports S0 S3 S4 S5)
[    9.339737] ACPI: Using PIC for interrupt routing
[    9.340006] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.346190] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    9.346194] ACPI: EC: driver started in interrupt mode
[    9.346242] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.346709] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    9.346713] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    9.347133] PCI: Transparent bridge - 0000:00:1e.0
[    9.347244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.347509] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.354096] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    9.354193] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    9.354287] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[    9.354380] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    9.354473] ACPI: PCI Interrupt Link [LNKE] (IRQs *5)
[    9.354566] ACPI: PCI Interrupt Link [LNKF] (IRQs 5) *0, disabled.
[    9.354660] ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
[    9.354754] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    9.354874] ACPI: Power Resource [PFAN] (on)
[    9.354925] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.354963] pnp: PnP ACPI init
[    9.354971] ACPI: bus type pnp registered
[    9.357391] pnp: PnP ACPI: found 8 devices
[    9.357394] ACPI: ACPI bus type pnp unregistered
[    9.357399] PnPBIOS: Disabled by ACPI PNP
[    9.357663] PCI: Using ACPI for IRQ routing
[    9.357667] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.369508] NET: Registered protocol family 8
[    9.369511] NET: Registered protocol family 20
[    9.369589] AppArmor: AppArmor Filesystem Enabled
[    9.373463] Time: tsc clocksource has been installed.
[    9.381502] system 00:04: ioport range 0x600-0x60f has been reserved
[    9.381505] system 00:04: ioport range 0x700-0x70f has been reserved
[    9.381509] system 00:04: ioport range 0x800-0x80f has been reserved
[    9.381512] system 00:04: ioport range 0x1000-0x107f has been reserved
[    9.381516] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    9.381521] system 00:04: iomem range 0xfec10000-0xfec1ffff could not be reserved
[    9.411982] PCI: Bus 3, cardbus bridge: 0000:02:03.0
[    9.411985]   IO window: 00003400-000034ff
[    9.411990]   IO window: 00003800-000038ff
[    9.411994]   PREFETCH window: 34000000-37ffffff
[    9.411998]   MEM window: 38000000-3bffffff
[    9.412002] PCI: Bus 7, cardbus bridge: 0000:02:03.1
[    9.412004]   IO window: 00003c00-00003cff
[    9.412008]   IO window: 00001400-000014ff
[    9.412012]   PREFETCH window: 3c000000-3fffffff
[    9.412016]   MEM window: 40000000-43ffffff
[    9.412020] PCI: Bridge: 0000:00:1e.0
[    9.412023]   IO window: 3000-3fff
[    9.412028]   MEM window: e0200000-e02fffff
[    9.412032]   PREFETCH window: disabled.
[    9.412045] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.412223] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    9.412226] PCI: setting IRQ 10 as level-triggered
[    9.412230] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    9.412237] PCI: Setting latency timer of device 0000:02:03.0 to 64
[    9.412249] PCI: Enabling device 0000:02:03.1 (0000 -> 0003)
[    9.412391] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    9.412394] ACPI: PCI Interrupt 0000:02:03.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    9.412402] PCI: Setting latency timer of device 0000:02:03.1 to 64
[    9.412416] NET: Registered protocol family 2
[    9.449473] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    9.449760] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    9.449884] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    9.450006] TCP: Hash tables configured (established 16384 bind 16384)
[    9.450010] TCP reno registered
[    9.461526] checking if image is initramfs... it is
[    9.912924] Switched to high resolution mode on CPU 0
[   10.327965] Freeing initrd memory: 7323k freed
[   10.328245] Simple Boot Flag at 0x36 set to 0x1
[   10.328707] audit: initializing netlink socket (disabled)
[   10.328727] audit(1230987764.568:1): initialized
[   10.331408] VFS: Disk quotas dquot_6.5.1
[   10.331511] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.331704] io scheduler noop registered
[   10.331707] io scheduler anticipatory registered
[   10.331710] io scheduler deadline registered
[   10.331729] io scheduler cfq registered (default)
[   10.331747] Boot video device is 0000:00:02.0
[   10.331817] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   10.332164] isapnp: Scanning for PnP cards...
[   10.685648] isapnp: No Plug & Play device found
[   10.723776] Real Time Clock Driver v1.12ac
[   10.723912] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.724654] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   10.724666] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   10.725433] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.725520] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.725636] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.728182] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.729800] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.729807] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.729810] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.729813] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.729816] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.732177] mice: PS/2 mouse device common for all mice
[   10.732312] EISA: Probing bus 0 at eisa.0
[   10.732321] Cannot allocate resource for EISA slot 1
[   10.732325] Cannot allocate resource for EISA slot 2
[   10.732328] Cannot allocate resource for EISA slot 3
[   10.732349] EISA: Detected 0 cards.
[   10.732353] cpuidle: using governor ladder
[   10.732356] cpuidle: using governor menu
[   10.732484] NET: Registered protocol family 1
[   10.732521] Using IPI No-Shortcut mode
[   10.732563] registered taskstats version 1
[   10.732701]   Magic number: 9:531:27
[   10.732711]   hash matches device ttyda
[   10.732896] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.732898] EDD information not available.
[   10.733119] Freeing unused kernel memory: 368k freed
[   10.733153] Write protecting the kernel read-only data: 801k
[   10.763910] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.985363] fuse init (API version 7.9)
[   12.003182] ACPI: Fan [FAN0] (on)
[   12.013024] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.013030] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.016982] ACPI: Thermal Zone [THRM] (41 C)
[   12.766345] usbcore: registered new interface driver usbfs
[   12.766378] usbcore: registered new interface driver hub
[   12.777664] usbcore: registered new device driver usb
[   12.793627] USB Universal Host Controller Interface driver v3.0
[   12.793721] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   12.793735] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.793740] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.794166] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.794194] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001820
[   12.794380] usb usb1: configuration #1 chosen from 1 choice
[   12.794410] hub 1-0:1.0: USB hub found
[   12.794417] hub 1-0:1.0: 2 ports detected
[   12.897820] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   12.897826] PCI: setting IRQ 11 as level-triggered
[   12.897830] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.897844] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.897849] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.897880] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.897907] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[   12.898056] usb usb2: configuration #1 chosen from 1 choice
[   12.898086] hub 2-0:1.0: USB hub found
[   12.898093] hub 2-0:1.0: 2 ports detected
[   12.905525] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   12.905529] e100: Copyright(c) 1999-2006 Intel Corporation
[   12.940840] SCSI subsystem initialized
[   13.001716] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   13.001723] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.001737] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.001742] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.001773] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.001799] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[   13.001943] usb usb3: configuration #1 chosen from 1 choice
[   13.001972] hub 3-0:1.0: USB hub found
[   13.001979] hub 3-0:1.0: 2 ports detected
[   13.022417] libata version 3.00 loaded.
[   13.106083] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   13.106090] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   13.106107] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.106112] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.106146] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   13.110064] ehci_hcd 0000:00:1d.7: debug port 1
[   13.110070] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.110079] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[   13.125912] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.126075] usb usb4: configuration #1 chosen from 1 choice
[   13.126107] hub 4-0:1.0: USB hub found
[   13.126115] hub 4-0:1.0: 6 ports detected
[   13.229626] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   13.229632] PCI: setting IRQ 5 as level-triggered
[   13.229636] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   13.229671] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x02, vendor 0x4243)
[   13.229678] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[   13.229684] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x01, vendor 0x4243)
[   13.229690] ssb: Core 3 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[   13.229695] ssb: Core 4 found: PCI (cc 0x804, rev 0x07, vendor 0x4243)
[   13.229701] ssb: Core 5 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[   13.229704] ssb: Ignoring additional 802.11 core
[   13.233007] ssb: Sonics Silicon Backplane found on PCI device 0000:02:07.0
[   13.233157] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   13.258026] e100: eth0: e100_probe: addr 0xe0202000, irq 5, MAC addr 00:00:00:60:32:f4
[   13.258064] ACPI: PCI Interrupt 0000:02:03.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.310777] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[e0203000-e02037ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   13.322987] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   13.322999] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.323042] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.323057] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   13.330353] ata_piix 0000:00:1f.1: version 2.12
[   13.330374] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.330409] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.331289] scsi0 : ata_piix
[   13.331865] scsi1 : ata_piix
[   13.332839] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   13.332843] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   13.493344] ata1.00: ATA-5: IC25N030ATCS04-0, CA3OA71A, max UDMA/100
[   13.493350] ata1.00: 58605120 sectors, multi 16: LBA 
[   13.509273] ata1.00: configured for UDMA/100
[   13.828690] ata2.00: ATAPI: SAMSUNG CDRW/DVD SN-324F, U200, max UDMA/33
[   14.000434] ata2.00: configured for UDMA/33
[   14.000593] scsi 0:0:0:0: Direct-Access     ATA      IC25N030ATCS04-0 CA3O PQ: 0 ANSI: 5
[   14.005938] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SN-324F U200 PQ: 0 ANSI: 5
[   14.022178] Driver 'sd' needs updating - please use bus_type methods
[   14.022292] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[   14.022308] sd 0:0:0:0: [sda] Write Protect is off
[   14.022312] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.022331] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.022393] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[   14.022404] sd 0:0:0:0: [sda] Write Protect is off
[   14.022407] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.022425] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.022430]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   14.048218]  sda1 sda2 < sda5 >
[   14.070480] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.077608] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.077636] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   14.110936] sr0: scsi3-mmc drive: 2x/24x writer cd/rw xa/form2 cdda tray
[   14.110944] Uniform CD-ROM driver Revision: 3.20
[   14.111020] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   14.386517] Attempting manual resume
[   14.386522] swsusp: Resume From Partition 8:5
[   14.386525] PM: Checking swsusp image.
[   14.386699] PM: Resume from disk failed.
[   14.403761] Clocksource tsc unstable (delta = -1183168085 ns)
[   14.407746] Time: acpi_pm clocksource has been installed.
[   14.591703] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80201003a5f]
[   14.696676] kjournald starting.  Commit interval 5 seconds
[   14.696690] EXT3-fs: mounted filesystem with ordered data mode.
[   31.258904] Linux agpgart interface v0.102
[   31.334841] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.398814] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.550533] intel_rng: FWH not detected
[   31.594601] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.690454] agpgart: Detected an Intel 855GM Chipset.
[   31.690798] agpgart: Detected 8060K stolen memory.
[   31.710377] agpgart: AGP aperture is 128M @ 0xe8000000
[   32.050112] input: Power Button (FF) as /devices/virtual/input/input3
[   32.061961] ACPI: Power Button (FF) [PWRF]
[   32.062061] input: Lid Switch as /devices/virtual/input/input4
[   32.062575] ACPI: Lid Switch [LID0]
[   32.062633] input: Sleep Button (CM) as /devices/virtual/input/input5
[   32.077906] ACPI: Sleep Button (CM) [SLPB]
[   32.077976] input: Power Button (CM) as /devices/virtual/input/input6
[   32.093905] ACPI: Power Button (CM) [PWRB]
[   32.097937] iTCO_vendor_support: vendor-support=0
[   32.141873] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   32.141977] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   32.142015] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.199128] ACPI: Battery Slot [BAT1] (battery present)
[   32.266814] ACPI: AC Adapter [ADP1] (on-line)
[   32.538493] Yenta: CardBus bridge found at 0000:02:03.0 [107b:0200]
[   32.665809] Yenta: ISA IRQ mask 0x0098, PCI irq 10
[   32.665815] Socket status: 30000006
[   32.665818] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   32.665826] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   32.665830] cs: IO port probe 0x3000-0x3fff: clean.
[   32.666120] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   32.737992] Yenta: CardBus bridge found at 0000:02:03.1 [107b:0200]
[   32.865568] Yenta: ISA IRQ mask 0x0098, PCI irq 10
[   32.865574] Socket status: 30000006
[   32.865577] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   32.865585] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   32.865589] cs: IO port probe 0x3000-0x3fff: clean.
[   32.865882] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   33.016955] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xae6eb1, caps: 0x944713/0xc0000
[   33.051790] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   33.861451] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input8
[   33.883915] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   34.411396] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   34.411431] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   35.016449] b43legacy-phy0: Broadcom 4306 WLAN found
[   35.038518] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   35.038541] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   35.062521] b43legacy-phy0 debug: Radio initialized
[   35.065786] phy0: Selected rate control algorithm 'simple'
[   35.238395] intel8x0_measure_ac97_clock: measured 55544 usecs
[   35.238402] intel8x0: clocking to 48000
[   36.785898] cs: IO port probe 0x100-0x3af: clean.
[   36.787546] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   36.788250] cs: IO port probe 0x820-0x8ff: clean.
[   36.788853] cs: IO port probe 0xc00-0xcf7: clean.
[   36.789611] cs: IO port probe 0xa00-0xaff: clean.
[   36.790438] cs: IO port probe 0x100-0x3af: clean.
[   36.792080] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   36.792800] cs: IO port probe 0x820-0x8ff: clean.
[   36.793382] cs: IO port probe 0xc00-0xcf7: clean.
[   36.794152] cs: IO port probe 0xa00-0xaff: clean.
[   36.967809] lp: driver loaded but no devices found
[   37.290818] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
[   37.925758] EXT3 FS on sda1, internal journal
[   38.925118] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.801700] No dock devices found.
[   41.204587] apm: BIOS not found.
[   41.391209] ppdev: user-space parallel port driver
[   41.804738] audit(1230987804.513:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4847 profile="/usr/sbin/cupsd" namespace="default"
[   98.095086] Marking TSC unstable due to: cpufreq changes.
[   75.937116] Bluetooth: Core ver 2.11
[   75.938068] NET: Registered protocol family 31
[   75.938075] Bluetooth: HCI device and connection manager initialized
[   75.938083] Bluetooth: HCI socket layer initialized
[   43.413351] Bluetooth: L2CAP ver 2.9
[   43.413358] Bluetooth: L2CAP socket layer initialized
[   43.497240] Bluetooth: RFCOMM socket layer initialized
[   43.497260] Bluetooth: RFCOMM TTY layer initialized
[   43.497262] Bluetooth: RFCOMM ver 1.8
[   76.621785] b43legacy-phy0 debug: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   76.689786] b43legacy-phy0 debug: Chip initialized
[   76.690485] b43legacy-phy0 debug: 30-bit DMA initialized
[   76.692902] b43legacy-phy0 debug: Wireless interface started
[   76.701580] b43legacy-phy0 debug: Adding Interface type 2
[   45.511906] [drm] Initialized drm 1.1.0 20060810
[   45.517442] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   45.517453] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   45.517546] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   45.517557] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   45.517615] [drm] Initialized i915 1.6.0 20060119 on minor 1
[  109.104154] NET: Registered protocol family 17
[  135.222598] NET: Registered protocol family 10
[  135.224456] lo: Disabled Privacy Extensions
[  135.226039] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  135.229285] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  163.319187] b43legacy-phy0 debug: Using software based encryption for mac: ff:ff:ff:ff:ff:ff
[  163.330901] wlan0: Initial auth_alg=0
[  163.330915] wlan0: authenticate with AP 00:13:46:86:fa:3a
[  163.332557] wlan0: RX authentication from 00:13:46:86:fa:3a (alg=0 transaction=2 status=0)
[  163.332567] wlan0: authenticated
[  163.332575] wlan0: associate with AP 00:13:46:86:fa:3a
[   69.932663] wlan0: RX AssocResp from 00:13:46:86:fa:3a (capab=0x431 status=0 aid=2)
[   69.932667] wlan0: associated
[   69.932672] wlan0: CTS protection enabled (BSSID=00:13:46:86:fa:3a)
[   69.932676] wlan0: switched to short barker preamble (BSSID=00:13:46:86:fa:3a)
[   69.932959] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  182.878471] wlan0: no IPv6 routers present
[  192.742515] wlan0: no IPv6 routers present
joe@joe-laptop:~$

---

### Post by superprash2003 on 2009-01-03
post output of ifconfig from the terminal

---

### Post by joejoe148 on 2009-01-03
joe@joe-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:60:32:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80700 (78.8 KB)  TX bytes:80700 (78.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:2d:00:e0  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe2d:e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3094205 (2.9 MB)  TX bytes:474447 (463.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-2D-00-E0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

joe@joe-laptop:~$

---

### Post by Ayuthia on 2009-01-03
If you can spare the bandwidth, you might try and use the 8.10 liveCD (not upgrade).  I think that they fixed a transmission issue with the 4306 cards, but I am not for sure if it was for the rev 02 or rev 03.

---

### Post by joejoe148 on 2009-01-03
I will start trying to find a reference to that.  I think I already downloaded a copy of intrepid.  somewhere.

update:  I booted into the live CD of intrepid.  I got a bunch of errors related to the drivers for the wireless.  One actually recommended that I download the correct drivers and gave me a site.  No automatic fix though.  I think the bcm drivers are still proprietary and ubuntu cant load them.

I guess I will try ndiswrapper

---

### Post by Ayuthia on 2009-01-03
> **joejoe148 said:**
> I will start trying to find a reference to that.  I think I already downloaded a copy of intrepid.  somewhere.

update:  I booted into the live CD of intrepid.  I got a bunch of errors related to the drivers for the wireless.  One actually recommended that I download the correct drivers and gave me a site.  No automatic fix though.  I think the bcm drivers are still proprietary and ubuntu cant load them.

I guess I will try ndiswrapper

It works the same way as the Hardy version.  You will still need to download the firmware to make it work.  You should be able to download that through Hardy and then copy the firmware over to the liveCD.

However, if you decide to go the ndiswrapper route, here is a link that might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by joejoe148 on 2009-01-03
That link for ndiswrapper was good.  I am having trouble with the keep permanent part of it though

thanks, at least after a minute of the history up arrow in terminal I can browse at a reasonable speed.

---

### Post by Ayuthia on 2009-01-03
> **joejoe148 said:**
> That link for ndiswrapper was good.  I am having trouble with the keep permanent part of it though

thanks, at least after a minute of the history up arrow in terminal I can browse at a reasonable speed.

It might be possible that you might not need it.  If you are having problems with connecting when you reboot, let us know and we can see what needs to be done.  It looks like you have an Intel wired ethernet card so the ssb workaround is not needed, but it is possible that the b43 and ssb modules are not blacklisted.  If you are having problems after rebooting, please post the results of:
```
lshw -C network
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper
cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper
```

You can always manually start your wireless card also by doing:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by joejoe148 on 2009-01-03
Yes, after reboot it drops back to 1Mbps.  

When trying to complete the steps for making it permanent... 
where are the line breaks in this?

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

is that all one command?  I am not good enough with the syntax, I got confused with the second line starting with a command.  Damn, When I actually pay attention it really appears to be one line. 

anyway here are the results of what you asked:
joe@joe-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:00:00:60:32:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:2d:00:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.103 multicast=yes wireless=IEEE 802.11g

joe@joe-laptop:~$ cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper
# replaced by b43 and ssb.

joe@joe-laptop:~$ cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper
ndiswrapper

---

### Post by Ayuthia on 2009-01-03
That set of commands is really one line.  If you look closely at the line, it has \n in there.  Those are the newlines.  That line will put a set of commands into /etc/modprobe.d/ndiswrapper to have it remove the conflicting modules, load ndiswrapper, and then load the b44 module (which you don't need).  You can first try the following to see if it works:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist
```

If that does not work, you can try the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```This is modified from the first because you don't need the b44 module (yours is using e100 and is not affected by the ssb module).

---

### Post by joejoe148 on 2009-01-03
It appears solved.  relooking at the command and what it would actually complete I wound up with this:

joe@joe-laptop:~$ echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;' | sudo tee -a /etc/modprobe.d/ndiswrapper

no b43, or b44 and the command completed.  restarted at full speed.:D

thanks a lot

---

