---
title: "Video jibberish"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by CuBone on 2007-03-19
I've installed a fresh install of ubuntu 6.10 on my htpc. I then installed mythTV, mplayer and vlc player. Everything seems to work like it's supposed to, I even got the Microsoft MCE remote to work with lirc. But there is something wrong with my videoplayback. When I watch a videofile I get [this]("http://www.wallgren.it/mplayer-screen.jpg") image after a while. Sometimes after a few minutes, sometimes it works fo 20-30 minutes. The sound keeps playing and the same thing happens in both mplayer and vlc. Anyone have the faintest idea where I should start looking for errors? 

I redirected the error output from mplayer with 2> to a file and this is the errors I get after playing a video file. 

```
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.

```

---

### Post by CuBone on 2007-03-19
Woops, double post.

---

### Post by majoridiot on 2007-03-20
if this is happening with mythtv while watching livetv, please post the appropriate portions of your
frontend and backend logs- they can be found in /var/log/mythv/

---

### Post by CuBone on 2007-03-21
This happens even if I start the videoplayers without running mythtv. But will post the loggs.

---

### Post by majoridiot on 2007-03-21
> **CuBone said:**
> This happens even if I start the videoplayers without running mythtv. But will post the loggs.

then a good place to start is to start by telling us what video capture card you have and to post
the result of this:

```
# dmesg 
```

---

### Post by CuBone on 2007-03-21
I dont have a video capture card. Had a pvr-150 installed but I removed it to see if that was the problem. 

The problem is when I play moviefiles (like *.avi) from my hard drive.

---

### Post by CuBone on 2007-03-21
dmesg:

```
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f4da0
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 VIAK8                                 ) @ 0x000f6770
[17179569.184000] ACPI: RSDT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff7980
[17179569.184000] ACPI: DSDT (v001 VIAK8  AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1800.395 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.808000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.808000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.816000] Memory: 510048k/524224k available (1911k kernel code, 13608k reserved, 1073k data, 308k init, 0k highmem)
[17179569.816000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.896000] Calibrating delay using timer specific routine.. 3605.69 BogoMIPS (lpj=7211397)
[17179569.896000] Security Framework v1.0.0 initialized
[17179569.896000] SELinux:  Disabled at boot.
[17179569.896000] Mount-cache hash table entries: 512
[17179569.896000] CPU: After generic identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.896000] CPU: After vendor identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.896000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.896000] CPU: L2 Cache: 256K (64 bytes/line)
[17179569.896000] CPU: After all inits, caps: 078bfbff c1d3fbff 00000000 00000410 00000000 00000000 00000000
[17179569.896000] Checking 'hlt' instruction... OK.
[17179569.912000] SMP alternatives: switching to UP code
[17179569.912000] Freeing SMP alternatives: 16k freed
[17179569.912000] checking if image is initramfs... it is
[17179570.408000] Freeing initrd memory: 5326k freed
[17179570.408000] ACPI: Core revision 20060707
[17179570.412000] ACPI: Looking for DSDT ... not found!
[17179570.416000] CPU0: AMD Sempron(tm) Processor 3100+ stepping 00
[17179570.416000] Total of 1 processors activated (3605.69 BogoMIPS).
[17179570.416000] ENABLING IO-APIC IRQs
[17179570.416000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[17179570.560000] Brought up 1 CPUs
[17179570.560000] migration_cost=0
[17179570.560000] NET: Registered protocol family 16
[17179570.560000] EISA bus registered
[17179570.560000] ACPI: bus type pci registered
[17179570.564000] PCI: PCI BIOS revision 2.10 entry at 0xfa9a0, last bus=1
[17179570.564000] PCI: Using configuration type 1
[17179570.564000] Setting up standard PCI resources
[17179570.572000] ACPI: Interpreter enabled
[17179570.572000] ACPI: Using IOAPIC for interrupt routing
[17179570.572000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.572000] PCI: Probing PCI hardware (bus 00)
[17179570.576000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.0
[17179570.576000] PCI: Quirk-MSI-K8T Soundcard On
[17179570.576000] PCI: MSI-K8T soundcard on
[17179570.576000] Boot video device is 0000:01:00.0
[17179570.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.620000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[17179570.620000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[17179570.620000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[17179570.620000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.620000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.620000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.620000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.620000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.624000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179570.624000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[17179570.624000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[17179570.624000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[17179570.624000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.624000] pnp: PnP ACPI init
[17179570.628000] pnp: PnP ACPI: found 13 devices
[17179570.628000] PnPBIOS: Disabled by ACPI PNP
[17179570.628000] PCI: Using ACPI for IRQ routing
[17179570.628000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.664000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179570.664000] pnp: 00:02: ioport range 0x40f0-0x40ff could not be reserved
[17179570.664000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[17179570.664000] PCI: Bridge: 0000:00:01.0
[17179570.664000]   IO window: disabled.
[17179570.664000]   MEM window: ec000000-edffffff
[17179570.664000]   PREFETCH window: e0000000-e7ffffff
[17179570.664000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.664000] NET: Registered protocol family 2
[17179570.696000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.696000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.696000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.696000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.696000] TCP reno registered
[17179570.696000] audit: initializing netlink socket (disabled)
[17179570.696000] audit(1174493070.696:1): initialized
[17179570.696000] VFS: Disk quotas dquot_6.5.1
[17179570.696000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.696000] Initializing Cryptographic API
[17179570.696000] io scheduler noop registered
[17179570.696000] io scheduler anticipatory registered
[17179570.696000] io scheduler deadline registered
[17179570.696000] io scheduler cfq registered (default)
[17179570.696000] isapnp: Scanning for PnP cards...
[17179571.052000] isapnp: No Plug & Play device found
[17179571.068000] Real Time Clock Driver v1.12ac
[17179571.068000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.068000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.068000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.068000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.068000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.068000] mice: PS/2 mouse device common for all mice
[17179571.072000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.072000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.072000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.072000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179571.072000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.076000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.076000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.076000] EISA: Probing bus 0 at eisa.0
[17179571.076000] Cannot allocate resource for EISA slot 4
[17179571.076000] Cannot allocate resource for EISA slot 5
[17179571.076000] EISA: Detected 0 cards.
[17179571.076000] TCP bic registered
[17179571.076000] NET: Registered protocol family 1
[17179571.076000] NET: Registered protocol family 8
[17179571.076000] NET: Registered protocol family 20
[17179571.076000] Using IPI No-Shortcut mode
[17179571.076000] ACPI: (supports S0 S1 S4 S5)
[17179571.076000] Freeing unused kernel memory: 308k freed
[17179571.160000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.280000] Capability LSM initialized
[17179572.712000] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[17179572.712000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179572.712000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179572.712000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 169
[17179572.712000] PCI: Via IRQ fixup for 0000:00:0f.0, from 255 to 9
[17179572.712000] VP_IDE: chipset revision 6
[17179572.712000] VP_IDE: not 100% native mode: will probe irqs later
[17179572.712000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[17179572.712000]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
[17179572.712000]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:pio
[17179572.712000] Probing IDE interface ide0...
[17179573.140000] hda: Maxtor 6Y080L0, ATA DISK drive
[17179573.820000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.824000] Probing IDE interface ide1...
[17179574.692000] hdc: PHILIPS DVD+/-RW SDVD8412, ATAPI CD/DVD-ROM drive
[17179575.368000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.372000] hda: max request size: 128KiB
[17179575.380000] hda: Host Protected Area detected.
[17179575.380000] 	current capacity is 160084415 sectors (81963 MB)
[17179575.380000] 	native  capacity is 160086528 sectors (81964 MB)
[17179575.400000] hda: Host Protected Area disabled.
[17179575.400000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179575.400000] hda: cache flushes supported
[17179575.400000]  hda: hda1 hda2 hda3 hda4
[17179575.440000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.440000] Uniform CD-ROM driver Revision: 3.20
[17179575.684000] usbcore: registered new driver usbfs
[17179575.684000] usbcore: registered new driver hub
[17179575.684000] USB Universal Host Controller Interface driver v3.0
[17179575.688000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[17179575.688000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179575.688000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.688000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 1
[17179575.688000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179575.688000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179575.688000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000d400
[17179575.688000] usb usb1: configuration #1 chosen from 1 choice
[17179575.688000] hub 1-0:1.0: USB hub found
[17179575.688000] hub 1-0:1.0: 2 ports detected
[17179575.792000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.792000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 1
[17179575.792000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179575.796000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179575.796000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000d800
[17179575.796000] usb usb2: configuration #1 chosen from 1 choice
[17179575.796000] hub 2-0:1.0: USB hub found
[17179575.796000] hub 2-0:1.0: 2 ports detected
[17179575.900000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.900000] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 1
[17179575.900000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179575.900000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179575.900000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000dc00
[17179575.904000] usb usb3: configuration #1 chosen from 1 choice
[17179575.904000] hub 3-0:1.0: USB hub found
[17179575.904000] hub 3-0:1.0: 2 ports detected
[17179576.008000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179576.008000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 1
[17179576.008000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179576.008000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179576.008000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000e000
[17179576.012000] usb usb4: configuration #1 chosen from 1 choice
[17179576.012000] hub 4-0:1.0: USB hub found
[17179576.012000] hub 4-0:1.0: 2 ports detected
[17179576.124000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179576.124000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 1
[17179576.124000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179576.124000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179576.124000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xee000000
[17179576.124000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.124000] usb usb5: configuration #1 chosen from 1 choice
[17179576.124000] hub 5-0:1.0: USB hub found
[17179576.124000] hub 5-0:1.0: 8 ports detected
[17179576.296000] Attempting manual resume
[17179576.312000] kjournald starting.  Commit interval 5 seconds
[17179576.312000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.424000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[17179577.600000] usb 4-1: configuration #1 chosen from 1 choice
[17179577.844000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[17179578.024000] usb 4-2: configuration #1 chosen from 1 choice
[17179584.372000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179584.376000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.000000] parport: PnPBIOS parport detected.
[17179585.000000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179585.008000] FDC 0 is a post-1991 82077
[17179585.012000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.032000] agpgart: Detected AGP bridge 0
[17179585.036000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179585.072000] 8139too Fast Ethernet driver 0.9.27
[17179585.072000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179585.072000] eth0: RealTek RTL8139 at 0xe08ec000, 00:0f:ea:3a:b8:9a, IRQ 185
[17179585.072000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179585.076000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179585.272000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179585.448000] input: PC Speaker as /class/input/input1
[17179585.608000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179585.608000] lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179585.608000] 
[17179585.608000] lirc_mceusb2: USB remote driver for LIRC v0.22
[17179585.608000] lirc_mceusb2: Martin Blatter <martin_a_blatter@yahoo.com>
[17179585.776000] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[17179585.776000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179585.776000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179585.776000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 193
[17179585.776000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 1
[17179585.776000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179585.948000] lirc_dev: lirc_register_plugin: sample_rate: 0
[17179585.952000] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb4:2
[17179585.952000] usbcore: registered new driver hiddev
[17179585.980000] nvidia: module license 'NVIDIA' taints kernel.
[17179585.984000] input: Logitech USB Receiver as /class/input/input2
[17179585.984000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.3-2
[17179585.984000] usbcore: registered new driver usbhid
[17179585.984000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179585.984000] usbcore: registered new driver lirc_mceusb2
[17179586.272000] ts: Compaq touchscreen protocol output
[17179586.308000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[17179586.308000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[17179586.412000] NET: Registered protocol family 17
[17179586.636000] lp0: using parport0 (interrupt-driven).
[17179586.664000] Adding 2096472k swap on /dev/disk/by-uuid/fb828a4f-19b6-4fcd-9f1c-ef2cb9a8a37f.  Priority:-1 extents:1 across:2096472k
[17179586.748000] EXT3 FS on hda1, internal journal
[17179586.968000] kjournald starting.  Commit interval 5 seconds
[17179586.976000] EXT3 FS on hda4, internal journal
[17179586.976000] EXT3-fs: mounted filesystem with ordered data mode.
[17179587.016000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179587.016000] SGI XFS Quota Management subsystem
[17179587.044000] XFS mounting filesystem hda2
[17179587.136000] Ending clean XFS mount for filesystem: hda2
[17179590.356000] CIFS: Unknown mount option cubone
[17179590.424000] NET: Registered protocol family 10
[17179590.424000] lo: Disabled Privacy Extensions
[17179590.424000] IPv6 over IPv4 tunneling driver
[17179593.772000] ACPI: Power Button (FF) [PWRF]
[17179593.772000] ACPI: Power Button (CM) [PWRB]
[17179593.868000] ibm_acpi: ec object not found
[17179593.896000] pcc_acpi: loading...
[17179594.200000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179594.200000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6 (1400 mV)
[17179594.200000] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179594.200000] cpu_init done, current fid 0xa, vid 0x6
[17179596.300000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179596.300000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179596.300000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179601.208000] eth0: no IPv6 routers present
[17179601.248000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179601.248000] apm: overridden by ACPI.
[17179607.856000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179608.312000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179608.320000] NFSD: starting 90-second grace period
[17179618.808000] Bluetooth: Core ver 2.8
[17179618.808000] NET: Registered protocol family 31
[17179618.808000] Bluetooth: HCI device and connection manager initialized
[17179618.808000] Bluetooth: HCI socket layer initialized
[17179618.900000] Bluetooth: L2CAP ver 2.8
[17179618.900000] Bluetooth: L2CAP socket layer initialized
[17179618.904000] Bluetooth: RFCOMM socket layer initialized
[17179618.904000] Bluetooth: RFCOMM TTY layer initialized
[17179618.904000] Bluetooth: RFCOMM ver 1.7
[17181208.856000] NVRM: Xid (0001:00): 6, PE0000 0104 00000000 0000fdf8 ff046104 00000000
[17181208.860000] NVRM: Xid (0001:00): 30,  L1 -> L0
[17181473.636000] NVRM: Xid (0001:00): 6, PE0000 0400 00ffffff 0000f690 ea086400 00ffffff
[17181545.652000] NVRM: Xid (0001:00): 6, PE0000 0400 00ffffff 0000fb2c ca086400 00ffffff
[17181592.620000] NVRM: Xid (0001:00): 6, PE0000 0400 00ffffff 0000fb2c ca086400 00ffffff
[17182662.300000] NVRM: Xid (0001:00): 6, PE0000 0104 00000000 00000030 fc046104 00000000
[17189722.124000] NVRM: Xid (0001:00): 6, PE0000 0400 ff81756a 0000fde0 ff4c6400 cdcdcdcd
[17189724.180000] NVRM: Xid (0001:00): 6, PE0000 0400 ff81756a 0000fca0 f0406400 4a9dc326
[17189724.200000] NVRM: Xid (0001:00): 13, 0000 01014200 00000062 00000300 00406400 00000002

```

