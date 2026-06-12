---
title: "No Sound, on board or PCI"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by 67comet on 2007-03-05
I'm an intermediate Linux user. Usually have a system up and running pretty quick.

I have a machine here now that's got sound issues all over the place.

On board sound (VIA) doesn't work (enabled in bios). And none of the 3 PCI soundcards have worked (I lie, I had sound for about 2 hours but it was really bad, and when I shutdown to finish the build it never worked again).

I have about worn out alsamixer to make sure I do not have MUTE selected on anything. I've double clicked the volume control (Gnome) to make sure I was selecting the correct output device (Even left it alone, started music via xmms and moved the speaker cord around (and yes the speakers are plugged in, hooked up and work)).

Here are the results of lspci -v:
MadDog Predator 5.1 DSP (PCI Sound card)
<code>
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 209
        I/O ports at d000 [size=256]
        Capabilities: [c0] Power Management version 2
</code>
On board audio:
<code>
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Flags: medium devsel, IRQ 201
        I/O ports at 1000 [size=256]
        Capabilities: [c0] Power Management version 2
</code>

I don't have the other sound cards plugged in so I'm not sure what their results were in lspci (I ran it, just can't remember what they listed as).

I also have a WinTV-PVR-PCI Model 880 card in my computer (This computer is "supposed" to be a media box when I'm done). I have tried sound with and with out this card installed. I connected the TV Card to the sound card internally and tried getting sound via the tuner card with silence.

Does anyone have another idea?
I've:
* ran alsaconfig to check nothing is muted, or conflicting (cranked up Master, PCM and Aux)
* ran volume control to select correct device (Even with it disabled in bios the on-board is still an option).
* Tried 5 devices for sound (to include on-board)
* Tried another set of speakers off my main box (and visa versa)

Help?

Thank you,
Justin

P.S. dmesg just in case someone needed it: I don't see anything in there about the PCI card and don't know how to get it in there:

<code>
$ dmesg
[17179569.184000] Linux version 2.6.17-11-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Thu Feb 1 19:50:13 UTC 2007 (Ubuntu 2.6.17-11.35-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 639MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5160
[17179569.184000] On node 0 totalpages: 393200
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 163824 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 P4M80P                                ) @ 0x000f6ac0
[17179569.184000] ACPI: RSDT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x5fff3000
[17179569.184000] ACPI: FADT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x5fff3040
[17179569.184000] ACPI: MADT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x5fff6200
[17179569.184000] ACPI: DSDT (v001 P4M80P AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2393.678 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.512000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.512000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.568000] Memory: 1549592k/1572800k available (1829k kernel code, 21920k reserved, 1041k data, 288k init, 655296k highmem)
[17179569.568000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.648000] Calibrating delay using timer specific routine.. 4793.10 BogoMIPS (lpj=9586209)
[17179569.648000] Security Framework v1.0.0 initialized
[17179569.648000] SELinux:  Disabled at boot.
[17179569.648000] Mount-cache hash table entries: 512
[17179569.648000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.648000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.648000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.648000] CPU: L2 cache: 512K
[17179569.648000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[17179569.648000] CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 04
[17179569.648000] Checking 'hlt' instruction... OK.
[17179569.664000] SMP alternatives: switching to UP code
[17179569.664000] Freeing SMP alternatives: 0k freed
[17179569.664000] checking if image is initramfs... it is
[17179570.208000] Freeing initrd memory: 5253k freed
[17179570.208000] ACPI: Core revision 20060707
[17179570.212000] ACPI: Looking for DSDT ... not found!
[17179570.232000] ENABLING IO-APIC IRQs
[17179570.232000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.376000] NET: Registered protocol family 16
[17179570.376000] EISA bus registered
[17179570.376000] ACPI: bus type pci registered
[17179570.380000] PCI: PCI BIOS revision 2.10 entry at 0xfafc0, last bus=1
[17179570.380000] PCI: Using configuration type 1
[17179570.380000] Setting up standard PCI resources
[17179570.392000] ACPI: Interpreter enabled
[17179570.392000] ACPI: Using IOAPIC for interrupt routing
[17179570.392000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.392000] PCI: Probing PCI hardware (bus 00)
[17179570.396000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.0
[17179570.396000] PCI: Quirk-MSI-K8T Soundcard On
[17179570.396000] PCI: MSI-K8T soundcard on
[17179570.396000] Boot video device is 0000:01:00.0
[17179570.396000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.432000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[17179570.432000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[17179570.432000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[17179570.432000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
[17179570.432000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.432000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.436000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.436000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179570.436000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179570.436000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[17179570.436000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[17179570.436000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[17179570.440000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.440000] pnp: PnP ACPI init
[17179570.440000] pnp: PnP ACPI: found 11 devices
[17179570.440000] PnPBIOS: Disabled by ACPI PNP
[17179570.440000] PCI: Using ACPI for IRQ routing
[17179570.440000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.460000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179570.460000] pnp: 00:02: ioport range 0x500-0x50f has been reserved
[17179570.460000] PCI: Bridge: 0000:00:01.0
[17179570.460000]   IO window: disabled.
[17179570.460000]   MEM window: e8000000-e9ffffff
[17179570.460000]   PREFETCH window: d0000000-dfffffff
[17179570.460000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.460000] NET: Registered protocol family 2
[17179570.492000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.492000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179570.492000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.492000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.492000] TCP reno registered
[17179570.492000] audit: initializing netlink socket (disabled)
[17179570.492000] audit(1173130690.492:1): initialized
[17179570.492000] highmem bounce pool size: 64 pages
[17179570.492000] VFS: Disk quotas dquot_6.5.1
[17179570.492000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.492000] Initializing Cryptographic API
[17179570.492000] io scheduler noop registered
[17179570.492000] io scheduler anticipatory registered
[17179570.492000] io scheduler deadline registered
[17179570.492000] io scheduler cfq registered (default)
[17179570.492000] PCI: Bypassing VIA 8237 APIC De-Assert Message
[17179570.492000] isapnp: Scanning for PnP cards...
[17179570.848000] isapnp: No Plug & Play device found
[17179570.872000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.872000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.872000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.872000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.872000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.872000] mice: PS/2 mouse device common for all mice
[17179570.872000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.872000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.872000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.872000] PNP: No PS/2 controller found. Probing ports directly.
[17179570.884000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.884000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.888000] EISA: Probing bus 0 at eisa.0
[17179570.888000] Cannot allocate resource for EISA slot 1
[17179570.888000] Cannot allocate resource for EISA slot 4
[17179570.888000] EISA: Detected 0 cards.
[17179570.888000] TCP bic registered
[17179570.888000] NET: Registered protocol family 1
[17179570.888000] NET: Registered protocol family 8
[17179570.888000] NET: Registered protocol family 20
[17179570.888000] Using IPI Shortcut mode
[17179570.888000] ACPI: (supports S0 S1 S4 S5)
[17179570.888000] Freeing unused kernel memory: 288k freed
[17179570.992000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.112000] Capability LSM initialized
[17179572.152000] ACPI: Getting cpuindex for acpiid 0x1
[17179572.680000] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[17179572.680000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179572.680000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179572.680000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 169
[17179572.680000] PCI: Via IRQ fixup for 0000:00:0f.0, from 255 to 9
[17179572.680000] VP_IDE: chipset revision 6
[17179572.680000] VP_IDE: not 100% native mode: will probe irqs later
[17179572.680000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[17179572.680000]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:pio
[17179572.680000]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
[17179572.680000] Probing IDE interface ide0...
[17179573.096000] hda: IBM-DPTA-372050, ATA DISK drive
[17179573.768000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.768000] Probing IDE interface ide1...
[17179574.184000] hdc: WDC WD1200JB-00GVA0, ATA DISK drive
[17179574.632000] hdd: DVD DC DW1670, ATAPI CD/DVD-ROM drive
[17179574.692000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.700000] hda: max request size: 128KiB
[17179574.712000] hda: Host Protected Area detected.
[17179574.712000]       current capacity is 40086047 sectors (20524 MB)
[17179574.712000]       native  capacity is 40088160 sectors (20525 MB)
[17179574.716000] hda: Host Protected Area disabled.
[17179574.716000] hda: 40088160 sectors (20525 MB) w/1961KiB Cache, CHS=39770/16/63, UDMA(33)
[17179574.716000] hda: cache flushes not supported
[17179574.716000]  hda: hda1 hda2 hda3
[17179574.736000] hdc: max request size: 512KiB
[17179574.752000] hdc: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(33)
[17179574.756000] hdc: cache flushes supported
[17179574.756000]  hdc: hdc1
[17179574.800000] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.800000] Uniform CD-ROM driver Revision: 3.20
[17179575.100000] usbcore: registered new driver usbfs
[17179575.100000] usbcore: registered new driver hub
[17179575.100000] USB Universal Host Controller Interface driver v3.0
[17179575.100000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[17179575.100000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179575.100000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.100000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 1
[17179575.100000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179575.100000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179575.100000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000d800
[17179575.100000] usb usb1: configuration #1 chosen from 1 choice
[17179575.100000] hub 1-0:1.0: USB hub found
[17179575.100000] hub 1-0:1.0: 2 ports detected
[17179575.204000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.204000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 1
[17179575.204000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179575.204000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179575.204000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000dc00
[17179575.204000] usb usb2: configuration #1 chosen from 1 choice
[17179575.204000] hub 2-0:1.0: USB hub found
[17179575.204000] hub 2-0:1.0: 2 ports detected
[17179575.308000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.308000] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 1
[17179575.308000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179575.308000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179575.308000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000e000
[17179575.308000] usb usb3: configuration #1 chosen from 1 choice
[17179575.308000] hub 3-0:1.0: USB hub found
[17179575.308000] hub 3-0:1.0: 2 ports detected
[17179575.412000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.412000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 1
[17179575.412000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179575.412000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179575.412000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000e400
[17179575.412000] usb usb4: configuration #1 chosen from 1 choice
[17179575.412000] hub 4-0:1.0: USB hub found
[17179575.412000] hub 4-0:1.0: 2 ports detected
[17179575.548000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.548000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 1
[17179575.548000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179575.548000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179575.548000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xea004000
[17179575.548000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.548000] usb usb5: configuration #1 chosen from 1 choice
[17179575.552000] hub 5-0:1.0: USB hub found
[17179575.552000] hub 5-0:1.0: 8 ports detected
[17179575.716000] Attempting manual resume
[17179575.728000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179575.728000] SGI XFS Quota Management subsystem
[17179575.728000] XFS mounting filesystem hda3
[17179575.856000] Ending clean XFS mount for filesystem: hda3
[17179576.764000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[17179576.940000] usb 4-1: configuration #1 chosen from 1 choice
[17179591.608000] hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
[17179591.608000] ide: failed opcode was: unknown
[17179591.608000] hda: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
[17179591.608000] ide: failed opcode was: unknown
[17179591.940000] input: PC Speaker as /class/input/input1
[17179591.960000] Real Time Clock Driver v1.12ac
[17179591.972000] Linux video capture interface: v1.00
[17179592.100000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.108000] agpgart: Detected VIA P4M800CE chipset
[17179592.116000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179592.124000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.128000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.300000] parport: PnPBIOS parport detected.
[17179592.300000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179592.380000] bttv: driver version 0.9.16 loaded
[17179592.380000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179592.380000] bttv: Bt8xx card found (0).
[17179592.380000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179592.380000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 185, latency: 32, mmio: 0xea003000
[17179592.380000] bttv0: detected: Hauppauge WinTV/PVR [card=80], PCI subsystem ID is 0070:4500
[17179592.380000] bttv0: using: Modular Technology MM201/MM202/MM205/MM210/MM215 PCTV, bt878 [card=23,insmod option]
[17179592.380000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[17179592.380000] i2c-algo-bit.o: (0) scl=1, sda=1
[17179592.380000] i2c-algo-bit.o: (1) scl=1, sda=0
[17179592.380000] i2c-algo-bit.o: (2) scl=1, sda=1
[17179592.380000] i2c-algo-bit.o: (3) scl=0, sda=1
[17179592.380000] i2c-algo-bit.o: (4) scl=1, sda=1
[17179592.380000] i2c-algo-bit.o: bt878 #0 [sw] passed test.
[17179592.472000] bttv0: Modtec: Unknown TunerString: r
[17179592.472000] bttv0: using tuner=18
[17179592.476000] bttv0: i2c: checking for Bt832 @ 0x88... not found
[17179592.476000] bttv0: i2c: checking for Bt832 @ 0x8a... not found
[17179592.480000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179592.480000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179592.484000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179592.548000] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179592.548000] tuner 1-0061: type set to 18 (Temic PAL_I (4066 FY5))
[17179592.604000] bttv0: registered device video0
[17179592.604000] bttv0: registered device vbi0
[17179592.604000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179592.840000] usbcore: registered new driver hiddev
[17179592.864000] input: Logitech USB Receiver as /class/input/input2
[17179592.864000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:10.3-1
[17179592.904000] input: Logitech USB Receiver as /class/input/input3
[17179592.904000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.3-1
[17179592.904000] usbcore: registered new driver usbhid
[17179592.904000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.212000] nvidia: module license 'NVIDIA' taints kernel.
[17179593.476000] bt878: AUDIO driver version 0.0.0 loaded
[17179593.476000] bt878: Bt878 AUDIO function found (0).
[17179593.476000] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 185
[17179593.476000] bt878_probe: card id=[0x45000070], Unknown card.
[17179593.476000] Exiting..
[17179593.476000] ACPI: PCI interrupt for device 0000:00:09.1 disabled
[17179593.476000] bt878: probe of 0000:00:09.1 failed with error -22
[17179593.548000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179593.548000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
[17179593.556000] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[17179593.556000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179593.556000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179593.556000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179593.556000] PCI: Via IRQ fixup for 0000:00:11.5, from 0 to 9
[17179593.556000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179593.612000] ts: Compaq touchscreen protocol output
[17179594.072000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179594.300000] lp0: using parport0 (interrupt-driven).
[17179594.360000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179594.484000] ndiswrapper: driver bcmwl5a (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179594.484000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179594.496000] ndiswrapper: using irq 217
[17179595.176000] wlan0: vendor: ''
[17179595.176000] wlan0: ethernet device 00:11:50:62:3a:9b using NDIS driver bcmwl5a, 14E4:4318.5.conf
[17179595.176000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179595.216000] ndiswrapper: changing interface name from 'wlan0' to 'eth0'
[17179595.244000] Adding 996020k swap on /dev/disk/by-uuid/cb82f60c-1e9a-40e8-9600-a27323aea5fe.  Priority:-1 extents:1 across:996020k
[17179595.468000] Filesystem "hda3": Disabling barriers, not supported by the underlying device
[17179595.948000] JFS: nTxBlock = 8192, nTxLock = 65536
[17179597.088000] NET: Registered protocol family 10
[17179597.088000] lo: Disabled Privacy Extensions
[17179597.088000] IPv6 over IPv4 tunneling driver
[17179597.592000] ACPI: Power Button (FF) [PWRF]
[17179597.592000] ACPI: Power Button (CM) [PWRB]
[17179597.724000] ibm_acpi: ec object not found
[17179597.756000] pcc_acpi: loading...
[17179598.204000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179601.416000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179601.416000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179601.416000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179602.728000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179602.728000] apm: overridden by ACPI.
[17179607.348000] eth0: no IPv6 routers present
[17179610.584000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[17179610.696000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179610.712000] NFSD: starting 90-second grace period
[17179611.320000] Bluetooth: Core ver 2.8
[17179611.320000] NET: Registered protocol family 31
[17179611.320000] Bluetooth: HCI device and connection manager initialized
[17179611.320000] Bluetooth: HCI socket layer initialized
[17179611.348000] Bluetooth: L2CAP ver 2.8
[17179611.348000] Bluetooth: L2CAP socket layer initialized
[17179611.368000] Bluetooth: RFCOMM socket layer initialized
[17179611.368000] Bluetooth: RFCOMM TTY layer initialized
[17179611.368000] Bluetooth: RFCOMM ver 1.7
</code>

---

### Post by pandu.rs on 2007-03-05
sudo lsof /dev/dsp

I guess this should not produce any output. Otherwise it means some process is using oss. kill it and then try playing some sound

---

### Post by 67comet on 2007-03-06
No results, and no sound.

I am just so stumped. There has always been an error log, message info etc when I've had issues. But this time (this machine) just baffles me).

Thanks for the idea pandu.rs,
Justin

---

### Post by CyberCod on 2007-03-22
I have the C-Media Electronics Inc CM8738  sound card as well.

I found i can get sound through it...  There's a box marked "IEC958 in Monitor" in the switches.  Make sure thats on.

Then get xmms set up so that it will use it... may take some fiddlin around.

Your speakers should be plugged into the green jack.

Note: its still buggy.  I lose sound on VLC whenever I have music playing from a web-page.
But it sounds good while it works.   Just sort of a one-at-a-time thing... dunno why yet.  I am in here trying to figure that out now when I came across your post.

Hope that helps ya....

---

