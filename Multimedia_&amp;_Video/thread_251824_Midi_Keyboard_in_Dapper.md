---
title: "Midi Keyboard in Dapper"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by _axiom_ on 2006-09-05
I had this problem before, and thought I knew how to fix it.

My midi keyboard *was* working in breezy after this post:
[http://ubuntuforums.org/showthread.php?t=108370](http://ubuntuforums.org/showthread.php?t=108370)

I've since switched too Dapper and the keyboard has been in the closet for a while.

I got it out, but it is not working anymore, or at least I forgot some important command needed to run it.

I used to be able to run

```
amidi -d -p <device>
```

and see random looking hex output in konsole when I played the keyboard, but I cannont even get that now.  If I could see that, I think I could get the rest of it working.

It is good to see this Ubuntu Studio project pregressing.  Hopefully we will get to the point where stuff "Just Works" someday.

---

### Post by dolson on 2006-09-06
Try this:

lsmod | grep snd_seq

If you get nothing on the screen, then you did not load the module, as per the wiki.

If you did load the module, please plug in the USB keyboard and then run dmesg and paste the last few lines here.

---

### Post by _axiom_ on 2006-09-06
My keyboard is not usb (I bet it would be working by now), it plugs into the gameport on my sound card.

I think I have the module loaded (at least I did before Dapper), but it could be gone for some reason.

```
$ lsmod | grep snd_seq
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd                    55268  17 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep

```

This is probabbly the most interesting line in dmesg
```
$ dmesg | grep game
[4294697.772000] gameport: EMU10K1 is pci0000:02:02.1/gameport0, io 0xa400, speed 978kHz
```

but I include the rest, just in case
```

$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu May 18 16:42:54 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 127MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000f57f0
[4294667.296000] On node 0 totalpages: 262128
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 32752 pages, LIFO batch:7
[4294667.296000] DMI 2.2 present.
[4294667.296000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f7230
[4294667.296000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[4294667.296000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[4294667.296000] ACPI: MADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff72c0
[4294667.296000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x408
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:2 APIC version 20
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hdb1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 2010.583 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.401000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294668.402000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.440000] Memory: 1028820k/1048512k available (1976k kernel code, 18924k reserved, 606k data, 288k init, 131008k highmem)
[4294668.440000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.500000] Calibrating delay using timer specific routine.. 4022.70 BogoMIPS (lpj=2011353)
[4294668.500000] Security Framework v1.0.0 initialized
[4294668.500000] SELinux:  Disabled at boot.
[4294668.500000] Mount-cache hash table entries: 512
[4294668.500000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.500000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.500000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294668.500000] CPU: L2 cache: 512K
[4294668.500000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[4294668.500000] mtrr: v2.0 (20020519)
[4294668.500000] CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[4294668.500000] Enabling fast FPU save and restore... done.
[4294668.500000] Enabling unmasked SIMD FPU exception support... done.
[4294668.500000] Checking 'hlt' instruction... OK.
[4294668.504000] checking if image is initramfs... it is
[4294669.224000] Freeing initrd memory: 6605k freed
[4294669.241000] ACPI: Looking for DSDT ... not found!
[4294669.271000] ENABLING IO-APIC IRQs
[4294669.271000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294669.382000] NET: Registered protocol family 16
[4294669.382000] EISA bus registered
[4294669.382000] ACPI: bus type pci registered
[4294669.395000] PCI: PCI BIOS revision 2.10 entry at 0xfb050, last bus=2
[4294669.395000] PCI: Using configuration type 1
[4294669.396000] ACPI: Subsystem revision 20051216
[4294669.407000] ACPI: Interpreter enabled
[4294669.407000] ACPI: Using IOAPIC for interrupt routing
[4294669.407000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.407000] PCI: Probing PCI hardware (bus 00)
[4294669.411000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[4294669.411000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[4294669.411000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.411000] Boot video device is 0000:01:00.0
[4294669.411000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.412000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.439000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[4294669.441000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294669.441000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294669.441000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[4294669.442000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294669.442000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294669.442000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294669.443000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294669.443000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[4294669.447000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.447000] pnp: PnP ACPI init
[4294669.452000] pnp: PnP ACPI: found 13 devices
[4294669.452000] PnPBIOS: Disabled by ACPI PNP
[4294669.452000] PCI: Using ACPI for IRQ routing
[4294669.452000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.471000] pnp: 00:02: ioport range 0x400-0x4bf could not be reserved
[4294669.472000] PCI: Bridge: 0000:00:01.0
[4294669.472000]   IO window: 9000-9fff
[4294669.472000]   MEM window: d8000000-d9ffffff
[4294669.472000]   PREFETCH window: d0000000-d7ffffff
[4294669.472000] PCI: Bridge: 0000:00:1e.0
[4294669.472000]   IO window: a000-afff
[4294669.472000]   MEM window: da000000-dbffffff
[4294669.472000]   PREFETCH window: 50000000-500fffff
[4294669.472000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294669.472000] audit: initializing netlink socket (disabled)
[4294669.472000] audit(1157562653.471:1): initialized
[4294669.472000] highmem bounce pool size: 64 pages
[4294669.473000] VFS: Disk quotas dquot_6.5.1
[4294669.473000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.473000] Initializing Cryptographic API
[4294669.473000] io scheduler noop registered
[4294669.473000] io scheduler anticipatory registered
[4294669.473000] io scheduler deadline registered
[4294669.473000] io scheduler cfq registered
[4294669.473000] isapnp: Scanning for PnP cards...
[4294669.830000] isapnp: No Plug & Play device found
[4294669.849000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[4294669.849000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[4294669.850000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.851000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.851000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.851000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.853000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.854000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.854000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.854000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.854000] mice: PS/2 mouse device common for all mice
[4294669.855000] EISA: Probing bus 0 at eisa.0
[4294669.855000] EISA: Detected 0 cards.
[4294669.855000] NET: Registered protocol family 2
[4294669.865000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.865000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[4294669.866000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.867000] TCP: Hash tables configured (established 262144 bind 65536)
[4294669.867000] TCP reno registered
[4294669.867000] TCP bic registered
[4294669.867000] NET: Registered protocol family 1
[4294669.867000] NET: Registered protocol family 8
[4294669.867000] NET: Registered protocol family 20
[4294669.867000] Using IPI Shortcut mode
[4294669.867000] ACPI wakeup devices:
[4294669.867000] PCI0 HUB0 USB0 USB1 USB2 USB3 MODM UAR1
[4294669.867000] ACPI: (supports S0 S1 S4 S5)
[4294669.867000] Freeing unused kernel memory: 288k freed
[4294669.932000] vga16fb: initializing
[4294669.932000] vga16fb: mapped to 0xc00a0000
[4294670.071000] Console: switching to colour frame buffer device 80x25
[4294670.071000] fb0: VGA16 VGA frame buffer device
[4294670.073000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.195000] Capability LSM initialized
[4294671.238000] ACPI: Fan [FAN] (on)
[4294671.243000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294671.246000] ACPI: Thermal Zone [THRM] (44 C)
[4294671.985000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294671.985000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[4294671.985000] ICH4: chipset revision 1
[4294671.985000] ICH4: not 100% native mode: will probe irqs later
[4294671.985000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294671.985000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294671.985000] Probing IDE interface ide0...
[4294672.249000] hda: ST380020A, ATA DISK drive
[4294672.504000] hdb: MAXTOR 4K080H4, ATA DISK drive
[4294672.558000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.579000] Probing IDE interface ide1...
[4294673.251000] hdc: OPTORITE CD-RW CW4002, ATAPI CD/DVD-ROM drive
[4294673.965000] hdd: PIONEER DVD-RW DVR-105, ATAPI CD/DVD-ROM drive
[4294674.016000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.027000] hda: max request size: 128KiB
[4294674.051000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[4294674.051000] hda: cache flushes not supported
[4294674.051000]  hda: hda1 hda2 hda3
[4294674.108000] hdb: max request size: 128KiB
[4294674.109000] hdb: 156301488 sectors (80026 MB) w/2000KiB Cache, CHS=65535/16/63, UDMA(33)
[4294674.109000] hdb: cache flushes supported
[4294674.109000]  hdb: hdb1 hdb2 < hdb5 >
[4294674.151000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294674.151000] Uniform CD-ROM driver Revision: 3.20
[4294674.166000] hdd: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[4294674.762000] usbcore: registered new driver usbfs
[4294674.762000] usbcore: registered new driver hub
[4294674.763000] USB Universal Host Controller Interface driver v2.3
[4294674.763000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294674.763000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294674.763000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294674.763000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294674.763000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000b800
[4294674.764000] hub 1-0:1.0: USB hub found
[4294674.764000] hub 1-0:1.0: 2 ports detected
[4294674.865000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 177
[4294674.865000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294674.865000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294674.865000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294674.865000] uhci_hcd 0000:00:1d.1: irq 177, io base 0x0000b000
[4294674.865000] hub 2-0:1.0: USB hub found
[4294674.865000] hub 2-0:1.0: 2 ports detected
[4294674.966000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[4294674.966000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294674.966000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294674.966000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294674.966000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x0000b400
[4294674.966000] hub 3-0:1.0: USB hub found
[4294674.966000] hub 3-0:1.0: 2 ports detected
[4294675.069000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[4294675.069000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.069000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294675.069000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294675.070000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294675.070000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xdc000000
[4294675.071000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294675.074000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294675.074000] hub 4-0:1.0: USB hub found
[4294675.074000] hub 4-0:1.0: 6 ports detected
[4294675.299000] Attempting manual resume
[4294675.348000] EXT3-fs: mounted filesystem with ordered data mode.
[4294675.363000] kjournald starting.  Commit interval 5 seconds
[4294675.571000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[4294691.196000] ip_tables: (C) 2000-2002 Netfilter core team
[4294691.351000] Netfilter messages via NETLINK v0.30.
[4294691.579000] ip_conntrack version 2.4 (8191 buckets, 65528 max) - 232 bytes per conntrack
[4294695.987000] Linux agpgart interface v0.101 (c) Dave Jones
[4294695.993000] agpgart: Detected an Intel i845 Chipset.
[4294696.008000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294696.352000] input: PC Speaker as /class/input/input1
[4294696.385000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294696.389000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294696.845000] hw_random: RNG not detected
[4294696.916000] Real Time Clock Driver v1.12
[4294697.582000] Floppy drive(s): fd0 is 1.44M
[4294697.600000] FDC 0 is a post-1991 82077
[4294697.697000] parport: PnPBIOS parport detected.
[4294697.697000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294697.708000] usbcore: registered new driver hiddev
[4294697.743000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[4294697.743000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1
[4294697.743000] usbcore: registered new driver usbhid
[4294697.743000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294697.772000] gameport: EMU10K1 is pci0000:02:02.1/gameport0, io 0xa400, speed 978kHz
[4294697.952000] ts: Compaq touchscreen protocol output
[4294698.074000] 8139too Fast Ethernet driver 0.9.27
[4294698.075000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 19 (level, low) -> IRQ 177
[4294698.077000] eth0: RealTek RTL8139 at 0xf89e8000, 00:50:8d:a4:32:83, IRQ 177
[4294698.077000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294698.184000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294698.313000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 23 (level, low) -> IRQ 193
[4294698.798000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294699.182000] lp0: using parport0 (interrupt-driven).
[4294699.328000] Adding 2650684k swap on /dev/hdb5.  Priority:-1 extents:1 across:2650684k
[4294699.504000] EXT3 FS on hdb1, internal journal
[4294699.764000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294699.849000] NET: Registered protocol family 17
[4294700.244000] cdrom: open failed.
[4294700.617000] cdrom: open failed.
[4294700.635000] cdrom: open failed.
[4294701.422000] ReiserFS: hda3: found reiserfs format "3.6" with standard journal
[4294703.356000] NET: Registered protocol family 10
[4294703.357000] lo: Disabled Privacy Extensions
[4294703.357000] IPv6 over IPv4 tunneling driver
[4294707.729000] ReiserFS: hda3: using ordered data mode
[4294707.765000] ReiserFS: hda3: journal params: device hda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294707.767000] ReiserFS: hda3: checking transaction log (hda3)
[4294707.843000] ReiserFS: hda3: Using r5 hash to sort names
[4294711.915000] ACPI: Power Button (FF) [PWRF]
[4294711.915000] ACPI: Power Button (CM) [PWRB]
[4294712.045000] ibm_acpi: ec object not found
[4294712.073000] pcc_acpi: loading...
[4294713.938000] eth0: no IPv6 routers present
[4294717.594000] ppdev: user-space parallel port driver
[4294718.691000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294718.692000] apm: overridden by ACPI.
[4294731.615000] [drm] Initialized drm 1.0.1 20051102
[4294731.686000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294731.687000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4294732.739000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294732.740000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294732.740000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294733.292000] [drm] Setting GART location based on new memory map
[4294733.292000] [drm] writeback test succeeded in 2 usecs
[4294798.100000] Bluetooth: Core ver 2.8
[4294798.100000] NET: Registered protocol family 31
[4294798.100000] Bluetooth: HCI device and connection manager initialized
[4294798.100000] Bluetooth: HCI socket layer initialized

```

Which wiki page are you refering to, I saw your site, but I didn't find instructions on how to install, or tell if you have the appropriate kernal module.

---

### Post by dolson on 2006-09-07
Can you run amidi -l ?

---

### Post by _axiom_ on 2006-09-07
```
$ amidi -l
Device    Name
hw:0,0    EMU10K1 MPU-401 (UART)
hw:0,1    Emu10k1 Synth MIDI (16 subdevices)
hw:0,2    Emu10k1 Synth MIDI (16 subdevices)

```

---

### Post by dolson on 2006-09-08
OK, so the device you want is hw:0,0. What command did you try to run, exactly, when you put in "amidi -d -p <device>"?

And can you paste the output here? Did you try just JACKing the MPU-401 into ZynAddSubFX and see if you get output?

---

### Post by _axiom_ on 2006-09-08
I ran:

```
axiom@axiom:~$ amidi -d -p hw:0,0
```
(follow by much bangin on the keyboard, then ctrl-z)
```
0 bytes read
axiom@axiom:~$
```

The screenshot shows the way I am trying to connect MPU-401 to zynaddsubfx with JACK, but of course that is not working.

I vaugely remember having to run something as root (sudo), but neither zynaddsubfx or the qtjackctl responds better that way.

Maybe I just need to start from scratch.  Do you have a tutorial on how to setup a gameport midi keyboard?  If I ever find a method that works, I wouldn't mind writing one (if only for my own reference in times like this!)

---

### Post by dolson on 2006-09-08
That doesn't make sense. Do you have your MIDI cable's ends plugged in wrong? or maybe not attached fully to the MIDI port of your sound card? It should be plug-n-play, especially with a sound card like yours. You don't get any errors about the sequencer or anything because it's loaded. So the only possible thing i can think is there is a problem external to Linux..

Also, do you get sound from zyn if you hit the virtual keyboard? I assume you do, just double-checking.

---

### Post by _axiom_ on 2006-09-09
If it made sense, I wouldn't be posting here.  :)

1.The cable is tightly plugged into the midi "Out" on the back of the keyboard, and screw in all the way to the gameport on the back of my sound card.

2. *In a popup ballon coming from the systray* New midi device detected ... You midi device it configured and ready to use. (That would be nice.)

3. I hear wonderful noises when I click the zynaddsubfx virtual keyboard, that is why I keep trying.

I hope we have not run out of things to try.

---

### Post by dolson on 2006-09-10
#2 - I don't think this sort of thing even happens in Windows, because I am pretty sure it would not be possible. Your MIDI device is your soundcard, and your system detects it at bootup. Whatever you plug into it doesn't make a difference. However, it would be neat if we were notified when new USB devices were plugged in, detected and drivers were or were not available. It just wouldn't apply for your case.

Now, your MIDI cable. It should have two MIDI plugs on it, the In and the Out. Try switching it. Or try a new MIDI cable if you can afford one or know someone you could borrow one from. It really sounds like it's something external to me.

Also, does your keyboard have any kind of option menu where you can enable/disable MIDI? If so, check that too.

If you have a spare hard drive, you could try reinstalling Dapper or try out Edgy and see if there is a difference, but I don't think it's a software issue. Who knows though..

---

### Post by _axiom_ on 2006-09-10
It works!

For some reason it works better if you plug the "in" into the "out" slot.  Who would have thought.

Thanks for all your patients.  (Although not having it on at boot may have caused me some problems eariler.  Didn't know.)

---

### Post by dolson on 2006-09-10
Hahah.

Well, glad you got it working.

---

