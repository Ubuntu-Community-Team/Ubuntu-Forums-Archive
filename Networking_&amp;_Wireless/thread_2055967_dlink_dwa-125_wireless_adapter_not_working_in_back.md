---
title: "dlink dwa-125 wireless adapter not working in backtrack 5"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by nepalihippo on 2012-09-10
I have been through the previous post but could not solve mine. Please help me out . 

i have post all the info below : 


1 ) Machine Brand and Model (PC/Laptop):
 VMware on Hp Pavilion g6 laptop intel core i5

2 ) Wireless Brand, Model and Wireless Chipset:
code : lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 0
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
02:00.0 USB Controller: VMware USB1.1 UHCI Controller
02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:03.0 USB Controller: VMware USB2 EHCI Controller

Code lsusb:
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2001:3c19 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


 
 Code: $ lspci -nn | grep 'Wireless Brand' 

nothing on this command
3 ) check interface:
 Code: $ ifconfig $ iwconfig (hint) if the Wireless interface name is wlan0 you can also use


eth1      Link encap:Ethernet  HWaddr 00:0c:29:2f:67:46  
          inet addr:192.168.29.130  Bcast:192.168.29.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe2f:6746/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2415 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3146984 (3.1 MB)  TX bytes:174215 (174.2 KB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90201 (90.2 KB)  TX bytes:90201 (90.2 KB)
code iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

 Code: $ iwconfig wlan0 
4 ) Check for modules:
 Code: $ lsmod (hint) search for the Wireless module
odule                  Size  Used by
vsock                  46691  0 
acpiphp                23176  0 
dm_crypt               22236  0 
snd_ens1371            24455  0 
gameport               14558  1 snd_ens1371
snd_ac97_codec        104623  1 snd_ens1371
ac97_bus               12602  1 snd_ac97_codec
snd_pcm                72878  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            24215  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14076  1 snd_seq_midi
snd_seq                50403  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23911  2 snd_pcm,snd_seq
snd_seq_device         13817  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    52787  7 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              12983  0 
btusb                  17979  0 
bluetooth             149909  1 btusb
joydev                 17161  0 
soundcore              12534  1 snd
snd_page_alloc         13709  1 snd_pcm
vmci                   69759  1 vsock
shpchp                 32187  0 
lp                     13321  0 
mac_hid                13037  0 
vmw_balloon            12593  0 
ppdev                  12840  0 
parport_pc             31867  1 
parport                34960  3 lp,ppdev,parport_pc
psmouse                72465  0 
serio_raw              13027  0 
dm_mirror              21585  0 
dm_region_hash         15035  1 dm_mirror
dm_log                 17871  2 dm_mirror,dm_region_hash
vmw_pvscsi             17939  0 
vmxnet3                44018  0 
aufs                  162169  0 
usbhid                 41119  0 
hid                    79842  1 usbhid
floppy                 59430  0 
mptspi                 22137  2 
mptscsih               37831  1 mptspi
pcnet32                40553  0 
mptbase                90054  2 mptspi,mptscsih
scsi_transport_spi     25091  1 mptspi

 Code: $ lsmod | grep "wlan_module_name" 
5 ) Kernel boot messages
 Code: $ dmesg (hint) the same as in (4)
