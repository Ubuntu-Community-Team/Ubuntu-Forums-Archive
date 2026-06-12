---
title: "Need help with DWL-650"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by supermistry on 2006-06-25
Hi,

I've been trying to get wifi to work on my laptop (IBM T21) using a D-Link DWL-650 card. I have been trying for almost a week now, and despite my best efforts and searching through these forums, I can not seem to get it to work.

Some of the things I have tried include installing Network Manager and Wireles Assistant, but neither have been very helpful so far. Also, I saw something about editting i think it was the sources file, again, that didn't help me much either.

The weird thing is that when I view network settings, I have a wireless connections (eth1) and when I'm in network properties, if I set the name to eth1, it says disconnected, but also shows 100% signal. If I set it to eth0 (my wired connection), my internet works just fine.

Can anyone help. It would be greatly appreciated as I have been struggling with this for a week now. Thanks a lot in advance,
- Kuran

---

### Post by tturrisi on 2006-06-25
The dwl650G has an atheros chipset and the interface should be ath0, not ethX.
Stick in your card, wait about 10 seconds and then in a terminal type:
iwconfig
next type:
iwpriv
next type iwlist ap
post all the results here.

---

### Post by supermistry on 2006-06-25
I am making this post from my laptop w/ eth0 being the wired connection to the router. eth1 is the wireless connection. I should probably mention that the router I'm using is a Linksys WRT54G and that it is WEP protected.

**iwconfig:**
supermistry@linuxbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"hemant0"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:76:6B:B9
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=-8 dBm  Noise level=-149 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**iwpriv:**
supermistry@linuxbox:~$ iwpriv
lo        no private ioctls.

eth0      no private ioctls.

irda0     no private ioctls.

eth1      Available private ioctls :
          force_reset      (8BE0) : set   0       & get   0
          card_reset       (8BE1) : set   0       & get   0
          set_port3        (8BE2) : set   1 int   & get   0
          get_port3        (8BE3) : set   0       & get   1 int
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get   1 int
          set_ibssport     (8BE6) : set   1 int   & get   0
          get_ibssport     (8BE7) : set   0       & get   1 int
          get_rid          (8BE9) : set   0       & get 1024 byte

sit0      no private ioctls.

**iwlist ap:**
supermistry@linuxbox:~$ iwlist ap
lo        Interface doesn't have a list of Peers/Access-Points

eth0      Interface doesn't have a list of Peers/Access-Points

irda0     Interface doesn't have a list of Peers/Access-Points

eth1      Interface doesn't have a list of Peers/Access-Points

sit0      Interface doesn't have a list of Peers/Access-Points

---

### Post by tturrisi on 2006-06-25
It shows that the card is not being detected.  Go to /var/log/dmesg and post the contents of dmesg.  That log may show that the notebook cardbus is unrecognized or similar.

---

### Post by supermistry on 2006-06-25
here is the contents of dmesg:

```

[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000fffec00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000fffec00 - 0000000010000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65520
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7160
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0fff4d07
[17179569.184000] ACPI: FADT (v001 IBM    TP-T21   0x06040000  0x00000000) @ 0x0fffeb65
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0fffebd9
[17179569.184000] ACPI: DSDT (v001 IBM    TP-T21   0x06040000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 796.625 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.228000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.232000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.260000] Memory: 249140k/262080k available (1976k kernel code, 12352k reserved, 606k data, 288k init, 0k highmem)
[17179570.260000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.340000] Calibrating delay using timer specific routine.. 1594.37 BogoMIPS (lpj=3188753)
[17179570.340000] Security Framework v1.0.0 initialized
[17179570.340000] SELinux:  Disabled at boot.
[17179570.340000] Mount-cache hash table entries: 512
[17179570.340000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.340000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.340000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179570.340000] CPU: L2 cache: 256K
[17179570.340000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179570.340000] mtrr: v2.0 (20020519)
[17179570.340000] CPU: Intel Pentium III (Coppermine) stepping 06
[17179570.340000] Enabling fast FPU save and restore... done.
[17179570.340000] Enabling unmasked SIMD FPU exception support... done.
[17179570.340000] Checking 'hlt' instruction... OK.
[17179570.356000] checking if image is initramfs... it is
[17179572.264000] Freeing initrd memory: 6614k freed
[17179572.304000] ACPI: Looking for DSDT ... not found!
[17179572.312000] ACPI: setting ELCR to 0200 (from 0800)
[17179572.340000] NET: Registered protocol family 16
[17179572.340000] EISA bus registered
[17179572.340000] ACPI: bus type pci registered
[17179572.340000] PCI: PCI BIOS revision 2.10 entry at 0xfd94f, last bus=7
[17179572.340000] PCI: Using configuration type 1
[17179572.344000] ACPI: Subsystem revision 20051216
[17179572.628000] ACPI: Interpreter enabled
[17179572.628000] ACPI: Using PIC for interrupt routing
[17179572.632000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.632000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.632000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.636000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.636000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.636000] PCI: Probing PCI hardware (bus 00)
[17179572.636000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.748000] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[17179572.748000] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[17179572.748000] PIIX4 devres C PIO at 15e8-15ef
[17179572.748000] PIIX4 devres I PIO at 03f0-03f7
[17179572.748000] PIIX4 devres J PIO at 002e-002f
[17179572.748000] Boot video device is 0000:01:00.0
[17179572.748000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.972000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179572.972000] ACPI: Power Resource [PSER] (off)
[17179572.972000] ACPI: Power Resource [PSIO] (on)
[17179572.976000] ACPI: Embedded Controller [EC] (gpe 9) interrupt mode.
[17179572.980000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.980000] pnp: PnP ACPI init
[17179573.092000] pnp: PnP ACPI: found 15 devices
[17179573.092000] PnPBIOS: Disabled by ACPI PNP
[17179573.092000] PCI: Using ACPI for IRQ routing
[17179573.092000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.100000] pnp: 00:01: ioport range 0x1000-0x103f could not be reserved
[17179573.100000] pnp: 00:01: ioport range 0x1040-0x104f has been reserved
[17179573.100000] pnp: 00:01: ioport range 0xfe00-0xfe0f has been reserved
[17179573.100000] pnp: 00:08: ioport range 0x15e0-0x15ef has been reserved
[17179573.100000] PCI: Bridge: 0000:00:01.0
[17179573.100000]   IO window: disabled.
[17179573.100000]   MEM window: f0000000-f7ffffff
[17179573.100000]   PREFETCH window: 28000000-280fffff
[17179573.100000] PCI: Bus 2, cardbus bridge: 0000:00:02.0
[17179573.100000]   IO window: 00001400-000014ff
[17179573.100000]   IO window: 00001c00-00001cff
[17179573.100000]   PREFETCH window: 20000000-21ffffff
[17179573.100000]   MEM window: 22000000-23ffffff
[17179573.100000] PCI: Bus 6, cardbus bridge: 0000:00:02.1
[17179573.100000]   IO window: 00002000-000020ff
[17179573.100000]   IO window: 00002400-000024ff
[17179573.100000]   PREFETCH window: 24000000-25ffffff
[17179573.100000]   MEM window: 26000000-27ffffff
[17179573.100000] **** SET: Misaligned resource pointer: ce96b3e2 Type 07 Len 0
[17179573.100000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179573.100000] PCI: setting IRQ 11 as level-triggered
[17179573.100000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179573.100000] **** SET: Misaligned resource pointer: ce96b3e2 Type 07 Len 0
[17179573.100000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179573.100000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179573.100000] Simple Boot Flag at 0x35 set to 0x1
[17179573.104000] audit: initializing netlink socket (disabled)
[17179573.104000] audit(1151273073.104:1): initialized
[17179573.104000] VFS: Disk quotas dquot_6.5.1
[17179573.104000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.104000] Initializing Cryptographic API
[17179573.104000] io scheduler noop registered
[17179573.104000] io scheduler anticipatory registered
[17179573.104000] io scheduler deadline registered
[17179573.104000] io scheduler cfq registered
[17179573.104000] Limiting direct PCI/PCI transfers.
[17179573.104000] isapnp: Scanning for PnP cards...
[17179573.456000] isapnp: No Plug & Play device found
[17179573.496000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179573.508000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.508000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.508000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.516000] **** SET: Misaligned resource pointer: cfea4ea2 Type 00 Len 42
[17179573.516000] pnp: Device 00:0b activated.
[17179573.516000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.516000] **** SET: Misaligned resource pointer: cfea4ea2 Type 07 Len 0
[17179573.516000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179573.516000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179573.520000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.520000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.520000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.520000] mice: PS/2 mouse device common for all mice
[17179573.520000] EISA: Probing bus 0 at eisa.0
[17179573.520000] Cannot allocate resource for EISA slot 1
[17179573.520000] Cannot allocate resource for EISA slot 2
[17179573.520000] EISA: Detected 0 cards.
[17179573.520000] NET: Registered protocol family 2
[17179573.544000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.564000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.564000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.564000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.564000] TCP: Hash tables configured (established 16384 bind 16384)
[17179573.564000] TCP reno registered
[17179573.564000] TCP bic registered
[17179573.564000] NET: Registered protocol family 1
[17179573.564000] NET: Registered protocol family 8
[17179573.564000] NET: Registered protocol family 20
[17179573.564000] Using IPI Shortcut mode
[17179573.564000] ACPI wakeup devices: 
[17179573.564000]  LID SLPB PCI0  USB UART 
[17179573.564000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.564000] Freeing unused kernel memory: 288k freed
[17179573.688000] vga16fb: initializing
[17179573.688000] vga16fb: mapped to 0xc00a0000
[17179573.820000] Console: switching to colour frame buffer device 80x25
[17179573.820000] fb0: VGA16 VGA frame buffer device
[17179574.936000] Capability LSM initialized
[17179575.020000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.020000] ACPI: Processor [CPU] (supports 8 throttling states)
[17179575.024000] ACPI: Thermal Zone [THM0] (33 C)
[17179576.208000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[17179576.208000] PIIX4: chipset revision 1
[17179576.208000] PIIX4: not 100% native mode: will probe irqs later
[17179576.208000]     ide0: BM-DMA at 0x1850-0x1857, BIOS settings: hda:DMA, hdb:pio
[17179576.208000]     ide1: BM-DMA at 0x1858-0x185f, BIOS settings: hdc:DMA, hdd:pio
[17179576.208000] Probing IDE interface ide0...
[17179576.500000] hda: IBM-DJSA-220, ATA DISK drive
[17179577.176000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.228000] Probing IDE interface ide1...
[17179577.964000] hdc: HITACHI DVD-ROM GD-S200, ATAPI CD/DVD-ROM drive
[17179578.644000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.664000] hda: max request size: 128KiB
[17179578.684000] hda: 39070080 sectors (20003 MB) w/1874KiB Cache, CHS=41344/15/63, UDMA(33)
[17179578.684000] hda: cache flushes not supported
[17179578.684000]  hda: hda1 hda2 < hda5 >
[17179578.760000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179578.760000] Uniform CD-ROM driver Revision: 3.20
[17179579.184000] usbcore: registered new driver usbfs
[17179579.184000] usbcore: registered new driver hub
[17179579.188000] USB Universal Host Controller Interface driver v2.3
[17179579.188000] **** SET: Misaligned resource pointer: cfc382e2 Type 07 Len 0
[17179579.192000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179579.192000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179579.192000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179579.192000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179579.192000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001860
[17179579.192000] hub 1-0:1.0: USB hub found
[17179579.192000] hub 1-0:1.0: 2 ports detected
[17179579.416000] Attempting manual resume
[17179579.540000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.576000] kjournald starting.  Commit interval 5 seconds
[17179600.720000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179600.720000] Yenta: CardBus bridge found at 0000:00:02.0 [1014:0130]
[17179600.720000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179600.720000] Yenta: Routing CardBus interrupts to PCI
[17179600.720000] Yenta TI: socket 0000:00:02.0, mfunc 0x00001000, devctl 0x66
[17179600.952000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179600.952000] Socket status: 30000006
[17179600.992000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179600.992000] Yenta: CardBus bridge found at 0000:00:02.1 [1014:0130]
[17179600.992000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179600.992000] Yenta: Routing CardBus interrupts to PCI
[17179600.992000] Yenta TI: socket 0000:00:02.1, mfunc 0x00001000, devctl 0x66
[17179601.224000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179601.224000] Socket status: 30000010
[17179601.228000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179601.432000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179601.472000] Linux agpgart interface v0.101 (c) Dave Jones
[17179601.808000] gameport: CS46xx Gameport is pci0000:00:05.0/gameport0, speed 1807kHz
[17179601.876000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179601.876000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[17179601.876000] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[17179601.992000] pccard: PCMCIA card inserted into slot 1
[17179602.048000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179602.068000] Real Time Clock Driver v1.12
[17179602.100000] agpgart: Detected an Intel 440BX Chipset.
[17179602.108000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179602.228000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179602.228000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179602.232000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179602.332000] e100: eth0: e100_probe: addr 0xe8120000, irq 11, MAC addr 00:10:A4:89:9B:8A
[17179602.560000] Floppy drive(s): fd0 is 1.44M
[17179602.576000] FDC 0 is a National Semiconductor PC87306
[17179603.048000] input: PC Speaker as /class/input/input1
[17179603.256000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17179603.280000] irda_init()
[17179603.280000] NET: Registered protocol family 23
[17179603.296000] input: TPPS/2 IBM TrackPoint as /class/input/input2
[17179603.344000] parport: PnPBIOS parport detected.
[17179603.344000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[17179603.440000] cs: IO port probe 0x100-0x3af: clean.
[17179603.440000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179603.440000] cs: IO port probe 0x820-0x8ff: clean.
[17179603.440000] cs: IO port probe 0xc00-0xcf7: clean.
[17179603.440000] cs: IO port probe 0xa00-0xaff: clean.
[17179603.444000] **** SET: Misaligned resource pointer: cb8a5242 Type 00 Len 42
[17179603.444000] **** SET: Misaligned resource pointer: cb8a52c6 Type 07 Len 0
[17179603.444000] pnp: Device 00:0d activated.
[17179603.444000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[17179603.444000] nsc-ircc, chip->init
[17179603.444000] nsc-ircc, Found chip at base=0x02e
[17179603.444000] nsc-ircc, driver loaded (Dag Brattli)
[17179603.444000] IrDA: Registered device irda0
[17179603.444000] nsc-ircc, Found dongle: Sharp RY5HD01
[17179603.464000] cs: IO port probe 0x100-0x3af: clean.
[17179603.468000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179603.468000] cs: IO port probe 0x820-0x8ff: clean.
[17179603.468000] cs: IO port probe 0xc00-0xcf7: clean.
[17179603.468000] cs: IO port probe 0xa00-0xaff: clean.
[17179603.468000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[17179603.788000] pcmcia: registering new device pcmcia1.0
[17179604.568000] ts: Compaq touchscreen protocol output
[17179604.760000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179605.000000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179605.008000] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179605.152000] eth1: Hardware identity 8008:0001:0001:0000
[17179605.152000] eth1: Station identity  001f:0002:0000:0008
[17179605.152000] eth1: Firmware determined as Intersil 0.8.2
[17179605.152000] eth1: Ad-hoc demo mode supported
[17179605.152000] eth1: IEEE standard IBSS ad-hoc mode supported
[17179605.152000] eth1: WEP supported, 104-bit key
[17179605.152000] eth1: MAC address 00:05:5D:A7:27:40
[17179605.152000] eth1: Station name "Prism  I"
[17179605.156000] eth1: ready
[17179605.156000] eth1: index 0x01: Vcc 3.3, irq 3, io 0x0100-0x013f
[17179605.212000] ieee80211_crypt: registered algorithm 'NULL'
[17179605.248000] hostap_cs: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179605.820000] lp0: using parport0 (interrupt-driven).
[17179605.840000] NET: Registered protocol family 17
[17179605.976000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[17179606.140000] EXT3 FS on hda1, internal journal
[17179606.472000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179606.472000] md: bitmap version 4.39
[17179607.596000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179608.872000] cdrom: open failed.
[17179609.752000] NET: Registered protocol family 10
[17179609.752000] lo: Disabled Privacy Extensions
[17179609.752000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179609.752000] IPv6 over IPv4 tunneling driver

```

