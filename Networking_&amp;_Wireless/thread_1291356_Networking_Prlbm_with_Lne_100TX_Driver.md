---
title: "Networking Prlbm with Lne 100TX Driver"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by azteka22 on 2009-10-14
Hello, I just transferred over from Sabayon Linux to try out Ubuntu I heard it was the best and its easy to use so I decided to try it out as well, however I do not know Ubuntu that well and do not know their Config Files as well.

 I installed Ubuntu and it did not recognize my Linksys LNE 100TX NIC Card so i went to their website and downloaded the driver I needed. However the Readme is focused for users on Redhat and not ubuntu therefore I cannot complete the steps since the config files do not match, Where do i need to install this driver on Ubuntu for my internet to work?? 

thx in advance for your help

---

### Post by chili555 on 2009-10-14
I believe the driver is already in place. Please connect the ethernet cable, open a terminal and do:```
sudo modprobe tulip
ifconfig
```Do you now have an interface, eth0 perhaps? Can you connect?

---

### Post by azteka22 on 2009-10-14
azteka@azteka-desktop:~$ sudo modprobe tulip
[sudo] password for azteka: 
azteka@azteka-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:35:6b:54  
          inet6 addr: fe80::2a0:ccff:fe35:6b54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1194 (1.1 KB)
          Interrupt:16 Base address:0xec00 

eth0:avahi Link encap:Ethernet  HWaddr 00:a0:cc:35:6b:54  
          inet addr:169.254.6.40  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:129540 (126.5 KB)  TX bytes:129540 (126.5 KB)

azteka@azteka-desktop:~$

---

### Post by azteka22 on 2009-10-14
still no internet..

---

### Post by chili555 on 2009-10-14
> azteka@azteka-desktop:~$ ifconfig
[COLOR="Red"]eth0[/COLOR] Link encap:Ethernet HWaddr 00:a0:cc:35:6b:54
inet6 addr: fe80::2a0:ccff:fe35:6b54/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1Looks like you have a living, breathing ethernet interface. Did you click the Network Manager icon and try to connect?

---

### Post by azteka22 on 2009-10-14
yes, I clicked on Network Manager and did connect and it tries to connect but it doesnt say anything afterwards.. however when i reboot it says something like networkmanager error dbus error or sumthing like that..

---

### Post by chili555 on 2009-10-14
Please open a terminal and do:```
dmesg > dmesg.txt
```You will find a text file in your user directory called *dmesg.txt* that you can transfer on a USB drive and please post it here. Thanks.

---

