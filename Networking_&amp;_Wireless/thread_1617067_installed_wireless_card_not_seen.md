---
title: "installed wireless card not seen"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by willy-be-frantic on 2010-11-08
G'day, eh.  This is my first post on this forum.  Let me say in advance that my experience with forums on other subjects has been extremely good.  There is a wealth of knowledge and expertise in these forums and I much appreciate the help I will undoubtedly get.

I had installed Ubuntu ( Version number: 8.04 ( Hardy Heron )) some time ago as a dual boot on my desktop computer ( i-Net Pro - Pentium(R) 4 - 2.40 Ghz - 504 MG of Ram ).  It works very well except I have no wireless connection to my router.  I changed to a D-Link DWA 552 wireless card, as I had read it had a native driver in Ubuntu.  Just as a matter of principle I did not want to use a "Windows" driver via ndiswrapper. 

The hardware seems to be recognized by the Ubuntu OS, but not seen enough to see the wireless signal.

In looking around in the forum I find the following by another user:

 > This page is my experience with the DWA-552, aka D-Link Xtreme N Desktop Adapter

Intrepid Ibex (8.10)

Works... But Causes 64bit and 32bit to experience freezing up completely. Use ndiswrapper method ----

I have a bit of experience with Unix.  Years ago I used HP-UX and SCO at work.  I primarily use my computer for web-surfing and have Windows XP as the other option on the dual-boot.  This will delay the response to any suggestion / help you may offer as I have to boot into Ubuntu, try the fix, then come back to Windows to communicate further.  I could hook up a ethernet line, computer to router, and have an internet connection in Ubuntu but I can't find my long cable.  I did have the hard connection when I installed Ubuntu originally.

I had found a suggestion in this forum about the power-saving mode on the wireless card.  It said that Windows, when it shuts down, goes to power-save mode on the wireless card and makes the card unavailable to Ubuntu when it boots up.  I went into "Device Manager" in Windows and changed the setting on the wireless card's Power-Save Mode from 'normal' to 'off'.  Sadly this did not fix the problem.

Thanks for your help and patience.

Here is a little info on what I have.


> willy@...-...:~$ lspci -nn | grep "Atheros"
01:00.0 Network controller [0280]: Atheros Communications Inc. Unknown device [168c:0029] (rev 01)
----
> willy@...-...:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:bc:80:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 00:11:11:bc:80:7f  
          inet addr:169.254.6.227  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:266452 (260.2 KB)  TX bytes:266452 (260.2 KB)
----
> willy@...-...:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.----
> willy@...-...:~$ lshw -C network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 81
       serial: 00:11:11:bc:80:7f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
----

> willy@...-...:~$ uname -mr
2.6.24-19-generic i686
----

---

### Post by uncaspi on 2010-11-08
Thanks for the info. Please post the content of dmesg after you try to connect. Do you see the wifi connections in network-manager?

---

### Post by uncaspi on 2010-11-08
Can't see any driver for the card in the listing.

---

### Post by willy-be-frantic on 2010-11-08
Oy - I got a lot of return for a 5 letter command.  I don't see any wireless connections in the network-manager.

Here is the output of 'dmesg':