---

### Post by klaas on 2006-06-26
I have the same card and tried a lot of things but nothing worked. Until I installed the following packages from the Ubuntu 6.06 cd with apt-get:
-linux-wlan-ng
-linux-wlan-ng-firmware

After installing these everything worked right away!

I hope this will help,
Klaas

---

### Post by tturrisi on 2006-06-26
OK, it shows the card is detected and drivers are loaded.  Go back to System > Administration > Networking and select eth1 from the dropdown menu.  Then click the configure button, enter password, & put a check in "enable this connection" (if not already checked).  Then choose YOUR access point from the dropdown list of available ap's.

How old is this dwl650?  It must be an older model w/ a prism chipset & should work.

---

### Post by supermistry on 2006-06-26
klaas - I'm not sure I follow what you are saying to do, but according to tturrisi, everything I need is already installed...

tturrisi - That's basically what I've been trying all along, but it hasn't been working. First off, eth1 isn't in the dropdown menu. There is eth0 and lo. I have to type in eth1 in order to get it. Secondly, you say to chose my access point from the dropdown list of available ap's... Well, after I click on wireless connections and go to properties...  I have the box checked to enable the connection, but under Network Name (ESSID), there is nothing in the drop down list. Again, i have to type in my ap, but I know there are at least 3 wifi signals in my area (from my neighbors), but it is not finding any of them. It never has and that has been bugging me all along.