[    0.924288] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.929310] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.931699] TCP: Hash tables configured (established 131072 bind 65536)
[    0.931780] TCP reno registered
[    0.931856] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.932048] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.933380] NET: Registered protocol family 1
[    0.933584] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.933811] pci 0000:00:0f.0: Boot video device
[    0.934935] PCI: CLS 32 bytes, default 64
[    0.938577] Trying to unpack rootfs image as initramfs...
[    1.465852] Freeing initrd memory: 17092k freed
[    1.469873] Simple Boot Flag at 0x36 set to 0x1
[    1.470448] audit: initializing netlink socket (disabled)
[    1.470490] type=2000 audit(1347290092.352:1): initialized
[    1.486565] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.490294] VFS: Disk quotas dquot_6.5.2
[    1.490336] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.494064] fuse init (API version 7.17)
[    1.494158] msgmni has been set to 1495
[    1.494856] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.494973] io scheduler noop registered
[    1.495014] io scheduler deadline registered
[    1.495056] io scheduler cfq registered (default)
[    1.495098] pcieport 0000:00:15.0: setting latency timer to 64
[    1.495140] pcieport 0000:00:15.0: irq 40 for MSI/MSI-X
[    1.495181] pcieport 0000:00:15.1: setting latency timer to 64
[    1.495223] pcieport 0000:00:15.1: irq 41 for MSI/MSI-X
[    1.495265] pcieport 0000:00:15.2: setting latency timer to 64
[    1.495307] pcieport 0000:00:15.2: irq 42 for MSI/MSI-X
[    1.495348] pcieport 0000:00:15.3: setting latency timer to 64
[    1.495390] pcieport 0000:00:15.3: irq 43 for MSI/MSI-X
[    1.495432] pcieport 0000:00:15.4: setting latency timer to 64
[    1.495474] pcieport 0000:00:15.4: irq 44 for MSI/MSI-X
[    1.495515] pcieport 0000:00:15.5: setting latency timer to 64
[    1.495557] pcieport 0000:00:15.5: irq 45 for MSI/MSI-X
[    1.495599] pcieport 0000:00:15.6: setting latency timer to 64
[    1.495641] pcieport 0000:00:15.6: irq 46 for MSI/MSI-X
[    1.495682] pcieport 0000:00:15.7: setting latency timer to 64
[    1.495724] pcieport 0000:00:15.7: irq 47 for MSI/MSI-X
[    1.495766] pcieport 0000:00:16.0: setting latency timer to 64
[    1.495807] pcieport 0000:00:16.0: irq 48 for MSI/MSI-X
[    1.495849] pcieport 0000:00:16.1: setting latency timer to 64
[    1.495891] pcieport 0000:00:16.1: irq 49 for MSI/MSI-X
[    1.495933] pcieport 0000:00:16.2: setting latency timer to 64
[    1.495974] pcieport 0000:00:16.2: irq 50 for MSI/MSI-X
[    1.496016] pcieport 0000:00:16.3: setting latency timer to 64
[    1.496058] pcieport 0000:00:16.3: irq 51 for MSI/MSI-X
[    1.496100] pcieport 0000:00:16.4: setting latency timer to 64
[    1.496141] pcieport 0000:00:16.4: irq 52 for MSI/MSI-X
[    1.496183] pcieport 0000:00:16.5: setting latency timer to 64
[    1.496225] pcieport 0000:00:16.5: irq 53 for MSI/MSI-X
[    1.496267] pcieport 0000:00:16.6: setting latency timer to 64
[    1.496308] pcieport 0000:00:16.6: irq 54 for MSI/MSI-X
[    1.496350] pcieport 0000:00:16.7: setting latency timer to 64
[    1.496392] pcieport 0000:00:16.7: irq 55 for MSI/MSI-X
[    1.496434] pcieport 0000:00:17.0: setting latency timer to 64
[    1.496475] pcieport 0000:00:17.0: irq 56 for MSI/MSI-X
[    1.496517] pcieport 0000:00:17.1: setting latency timer to 64
[    1.496559] pcieport 0000:00:17.1: irq 57 for MSI/MSI-X
[    1.496601] pcieport 0000:00:17.2: setting latency timer to 64
[    1.496642] pcieport 0000:00:17.2: irq 58 for MSI/MSI-X
[    1.496684] pcieport 0000:00:17.3: setting latency timer to 64
[    1.496726] pcieport 0000:00:17.3: irq 59 for MSI/MSI-X
[    1.496767] pcieport 0000:00:17.4: setting latency timer to 64
[    1.496809] pcieport 0000:00:17.4: irq 60 for MSI/MSI-X
[    1.496851] pcieport 0000:00:17.5: setting latency timer to 64
[    1.496893] pcieport 0000:00:17.5: irq 61 for MSI/MSI-X
[    1.496934] pcieport 0000:00:17.6: setting latency timer to 64
[    1.496976] pcieport 0000:00:17.6: irq 62 for MSI/MSI-X
[    1.497018] pcieport 0000:00:17.7: setting latency timer to 64
[    1.497060] pcieport 0000:00:17.7: irq 63 for MSI/MSI-X
[    1.497101] pcieport 0000:00:18.0: setting latency timer to 64
[    1.497143] pcieport 0000:00:18.0: irq 64 for MSI/MSI-X
[    1.497185] pcieport 0000:00:18.1: setting latency timer to 64
[    1.497227] pcieport 0000:00:18.1: irq 65 for MSI/MSI-X
[    1.497794] pcieport 0000:00:18.2: setting latency timer to 64
[    1.497836] pcieport 0000:00:18.2: irq 66 for MSI/MSI-X
[    1.497878] pcieport 0000:00:18.3: setting latency timer to 64
[    1.497919] pcieport 0000:00:18.3: irq 67 for MSI/MSI-X
[    1.497961] pcieport 0000:00:18.4: setting latency timer to 64
[    1.498003] pcieport 0000:00:18.4: irq 68 for MSI/MSI-X
[    1.498045] pcieport 0000:00:18.5: setting latency timer to 64
[    1.498086] pcieport 0000:00:18.5: irq 69 for MSI/MSI-X
[    1.498128] pcieport 0000:00:18.6: setting latency timer to 64
[    1.498170] pcieport 0000:00:18.6: irq 70 for MSI/MSI-X
[    1.498212] pcieport 0000:00:18.7: setting latency timer to 64
[    1.498253] pcieport 0000:00:18.7: irq 71 for MSI/MSI-X
[    1.498295] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    1.498337] pcie_pme 0000:00:15.0cie01: service driver pcie_pme loaded
[    1.498379] pcieport 0000:00:15.1: Signaling PME through PCIe PME interrupt
[    1.498405] pcie_pme 0000:00:15.1cie01: service driver pcie_pme loaded
[    1.498447] pcieport 0000:00:15.2: Signaling PME through PCIe PME interrupt
[    1.498472] pcie_pme 0000:00:15.2cie01: service driver pcie_pme loaded
[    1.498514] pcieport 0000:00:15.3: Signaling PME through PCIe PME interrupt
[    1.498539] pcie_pme 0000:00:15.3cie01: service driver pcie_pme loaded
[    1.498581] pcieport 0000:00:15.4: Signaling PME through PCIe PME interrupt
[    1.498605] pcie_pme 0000:00:15.4cie01: service driver pcie_pme loaded
[    1.498647] pcieport 0000:00:15.5: Signaling PME through PCIe PME interrupt
[    1.498672] pcie_pme 0000:00:15.5ie01: service driver pcie_pme loaded
[    1.498713] pcieport 0000:00:15.6: Signaling PME through PCIe PME interrupt
[    1.498738] pcie_pme 0000:00:15.6cie01: service driver pcie_pme loaded
[    1.498780] pcieport 0000:00:15.7: Signaling PME through PCIe PME interrupt
[    1.498805] pcie_pme 0000:00:15.7cie01: service driver pcie_pme loaded
[    1.498847] pcieport 0000:00:16.0: Signaling PME through PCIe PME interrupt
.
.
[    1.504454] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.504496] vesafb: mode is 1024x768x16, linelength=2048, pages=0
[    1.504536] vesafb: scrolling: redraw
[    1.504578] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    1.504619] vesafb: framebuffer at 0xd0000000, mapped to 0xf0880000, using 1536k, total 1536k
[    1.504727] fbcon: VESA VGA (fb0) is primary device
[    1.505752] bootsplash 3.1.6-2004/03/31: looking for picture...
[    1.513734]  silentjpeg size 69816 bytes,
[    1.513776] ...found (1024x768, 69708 bytes, v3).
[    1.529703] Console: switching to colour frame buffer device 107x34
[    1.541700] fb0: VESA VGA frame buffer device
[    1.541779] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.541857] ACPI: AC Adapter [ACAD] (on-line)
[    1.542024] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.542065] ACPI: Power Button [PWRF]
[    1.561792] ERST: Table is not found!
[    1.561833] GHES: HEST is not enabled!
[    1.561875] isapnp: Scanning for PnP cards...
[    1.872014] isapnp: No Plug & Play device found
[    1.874255] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.903972] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.932743] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.960772] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.986974] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.989365] Linux agpgart interface v0.103
[    1.989406] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[    1.989520] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x0
[    1.993498] brd: module loaded
[    1.994007] loop: module loaded
[    1.996657] ata_piix 0000:00:07.1: version 2.13
[    2.000750] scsi0 : ata_piix
[    2.000881] scsi1 : ata_piix
[    2.000923] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x10c0 irq 14
[    2.000965] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x10c8 irq 15
[    2.001048] Fixed MDIO Bus: probed
[    2.001090] tun: Universal TUN/TAP device driver, 1.6
[    2.001132] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.001467] arcnet loaded.
[    2.001508] PPP generic driver version 2.4.2
[    2.001688] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.001729] ehci_hcd 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.001771] ehci_hcd 0000:02:03.0: EHCI Host Controller
[    2.001885] ehci_hcd 0000:02:03.0: new USB bus registered, assigned bus number 1
[    2.001927] ehci_hcd 0000:02:03.0: cache line size of 32 is not supported
[    2.001968] ehci_hcd 0000:02:03.0: irq 17, io mem 0xc9000000
[    2.013011] ehci_hcd 0000:02:03.0: USB 2.0 started, EHCI 1.00
[    2.016687] hub 1-0:1.0: USB hub found
[    2.016729] hub 1-0:1.0: 6 ports detected
[    2.016771] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.016812] uhci_hcd: USB Universal Host Controller Interface driver
[    2.016854] uhci_hcd 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.016896] uhci_hcd 0000:02:00.0: UHCI Host Controller
[    2.017021] uhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 2
[    2.017110] uhci_hcd 0000:02:00.0: irq 18, io base 0x000020c0
[    2.017235] hub 2-0:1.0: USB hub found
[    2.017276] hub 2-0:1.0: 2 ports detected
[    2.017318] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[    2.525544] Refined TSC clocksource calibration: 2660.548 MHz.
[    2.563313] Switching to clocksource tsc
[    2.563797] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.563899] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.564194] mousedev: PS/2 mouse device common for all mice
[    2.584740] ata2.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
[    2.585589] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.586138] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.586361] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.588243] ata2.00: configured for UDMA/33
[    2.588961] scsi 1:0:0:0: CD-ROM            NECVMWar VMware IDE CDR10 1.00 PQ: 0 ANSI: 5
[    2.595610] sr0: scsi3-mmc drive: 1x/1x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.595671] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.595863] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.595998] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    2.596584] device-mapper: uevent: version 1.0.3
[    2.596768] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.596830] EISA: Probing bus 0 at eisa.0
[    2.596891] EISA: Cannot allocate resource for mainboard
[    2.596953] Cannot allocate resource for EISA slot 1
[    2.597014] Cannot allocate resource for EISA slot 2
[    2.597076] Cannot allocate resource for EISA slot 3
[    2.597137] Cannot allocate resource for EISA slot 4
[    2.597199] Cannot allocate resource for EISA slot 5
[    2.597260] Cannot allocate resource for EISA slot 6
[    2.597322] Cannot allocate resource for EISA slot 7
[    2.597383] Cannot allocate resource for EISA slot 8
[    2.597445] EISA: Detected 0 cards.
[    2.597568] cpufreq-nforce2: No nForce2 chipset.
[    2.599366] cpuidle: using governor ladder
[    2.599427] cpuidle: using governor menu
[    2.599489] EFI Variables Facility v0.08 2004-May-17
[    2.602015] TCP cubic registered
[    2.603290] NET: Registered protocol family 10
[    2.607322] NET: Registered protocol family 17
[    2.607384] Registering the dns_resolver key type
[    2.607445] Using IPI No-Shortcut mode
[    2.607765] registered taskstats version 1
[    2.635492] rtc_cmos 00:04: setting system clock to 2012-09-10 15:14:54 UTC (1347290094)
[    2.635554] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.635615] EDD information not available.
[    2.635921] Freeing unused kernel memory: 704k freed
[    2.639324] Write protecting the kernel text: 5508k
[    2.639385] Write protecting the kernel read-only data: 2108k
[    2.668279] udev: starting version 151
[    2.668512] udevd (82): /proc/82/oom_adj is deprecated, please use /proc/82/oom_score_adj instead.
[    2.735040] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    2.801314] Fusion MPT base driver 3.04.20
[    2.803563] Copyright (c) 1999-2008 LSI Corporation
[    2.810940] pcnet32: pcnet32.c:v1.35 21.Apr.2008 [EMAIL="tsbogend@alpha.franken.de"]tsbogend@alpha.franken.de[/EMAIL]
[    2.811001] pcnet32 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.811063] pcnet32: PCnet/PCI II 79C970A at 0x2000, 00:0c:29:2f:67:46 assigned IRQ 19
[    2.832614] Fusion MPT SPI Host driver 3.04.20
[    2.857398] mptspi 0000:00:10.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.859863] pcnet32: eth0: registered as PCnet/PCI II 79C970A
[    2.859924] pcnet32: 1 cards_found
[    2.875562] Floppy drive(s): fd0 is 1.44M
[    2.879655] mptbase: ioc0: Initiating bringup
[    2.891250] FDC 0 is a post-1991 82077
[    2.954542] ioc0: LSI53C1030 B0: Capabilities={Initiator}
[    3.002432] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    3.114556] scsi2 : ioc0: LSI53C1030 B0, FwRev=01032920h, Ports=1, MaxQ=128, IRQ=17
[    3.133036] hub 2-2:1.0: USB hub found
[    3.135704] hub 2-2:1.0: 7 ports detected
[    3.150446] input: VMware VMware Virtual USB Mouse as /devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.0/input/input2
[    3.151095] generic-usb 0003:0E0F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [VMware VMware Virtual USB Mouse] on usb-0000:02:00.0-1/input0
[    3.154311] input: VMware VMware Virtual USB Mouse as /devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.1/input/input3
[    3.159097] generic-usb 0003:0E0F:0003.0002: input,hidraw1: USB HID v1.10 Mouse [VMware VMware Virtual USB Mouse] on usb-0000:02:00.0-1/input1
[    3.159659] usbcore: registered new interface driver usbhid
[    3.159754] usbhid: USB HID core driver
[    3.227105] scsi 2:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2
[    3.230216] scsi target2:0:0: Beginning Domain Validation
[    3.231009] scsi target2:0:0: Domain Validation skipping write tests
[    3.231105] scsi target2:0:0: Ending Domain Validation
[    3.231200] scsi target2:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
[    3.235052] sd 2:0:0:0: [sda] 41943040 512-byte logical blocks: (21.4 GB/20.0 GiB)
[    3.235243] sd 2:0:0:0: [sda] Write Protect is off
[    3.235339] sd 2:0:0:0: [sda] Mode Sense: 61 00 00 00
[    3.235515] sd 2:0:0:0: [sda] Cache data unavailable
[    3.235610] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    3.236247] sd 2:0:0:0: [sda] Cache data unavailable
[    3.240344] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    3.243291] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.310216]  sda: sda1 sda2 < sda5 >
[    3.311230] sd 2:0:0:0: [sda] Cache data unavailable
[    3.311325] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    3.311420] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.425518] usb 2-2.1: new full-speed USB device number 4 using uhci_hcd
[    3.861387] aufs 3.2-20120109
[    3.869335] VMware vmxnet3 virtual NIC driver - version 1.1.18.0-k-NAPI
[    3.873921] VMware PVSCSI driver - version 1.0.1.0-k
[    3.948354] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.573202] Adding 916476k swap on /dev/sda5.  Priority:-1 extents:1 across:916476k 
[    5.645439] udev: starting version 151
[    5.798646] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    6.179172] psmouse serio1: hgpk: ID: 10 00 64
[    6.188855] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[    6.279262] parport_pc 00:09: reported by Plug and Play ACPI
[    6.279334] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    6.334204] ppdev: user-space parallel port driver
[    6.356323] lp: driver loaded but no devices found
[    6.374862] lp0: using parport0 (interrupt-driven).
[    6.378744] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.409569] [420]: VMCI: shared components initialized.
[    6.409642] Probing for vmci/PCI.
[    6.413557] vmci 0000:00:07.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.413629] Found vmci/PCI at 0x1080, irq 16.
[    6.413701] VMCI: using capabilities 0xc.
[    6.413773] [420]: VMCI: Host capability check: PASSED.
[    6.414914] vmci 0000:00:07.7: irq 72 for MSI/MSI-X
[    6.414986] vmci 0000:00:07.7: irq 73 for MSI/MSI-X
[    6.415058] Registered vmci device.
[    6.415853] [420]: VMCI: Using guest personality
[    6.415925] [420]: VMCI: host components initialized.
[    6.416691] [420]: VMCI: Module registered (name=vmci,major=10,minor=57).
[    6.416717] [420]: VMCI: Using host personality
[    6.416733] [420]: VMCI: Module (name=vmci) is initialized
[    6.652953] Bluetooth: Core ver 2.16
[    6.653167] NET: Registered protocol family 31
[    6.653193] Bluetooth: HCI device and connection manager initialized
[    6.653263] Bluetooth: HCI socket layer initialized
[    6.653324] Bluetooth: L2CAP socket layer initialized
[    6.654018] Bluetooth: SCO socket layer initialized
[    6.656506] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    6.659046] usbcore: registered new interface driver btusb
[    6.676336] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[    6.773723] udev: renamed network interface eth0 to eth1
[    7.630552] snd_ens1371 0000:02:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.991033] pcnet32 0000:02:01.0: eth1: link up
[   19.911691] eth1: no IPv6 routers present
[   20.965381] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[   20.969078] acpiphp: Slot [32] registered
[   20.969978] acpiphp: Slot [33] registered
[   20.970460] acpiphp: Slot [34] registered
[   20.970882] acpiphp: Slot [35] registered
[   20.971300] acpiphp: Slot [36] registered
[   20.971954] acpiphp: Slot [37] registered
[   20.972382] acpiphp: Slot [38] registered
[   20.972804] acpiphp: Slot [39] registered
[   20.973503] acpiphp: Slot [40] registered
[   20.973927] acpiphp: Slot [41] registered
[   20.974430] acpiphp: Slot [42] registered
[   20.974915] acpiphp: Slot [43] registered
[   20.975389] acpiphp: Slot [44] registered
[   20.975811] acpiphp: Slot [45] registered
[   20.976243] acpiphp: Slot [46] registered
[   20.976987] acpiphp: Slot [47] registered
[   20.977758] acpiphp: Slot [48] registered
[   20.978182] acpiphp: Slot [49] registered
[   20.979754] acpiphp: Slot [50] registered
[   20.980203] acpiphp: Slot [51] registered
[   20.980628] acpiphp: Slot [52] registered
[   20.981493] acpiphp: Slot [53] registered
[   20.981585] acpiphp: Slot [54] registered
[   20.981630] acpiphp: Slot [55] registered
[   20.981667] acpiphp: Slot [56] registered
[   20.981702] acpiphp: Slot [57] registered
[   20.981731] acpiphp: Slot [58] registered
[   20.981762] acpiphp: Slot [59] registered
[   20.981791] acpiphp: Slot [60] registered
[   20.981825] acpiphp: Slot [61] registered
[   20.981854] acpiphp: Slot [62] registered
[   20.981883] acpiphp: Slot [63] registered
[  156.790606] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[ 1294.136983] sched: RT throttling activated
[ 1346.613748] psmouse serio1: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1347.173543] psmouse serio1: resync failed, issuing reconnect request
[ 1347.177249] psmouse serio1: hgpk: ID: 10 00 64
[ 1423.600707] psmouse serio1: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1424.316730] psmouse serio1: resync failed, issuing reconnect request
[ 1424.318542] psmouse serio1: hgpk: ID: 10 00 64
[ 1433.994450] psmouse serio1: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1434.648700] psmouse serio1: resync failed, issuing reconnect request
[ 1435.028411] psmouse serio1: hgpk: ID: 10 00 64

