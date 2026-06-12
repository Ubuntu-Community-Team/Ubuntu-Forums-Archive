---
title: "Fusion HDTV 3 Gold-Q"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by p110011 on 2007-01-15
First time Linux user-One week using edgy 6.10
Had several devices that were not working and I did a bunch of reading here to get most of my pc working. Wifi, audio, video, all had problems, so I may have gotten something twisted up.
The Device manager shows my TV card as a FusionHDTV Gold-T and I see cx8800 driver.
id is 34816 (0x8800) 
I tyied to get Mythtv to work but I can't make heads or tail out of it. 
When I go Applications/sound & video alls I get is Mythtv front end, and that does not connect.
Does Myth alow users to log in and watch your cards channels?
I just want to watch TV on my monitor like I do in Windows.

Here is my lspci
lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0d.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0d.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:0d.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:13.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:13.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:13.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

---

### Post by Erlander on 2007-01-16
Try installing Kaffiene.  Its much easier to get going than Mythtv.

Rob

---

### Post by p110011 on 2007-01-16
> **Erlander said:**
> Try installing Kaffiene.  Its much easier to get going than Mythtv.

Rob

I've tried that one too, nothing happens when I scan channels.
One other thing, I have amsn and if I go to my web cam settings it shows the fusion card as a web cam?](*,)

---

### Post by Erlander on 2007-01-17
Sorry I can't help more than that.  I'm new too and my tuner is a Dvico USB2 not pci and to make matters worse I'm in DVB land so there is even a different TV standard here!!!!!

It would be worth looking at dmesg to see what happens at boot up.  The lines to look at I think are the Conexant CX23880 as I think that is the chip in your tuner.

In terminal:  sudo dmesg

You'll get a fairly long reply to the command but look for the Conexant CX23880 entries.

Good luck.

Rob

---

### Post by p110011 on 2007-01-17
> **Erlander said:**
> Sorry I can't help more than that.  I'm new too and my tuner is a Dvico USB2 not pci and to make matters worse I'm in DVB land so there is even a different TV standard here!!!!!

It would be worth looking at dmesg to see what happens at boot up.  The lines to look at I think are the Conexant CX23880 as I think that is the chip in your tuner.

In terminal:  sudo dmesg

You'll get a fairly long reply to the command but look for the Conexant CX23880 entries.

Good luck.

Rob

Thanks Mate (hope I got that right):) 
I'll check out dmesg

---