---

### Post by klaas on 2006-06-27
Supermistry,

Normally you should have everything installed but according to a lot of posts (in non ubuntu newsgroups) there is something wrong with the hostap drivers, the installed kernel and prism chipsets. To avoid this, it is necessary to install other drivers like inux-wlan-ng and linux-wlan-ng-firmware.

Because you probably don't have internet access you must add the ubuntu cdrom to your sources.list (you can do this in synaptic) and then install those two packages (from cdrom).

Klaas

---

### Post by supermistry on 2006-06-28
klaas, I actually do have internet, I made the majority of those posts from my laptop, but was just using a wired connection (I have a router, but it's not in a convenient location for normal use, even my desktop uses wireless). However, I'm not sure how to run those commands.

I tried to do it from the terminal as follows:
apt-get -linux-wlan-ng

it gave me an error however (I'm not on ubuntu right now, so I can't copy the error over, sorry =/) and I was unable to figure out how exactly I should type the command. Probably a basic question, but I'm rather new to all of this.

Also, if you know of any reading (web or print) that'll help me get my feet wet, it'd be appreciated. Kind of a n00b's guide, so to speak.

---

### Post by klaas on 2006-06-28
Ok, if you have an internet connection you don't need the cdrom. 

So to install open a terminal session an type folowing commands (you will need to provide your password after the first command):

sudo apt-get update
sudo apt-get install linux-wlan-ng
sudo apt-get install linux-wlan-ng-firmware

Reboot your system and if you are lucky your wireless should work.

Klaas

---

### Post by supermistry on 2006-06-29
I tried to do that, but I keep running into errors. First it said it can;t find something off of the cdrom and to mount it using sudo apt-cdrom add so I did and it found that. Then I did the linux-wlan-ng, and that went through no problem, but when I try to do the firmware, I keep getting the following:

supermistry@linuxbox:~$ sudo apt-get install linux-wlan-ng-firmware
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-wlan-ng-firmware

I tried going in through Synaptic Package Managemer, and did a search for wlan, and the only things that came up were linux-wlan-ng and the documents for that, but nothing of the firmware. I'm connected to the internet (I'm posting from the laptop), so I'm not sure how I would go about finding said package =/

Edit: I found the package here:[http://packages.ubuntulinux.org/dapper/admin/linux-wlan-ng-firmware](http://packages.ubuntulinux.org/dapper/admin/linux-wlan-ng-firmware)

However, it still doesn't work =(

---

### Post by Jaxilian on 2006-07-21
D-Link DWL-650 works for me on my Thinkpad T20 right out of the box.

It's Atheros so it's name will be ath0

---