### Post by azteka22 on 2009-10-14
Heres the dmesg.txt file

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-24-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Tue Jul 7 19:46:39 UTC 2009 (Ubuntu 2.6.24-24.56-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb820
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA5C0 checksum 0
[    0.000000] ACPI: RSDP 000FA5C0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 3FFF0000, 002C (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 3FFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 3FFF0120, 30E9 (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 3FFF8000, 0040
[    0.000000] ACPI: APIC 3FFF00C0, 0054 (r1 AMIINT VIA_K7          9 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=e19037be-d660-4a4e-ad91-58c55b2c4353 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1831.116 MHz processor.
[   24.525354] Console: colour VGA+ 80x25
[   24.525359] console [tty0] enabled
[   24.526363] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.527033] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.567704] Memory: 1026968k/1048512k available (2179k kernel code, 20828k reserved, 1007k data, 368k init, 131008k highmem)
[   24.567714] virtual kernel memory layout:
[   24.567715]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.567716]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.567718]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.567719]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.567720]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   24.567721]       .data : 0xc0320de8 - 0xc041cdc4   (1007 kB)
[   24.567723]       .text : 0xc0100000 - 0xc0320de8   (2179 kB)
[   24.567727] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.567791] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.647789] Calibrating delay using timer specific routine.. 3666.32 BogoMIPS (lpj=7332656)
[   24.647833] Security Framework initialized
[   24.647846] SELinux:  Disabled at boot.
[   24.647875] AppArmor: AppArmor initialized
[   24.647881] Failure registering capabilities with primary security module.
[   24.647894] Mount-cache hash table entries: 512
[   24.648086] Initializing cgroup subsys ns
[   24.648092] Initializing cgroup subsys cpuacct
[   24.648107] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   24.648125] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[   24.648130] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.648133] CPU: L2 Cache: 512K (64 bytes/line)
[   24.648138] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000
[   24.648153] Compat vDSO mapped to ffffe000.
[   24.648170] Checking 'hlt' instruction... OK.
[   24.664093] SMP alternatives: switching to UP code
[   24.665438] Freeing SMP alternatives: 11k freed
[   24.665587] Early unpacking initramfs... done
[   25.046547] ACPI: Core revision 20070126
[   25.046647] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.048383] CPU0: AMD Athlon(tm) XP 2500+ stepping 00
[   25.048405] Total of 1 processors activated (3666.32 BogoMIPS).
[   25.049155] ENABLING IO-APIC IRQs
[   25.049483] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.195635] Brought up 1 CPUs
[   25.195709] CPU0 attaching sched-domain:
[   25.195712]  domain 0: span 01
[   25.195714]   groups: 01
[   25.195958] net_namespace: 64 bytes
[   25.195968] Booting paravirtualized kernel on bare hardware
[   25.196507] Time: 18:06:02  Date: 10/14/09
[   25.196547] NET: Registered protocol family 16
[   25.196812] EISA bus registered
[   25.196847] ACPI: bus type pci registered
[   25.200691] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[   25.200694] PCI: Using configuration type 1
[   25.200702] Setting up standard PCI resources
[   25.206195] ACPI: EC: Look up EC in DSDT
[   25.209941] ACPI: Interpreter enabled
[   25.209945] ACPI: (supports S0 S1 S4 S5)
[   25.209959] ACPI: Using IOAPIC for interrupt routing
[   25.213137] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.213517] PCI quirk: region 0800-087f claimed by vt8235 PM
[   25.213521] PCI quirk: region 0400-040f claimed by vt8235 SMB
[   25.213739] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.223059] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   25.223149] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   25.223235] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   25.223320] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[   25.223417] ACPI: Power Resource [URP1] (off)
[   25.223445] ACPI: Power Resource [URP2] (off)
[   25.223471] ACPI: Power Resource [FDDP] (off)
[   25.223498] ACPI: Power Resource [LPTP] (off)
[   25.223548] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.223589] pnp: PnP ACPI init
[   25.223597] ACPI: bus type pnp registered
[   25.225383] pnp: PnP ACPI: found 7 devices
[   25.225386] ACPI: ACPI bus type pnp unregistered
[   25.225391] PnPBIOS: Disabled by ACPI PNP
[   25.225677] PCI: Using ACPI for IRQ routing
[   25.225681] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.239575] NET: Registered protocol family 8
[   25.239578] NET: Registered protocol family 20
[   25.239672] AppArmor: AppArmor Filesystem Enabled
[   25.243550] Time: tsc clocksource has been installed.
[   25.251587] system 00:02: ioport range 0x3f0-0x3f1 has been reserved
[   25.251591] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   25.251594] system 00:02: ioport range 0x400-0x40f has been reserved
[   25.251597] system 00:02: ioport range 0x820-0x821 has been reserved
[   25.251601] system 00:02: iomem range 0xfee00000-0xfee00fff could not be reserved
[   25.282070] PCI: Bridge: 0000:00:01.0
[   25.282073]   IO window: disabled.
[   25.282077]   MEM window: dde00000-dfefffff
[   25.282081]   PREFETCH window: cdd00000-ddcfffff
[   25.282097] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.282110] NET: Registered protocol family 2
[   25.319642] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.320114] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   25.322089] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.323098] TCP: Hash tables configured (established 131072 bind 65536)
[   25.323102] TCP reno registered
[   25.331714] checking if image is initramfs... it is
[   25.783332] Switched to high resolution mode on CPU 0
[   26.046588] Freeing initrd memory: 7686k freed
[   26.047487] audit: initializing netlink socket (disabled)
[   26.047509] audit(1255543562.376:1): initialized
[   26.047713] highmem bounce pool size: 64 pages
[   26.049928] VFS: Disk quotas dquot_6.5.1
[   26.050015] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.050181] io scheduler noop registered
[   26.050184] io scheduler anticipatory registered
[   26.050186] io scheduler deadline registered
[   26.050198] io scheduler cfq registered (default)
[   26.050212] PCI: VIA PCI bridge detected. Disabling DAC.
[   26.050279] Boot video device is 0000:01:00.0
[   26.050597] isapnp: Scanning for PnP cards...
[   26.404121] isapnp: No Plug & Play device found
[   26.438400] Real Time Clock Driver v1.12ac
[   26.438522] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.438652] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.439294] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.440235] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.440322] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.440487] PNP: No PS/2 controller found. Probing ports directly.
[   26.440891] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.440897] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.447198] mice: PS/2 mouse device common for all mice
[   26.447336] EISA: Probing bus 0 at eisa.0
[   26.447371] EISA: Detected 0 cards.
[   26.447376] cpuidle: using governor ladder
[   26.447378] cpuidle: using governor menu
[   26.447546] NET: Registered protocol family 1
[   26.447579] Using IPI No-Shortcut mode
[   26.447621] registered taskstats version 1
[   26.447717]   Magic number: 13:51:140
[   26.447951] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.447953] EDD information not available.
[   26.448513] Freeing unused kernel memory: 368k freed
[   26.448546] Write protecting the kernel read-only data: 806k
[   27.701620] fuse init (API version 7.9)
[   27.724644] ACPI: Processor [CPU1] (supports 16 throttling states)
[   28.172403] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   28.172489] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 16
[   28.240006] usbcore: registered new interface driver usbfs
[   28.240039] usbcore: registered new interface driver hub
[   28.258244] usbcore: registered new device driver usb
[   28.266497] eth0: Lite-On PNIC-II rev 37 at Port 0xec00, 00:a0:cc:35:6b:54, IRQ 16.
[   28.296302] SCSI subsystem initialized
[   28.308770] USB Universal Host Controller Interface driver v3.0
[   28.308892] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[   28.308907] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   28.309242] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   28.309276] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000e000
[   28.309458] usb usb1: configuration #1 chosen from 1 choice
[   28.309486] hub 1-0:1.0: USB hub found
[   28.309495] hub 1-0:1.0: 2 ports detected
[   28.336800] libata version 3.00 loaded.
[   28.410273] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 17
[   28.410292] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   28.410326] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   28.410352] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000e400
[   28.410489] usb usb2: configuration #1 chosen from 1 choice
[   28.410516] hub 2-0:1.0: USB hub found
[   28.410523] hub 2-0:1.0: 2 ports detected
[   28.514249] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 17
[   28.514266] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   28.514302] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   28.514327] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000e800
[   28.514465] usb usb3: configuration #1 chosen from 1 choice
[   28.514493] hub 3-0:1.0: USB hub found
[   28.514501] hub 3-0:1.0: 2 ports detected
[   28.618366] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 17
[   28.618385] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   28.618417] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   28.618470] ehci_hcd 0000:00:10.3: irq 17, io mem 0xdffffe00
[   28.650039] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   28.662021] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.662176] usb usb4: configuration #1 chosen from 1 choice
[   28.662213] hub 4-0:1.0: USB hub found
[   28.662222] hub 4-0:1.0: 6 ports detected
[   28.766377] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   28.766452] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   28.775575] pata_via 0000:00:11.1: version 0.3.3
[   28.775604] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   28.776673] scsi0 : pata_via
[   28.777470] scsi1 : pata_via
[   28.778990] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   28.778994] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   28.942378] ata1.00: ATA-5: ST360021A, 3.19, max UDMA/100
[   28.942385] ata1.00: 117231408 sectors, multi 16: LBA 
[   28.958190] ata1.00: configured for UDMA/100
[   29.278059] ata2.00: ATAPI: PIONEER DVD-RW  DVR-108, 1.20, max UDMA/66
[   29.441859] ata2.00: configured for UDMA/66
[   29.442014] scsi 0:0:0:0: Direct-Access     ATA      ST360021A        3.19 PQ: 0 ANSI: 5
[   29.448254] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-108  1.20 PQ: 0 ANSI: 5
[   29.459444] Driver 'sd' needs updating - please use bus_type methods
[   29.459572] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   29.459590] sd 0:0:0:0: [sda] Write Protect is off
[   29.459593] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.459615] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.459674] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   29.459685] sd 0:0:0:0: [sda] Write Protect is off
[   29.459688] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.459705] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.459710]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   29.470462]  sda1 sda2 sda3
[   29.495516] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.502535] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.502560] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   29.531556] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   29.531566] Uniform CD-ROM driver Revision: 3.20
[   29.531644] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.853318] Attempting manual resume
[   29.853324] swsusp: Resume From Partition 8:3
[   29.853325] PM: Checking swsusp image.
[   29.853599] PM: Resume from disk failed.
[   29.896427] kjournald starting.  Commit interval 5 seconds
[   29.896448] EXT3-fs: mounted filesystem with ordered data mode.
[   29.965424] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   30.140247] usb 1-1: configuration #1 chosen from 1 choice
[   30.381231] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   30.557969] usb 1-2: configuration #1 chosen from 1 choice
[   37.408030] Linux agpgart interface v0.102
[   37.499328] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.746024] agpgart: Detected VIA KM400/KM400A chipset
[   37.747486] agpgart: AGP aperture is 16M @ 0xe0000000
[   37.794000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.926104] input: Power Button (FF) as /devices/virtual/input/input1
[   37.941899] ACPI: Power Button (FF) [PWRF]
[   37.942018] input: Power Button (CM) as /devices/virtual/input/input2
[   37.957804] ACPI: Power Button (CM) [PWRB]
[   37.957944] input: Sleep Button (CM) as /devices/virtual/input/input3
[   37.973787] ACPI: Sleep Button (CM) [SLPB]
[   38.009812] irda_init()
[   38.009848] NET: Registered protocol family 23
[   39.325277] input: Logitech USB RECEIVER as /devices/virtual/input/input4
[   39.349223] lmpcm_usb.c: Detected device: Logitech USB RECEIVER
[   39.349254] usbcore: registered new interface driver lmpcm_usb
[   39.349259] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   39.549440] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   39.577703] usbcore: registered new interface driver hiddev
[   39.591257] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input6
[   39.605149] input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:10.0-2
[   39.605178] usbcore: registered new interface driver usbhid
[   39.605183] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   39.887087] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 18
[   39.887230] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   41.677534] lp: driver loaded but no devices found
[   41.869805] Adding 2096472k swap on /dev/sda3.  Priority:-1 extents:1 across:2096472k
[   42.420261] EXT3 FS on sda2, internal journal
[   43.632549] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.046428] No dock devices found.
[   45.187630] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   45.187638] apm: overridden by ACPI.
[   45.340782] ppdev: user-space parallel port driver
[   45.495703] audit(1255557982.957:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4642 profile="/usr/sbin/cupsd" namespace="default"
[   46.583642] Bluetooth: Core ver 2.11
[   46.584526] NET: Registered protocol family 31
[   46.584532] Bluetooth: HCI device and connection manager initialized
[   46.584537] Bluetooth: HCI socket layer initialized
[   46.621879] Bluetooth: L2CAP ver 2.9
[   46.621887] Bluetooth: L2CAP socket layer initialized
[   46.673039] Bluetooth: RFCOMM socket layer initialized
[   46.673065] Bluetooth: RFCOMM TTY layer initialized
[   46.673067] Bluetooth: RFCOMM ver 1.8
[   50.581414] NET: Registered protocol family 17
[   67.399585] NET: Registered protocol family 10
[   67.400156] lo: Disabled Privacy Extensions
[   78.343442] eth0: no IPv6 routers present

---

### Post by azteka22 on 2009-10-14
in this dmesg it doesnt say anything about networkmanager error though...

---

### Post by chili555 on 2009-10-14
> **azteka22 said:**
> in this dmesg it doesnt say anything about networkmanager error though...Nor dbus; we have no clues, yet, to the problem. Let's try two things. First:```
sudo /etc/init.d/NetworkManager stop
sudo dhclient eth0
```Then do:```
sudo /etc/init.d/NetworkManager start
```You can copy and paste from the terminal to a text document (Applications -> Accessories -> Text Editor) and save it as any convenient name and transfer by USB, as before. We are looking for errors, clues...anything that will help us fix this.

Incidentally, with a big file like dmesg.txt, you could have added it as an attachment to your post (see the little paperclip?) rather than flooding the forum. No real harm the way you did it; it's just a bit tidier when posting a big file.

---

### Post by chaparrazo on 2009-10-14
i'm having a similar issue and found this thread by searching for the irregularity in my situation: it's the "avahi" after eth0 in your (and my) ifconfig at the beginning of the second paragraph. 

-------------

eth0 Link encap:Ethernet HWaddr 00:a0:cc:35:6b:54
inet6 addr: fe80::2a0:ccff:fe35:6b54/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:7 errors:2 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:1194 (1.1 KB)
Interrupt:16 Base address:0xec00

eth0:avahi Link encap:Ethernet HWaddr 00:a0:cc:35:6b:54
inet addr:169.254.6.40 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:16 Base address:0xec00

------------- 

i found this by comparing to 2 other boxes running on the network nearby. 

if you go into system / administration / network tools and click where you select the network device, does it open three items? 1st is loopback, then a line that ends (eth0) and (here's the kicker i think) (eth0:avahi) 

when you select the eth0 on mine, the protocol is IPv6 only and then when you select the eth0:anahi you get the protocol IPv4. they're both supposed to be there on the eth0 alone. seems to me it's gone schizoid . . . 

anyway, that's this newbie's observation. does that help anyone identify the problem that will get us back on the superhighway? 

my problem is on a box with ubuntu 8.04 that was working fine, then one day no longer connected to the internet. i can ping it from another machine on the net here but no way to the highway. 

my daughter and i just did a fresh install, crossed our fingers and (drum roll please) . . . started to cry when it was just the same

---

### Post by chili555 on 2009-10-14
> [COLOR="Red"]eth0:avahi[/COLOR] Link encap:Ethernet HWaddr 00:a0:cc:35:6b:54
inet addr:[COLOR="Red"]169.254.6.40[/COLOR]This is simply a placeholder IP address. It indicates that the interface has attempted to get an IP address from the router or other access point and failed. It (rarely) may be the driver, the cable, a setting in the router or an oops in Network Manager. > i can ping it from another machine on the net here but no way to the highway.Weird. Please open a terminal and do:```
cat /etc/resolv.conf
```Please post the result.

---

### Post by chaparrazo on 2009-10-14
nameserver 24.116.2.50
nameserver 24.116.2.34 

i currently have 2 nics on this box, one's built in (broadcom netxtreme bcm5782 gigabit ethernet) and a card that's in a slot (Intel 82557/8/9/0/1 ethernet pro 100). we thought maybe the nic was bad.

---

### Post by chili555 on 2009-10-14
> (Intel 82557/8/9/0/1 ethernet pro 100). we thought maybe the nic was bad.Is that eth0? Please post:```
sudo ethtool eth0
dmesg | grep eth0
```We can probably get some idea if the NIC is acting up.

---

### Post by chaparrazo on 2009-10-14
eth0 is the gigabit built in. here's the goop: 

hannah@qwerty:~$ sudo ethtool eth0
[sudo] password for hannah: 

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
        Link detected: yes


hannah@qwerty:~$ dmesg | grep eth0

[   17.046859] eth0: Tigon3 [partno(BCM95782A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0d:9d:56:1a:23
[   17.046868] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[   17.046871] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[   83.756292] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2829.263460] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 2829.263466] tg3: eth0: Flow control is on for TX and on for RX.
[ 2829.264257] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2839.978657] eth0: no IPv6 routers present
[ 2947.817704] tg3: eth0: Link is down.
[ 3040.723460] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 3040.723466] tg3: eth0: Flow control is on for TX and on for RX.
[ 3040.723807] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3051.094209] eth0: no IPv6 routers present
[ 3212.873481] tg3: eth0: Link is down.
[ 3776.132173] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 3776.132179] tg3: eth0: Flow control is on for TX and on for RX.
[ 3776.132838] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3786.421327] eth0: no IPv6 routers present

---

### Post by azteka22 on 2009-10-14
fazteka@azteka-desktop:~$ sudo /etc/init.d/NetworkManager stop
sudo: /etc/init.d/NetworkManager: command not found
azteka@azteka-desktop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:a0:cc:35:6b:54
Sending on   LPF/eth0/00:a0:cc:35:6b:54
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
azteka@azteka-desktop:~$

---

### Post by azteka22 on 2009-10-14
are you sure it is not the driver the main cause of the problem? because on the router the light for the ethernet port is not turned on however on the computer the internet light does flash, so this could be that I do not have the appropriat driver installed?

---

### Post by azteka22 on 2009-10-15
I am still trying to troubleshoot this problem. I connected the same cable that I was using to connect my desktop computer to the router to my laptop running Sabayon Linux to the router and everything works perfectly, so this determines for a fact that the cable nor the router is the problem behind this error. 

I just saw this, in one of the commands that you had me run..

> [ 2839.978657] eth0: no IPv6 routers present
[ 2947.817704] tg3: eth0: Link is down.

Does this mean that my ubuntu desktop is configured to look for an ipv6 address instead of a ipv4 address?? 

any ideas?

---

### Post by chili555 on 2009-10-15
> I just saw this, in one of the commands that you had me run..

Quote:
[ 2839.978657] eth0: no IPv6 routers present
[ 2947.817704] tg3: eth0: Link is down. I thought that was in chaparrazo's response, not yours. Maybe I am confused. I should have asked that he start a new thread. If he/she is reading this, please do so.

However, I would be very interested in your output:```
dmesg | grep eth0

```> Does this mean that my ubuntu desktop is configured to look for an ipv6 address instead of a ipv4 address??It's configured to look for both. In this instance, it found no IPv6 routers. It's not forthcoming about IPv4 routers, but I assume, if it found one, it would have connected.

---

### Post by azteka22 on 2009-10-15
```
azteka:~$ sudo dmesg | grep eth0[sudo] password for azteka:
[ 27.739745] eth0: Lite-On PNIC-II rev 37 at Port 0xec00, 00:a0:cc:35:6b:54, IRQ 16.
[ 100.316800] eth0: no IPv6 routers present
azteka:~$
```

i also attached a picture of the error message i get when i turn my computer off

---

### Post by azteka22 on 2009-10-16
```
 sudo ethtool eth0
[sudo] password for azteka:
Settings for eth0:
No data availaable

```

```
ethtool -i eth0
driver: tulip
version: 1.1.15
firmware-version:
bus-info: 0000:00:09.0
```

Do I have the appropriate driver version installed?

---

### Post by chili555 on 2009-10-17
> Do I have the appropriate driver version installed? Yes, indeed. Your *dmesg* file looks like the driver is getting loaded and an interface, *eth0*, is getting created. It just never connects. This part is bothersome:> fazteka@azteka-desktop:~$ sudo /etc/init.d/NetworkManager stop
sudo: /etc/init.d/NetworkManager: command not foundPlease show us:```
ls /etc/init.d | grep -i network
```Your dbus error, associated with Network Manager, is also bothersome. I have Googled it some and so far, have not found a fix. I will keep going.

---

### Post by azteka22 on 2009-10-17
Problem Solved, I kept researching this problem and I found the solution here in the Ubuntu forums, I typed in these commands:

```
> sudo ip addr flush dev eth0 && sudo ip link set eth0 down
 > sudo ip link set eth0 up
 > sudo /sbin/dhclient eth0
```
and somehow It started working
but thank u chilli555 for helping, I appreciated it.

---

