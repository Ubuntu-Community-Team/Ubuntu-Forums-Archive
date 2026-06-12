---
title: "No volume control GStreamer plugins and/or devices found."
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by Jerim on 2006-08-16
Just a little backstory here. I was trying to set up my computer to dual boot Windows and Ubuntu. So I had two partitions. After using Ubuntu for a while, I decided to format the Windows partition to use in Ubuntu. The sound worked for a while, but then after running Automatix I started getting the above error. I tried formatting the different partitions one at a time to install a fresh version of Ubunutu (I used the other partition for backup.) Even after a fresh install I kept getting the error message. Finally I upload all my data to an FTP site and formatted the whole harddrive as one partition, which is what I am currently running. The sound worked great the first time I booted up. I lowered the sound all the way down to mute using the speaker icon up at the top. Now I get that error message every time. Rebooting doesn't help. I tried using this: [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=snd-hda-intel](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=snd-hda-intel)
Here is what I get:

**aplay -l**
jerim@jerim:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
--------------------------------------------------------------------------
**lspci -v**
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Dell: Unknown device 01c9
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]
--------------------------------------------------------------------------
Since both of those checked out okay, I used alsamixer as the guide suggested. I turned everything all the way up but still nothing. I have also walked through the steps of getting the driver from a fresh kernel. The exact problem is that I get sound at the login screen as in the little drum beats. But once I log in the sound is gone. I have tried going to System -> Preferences -> Sound but there is no option for Default Sound Card. There are literally no cards in there. I would appreciate any help. If there is a guide, please post a link. Searching through every thread can get tiresome.

---

### Post by encompass on 2006-08-16
Do you have an sneaky second sound cards.  I has a similar issue with my USB camera.  It is a sound card because it has a micraphone on it.
Try unpluging everything usb and rebooting... still have the issue?

---

### Post by Jerim on 2006-08-16
I am running a Dell B130 laptop. The only USB device I have is my mouse. I unplugged it, and restarted. Still no sound. I also get this error message when I try to turn up the volume using the speaker icon up at the top:

[B]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/B]

If that helps any.

---

### Post by Jerim on 2006-08-18
I found this command in another thread:

gst-register-0.8

Suppossedly you do that as root and then restart. It didn't work for me, but might work for others. I am still searching for the solution. I opened up a bug report with Alsa. The sound before login works fine, but sound doesn't work after login. So something is loading between those two states to cause the problem.

Also, here is some output from lsmod:

snd_hda_intel          18964  0
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
psmouse                36100  0
snd                    55268  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm


It appears that the sound is loading correctly.

---

### Post by Jerim on 2006-08-18
Some additional info:

Checking the /var/log/messages log I find not metion of snd-hda-intel. 
Using dmesg, I see no mention of anything to do with sound:

[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f7d3800 (usable)
[17179569.184000]  BIOS-e820: 000000001f7d3800 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 503MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 128979
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124883 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc970
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d50b15 ASL  0x00000061) @ 0x1f7d4425
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d50b15 ASL  0x00000061) @ 0x1f7d4c00
[17179569.184000] ACPI: MADT (v001 DELL    CPi R   0x27d50b15 ASL  0x00000047) @ 0x1f7d5400
[17179569.184000] ACPI: MCFG (v016 DELL    CPi R   0x27d50b15 ASL  0x00000061) @ 0x1f7d53c0
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x1f7d4658
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x1f7d445d
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1396.614 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.284000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.284000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.300000] Memory: 501044k/515916k available (1976k kernel code, 14352k reserved, 606k data, 288k init, 0k highmem)
[17179569.300000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.380000] Calibrating delay using timer specific routine.. 2797.24 BogoMIPS (lpj=5594498)
[17179569.380000] Security Framework v1.0.0 initialized
[17179569.380000] SELinux:  Disabled at boot.
[17179569.380000] Mount-cache hash table entries: 512
[17179569.380000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179569.380000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179569.380000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.380000] CPU: L2 cache: 1024K
[17179569.380000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[17179569.380000] mtrr: v2.0 (20020519)
[17179569.380000] CPU: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[17179569.380000] Enabling fast FPU save and restore... done.
[17179569.380000] Enabling unmasked SIMD FPU exception support... done.
[17179569.380000] Checking 'hlt' instruction... OK.
[17179569.396000] checking if image is initramfs... it is
[17179570.140000] Freeing initrd memory: 6617k freed
[17179570.152000] ACPI: Looking for DSDT ... not found!
[17179570.156000] ENABLING IO-APIC IRQs
[17179570.156000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.300000] NET: Registered protocol family 16
[17179570.300000] EISA bus registered
[17179570.300000] ACPI: bus type pci registered
[17179570.312000] PCI: PCI BIOS revision 2.10 entry at 0xfba7e, last bus=13
[17179570.312000] PCI: Using MMCONFIG
[17179570.312000] ACPI: Subsystem revision 20051216
[17179570.328000] ACPI: Interpreter enabled
[17179570.328000] ACPI: Using IOAPIC for interrupt routing
[17179570.332000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.332000] PCI: Probing PCI hardware (bus 00)
[17179570.332000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.352000] Boot video device is 0000:00:02.0
[17179570.352000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179570.352000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[17179570.352000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.352000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.352000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.372000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179570.372000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[17179570.376000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[17179570.376000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[17179570.376000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.376000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.376000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.376000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179570.376000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.376000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[17179570.376000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.376000] pnp: PnP ACPI init
[17179570.400000] pnp: PnP ACPI: found 10 devices
[17179570.400000] PnPBIOS: Disabled by ACPI PNP
[17179570.400000] PCI: Using ACPI for IRQ routing
[17179570.400000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.448000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[17179570.448000] pnp: 00:01: ioport range 0x1000-0x1005 could not be reserved
[17179570.448000] pnp: 00:01: ioport range 0x1008-0x100f could not be reserved
[17179570.448000] pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
[17179570.448000] pnp: 00:02: ioport range 0x1006-0x1007 has been reserved
[17179570.448000] pnp: 00:02: ioport range 0x100a-0x1059 could not be reserved
[17179570.448000] pnp: 00:02: ioport range 0x1060-0x107f has been reserved
[17179570.448000] pnp: 00:02: ioport range 0x1080-0x10bf has been reserved
[17179570.448000] pnp: 00:02: ioport range 0x10c0-0x10df has been reserved
[17179570.448000] pnp: 00:07: ioport range 0x900-0x90f has been reserved
[17179570.448000] pnp: 00:07: ioport range 0x910-0x91f has been reserved
[17179570.448000] pnp: 00:07: ioport range 0x920-0x92f has been reserved
[17179570.448000] pnp: 00:07: ioport range 0x930-0x93f has been reserved
[17179570.448000] pnp: 00:07: ioport range 0x940-0x97f has been reserved
[17179570.448000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.448000] PCI: Bridge: 0000:00:1c.0
[17179570.448000]   IO window: disabled.
[17179570.448000]   MEM window: disabled.
[17179570.448000]   PREFETCH window: disabled.
[17179570.448000] PCI: Bridge: 0000:00:1c.3
[17179570.448000]   IO window: d000-dfff
[17179570.448000]   MEM window: dfc00000-dfdfffff
[17179570.448000]   PREFETCH window: d0000000-d01fffff
[17179570.448000] PCI: Bridge: 0000:00:1e.0
[17179570.448000]   IO window: disabled.
[17179570.448000]   MEM window: dfb00000-dfbfffff
[17179570.448000]   PREFETCH window: disabled.
[17179570.448000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.448000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.448000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179570.448000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.448000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.448000] audit: initializing netlink socket (disabled)
[17179570.448000] audit(1155917273.448:1): initialized
[17179570.448000] VFS: Disk quotas dquot_6.5.1
[17179570.448000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.448000] Initializing Cryptographic API
[17179570.448000] io scheduler noop registered
[17179570.448000] io scheduler anticipatory registered
[17179570.448000] io scheduler deadline registered
[17179570.448000] io scheduler cfq registered
[17179570.448000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.448000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.448000] assign_interrupt_mode Found MSI capability
[17179570.448000] Allocate Port Service[pcie00]
[17179570.448000] Allocate Port Service[pcie02]
[17179570.448000] Allocate Port Service[pcie03]
[17179570.448000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179570.448000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.448000] assign_interrupt_mode Found MSI capability
[17179570.448000] Allocate Port Service[pcie00]
[17179570.448000] Allocate Port Service[pcie02]
[17179570.448000] Allocate Port Service[pcie03]
[17179570.448000] isapnp: Scanning for PnP cards...
[17179570.804000] isapnp: No Plug & Play device found
[17179570.820000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.820000] i8042.c: Warning: Keylock active.
[17179570.820000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.820000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.820000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.824000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.824000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.824000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx[17179570.824000] mice: PS/2 mouse device common for all mice
[17179570.824000] EISA: Probing bus 0 at eisa.0
[17179570.824000] Cannot allocate resource for EISA slot 1
[17179570.824000] EISA: Detected 0 cards.
[17179570.824000] NET: Registered protocol family 2
[17179570.832000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.868000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.868000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.868000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.868000] TCP: Hash tables configured (established 16384 bind 16384)
[17179570.868000] TCP reno registered
[17179570.868000] TCP bic registered
[17179570.868000] NET: Registered protocol family 1
[17179570.868000] NET: Registered protocol family 8
[17179570.868000] NET: Registered protocol family 20
[17179570.868000] Using IPI Shortcut mode
[17179570.868000] ACPI wakeup devices:
[17179570.868000]  LID PBTN PCI0 USB0 USB1 USB2 USB4 USB3 AZAL MODM PCIE RP01 RP02 RP03 RP04 RP05 RP06
[17179570.868000] ACPI: (supports S0 S3 S4 S5)
[17179570.868000] Freeing unused kernel memory: 288k freed
[17179570.916000] vga16fb: initializing
[17179570.916000] vga16fb: mapped to 0xc00a0000
[17179571.048000] Console: switching to colour frame buffer device 80x25
[17179571.048000] fb0: VGA16 VGA frame buffer device
[17179572.072000] Capability LSM initialized
[17179572.192000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179572.192000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.196000] ACPI: Thermal Zone [THM] (64 C)
[17179572.628000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179572.628000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.628000] ICH6: chipset revision 3
[17179572.628000] ICH6: not 100% native mode: will probe irqs later
[17179572.628000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:DMA
[17179572.628000] Probing IDE interface ide0...
[17179572.916000] hda: TOSHIBA MK4026GAX, ATA DISK drive
[17179573.700000] hdb: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
[17179573.756000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.812000] hda: max request size: 128KiB
[17179573.816000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
[17179573.816000] hda: cache flushes supported
[17179573.816000]  hda: hda1 hda2 < hda5 >
[17179573.848000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179573.848000] Uniform CD-ROM driver Revision: 3.20
[17179574.120000] usbcore: registered new driver usbfs
[17179574.120000] usbcore: registered new driver hub
[17179574.120000] USB Universal Host Controller Interface driver v2.3
[17179574.120000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.120000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.120000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.120000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.120000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000bf80
[17179574.120000] hub 1-0:1.0: USB hub found
[17179574.120000] hub 1-0:1.0: 2 ports detected
[17179574.224000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 209
[17179574.224000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.224000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.224000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.224000] uhci_hcd 0000:00:1d.1: irq 209, io base 0x0000bf60
[17179574.224000] hub 2-0:1.0: USB hub found
[17179574.224000] hub 2-0:1.0: 2 ports detected
[17179574.328000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 217
[17179574.328000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179574.328000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179574.328000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179574.328000] uhci_hcd 0000:00:1d.2: irq 217, io base 0x0000bf40
[17179574.328000] hub 3-0:1.0: USB hub found
[17179574.328000] hub 3-0:1.0: 2 ports detected
[17179574.432000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179574.432000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179574.432000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179574.432000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179574.432000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000bf20
[17179574.432000] hub 4-0:1.0: USB hub found
[17179574.432000] hub 4-0:1.0: 2 ports detected
[17179574.464000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179574.536000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.536000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179574.536000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179574.536000] ehci_hcd 0000:00:1d.7: debug port 1
[17179574.536000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179574.536000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179574.536000] ehci_hcd 0000:00:1d.7: irq 169, io mem 0xb0000000
[17179574.540000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.540000] hub 5-0:1.0: USB hub found
[17179574.540000] hub 5-0:1.0: 8 ports detected
[17179574.660000] Probing IDE interface ide1...
[17179574.988000] usb 1-1: device not accepting address 2, error -71
[17179575.328000] Attempting manual resume
[17179575.392000] EXT3-fs: mounted filesystem with ordered data mode.
[17179575.404000] kjournald starting.  Commit interval 5 seconds
[17179575.472000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179586.116000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.120000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.184000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.184000] agpgart: Detected an Intel 915GM Chipset.
[17179586.184000] agpgart: Detected 7932K stolen memory.
[17179586.204000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179586.360000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179586.364000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179586.860000] hw_random hardware driver 1.0.0 loaded
[17179586.872000] Real Time Clock Driver v1.12
[17179586.872000] input: PC Speaker as /class/input/input1
[17179586.888000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[17179586.924000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179586.972000] usbcore: registered new driver hiddev
[17179587.000000] input: Logitech Optical USB Mouse as /class/input/input3
[17179587.000000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[17179587.000000] usbcore: registered new driver usbhid
[17179587.000000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179587.224000] b44.c:v0.97 (Nov 30, 2005)
[17179587.224000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 217
[17179587.228000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:14:22:92:b0:00
[17179587.240000] ts: Compaq touchscreen protocol output
[17179588.556000] lp: driver loaded but no devices found
[17179588.592000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179588.680000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[17179588.680000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179588.688000] ndiswrapper: using irq 209
[17179589.828000] wlan0: vendor: ''
[17179589.828000] wlan0: ndiswrapper ethernet device 00:14:a4:58:bd:bc using driver bcmwl5, 14E4:4318.5.conf
[17179589.828000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179589.864000] Adding 1485972k swap on /dev/hda5.  Priority:-1 extents:1 across:1485972k
[17179590.044000] EXT3 FS on hda1, internal journal
[17179590.220000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179590.220000] md: bitmap version 4.39
[17179590.776000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179591.544000] cdrom: open failed.
[17179593.028000] ACPI: AC Adapter [AC] (on-line)
[17179593.304000] ACPI: Battery Slot [BAT0] (battery present)
[17179593.388000] ACPI: Lid Switch [LID]
[17179593.388000] ACPI: Power Button (CM) [PBTN]
[17179593.388000] ACPI: Sleep Button (CM) [SBTN]
[17179593.488000] ibm_acpi: ec object not found
[17179593.520000] pcc_acpi: loading...
[17179593.616000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179593.616000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179599.132000] [drm] Initialized drm 1.0.1 20051102
[17179599.136000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179599.136000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179601.104000] ppdev: user-space parallel port driver
[17179601.468000] apm: BIOS not found.
[17179605.724000] NET: Registered protocol family 10
[17179605.724000] lo: Disabled Privacy Extensions
[17179605.724000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179605.724000] IPv6 over IPv4 tunneling driver
[17179607.192000] Bluetooth: Core ver 2.8
[17179607.192000] NET: Registered protocol family 31
[17179607.192000] Bluetooth: HCI device and connection manager initialized
[17179607.192000] Bluetooth: HCI socket layer initialized
[17179607.228000] Bluetooth: L2CAP ver 2.8
[17179607.228000] Bluetooth: L2CAP socket layer initialized
[17179607.228000] Bluetooth: RFCOMM socket layer initialized
[17179607.228000] Bluetooth: RFCOMM TTY layer initialized
[17179607.228000] Bluetooth: RFCOMM ver 1.7
[17179607.768000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179607.768000] b44: eth0: Flow control is on for TX and on for RX.
[17179607.768000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179610.308000] NET: Registered protocol family 17
[17179616.488000] eth1: no IPv6 routers present
[17179625.824000] eth0: no IPv6 routers present
[17179695.448000] eth1: no IPv6 routers present
[17179709.768000] b44: eth0: Link is down.

---

### Post by encompass on 2006-08-18
try shutting everything off that is gstreamer... in the sound prefs disable system sounds... and run a "sudo killall esd"
and sounds?
restart and check too....
I am swinging... I just hope I get a hit...

---

### Post by john.ennew on 2006-08-19
OK, I found a fix for me

There is a user group called audio and all users which are to have control of the audio device must be a member of that group. I have no idea how my user account stopped being a member of that group, but adding it back and restarting the computer brought back the sound.

Work instructions:
System->Administration->Users and Groups
Choose the Groups Tab
Make sure the box "Show all users and groups" is ticked and scroll down the window to find the audio group (it's not in alphabetical order)
Highlight it and click Properties
Add all group members which need audio by highlighting the name in the left collumn and clicking add so they appear in the right collumn.
Click OK, OK and restart the computer.

Hope this helps someone,
John

---

### Post by Jerim on 2006-08-21
Thanks, that worked perfectly for me.

---

