---
title: "Pcmcia Doesn't Work"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by senzazoo on 2006-07-01
Hi, I will be grateful who wants consider my following problem: I have a PCMCIA card network "**HAMLET RE450CT**" (the technical Hamlet support advises to refer to HRE450 model), even though the link is on and the pcmcia service gives OK during boot, it doesn't work. In particular in the NETWORK-ADMIN window the ethernet connection doesn't appear. From my modest experience I think that driver misses. Is there someone which can suggest me from where to begin to solve this problem?
I take back to you a few data: 

out of ifconfig
```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

```

out of dmesg
```

[4294708.669000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294709.308000] pccard: PCMCIA card inserted into slot 0
[4294709.439000] parport: PnPBIOS parport detected.
[4294709.439000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[4294709.459000] Real Time Clock Driver v1.12
[4294709.981000] ts: Compaq touchscreen protocol output
[4294710.075000] cs: warning: no high memory space available!
[4294710.075000] cs: unable to map card memory!
[4294710.075000] cs: unable to map card memory

```

oyt of lshw
```

*-pcmcia
             description: CardBus bridge
             product: OZ6812 CardBus Controller
             vendor: O2 Micro, Inc.
             physical id: 3
             bus info: pci@00:03.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:14000000-14000fff irq:10

```

Thanks for your interest.

---

### Post by efreddi on 2006-07-01
Similar problem: after the upgrade from Breezy to Dapper my Xircom modem/ethernet card doesn't work.  It looks that it's correctly recognized (the correct modulus is loaded) but no connection to the net - **etho** doesn't exit.
After the login, I unplug/plug the card and then it's recognized and everything works as before the upgrade.

This is the output of **dmesg**:

```

...cut...
[17179572.156000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.236000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179572.236000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[17179572.236000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *0, disabled.
[17179572.236000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[17179572.240000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179572.240000] ACPI: Power Resource [PADA] (on)
[17179572.240000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.240000] pnp: PnP ACPI init
[17179572.320000] pnp: PnP ACPI: found 15 devices
[17179572.320000] PnPBIOS: Disabled by ACPI PNP
[17179572.320000] PCI: Using ACPI for IRQ routing
[17179572.320000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.332000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179572.332000] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[17179572.332000] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[17179572.332000] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[17179572.332000] pnp: 00:03: ioport range 0x850-0x853 has been reserved
[17179572.332000] pnp: 00:03: ioport range 0x856-0x85f has been reserved
[17179572.332000] pnp: 00:03: ioport range 0x810-0x83f has been reserved
[17179572.332000] pnp: 00:03: ioport range 0x840-0x84f has been reserved
[17179572.332000] pnp: 00:03: ioport range 0x600-0x67f has been reserved
[17179572.332000] pnp: 00:03: ioport range 0x680-0x6ff has been reserved
[17179572.332000] pnp: 00:04: ioport range 0xf000-0xf0fe has been reserved
[17179572.332000] pnp: 00:04: ioport range 0xf100-0xf1fe has been reserved
[17179572.332000] pnp: 00:04: ioport range 0xf200-0xf2fe has been reserved
[17179572.332000] pnp: 00:04: ioport range 0xf400-0xf4fe has been reserved
[17179572.332000] pnp: 00:04: ioport range 0xf500-0xf5fe has been reserved
[17179572.332000] pnp: 00:04: ioport range 0xf600-0xf6fe has been reserved
[17179572.332000] pnp: 00:04: ioport range 0xf800-0xf8fe has been reserved
[17179572.332000] pnp: 00:04: ioport range 0xf900-0xf9fe has been reserved
[17179572.336000] pnp: 00:09: ioport range 0x3f0-0x3f1 has been reserved
[17179572.336000] PCI: Bridge: 0000:00:01.0
[17179572.336000]   IO window: e000-efff
[17179572.336000]   MEM window: fd000000-feffffff
[17179572.336000]   PREFETCH window: f8000000-fbffffff
[17179572.336000] PCI: Bus 2, cardbus bridge: 0000:00:03.0
[17179572.336000]   IO window: 00001000-000010ff
[17179572.336000]   IO window: 00001400-000014ff
[17179572.336000]   PREFETCH window: 20000000-21ffffff
[17179572.336000]   MEM window: 22000000-23ffffff
[17179572.336000] PCI: Bus 6, cardbus bridge: 0000:00:03.1
[17179572.336000]   IO window: 00001800-000018ff
[17179572.336000]   IO window: 00001c00-00001cff
[17179572.336000]   PREFETCH window: 24000000-25ffffff
[17179572.336000]   MEM window: 26000000-27ffffff
[17179572.336000] PCI: Enabling device 0000:00:03.0 (0000 -> 0003)
[17179572.336000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179572.336000] PCI: setting IRQ 11 as level-triggered
[17179572.336000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179572.336000] PCI: Enabling device 0000:00:03.1 (0000 -> 0003)
[17179572.336000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179572.336000] NET: Registered protocol family 2
[17179572.372000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179572.372000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.372000] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.372000] TCP: Hash tables configured (established 8192 bind 4096)
[17179572.372000] TCP reno registered
[17179572.372000] audit: initializing netlink socket (disabled)
[17179572.372000] audit(1151776952.372:1): initialized
[17179572.372000] VFS: Disk quotas dquot_6.5.1
[17179572.372000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.372000] Initializing Cryptographic API
[17179572.372000] io scheduler noop registered
[17179572.372000] io scheduler anticipatory registered (default)
[17179572.372000] io scheduler deadline registered
[17179572.372000] io scheduler cfq registered
[17179572.372000] Limiting direct PCI/PCI transfers.
[17179572.372000] isapnp: Scanning for PnP cards...
[17179572.724000] isapnp: No Plug & Play device found
[17179572.780000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.780000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.780000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.780000] mice: PS/2 mouse device common for all mice
[17179572.784000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.784000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.784000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.784000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179572.792000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.792000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.792000] EISA: Probing bus 0 at eisa.0
[17179572.792000] Cannot allocate resource for EISA slot 1
[17179572.792000] EISA: Detected 0 cards.
[17179572.792000] TCP bic registered
[17179572.792000] NET: Registered protocol family 1
[17179572.792000] NET: Registered protocol family 8
[17179572.792000] NET: Registered protocol family 20
[17179572.792000] Using IPI Shortcut mode
[17179572.792000] ACPI wakeup devices: 
[17179572.792000]  LID PBTN PCI0 UAR1 USB0 MPCI 
[17179572.792000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.796000] Freeing unused kernel memory: 288k freed
[17179572.808000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.916000] vga16fb: initializing
[17179572.916000] vga16fb: mapped to 0xc00a0000
[17179573.032000] Console: switching to colour frame buffer device 80x25
[17179573.032000] fb0: VGA16 VGA frame buffer device
[17179574.112000] Capability LSM initialized
[17179574.188000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179574.212000] ACPI: Thermal Zone [THM] (62 C)
[17179575.224000] SCSI subsystem initialized
[17179575.236000] libata version 1.20 loaded.
[17179575.244000] ata_piix 0000:00:07.1: version 1.05-ac7
[17179575.244000] ata1: PATA max UDMA/33 cmd 0x1F0 ctl 0x3F6 bmdma 0x860 irq 14
[17179575.408000] ata1: dev 0 cfg 49:0f00 82:746b 83:49a8 84:4003 85:f469 86:0808 87:4003 88:043f
[17179575.408000] ata1: dev 0 ATA-5, max UDMA/100, 39070080 sectors: LBA
[17179575.416000] ata1: dev 0 configured for UDMA/33
[17179575.416000] scsi0 : ata_piix
[17179575.416000]   Vendor: ATA       Model: IC25N020ATDA04-0  Rev: DA3O
[17179575.416000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179575.416000] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x868 irq 15
[17179575.736000] ata2: dev 0 cfg 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179575.736000] ata2: dev 0 ATAPI, max UDMA/33
[17179575.900000] ata2: dev 0 configured for UDMA/33
[17179575.900000] scsi1 : ata_piix
[17179575.900000]   Vendor: LG        Model: CD-ROM CRN-8245B  Rev: 1.15
[17179575.900000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179575.960000] SCSI device sda: 39070080 512-byte hdwr sectors (20004 MB)
[17179575.960000] sda: Write Protect is off
[17179575.960000] sda: Mode Sense: 00 3a 00 00
[17179575.960000] SCSI device sda: drive cache: write back
[17179575.964000] SCSI device sda: 39070080 512-byte hdwr sectors (20004 MB)
[17179575.964000] sda: Write Protect is off
[17179575.964000] sda: Mode Sense: 00 3a 00 00
[17179575.964000] SCSI device sda: drive cache: write back
[17179575.964000]  sda: sda1 sda2 < sda5 >
[17179576.004000] sd 0:0:0:0: Attached scsi disk sda
[17179576.180000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179576.180000] ide0: ports already in use, skipping probe
[17179576.180000] ide1: I/O resource 0x170-0x177 not free.
[17179576.180000] ide1: ports already in use, skipping probe
[17179576.232000] usbcore: registered new driver usbfs
[17179576.232000] usbcore: registered new driver hub
[17179576.232000] USB Universal Host Controller Interface driver v3.0
[17179576.232000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.232000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179576.232000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179576.232000] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000dce0
[17179576.236000] usb usb1: configuration #1 chosen from 1 choice
[17179576.236000] hub 1-0:1.0: USB hub found
[17179576.236000] hub 1-0:1.0: 2 ports detected
[17179576.412000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179576.608000] Attempting manual resume
[17179576.688000] kjournald starting.  Commit interval 5 seconds
[17179576.688000] EXT3-fs: mounted filesystem with ordered data mode.
[17179599.388000] Floppy drive(s): fd0 is 1.44M
[17179599.404000] FDC 0 is a post-1991 82077
[17179599.460000] parport: PnPBIOS parport detected.
[17179599.460000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179599.476000] input: PC Speaker as /class/input/input1
[17179599.580000] ltmodem: module license 'Proprietary' taints kernel.
[17179599.584000] Loading Lucent Modem Controller driver version 8.26-alk-8
[17179599.588000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179599.588000] Detected Parameters Irq=11 BaseAddress=0xd400 ComAddress=0xdcd8
[17179599.588000] ttyLTM0 at I/O 0xd400 (irq = 11) is a Lucent/Agere Modem
[17179600.448000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179600.760000] Real Time Clock Driver v1.12ac
[17179600.844000] Linux agpgart interface v0.101 (c) Dave Jones
[17179600.888000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179601.472000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179601.472000] PCI: setting IRQ 5 as level-triggered
[17179601.472000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179601.780000] ts: Compaq touchscreen protocol output
[17179601.968000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179602.188000] agpgart: Detected an Intel 440BX Chipset.
[17179602.196000] agpgart: AGP aperture is 64M @ 0xf4000000
[17179602.196000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179602.196000] Yenta: CardBus bridge found at 0000:00:03.0 [1028:00b1]
[17179602.196000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179602.196000] Yenta: Routing CardBus interrupts to PCI
[17179602.196000] Yenta TI: socket 0000:00:03.0, mfunc 0x01261222, devctl 0x64
[17179602.428000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179602.428000] Socket status: 30000010
[17179602.428000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179602.428000] Yenta: CardBus bridge found at 0000:00:03.1 [1028:00b1]
[17179602.428000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179602.428000] Yenta: Routing CardBus interrupts to PCI
[17179602.428000] Yenta TI: socket 0000:00:03.1, mfunc 0x01261222, devctl 0x64
[17179602.596000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179602.604000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179602.632000] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[17179602.632000] Uniform CD-ROM driver Revision: 3.20
[17179602.632000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179602.660000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179602.660000] Socket status: 30000006
[17179602.672000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179603.064000] pccard: PCMCIA card inserted into slot 0
[17179603.388000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x207 0x370-0x37f
[17179603.388000] cs: IO port probe 0xc00-0xcf7: clean.
[17179603.388000] cs: IO port probe 0xa00-0xaff: clean.
[17179603.388000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x207 0x370-0x37f
[17179603.392000] cs: IO port probe 0xc00-0xcf7: clean.
[17179603.392000] cs: IO port probe 0xa00-0xaff: clean.
[17179603.392000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[17179603.400000] pcmcia: registering new device pcmcia0.0
[17179603.608000] 0.0: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[17179604.024000] lp0: using parport0 (interrupt-driven).
[17179604.328000] Adding 765944k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1 across:765944k
[17179604.468000] EXT3 FS on dm-0, internal journal
[17179604.844000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179604.844000] md: bitmap version 4.39
[17179613.260000] NET: Registered protocol family 17
[17179614.856000] ACPI: AC Adapter [AC] (on-line)
[17179615.200000] ACPI: Battery Slot [BAT0] (battery present)
[17179615.200000] ACPI: Battery Slot [BAT1] (battery absent)
[17179615.380000] ACPI: Lid Switch [LID]
[17179615.380000] ACPI: Power Button (CM) [PBTN]
[17179615.380000] ACPI: Sleep Button (CM) [SBTN]
[17179615.624000] ibm_acpi: ec object not found
[17179615.680000] pcc_acpi: loading...
[17179616.028000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179626.652000] ppdev: user-space parallel port driver
[17179633.716000] Dell Latitude C600 machine detected. Mousepad Resume Bug workaround hopefully not needed.
[17179633.716000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179633.716000] apm: overridden by ACPI.
[17179635.732000] Bluetooth: Core ver 2.8
[17179635.732000] NET: Registered protocol family 31
[17179635.732000] Bluetooth: HCI device and connection manager initialized
[17179635.732000] Bluetooth: HCI socket layer initialized
[17179636.496000] Bluetooth: L2CAP ver 2.8
[17179636.496000] Bluetooth: L2CAP socket layer initialized
[17179636.692000] Bluetooth: RFCOMM socket layer initialized
[17179636.692000] Bluetooth: RFCOMM TTY layer initialized
[17179636.692000] Bluetooth: RFCOMM ver 1.7
[17179652.452000] NET: Registered protocol family 10
[17179652.452000] lo: Disabled Privacy Extensions
[17179652.452000] IPv6 over IPv4 tunneling driver
[17179924.800000] pccard: card ejected from slot 0
[17179927.760000] pccard: PCMCIA card inserted into slot 0
[17179927.760000] pcmcia: registering new device pcmcia0.0
[17179930.356000] eth%d: MII link partner: 05e1
[17179930.356000] eth%d: MII selected
[17179930.380000] eth%d: media 100BaseT, silicon revision 5
[17179930.380000] eth0: Xircom: port 0x300, irq 3, hwaddr 00:10:A4:FF:59:F6
[17179930.380000] pcmcia: registering new device pcmcia0.1
[17179930.380000] 0.1: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[17179933.416000] eth0: MII link partner: 45e1
[17179933.416000] eth0: MII selected
[17179933.440000] eth0: media 100BaseT, silicon revision 5
[17179943.512000] eth0: no IPv6 routers present

```