> [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f740000 (usable)
[    0.000000]  BIOS-e820: 000000001f740000 - 000000001f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f750000 - 000000001f800000 (ACPI NVS)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 128832) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128832
[    0.000000]   HighMem    128832 ->   128832
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128832
[    0.000000] On node 0 totalpages: 128832
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 974 pages used for memmap
[    0.000000]   Normal zone: 123762 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F77A0 checksum 0
[    0.000000] ACPI: RSDP 000F77A0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1F740000, 0030 (r1 INTEL  D845GVS1 20050316 MSFT       97)
[    0.000000] ACPI: FACP 1F740200, 0074 (r1 INTEL  D845GVS1 20050316 MSFT       97)
[    0.000000] ACPI: DSDT 1F740370, 415D (r1 INTEL  D845GVS1      10A MSFT  100000D)
[    0.000000] ACPI: FACS 1F750000, 0040
[    0.000000] ACPI: APIC 1F740300, 0068 (r1 INTEL  D845GVS1 20050316 MSFT       97)
[    0.000000] ACPI: ASF! 1F7444D0, 0084 (r16 AMIASF I845GASF        1 MSFT  100000D)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:e0800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127826
[    0.000000] Kernel command line: root=UUID=a9a8897d-5b1e-4b6d-8c99-0f157c4eda3d ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2400.241 MHz processor.
[   24.401708] Console: colour VGA+ 80x25
[   24.401714] console [tty0] enabled
[   24.402131] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.402461] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.412833] Memory: 498820k/515328k available (2177k kernel code, 15848k reserved, 1006k data, 368k init, 0k highmem)
[   24.412842] virtual kernel memory layout:
[   24.412843]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.412845]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.412846]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   24.412847]     lowmem  : 0xc0000000 - 0xdf740000   ( 503 MB)
[   24.412848]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   24.412849]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   24.412851]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   24.412854] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.412896] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.492802] Calibrating delay using timer specific routine.. 4804.71 BogoMIPS (lpj=9609422)
[   24.492832] Security Framework initialized
[   24.492837] SELinux:  Disabled at boot.
[   24.492853] AppArmor: AppArmor initialized
[   24.492859] Failure registering capabilities with primary security module.
[   24.492869] Mount-cache hash table entries: 512
[   24.493008] Initializing cgroup subsys ns
[   24.493013] Initializing cgroup subsys cpuacct
[   24.493028] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   24.493039] monitor/mwait feature present.
[   24.493042] using mwait in idle threads.
[   24.493049] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   24.493052] CPU: L2 cache: 1024K
[   24.493055] CPU: Hyper-Threading is disabled
[   24.493058] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
[   24.493071] Compat vDSO mapped to ffffe000.
[   24.493089] Checking 'hlt' instruction... OK.
[   24.509306] SMP alternatives: switching to UP code
[   24.511437] Freeing SMP alternatives: 11k freed
[   24.511582] Early unpacking initramfs... done
[   24.874718] ACPI: Core revision 20070126
[   24.874784] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.877419] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 01
[   24.877466] Total of 1 processors activated (4804.71 BogoMIPS).
[   24.877599] ENABLING IO-APIC IRQs
[   24.877784] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.024089] Brought up 1 CPUs
[   25.024115] CPU0 attaching sched-domain:
[   25.024119]  domain 0: span 01
[   25.024122]   groups: 01
[   25.024340] net_namespace: 64 bytes
[   25.024356] Booting paravirtualized kernel on bare hardware
[   25.025087] Time: 22:05:53  Date: 10/08/10
[   25.025118] NET: Registered protocol family 16
[   25.025398] EISA bus registered
[   25.025424] ACPI: bus type pci registered
[   25.025625] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   25.025628] PCI: Using configuration type 1
[   25.025659] Setting up standard PCI resources
[   25.037392] ACPI: EC: Look up EC in DSDT
[   25.041982] ACPI: Interpreter enabled
[   25.041987] ACPI: (supports S0 S1 S4 S5)
[   25.042006] ACPI: Using IOAPIC for interrupt routing
[   25.049421] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.049924] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   25.049927] * this clock source is slow. If you are sure your timer does not have
[   25.049928] * this bug, please use "acpi_pm_good" to disable the workaround
[   25.049979] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   25.049983] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   25.050372] PCI: Transparent bridge - 0000:00:1e.0
[   25.050398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.050532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   25.052309] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.052511] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   25.052708] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   25.052903] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   25.053100] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.053296] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.053495] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.053693] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   25.053866] ACPI: Power Resource [URP1] (off)
[   25.053909] ACPI: Power Resource [URP2] (off)
[   25.053951] ACPI: Power Resource [FDDP] (off)
[   25.053993] ACPI: Power Resource [LPTP] (off)
[   25.054050] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.054092] pnp: PnP ACPI init
[   25.054101] ACPI: bus type pnp registered
[   25.058460] pnp: PnP ACPI: found 13 devices
[   25.058463] ACPI: ACPI bus type pnp unregistered
[   25.058469] PnPBIOS: Disabled by ACPI PNP
[   25.058784] PCI: Using ACPI for IRQ routing
[   25.058787] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.071986] NET: Registered protocol family 8
[   25.071989] NET: Registered protocol family 20
[   25.072075] AppArmor: AppArmor Filesystem Enabled
[   25.075958] Time: tsc clocksource has been installed.
[   25.084001] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[   25.084013] system 00:0b: ioport range 0x400-0x47f has been reserved
[   25.084016] system 00:0b: ioport range 0x680-0x6ff has been reserved
[   25.084019] system 00:0b: ioport range 0x480-0x4bf has been reserved
[   25.084023] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   25.084026] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[   25.084033] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   25.084036] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved
[   25.084039] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   25.084042] system 00:0c: iomem range 0x100000-0x1f7fffff could not be reserved
[   25.084045] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   25.114557] PCI: Bridge: 0000:00:1e.0
[   25.114563]   IO window: d000-dfff
[   25.114569]   MEM window: ff800000-ff8fffff
[   25.114574]   PREFETCH window: e6a00000-e6afffff
[   25.114590] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.114603] NET: Registered protocol family 2
[   25.151941] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   25.152225] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   25.152326] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   25.152426] TCP: Hash tables configured (established 16384 bind 16384)
[   25.152429] TCP reno registered
[   25.163982] checking if image is initramfs... it is
[   25.615171] Switched to high resolution mode on CPU 0
[   25.878632] Freeing initrd memory: 7274k freed
[   25.879554] audit: initializing netlink socket (disabled)
[   25.879575] audit(1286575553.364:1): initialized
[   25.882279] VFS: Disk quotas dquot_6.5.1
[   25.882382] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.882558] io scheduler noop registered
[   25.882561] io scheduler anticipatory registered
[   25.882563] io scheduler deadline registered
[   25.882578] io scheduler cfq registered (default)
[   25.882595] Boot video device is 0000:00:02.0
[   25.882662] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   25.883025] isapnp: Scanning for PnP cards...
[   26.234676] isapnp: No Plug & Play device found
[   26.275435] Real Time Clock Driver v1.12ac
[   26.275565] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.275700] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.276676] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.277702] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.277793] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.277922] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.277925] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   26.278496] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.286277] mice: PS/2 mouse device common for all mice
[   26.286428] EISA: Probing bus 0 at eisa.0
[   26.286467] EISA: Detected 0 cards.
[   26.286471] cpuidle: using governor ladder
[   26.286473] cpuidle: using governor menu
[   26.286575] NET: Registered protocol family 1
[   26.286610] Using IPI No-Shortcut mode
[   26.286646] registered taskstats version 1
[   26.286741]   Magic number: 14:472:97
[   26.286866] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.286868] EDD information not available.
[   26.287269] Freeing unused kernel memory: 368k freed
[   26.322091] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.533532] fuse init (API version 7.9)
[   27.563663] ACPI: Processor [CPU1] (supports 8 throttling states)
[   27.563683] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.215506] usbcore: registered new interface driver usbfs
[   28.215539] usbcore: registered new interface driver hub
[   28.220097] usbcore: registered new device driver usb
[   28.240770] USB Universal Host Controller Interface driver v3.0
[   28.240858] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.240873] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   28.240878] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   28.241220] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   28.241252] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[   28.241435] usb usb1: configuration #1 chosen from 1 choice
[   28.241473] hub 1-0:1.0: USB hub found
[   28.241481] hub 1-0:1.0: 2 ports detected
[   28.307391] SCSI subsystem initialized
[   28.343136] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   28.343153] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   28.343158] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   28.343196] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   28.343227] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880
[   28.343366] usb usb2: configuration #1 chosen from 1 choice
[   28.343398] hub 2-0:1.0: USB hub found
[   28.343405] hub 2-0:1.0: 2 ports detected
[   28.379743] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   28.379748] e100: Copyright(c) 1999-2006 Intel Corporation
[   28.383642] libata version 3.00 loaded.
[   28.446981] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.446998] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   28.447003] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   28.447041] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   28.447072] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[   28.447220] usb usb3: configuration #1 chosen from 1 choice
[   28.447257] hub 3-0:1.0: USB hub found
[   28.447265] hub 3-0:1.0: 2 ports detected
[   28.466902] Floppy drive(s): fd0 is 1.44M
[   28.486671] FDC 0 is a post-1991 82077
[   28.550952] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   28.550972] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   28.550976] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   28.551012] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   28.554916] ehci_hcd 0000:00:1d.7: debug port 1
[   28.554924] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   28.554937] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00
[   28.582650] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   28.594647] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.594847] usb usb4: configuration #1 chosen from 1 choice
[   28.594881] hub 4-0:1.0: USB hub found
[   28.594890] hub 4-0:1.0: 6 ports detected
[   28.698712] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   28.721451] e100: eth0: e100_probe: addr 0xff8ef000, irq 20, MAC addr 00:11:11:bc:80:7f
[   28.726240] ata_piix 0000:00:1f.1: version 2.12
[   28.726260] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   28.726268] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   28.726323] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.727910] scsi0 : ata_piix
[   28.728722] scsi1 : ata_piix
[   28.730322] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   28.730326] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   28.894654] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
[   28.894660] ata1.00: 156301488 sectors, multi 16: LBA48 
[   28.910620] ata1.00: configured for UDMA/100
[   29.278726] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A102, max UDMA/33
[   29.278762] ata2.01: ATA-3: IBM-DHEA-36481, HP6OA20C, max UDMA/33
[   29.278766] ata2.01: 12692736 sectors, multi 16: LBA 
[   29.449543] ata2.00: configured for UDMA/33
[   29.481491] ata2.01: configured for UDMA/33
[   29.678031] ata2.00: configured for UDMA/33
[   29.693167] ata2.01: configured for UDMA/33
[   29.693173] ata2: EH complete
[   29.693323] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
[   29.697459] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A102 PQ: 0 ANSI: 5
[   29.697865] scsi 1:0:1:0: Direct-Access     ATA      IBM-DHEA-36481   HP6O PQ: 0 ANSI: 5
[   29.713404] Driver 'sd' needs updating - please use bus_type methods
[   29.713522] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   29.713542] sd 0:0:0:0: [sda] Write Protect is off
[   29.713546] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.713573] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.713639] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   29.713655] sd 0:0:0:0: [sda] Write Protect is off
[   29.713658] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.713684] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.713689]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   29.735367]  sda1
[   29.735447] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.739213] sd 1:0:1:0: [sdb] 12692736 512-byte hardware sectors (6499 MB)
[   29.742360] sd 1:0:1:0: [sdb] Write Protect is off
[   29.742364] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.748706] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   29.754103] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.754108] Uniform CD-ROM driver Revision: 3.20
[   29.754158] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.754169] sd 1:0:1:0: [sdb] 12692736 512-byte hardware sectors (6499 MB)
[   29.754186] sd 1:0:1:0: [sdb] Write Protect is off
[   29.754189] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.754217] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   29.754221]  sdb: sdb1 sdb2
[   29.764313] sd 1:0:1:0: [sdb] Attached SCSI disk
[   29.777299] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.777330] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   29.777355] sd 1:0:1:0: Attached scsi generic sg2 type 0
[   29.940575] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   30.118245] usb 1-2: configuration #1 chosen from 1 choice
[   30.359928] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   30.532673] usb 2-1: configuration #1 chosen from 1 choice
[   30.535594] hub 2-1:1.0: USB hub found
[   30.537559] hub 2-1:1.0: 2 ports detected
[   31.028708] usb 2-1.1: new full speed USB device using uhci_hcd and address 3
[   31.168582] usb 2-1.1: configuration #1 chosen from 1 choice
[   31.380112] usb 2-1.2: new full speed USB device using uhci_hcd and address 4
[   31.521998] usb 2-1.2: configuration #1 chosen from 1 choice
[   31.525029] usbcore: registered new interface driver hiddev
[   31.718668] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[   31.729884] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
[   31.729907] usbcore: registered new interface driver usbhid
[   31.729912] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.014321] Attempting manual resume
[   32.014326] swsusp: Resume From Partition 8:17
[   32.014329] PM: Checking swsusp image.
[   32.022367] PM: Resume from disk failed.
[   32.700370] usb 4-1: new high speed USB device using ehci_hcd and address 12
[   33.187628] usb 4-1: new high speed USB device using ehci_hcd and address 14
[   35.927458] usb 4-1: new high speed USB device using ehci_hcd and address 28
[   36.414714] usb 4-1: new high speed USB device using ehci_hcd and address 30
[   36.901971] usb 4-1: new high speed USB device using ehci_hcd and address 32
[   37.576945] usb 4-1: new high speed USB device using ehci_hcd and address 35
[   37.876494] usb 4-1: new high speed USB device using ehci_hcd and address 36
[   39.865464] usb 4-1: new high speed USB device using ehci_hcd and address 46
[   40.352722] usb 4-1: new high speed USB device using ehci_hcd and address 48
[   41.027697] usb 4-1: new high speed USB device using ehci_hcd and address 51
[   41.327238] usb 4-1: new high speed USB device using ehci_hcd and address 52
[   41.626794] usb 4-1: new high speed USB device using ehci_hcd and address 53
[   42.677202] usb 4-1: new high speed USB device using ehci_hcd and address 58
[   43.727602] usb 4-1: new high speed USB device using ehci_hcd and address 63
[   44.214866] usb 4-1: new high speed USB device using ehci_hcd and address 65
[   44.349565] usb 4-1: configuration #1 chosen from 1 choice
[   52.401956] Linux agpgart interface v0.102
[   52.675777] agpgart: Detected an Intel 830M Chipset.
[   52.676242] agpgart: Detected 8060K stolen memory.
[   52.690635] agpgart: AGP aperture is 128M @ 0xf0000000
[   52.769870] iTCO_vendor_support: vendor-support=0
[   52.828131] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   52.828246] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   52.828285] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   52.905724] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.985628] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.125355] intel_rng: Firmware space is locked read-only. If you can't or
[   53.125358] intel_rng: don't want to disable this in firmware setup, and if
[   53.125360] intel_rng: you are certain that your system has a functional
[   53.125362] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   53.174742] input: Power Button (FF) as /devices/virtual/input/input3
[   53.185211] ACPI: Power Button (FF) [PWRF]
[   53.185325] input: Sleep Button (CM) as /devices/virtual/input/input4
[   53.197184] ACPI: Sleep Button (CM) [SLPB]
[   53.218702] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   53.774003] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   55.587583] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   55.587620] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   55.908520] usbcore: registered new interface driver libusual
[   55.913059] intel8x0_measure_ac97_clock: measured 59070 usecs
[   55.913063] intel8x0: clocking to 48000
[   55.961571] Initializing USB Mass Storage driver...
[   56.008434] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x043D pid 0x00FF
[   56.030772] scsi2 : SCSI emulation for USB Mass Storage devices
[   56.056869] usbcore: registered new interface driver usb-storage
[   56.056877] USB Mass Storage support registered.
[   56.056976] usbcore: registered new interface driver usblp
[   56.057399] usb-storage: device found at 65
[   56.057402] usb-storage: waiting for device to settle before scanning
[   56.181233] parport_pc 00:09: reported by Plug and Play ACPI
[   56.181294] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   57.076160] NET: Registered protocol family 17
[   58.446470] lp0: using parport0 (interrupt-driven).
[   58.508116] Adding 1020088k swap on /dev/sdb1.  Priority:-1 extents:1 across:1020088k
[   60.537235] ip_tables: (C) 2000-2006 Netfilter Core Team
[   60.994050] No dock devices found.
[   61.057262] usb-storage: device scan complete
[   61.058113] scsi 2:0:0:0: Direct-Access     Lexar    Media Inc. CF    019D PQ: 0 ANSI: 0 CCS
[   61.058974] scsi 2:0:0:1: Direct-Access     Lexar    Media Inc. SD    019D PQ: 0 ANSI: 0 CCS
[   61.059721] scsi 2:0:0:2: Direct-Access     Lexar    Media Inc. SM/xD 019D PQ: 0 ANSI: 0 CCS
[   61.060469] scsi 2:0:0:3: Direct-Access     Lexar    Media Inc. MS    019D PQ: 0 ANSI: 0 CCS
[   61.072605] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   61.072662] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   61.073718] sd 2:0:0:1: [sdd] Attached SCSI removable disk
[   61.073759] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   61.074842] sd 2:0:0:2: [sde] Attached SCSI removable disk
[   61.074885] sd 2:0:0:2: Attached scsi generic sg5 type 0
[   61.075984] sd 2:0:0:3: [sdf] Attached SCSI removable disk
[   61.076039] sd 2:0:0:3: Attached scsi generic sg6 type 0
[   63.547407] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   63.547414] apm: overridden by ACPI.
[   63.718007] ppdev: user-space parallel port driver
[   64.096415] audit(1286597192.807:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4934 profile="/usr/sbin/cupsd" namespace="default"
[   66.516466] Bluetooth: Core ver 2.11
[   66.517306] NET: Registered protocol family 31
[   66.517311] Bluetooth: HCI device and connection manager initialized
[   66.517316] Bluetooth: HCI socket layer initialized
[   66.673930] Bluetooth: L2CAP ver 2.9
[   66.673938] Bluetooth: L2CAP socket layer initialized
[   66.739221] Bluetooth: RFCOMM socket layer initialized
[   66.739241] Bluetooth: RFCOMM TTY layer initialized
[   66.739244] Bluetooth: RFCOMM ver 1.8
[   70.099490] [drm] Initialized drm 1.1.0 20060810
[   70.117187] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   70.117199] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   70.117296] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   91.864133] NET: Registered protocol family 10
[   91.864715] lo: Disabled Privacy Extensions
[   91.865465] ADDRCONF(NETDEV_UP): eth0: link is not ready
willy@mall-work:~$ 

---

### Post by uncaspi on 2010-11-09
Hardy Heron have problems with wireless. I recommend that you upgrade to 
10.04 Lucid Lynx.

---

### Post by willy-be-frantic on 2010-11-09
Thanks, I will try that.  Now the hunt is on for a long enough cable.

---

### Post by grahammechanical on 2010-11-10
Do not take me for an expert but, that listing from ifconfig should show wlan0 and it doesn't. I would say that either the wireless card is not turned on or the system does not recognize your card. Yet lshw picks up an unclaimed network that is most probably your wireless card. Where does this get you? No where! I am sorry. I am still trying to work out what information these kinds of listing give us.

regards.

---

