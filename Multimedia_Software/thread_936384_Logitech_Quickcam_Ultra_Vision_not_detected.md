---
title: "Logitech Quickcam Ultra Vision not detected"
date: 2008-10-02
forum: Multimedia Software
---

### Post by sifar786 on 2008-10-02
hi all,

I have plugged in my Logitech Webcam Ultravision webcam, but it does not seem to get detected in Ubuntu 6.06 LTS. It had worked in Windows XP, but since the time i recently shifted to Linux, it does not seem to work. 

Also i cannot download and install Skype as it always gives me dependencies errors.

I tried dmesg and this is the output:
------------------------------------
```

[17179569.184000] Linux version 2.6.15-52-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Aug 20 13:21:00 UTC 2008
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fef0000 - 000000000fef3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000fef3000 - 000000000ff00000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 254MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65264
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61168 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f6680
[17179569.184000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fef3000
[17179569.184000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fef3040
[17179569.184000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0ff00000:efc00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (011ff000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 701.342 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.328000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.332000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.364000] Memory: 248244k/261056k available (1978k kernel code, 12208k reserved, 604k data, 288k init, 0k highmem)
[17179573.364000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.444000] Calibrating delay using timer specific routine.. 1403.96 BogoMIPS (lpj=2807930)
[17179573.444000] Security Framework v1.0.0 initialized
[17179573.444000] SELinux:  Disabled at boot.
[17179573.444000] Mount-cache hash table entries: 512
[17179573.444000] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.444000] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.444000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179573.444000] CPU: L2 cache: 256K
[17179573.444000] CPU serial number disabled.
[17179573.444000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179573.444000] mtrr: v2.0 (20020519)
[17179573.444000] CPU: Intel Pentium III (Coppermine) stepping 03
[17179573.444000] Enabling fast FPU save and restore... done.
[17179573.444000] Enabling unmasked SIMD FPU exception support... done.
[17179573.444000] Checking 'hlt' instruction... OK.
[17179573.460000] checking if image is initramfs... it is
[17179575.668000] Freeing initrd memory: 6668k freed
[17179575.724000] ACPI: Looking for DSDT ... not found!
[17179575.728000] ACPI: setting ELCR to 0200 (from 0a20)
[17179575.760000] NET: Registered protocol family 16
[17179575.760000] EISA bus registered
[17179575.760000] ACPI: bus type pci registered
[17179575.772000] PCI: PCI BIOS revision 2.10 entry at 0xfb1b0, last bus=1
[17179575.772000] PCI: Using configuration type 1
[17179575.772000] ACPI: Subsystem revision 20051216
[17179575.788000] ACPI: Interpreter enabled
[17179575.788000] ACPI: Using PIC for interrupt routing
[17179575.788000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179575.788000] PCI: Probing PCI hardware (bus 00)
[17179575.788000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179575.792000] Boot video device is 0000:00:01.0
[17179575.796000] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[17179575.796000] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[17179575.796000] PCI: Transparent bridge - 0000:00:1e.0
[17179575.796000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179575.832000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179575.832000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179575.832000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179575.836000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179575.844000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179575.844000] pnp: PnP ACPI init
[17179575.852000] pnp: PnP ACPI: found 15 devices
[17179575.852000] PnPBIOS: Disabled by ACPI PNP
[17179575.852000] PCI: Using ACPI for IRQ routing
[17179575.852000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179575.864000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[17179575.864000] PCI: Bridge: 0000:00:1e.0
[17179575.864000]   IO window: c000-cfff
[17179575.864000]   MEM window: d4000000-d40fffff
[17179575.864000]   PREFETCH window: disabled.
[17179575.864000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179575.864000] audit: initializing netlink socket (disabled)
[17179575.864000] audit(1222982596.864:1): initialized
[17179575.864000] VFS: Disk quotas dquot_6.5.1
[17179575.864000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179575.864000] Initializing Cryptographic API
[17179575.864000] io scheduler noop registered
[17179575.864000] io scheduler anticipatory registered
[17179575.864000] io scheduler deadline registered
[17179575.864000] io scheduler cfq registered
[17179575.868000] isapnp: Scanning for PnP cards...
[17179576.220000] isapnp: No Plug & Play device found
[17179576.268000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179576.272000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179576.272000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179576.272000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179576.272000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179576.272000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179576.280000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179576.280000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179576.280000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179576.280000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179576.280000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179576.280000] mice: PS/2 mouse device common for all mice
[17179576.280000] EISA: Probing bus 0 at eisa.0
[17179576.284000] Cannot allocate resource for EISA slot 4
[17179576.284000] Cannot allocate resource for EISA slot 5
[17179576.284000] EISA: Detected 0 cards.
[17179576.284000] NET: Registered protocol family 2
[17179576.312000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179576.320000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179576.320000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[17179576.320000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179576.320000] TCP: Hash tables configured (established 8192 bind 8192)
[17179576.320000] TCP reno registered
[17179576.320000] TCP bic registered
[17179576.320000] NET: Registered protocol family 1
[17179576.320000] NET: Registered protocol family 8
[17179576.320000] NET: Registered protocol family 20
[17179576.320000] Using IPI Shortcut mode
[17179576.320000] ACPI wakeup devices: 
[17179576.320000] SLPB PCI0 HUB0 USB0 UAR1 UAR2 LPT1 
[17179576.320000] ACPI: (supports S0 S1 S4 S5)
[17179576.320000] Freeing unused kernel memory: 288k freed
[17179576.472000] vga16fb: initializing
[17179576.472000] vga16fb: mapped to 0xc00a0000
[17179576.584000] Console: switching to colour frame buffer device 80x25
[17179576.584000] fb0: VGA16 VGA frame buffer device
[17179577.756000] Capability LSM initialized
[17179577.844000] ACPI: Fan [FAN] (on)
[17179577.856000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179577.856000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179577.860000] ACPI: Thermal Zone [THRM] (22 C)
[17179579.248000] ICH: IDE controller at PCI slot 0000:00:1f.1
[17179579.248000] ICH: chipset revision 2
[17179579.248000] ICH: not 100% native mode: will probe irqs later
[17179579.248000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179579.248000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:DMA
[17179579.248000] Probing IDE interface ide0...
[17179579.540000] hda: SAMSUNG SV4012H, ATA DISK drive
[17179580.212000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179580.212000] Probing IDE interface ide1...
[17179581.228000] hdd: SAMSUNG CDRW/DVD SM-352F, ATAPI CD/DVD-ROM drive
[17179581.284000] ide1 at 0x170-0x177,0x376 on irq 15
[17179581.300000] hda: max request size: 128KiB
[17179581.324000] hda: 78242976 sectors (40060 MB) w/1824KiB Cache, CHS=65535/16/63, UDMA(33)
[17179581.328000] hda: cache flushes supported
[17179581.328000]  hda: hda1 hda2 < hda5 >
[17179581.352000] hdd: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179581.352000] Uniform CD-ROM driver Revision: 3.20
[17179581.724000] usbcore: registered new driver usbfs
[17179581.724000] usbcore: registered new driver hub
[17179581.732000] USB Universal Host Controller Interface driver v2.3
[17179581.732000] **** SET: Misaligned resource pointer: cfdcb5e2 Type 07 Len 0
[17179581.732000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179581.732000] PCI: setting IRQ 11 as level-triggered
[17179581.732000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179581.732000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179581.732000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179581.732000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179581.732000] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000d000
[17179581.736000] hub 1-0:1.0: USB hub found
[17179581.736000] hub 1-0:1.0: 2 ports detected
[17179581.980000] Attempting manual resume
[17179582.056000] EXT3-fs: mounted filesystem with ordered data mode.
[17179582.072000] kjournald starting.  Commit interval 5 seconds
[17179582.080000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[17179597.572000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.608000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.672000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.680000] agpgart: Detected an Intel i810 Chipset.
[17179597.692000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179597.692000] hw_random hardware driver 1.0.0 loaded
[17179597.704000] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[17179598.384000] 8139too Fast Ethernet driver 0.9.27
[17179598.384000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179598.384000] eth0: RealTek RTL8139 at 0xd08fc000, 00:08:a1:83:f7:2d, IRQ 11
[17179598.384000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179598.428000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179598.492000] logips2pp: Detected unknown logitech mouse model 106
[17179598.820000] input: PC Speaker as /class/input/input1
[17179598.952000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[17179599.128000] **** SET: Misaligned resource pointer: cc2c9922 Type 07 Len 0
[17179599.128000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179599.128000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179599.128000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179599.140000] Real Time Clock Driver v1.12
[17179599.444000] intel8x0_measure_ac97_clock: measured 55221 usecs
[17179599.444000] intel8x0: clocking to 48000
[17179599.448000] Floppy drive(s): fd0 is 1.44M
[17179599.464000] FDC 0 is a post-1991 82077
[17179599.556000] usbcore: registered new driver snd-usb-audio
[17179600.636000] ts: Compaq touchscreen protocol output
[17179600.656000] parport: PnPBIOS parport detected.
[17179600.656000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179601.552000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179602.612000] NET: Registered protocol family 17
[17179602.760000] lp0: using parport0 (interrupt-driven).
[17179602.920000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[17179603.084000] EXT3 FS on hda1, internal journal
[17179603.448000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179603.448000] md: bitmap version 4.39
[17179604.152000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179604.932000] cdrom: open failed.
[17179606.200000] NET: Registered protocol family 10
[17179606.200000] lo: Disabled Privacy Extensions
[17179606.200000] IPv6 over IPv4 tunneling driver
[17179613.476000] ACPI: Power Button (FF) [PWRF]
[17179613.476000] ACPI: Power Button (CM) [PWRB]
[17179613.476000] ACPI: Sleep Button (CM) [SLPB]
[17179613.764000] ibm_acpi: ec object not found
[17179613.832000] pcc_acpi: loading...
[17179617.060000] eth0: no IPv6 routers present
[17179626.448000] ppdev: user-space parallel port driver
[17179626.996000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179626.996000] apm: overridden by ACPI.
[17179638.128000] Bluetooth: Core ver 2.8
[17179638.128000] NET: Registered protocol family 31
[17179638.128000] Bluetooth: HCI device and connection manager initialized
[17179638.128000] Bluetooth: HCI socket layer initialized
[17179638.176000] Bluetooth: L2CAP ver 2.8
[17179638.176000] Bluetooth: L2CAP socket layer initialized
[17179638.188000] Bluetooth: RFCOMM socket layer initialized
[17179638.188000] Bluetooth: RFCOMM TTY layer initialized
[17179638.188000] Bluetooth: RFCOMM ver 1.7

```

I searched for any "spca" or "video0" string but could not locate any.

Please advice how i can use this webcam with Ubuntu as i have already invested a lot of money on this good camera.


Regards,

---

### Post by sifar786 on 2008-10-02
hi all,

Just to bring to your notice, i have 2 usb ports, 1 unused, and on other logitech webcam is connected.

i have used lsusb and it shows me this:
--------------------
```

Bus 001 Device 005: ID 046d:08c9 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

i have used installed lucview and this is the output:
--------------------------
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 

i have used **lsmod | grep uvc** but no results displayed.
i have used **insmod /dev/video0** but no get msg "no such file or directory"
i have tried **modprobe V4L** but no results displayed.
i have tried **modprobe spca5xx** but no results displayed.

please help!

---

### Post by sifar786 on 2008-10-03
Isnt there anyone who can help me with this???

---

### Post by sifar786 on 2008-10-06
Hey all,
I downloaded the latest Ubuntu 8.04.1 Desktop last night and it installed Luvcview from command terminal tonight :)

 sudo apt-get install luvcview

It automatically switched on my Logitech Quickcam Ultra Vision and i was able to see myself once i typed:

luvcview


This OS is cooooooooool man :))

regards to all.

---