---

### Post by majoridiot on 2007-03-21
could be a codec problem then.  install **Automatix** and then use it to install all of the availavle
and "restricted" multimedia codecs to see if that helps.

you can install automatix from synaptic package manager- make sure you have all of your repositories
enabled and updated and then install it.

it will then be on your menu under Applications-->System tools

---

### Post by CuBone on 2007-03-22
It seems that I can play videos just fine if I start the player with sudo. Therefor I think there is some permissionproblem somewhere, but I haven't the faintest Idea where to look for it.

---

### Post by majoridiot on 2007-03-22
> **CuBone said:**
> It seems that I can play videos just fine if I start the player with sudo. Therefor I think there is some permissionproblem somewhere, but I haven't the faintest Idea where to look for it.

is this after installing the codec packs?

download (or move) a small video to your desktop.  then:

```
# sudo chown username:username ~/Desktop/videofilename
# chmod +r videofilename
```

wnere username is your main user and videofilename is the video file to play.  then try playing the
file with your various players, first without sudo and then with.

---

### Post by CuBone on 2007-03-22
> **majoridiot said:**
> iwnere username is your main user and videofilename is the video file to play.  then try playing the
file with your various players, first without sudo and then with.
Yes, I installled all the codecs. 
I can play the files for a few minutes up to 25-30 minutes before the error occurs and I allready own the files I try to play with full rw permissions.

---

### Post by majoridiot on 2007-03-22
> **CuBone said:**
> Yes, I installled all the codecs. 
I can play the files for a few minutes up to 25-30 minutes before the error occurs...

hm.  odd.

does the error occur when you run the player(s) as sudo, too- or just as your regular user?

also, is there any chance a screensaver is interfering?  you might try disabling any that might be
active, and also check your power settings to see if anything there might be interfering.

---

### Post by CuBone on 2007-03-22
Haven't had any interruptions while running the player as sudo. I just turned of screensaver and the powersavingstuff that turns the screen off. Will let you know if it has any effect

---