6 ) Network configuration
 Code: $ sudo lshw -C network 

  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 10
       serial: 00:0c:29:2f:67:46
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.35 ip=192.168.29.130 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes
       resources: irq:19 ioport:2000(size=128) memory:d8400000-d840ffff

7 ) Scan for networks:
 Code: $ iwlist scan (hint) the same as in (3)

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.


 Code: $ iwlist scan wlan0 
8 ) Ubuntu Version: 
 Code: $ lsb_release -d 
Description:    Ubuntu 10.04.3 LTS
9 ) Kernel/architecture (including 32 vs. 64 bit): 
 Code: $ uname -mr 
3.2.6 i686
10 ) Restarting the network:
 Code: $ sudo /etc/init.d/networking restart Add this information to the post, even is the output is and error, and more if you have, and describe your issue.b

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 1136
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:0c:29:2f:67:46
Sending on   LPF/eth1/00:0c:29:2f:67:46
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.29.254 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:0c:29:2f:67:46
Sending on   LPF/eth1/00:0c:29:2f:67:46
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.29.130 from 192.168.29.254
DHCPREQUEST of 192.168.29.130 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.29.130 from 192.168.29.254
bound to 192.168.29.130 -- renewal in 685 seconds.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]

---

### Post by chili555 on 2012-09-10
Wireless works a little differently in virtual machines. For example, see: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=760](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=760)