the last 14 rows appear after I unplug/plug the card.

This the output of **lshw** before the unplug/plug operation:

```

elia
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.10
          size: 100MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f4000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f4000000-f7ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility M3 AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 02
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f8000000-fbffffff ioport:ec00-ecff iomemory:fdffc000-fdffffff irq:11
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 3
             bus info: pci@00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:28000000-28000fff irq:11
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 3.1
             bus info: pci@00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:28001000-28001fff irq:11
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix
             resources: ioport:860-86f
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:dce0-dcff irq:11
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1983S Maestro-3i PCI Audio Accelerator
             vendor: ESS Technology
             physical id: 8
             bus info: pci@00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Maestro3
             resources: ioport:d800-d8ff iomemory:f3ffe000-f3ffffff irq:5
        *-communication UNCLAIMED
             description: Communication controller
             product: WinModem 56k
             vendor: Agere Systems
             physical id: 10
             bus info: pci@00:10.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:f3ffdc00-f3ffdcff ioport:dcd8-dcdf ioport:d400-d4ff irq:11

```

and this after:

```

elia
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.10
          size: 100MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f4000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f4000000-f7ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility M3 AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 02
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f8000000-fbffffff ioport:ec00-ecff iomemory:fdffc000-fdffffff irq:11
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 3
             bus info: pci@00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:28000000-28000fff irq:11
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 3.1
             bus info: pci@00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:28001000-28001fff irq:11
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix
             resources: ioport:860-86f
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:dce0-dcff irq:11
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1983S Maestro-3i PCI Audio Accelerator
             vendor: ESS Technology
             physical id: 8
             bus info: pci@00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Maestro3
             resources: ioport:d800-d8ff iomemory:f3ffe000-f3ffffff irq:5
        *-communication UNCLAIMED
             description: Communication controller
             product: WinModem 56k
             vendor: Agere Systems
             physical id: 10
             bus info: pci@00:10.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:f3ffdc00-f3ffdcff ioport:dcd8-dcdf ioport:d400-d4ff irq:11
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:10:a4:ff:59:f6
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes

```