### Post by p110011 on 2007-01-18
OK here is what I get:
p110011@gilles-desktop:~$ sudo dmesg
Password:
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000002fff0000 - 000000002fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000002fff8000 - 0000000030000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 767MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 196592
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 192496 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2c0
[17179569.184000] ACPI: RSDT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x2fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x2fff0030
[17179569.184000] ACPI: DSDT (v001    SiS      735 0x00000100 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0160c000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1792.733 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.944000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.948000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.984000] Memory: 769640k/786368k available (1910k kernel code, 16048k reserved, 1069k data, 308k init, 0k highmem)
[17179569.984000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.064000] Calibrating delay using timer specific routine.. 3587.05 BogoMIPS (lpj=7174116)
[17179570.064000] Security Framework v1.0.0 initialized
[17179570.064000] SELinux:  Disabled at boot.
[17179570.064000] Mount-cache hash table entries: 512
[17179570.064000] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179570.064000] CPU: After vendor identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179570.064000] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[17179570.064000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.064000] CPU: L2 Cache: 256K (64 bytes/line)
[17179570.064000] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[17179570.064000] Checking 'hlt' instruction... OK.
[17179570.080000] SMP alternatives: switching to UP code
[17179570.080000] Freeing SMP alternatives: 16k freed
[17179570.080000] checking if image is initramfs... it is
[17179570.612000] Freeing initrd memory: 5322k freed
[17179570.612000] ACPI: Core revision 20060707
[17179570.612000] ACPI: Looking for DSDT ... not found!
[17179570.612000] ACPI: setting ELCR to 0200 (from 1c20)
[17179570.616000] CPU0: AMD Athlon(tm) XP 2200+ stepping 01
[17179570.616000] SMP motherboard not detected.
[17179570.616000] Local APIC not detected. Using dummy APIC emulation.
[17179570.616000] Brought up 1 CPUs
[17179570.616000] migration_cost=0
[17179570.616000] NET: Registered protocol family 16
[17179570.616000] EISA bus registered
[17179570.616000] ACPI: bus type pci registered
[17179570.620000] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[17179570.620000] PCI: Using configuration type 1
[17179570.620000] Setting up standard PCI resources
[17179570.624000] ACPI: Interpreter enabled
[17179570.624000] ACPI: Using PIC for interrupt routing
[17179570.624000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.624000] PCI: Probing PCI hardware (bus 00)
[17179570.628000] Uncovering SIS18 that hid as a SIS503 (compatible=1)
[17179570.628000] Enabling SiS 96x SMBus.
[17179570.628000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179570.628000] Boot video device is 0000:01:00.0
[17179570.628000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.632000] ACPI: Power Resource [URP1] (off)
[17179570.632000] ACPI: Power Resource [URP2] (off)
[17179570.632000] ACPI: Power Resource [FDDP] (off)
[17179570.632000] ACPI: Power Resource [LPTP] (off)
[17179570.632000] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[17179570.632000] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[17179570.632000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 12 14 15)
[17179570.636000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *12 14 15)
[17179570.636000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[17179570.636000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[17179570.636000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *10 12 14 15)
[17179570.636000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 12 14 15)
[17179570.636000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.636000] pnp: PnP ACPI init
[17179570.640000] pnp: PnP ACPI: found 10 devices
[17179570.640000] PnPBIOS: Disabled by ACPI PNP
[17179570.640000] PCI: Using ACPI for IRQ routing
[17179570.640000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.652000] PCI: Bridge: 0000:00:01.0
[17179570.652000]   IO window: a000-afff
[17179570.652000]   MEM window: c9e00000-c9efffff
[17179570.652000]   PREFETCH window: a9c00000-c9cfffff
[17179570.652000] NET: Registered protocol family 2
[17179570.692000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.692000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.696000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.696000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.696000] TCP reno registered
[17179570.696000] audit: initializing netlink socket (disabled)
[17179570.696000] audit(1169138547.696:1): initialized
[17179570.696000] VFS: Disk quotas dquot_6.5.1
[17179570.696000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.696000] Initializing Cryptographic API
[17179570.696000] io scheduler noop registered
[17179570.696000] io scheduler anticipatory registered
[17179570.696000] io scheduler deadline registered
[17179570.696000] io scheduler cfq registered (default)
[17179570.696000] isapnp: Scanning for PnP cards...
[17179571.052000] isapnp: No Plug & Play device found
[17179571.080000] Real Time Clock Driver v1.12ac
[17179571.080000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.080000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.080000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.080000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.080000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.080000] mice: PS/2 mouse device common for all mice
[17179571.084000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.084000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.084000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.084000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179571.084000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.088000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.088000] EISA: Probing bus 0 at eisa.0
[17179571.088000] EISA: Detected 0 cards.
[17179571.088000] TCP bic registered
[17179571.088000] NET: Registered protocol family 1
[17179571.088000] NET: Registered protocol family 8
[17179571.088000] NET: Registered protocol family 20
[17179571.088000] Using IPI No-Shortcut mode
[17179571.088000] ACPI: (supports S0 S1 S4 S5)
[17179571.088000] Freeing unused kernel memory: 308k freed
[17179571.108000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.228000] Capability LSM initialized
[17179572.904000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179572.904000] SIS5513: chipset revision 208
[17179572.904000] SIS5513: not 100% native mode: will probe irqs later
[17179572.904000] SIS5513: SiS735 ATA 100 (2nd gen) controller
[17179572.904000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[17179572.904000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[17179572.904000] Probing IDE interface ide0...
[17179573.192000] hda: WDC WD400BB-75DKA0, ATA DISK drive
[17179573.864000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.888000] Probing IDE interface ide1...
[17179574.624000] hdc: PLEXTOR DVDR PX-716A, ATAPI CD/DVD-ROM drive
[17179575.408000] hdd: OEM CD-ROM F564E, ATAPI CD/DVD-ROM drive
[17179575.464000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.472000] hda: max request size: 512KiB
[17179575.492000] hda: 78125000 sectors (40000 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.492000] hda: cache flushes supported
[17179575.492000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179575.580000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(33)
[17179575.580000] Uniform CD-ROM driver Revision: 3.20
[17179575.584000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache, UDMA(33)
[17179576.048000] usbcore: registered new driver usbfs
[17179576.052000] usbcore: registered new driver hub
[17179576.052000] USB Universal Host Controller Interface driver v3.0
[17179576.052000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179576.052000] PCI: setting IRQ 11 as level-triggered
[17179576.052000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.052000] uhci_hcd 0000:00:13.0: UHCI Host Controller
[17179576.052000] uhci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179576.052000] uhci_hcd 0000:00:13.0: irq 11, io base 0x0000cc00
[17179576.052000] usb usb1: configuration #1 chosen from 1 choice
[17179576.052000] hub 1-0:1.0: USB hub found
[17179576.052000] hub 1-0:1.0: 2 ports detected
[17179576.068000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.156000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179576.156000] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179576.156000] uhci_hcd 0000:00:13.1: UHCI Host Controller
[17179576.156000] uhci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179576.156000] uhci_hcd 0000:00:13.1: irq 11, io base 0x0000d000
[17179576.156000] usb usb2: configuration #1 chosen from 1 choice
[17179576.156000] hub 2-0:1.0: USB hub found
[17179576.156000] hub 2-0:1.0: 2 ports detected
[17179576.268000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[17179576.268000] PCI: setting IRQ 12 as level-triggered
[17179576.268000] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179576.268000] ohci_hcd 0000:00:02.2: OHCI Host Controller
[17179576.268000] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179576.268000] ohci_hcd 0000:00:02.2: irq 12, io mem 0xcfffe000
[17179576.324000] usb usb3: configuration #1 chosen from 1 choice
[17179576.324000] hub 3-0:1.0: USB hub found
[17179576.324000] hub 3-0:1.0: 3 ports detected
[17179576.396000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179576.428000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[17179576.428000] PCI: setting IRQ 5 as level-triggered
[17179576.428000] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[17179576.428000] ohci_hcd 0000:00:02.3: OHCI Host Controller
[17179576.428000] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 4
[17179576.428000] ohci_hcd 0000:00:02.3: irq 5, io mem 0xcffff000
[17179576.484000] usb usb4: configuration #1 chosen from 1 choice
[17179576.484000] hub 4-0:1.0: USB hub found
[17179576.484000] hub 4-0:1.0: 3 ports detected
[17179576.576000] usb 1-1: configuration #1 chosen from 1 choice
[17179576.588000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179576.588000] PCI: setting IRQ 10 as level-triggered
[17179576.588000] ACPI: PCI Interrupt 0000:00:13.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179576.588000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179576.588000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 5
[17179576.588000] ehci_hcd 0000:00:13.2: irq 10, io mem 0xcfffcf00
[17179576.588000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[17179576.588000] usb usb5: configuration #1 chosen from 1 choice
[17179576.588000] hub 5-0:1.0: USB hub found
[17179576.588000] hub 5-0:1.0: 4 ports detected
[17179576.740000] usb 1-1: USB disconnect, address 2
[17179576.820000] Attempting manual resume
[17179576.864000] kjournald starting.  Commit interval 5 seconds
[17179576.864000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.916000] usb 5-4: new high speed USB device using ehci_hcd and address 5
[17179578.232000] usb 5-4: configuration #1 chosen from 1 choice
[17179578.472000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179578.660000] usb 1-1: configuration #1 chosen from 1 choice
[17179578.904000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[17179579.056000] usb 1-2: configuration #1 chosen from 1 choice
[17179579.060000] hub 1-2:1.0: USB hub found
[17179579.060000] hub 1-2:1.0: 4 ports detected
[17179579.412000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179579.588000] usb 2-1: configuration #1 chosen from 1 choice
[17179579.796000] usb 1-2.3: new low speed USB device using uhci_hcd and address 5
[17179579.936000] usb 1-2.3: configuration #1 chosen from 1 choice
[17179587.816000] Linux video capture interface: v1.00
[17179587.908000] sis900.c: v1.08.09 Sep. 19 2005
[17179587.908000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[17179587.908000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[17179587.912000] 0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
[17179587.920000] 0000:00:03.0: Using transceiver found at address 1 as default
[17179587.920000] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 10, 00:0a:e6:78:89:5c.
[17179588.052000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.112000] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[17179588.156000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.160000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.392000] cx2388x v4l2 driver version 0.0.5 loaded
[17179588.392000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179588.392000] CORE cx88[0]: subsystem: 18ac:d820, board: DViCO FusionHDTV 3 Gold-T [card=28,autodetected]
[17179588.392000] TV tuner 60 at 0x1fe, Radio tuner -1 at 0x1fe
[17179588.604000] cx88[0]/0: found at 0000:00:0d.0, rev: 5, irq: 10, latency: 64, mmio: 0xcc000000
[17179589.024000] eth1: Media Link Off
[17179589.168000] quickcam [46.044421]: ----------LOADING QUICKCAM MODULE------------
[17179589.168000] quickcam [46.044433]: struct quickcam size: 4148
[17179589.168000] quickcam: QuickCam USB camera found (driver version QuickCam Messenger/Communicate USB 1.5 $Date: 2006/11/05 00:00:00 $)
[17179589.168000] quickcam: Kernel:2.6.17-10-generic bus:1 class:FF subclass:FF vendor:046D product:08F0
[17179589.168000] quickcam [46.044523]: poisoning qc in qc_usb_init
[17179589.172000] quickcam [46.047855]: E00A contains 08F0
[17179589.172000] quickcam: Sensor VV6450 detected
[17179589.172000] input: Quickcam snapshot button as /class/input/input1
[17179589.172000] quickcam [46.049162]: Quickcam snapshot button registered on usb-0000:00:13.0-1/input0
[17179589.172000] quickcam: Registered device: /dev/video0
[17179589.172000] usbcore: registered new driver quickcam
[17179589.348000] Floppy drive(s): fd0 is 1.44M
[17179589.368000] FDC 0 is a post-1991 82077
[17179589.420000] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[17179589.420000] tuner 0-0061: type set to 60 (Thomson DTT 761X (ATSC/NTSC))
[17179589.488000] tda9887 0-0043: chip found @ 0x86 (cx88[0])
[17179589.496000] cx88[0]/0: registered device video1 [v4l2]
[17179589.496000] cx88[0]/0: registered device vbi0
[17179589.540000] agpgart: Detected SiS 735 chipset
[17179589.552000] agpgart: AGP aperture is 128M @ 0xd0000000
[17179589.552000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[17179589.624000] usbcore: registered new driver hiddev
[17179589.636000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179589.636000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.1-1
[17179589.640000] input: PC Speaker as /class/input/input3
[17179589.660000] hiddev96: USB HID v1.10 Device [DVICO DVICO USB HID Remocon V1.00] on usb-0000:00:13.0-2.3
[17179589.660000] usbcore: registered new driver usbhid
[17179589.660000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.804000] parport: PnPBIOS parport detected.
[17179589.804000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179589.920000] cx2388x dvb driver version 0.0.5 loaded
[17179589.920000] ACPI: PCI Interrupt 0000:00:0d.2[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179589.920000] cx88[0]/2: found at 0000:00:0d.2, rev: 5, irq: 10, latency: 64, mmio: 0xce000000
[17179589.920000] cx88[0]/2: cx2388x based dvb card
[17179590.228000] DVB: registering new adapter (cx88[0]).
[17179590.228000] DVB: registering frontend 0 (LG Electronics LGDT3302 VSB/QAM Frontend)...
[17179590.296000] cx2388x blackbird driver version 0.0.5 loaded
[17179590.348000] rtusb init ====>
[17179590.348000] idVendor = 0x13b1, idProduct = 0x20 
[17179590.348000] usbcore: registered new driver rt73
[17179590.444000] rt73 driver version - 1.0.3.6
[17179590.444000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179590.472000] NET: Registered protocol family 17
[17179590.548000] usbcore: registered new driver snd-usb-audio
[17179590.568000] cx2388x alsa driver version 0.0.5 loaded
[17179590.584000] ts: Compaq touchscreen protocol output
[17179590.760000] intel8x0_measure_ac97_clock: measured 55812 usecs
[17179590.760000] intel8x0: clocking to 48000
[17179590.760000] ACPI: PCI Interrupt 0000:00:0d.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179590.880000] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[17179591.032000] lp0: using parport0 (interrupt-driven).
[17179591.088000] Adding 385520k swap on /dev/disk/by-uuid/8ed9b415-61c5-4396-a87e-8d7da1feb6d8.  Priority:-1 extents:1 across:385520k
[17179591.176000] EXT3 FS on hda3, internal journal
[17179591.356000] rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179596.296000] ACPI: Power Button (FF) [PWRF]
[17179596.296000] ACPI: Sleep Button (CM) [SLPB]
[17179596.456000] ibm_acpi: ec object not found
[17179596.492000] pcc_acpi: loading...
[17179599.636000] NET: Registered protocol family 10
[17179599.636000] lo: Disabled Privacy Extensions
[17179599.640000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179599.640000] IPv6 over IPv4 tunneling driver
[17179599.732000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179599.740000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[17179599.740000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179600.056000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179602.556000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179602.556000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179602.556000] [fglrx] AGP detected, AgpState   = 0x1f000207 (hardware caps of chipset)
[17179602.556000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179602.556000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179602.556000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179602.556000] [fglrx] AGP enabled,  AgpCommand = 0x1f000304 (selected caps)
[17179602.576000] [fglrx] total      GART = 134217728
[17179602.576000] [fglrx] free       GART = 118222848
[17179602.576000] [fglrx] max single GART = 118222848
[17179602.576000] [fglrx] total      LFB  = 126791680
[17179602.576000] [fglrx] free       LFB  = 116211712
[17179602.576000] [fglrx] max single LFB  = 116211712
[17179602.576000] [fglrx] total      Inv  = 0
[17179602.576000] [fglrx] free       Inv  = 0
[17179602.576000] [fglrx] max single Inv  = 0
[17179602.576000] [fglrx] total      TIM  = 0
[17179606.548000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179606.548000] apm: overridden by ACPI.
[17179610.368000] rausb0: no IPv6 routers present

---