---

### Post by nepalihippo on 2012-09-11
thank you chilli for the link and advise but following the link doesn't provide any solution to set the dlink dwa-125 driver in my Vmware workstation 8 . 

Can anybody guide me to setup the driver so that the vmware backtrack 5 can take the dlink wireless adapter :(

---

### Post by chili555 on 2012-09-11
> **nepalihippo said:**
> Can anybody guide me to setup the driver so that the vmware backtrack 5 can take the dlink wireless adapter :(Perhaps I didn't make it clear. The answer is *NO*. Please see: [http://pubs.vmware.com/ws8/wwhelp/wwhimpl/js/html/wwhelp.htm#href=using_ws/GUID-BAFA66C3-81F0-4FCA-84C4-D9F7D258A60A.html#1_14_9_1](http://pubs.vmware.com/ws8/wwhelp/wwhimpl/js/html/wwhelp.htm#href=using_ws/GUID-BAFA66C3-81F0-4FCA-84C4-D9F7D258A60A.html#1_14_9_1)> When you install Workstation on a Windows or Linux host system, a bridged network (VMnet0) is set up for you. Bridged networking connects a virtual machine to a network by *using the network adapter on the host system.* If the host system is on a network, bridged networking is often the easiest way to give the virtual machine access to that network.
With bridged networking, the virtual network adapter in the virtual machine connects to a physical network adapter in the host system. The host network adapter enables the virtual machine to connect to the LAN that the host system uses. Bridged networking works with both wired and wireless host network adapters.
Bridged networking configures the virtual machine as a unique identity on the network, separate from and unrelated to the host system. The virtual machine is a full participant in the network. It has access to other machines on the network, and other machines on the network can contact it as if it were a physical computer on the network.

---