and this the output of **lspcmcia** before the unplug/plug:

```

Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:03.0)
Socket 0 Device 0:	[serial_cs]		(bus ID: 0.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:03.1)

```

andf this after:

```

Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:03.0)
Socket 0 Device 0:      [xirc2ps_cs]            (bus ID: 0.0)
Socket 0 Device 1:      [serial_cs]             (bus ID: 0.1)
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:03.1)

```

Sorry for the long detail list, but maybe somebody is able to find some hint in these lines.
Any idea is wellcome! Thanks



Elia

---

### Post by efreddi on 2006-07-02
I found a quick workaround:

[B]sudo pccardctl eject
sudo pccardctl insert[/B]

This make by software the same hardware hot unplug/plug and the card works correctly, but this is not the solution of the problem...

Stilll waiting for some suggestion, thanks!


Elia

---

### Post by efreddi on 2006-07-29
I found an automatic workaround. I prepared a script that is exectuted at the beginning, following the instruction I found on [http://www.fperkins.com/HowToCreateaStartupScriptinDebian.html]("http://www.fperkins.com/HowToCreateaStartupScriptinDebian.html"), in detail:

> 
This is what you do:
- Go to your **/etc/init.d** dir as root and copy the **reboot** script and use that as your base script.
- Put your code that you want to execute in the script and save it. Make sure to **chmod 755** it just in case
- Now in order for Debian to run it at boot up, you must update your run levels, so do **update-rc.d script name defaults 20**



This is the script:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          restart_pcmcia
# Short-Description: reset the pcmcia cards
# Description:
### END INIT INFO
#
#

pccardctl eject
pccardctl insert

```

At least now it works without any manual operation.
Ciao


Elia Freddi

---

