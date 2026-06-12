---
title: "Help with Ethernet on new Dell"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by 94west on 2006-02-09
I just got a Dell Dual Core with built in Ethernet that Ubuntu doesn't seem to like.

```
lspci | grep Eth
Ethernet Controller: Intel Corp.:Unknown device 109a (rev01)
```

also ```
sudo mii-tool eth0
``` gives me ```
"device not found"
```

So how do I make this work? Or am I screwed? The installer claimed there were no network interfaces at all. I also have a Dell USB Wifi adaptor, but i didn't figure I would even try to go there in linux.

Any help offered is much appreciated. Also, I am pretty new to linux, so be gentle. :-)

---

### Post by mips on 2006-02-09
Look for the device in the output of dmesg and post it hear.

---

### Post by 94west on 2006-02-10
Sorry to be a newb, but can you tell me more explicitly where to find the output of dmesg? Is that an application I need to run? I only have command line access as I need to work on the drivers for the xserver next, after I get ethernet running.

thanks
jack

---

### Post by mips on 2006-02-10
just type in **dmesg** followed by the enter/return key....

---

### Post by 94west on 2006-02-10
Ok, thanks .... I have paged through the output 3 times and I don't see anything that looks like its referring to Ethernet cards anywhere. I see some references to TCP, hard disks, USB ports, etc. ... but nothing about ethernet, MAC address, NICs etc.

---

### Post by cwaldbieser on 2006-02-10
[QUOTE=94west]Ok, thanks .... I have paged through the output 3 times and I don't see anything that looks like its referring to Ethernet cards anywhere. I see some references to TCP, hard disks, USB ports, etc. ... but nothing about ethernet, MAC address, NICs etc.[/QUOTE]
Do you know the type or model of the NIC?  Sometimes the manufacturer has something useful on their web site.

---

### Post by mips on 2006-02-11
[QUOTE=94west]Ok, thanks .... I have paged through the output 3 times and I don't see anything that looks like its referring to Ethernet cards anywhere. I see some references to TCP, hard disks, USB ports, etc. ... but nothing about ethernet, MAC address, NICs etc.[/QUOTE]

Could you copy the output to a file and attach it here ?

---

### Post by 94west on 2006-02-11
Thanks for your help, mips. I am trying to find out from Dell what the specifics are for the NIC.  They don't provide much detail in the info I can find. Also, I don't know how I can get the entire output off of that computer since I can't get it on the network and don't have a floppy drive. I'll see if I can direct the output to a file and then access it from the Windows side of the computer.

---

### Post by 94west on 2006-02-11
OK from Dell, its' a "Intel PRO/1000PL Network Connection"

I also have a "dell wireless 1450 dual-band usb 2.0 adapter" if that is easier to get working.

---

### Post by 94west on 2006-02-11
```
[4294669.227000] pnp: 00:00: ioport range 0x800-0x85f could not be reserved
[4294669.227000] pnp: 00:00: ioport range 0xc00-0xc7f has been reserved
[4294669.227000] pnp: 00:00: ioport range 0x860-0x8ff has been reserved
[4294669.227000] pnp: 00:06: ioport range 0x100-0x1fe has been reserved
[4294669.227000] pnp: 00:06: ioport range 0x200-0x277 has been reserved
[4294669.227000] pnp: 00:06: ioport range 0x280-0x2e7 has been reserved
[4294669.227000] pnp: 00:06: ioport range 0x2e8-0x2ef has been reserved
[4294669.227000] pnp: 00:06: ioport range 0x2f0-0x2f7 has been reserved
[4294669.227000] pnp: 00:06: ioport range 0x2f8-0x2ff has been reserved
[4294669.227000] pnp: 00:06: ioport range 0x300-0x377 has been reserved
[4294669.227000] pnp: 00:06: ioport range 0x380-0x3bb has been reserved
[4294669.227000] Simple Boot Flag at 0x7a set to 0x1
[4294669.228000] audit: initializing netlink socket (disabled)
[4294669.228000] audit: initialized
[4294669.228000] highmem bounce pool size: 64 pages
[4294669.228000] VFS: Disk quotas dquot_6.5.1
[4294669.228000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.228000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.228000] devfs: boot_options: 0x0
[4294669.228000] Initializing Cryptographic API
[4294669.228000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294669.228000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294669.228000] assign_interrupt_mode Found MSI capability
[4294669.228000] Allocate Port Service[pcie00]
[4294669.228000] Allocate Port Service[pcie03]
[4294669.228000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294669.228000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294669.228000] assign_interrupt_mode Found MSI capability
[4294669.228000] Allocate Port Service[pcie00]
[4294669.228000] Allocate Port Service[pcie02]
[4294669.228000] Allocate Port Service[pcie03]
[4294669.228000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[4294669.228000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[4294669.228000] assign_interrupt_mode Found MSI capability
[4294669.228000] Allocate Port Service[pcie00]
[4294669.228000] Allocate Port Service[pcie02]
[4294669.228000] Allocate Port Service[pcie03]
[4294669.228000] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294669.228000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[4294669.228000] assign_interrupt_mode Found MSI capability
[4294669.228000] Allocate Port Service[pcie00]
[4294669.228000] Allocate Port Service[pcie02]
[4294669.228000] Allocate Port Service[pcie03]
[4294669.228000] isapnp: Scanning for PnP cards...
[4294669.583000] isapnp: No Plug & Play device found
[4294669.601000] PNP: No PS/2 controller found. Probing ports directly.
[4294669.608000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.608000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.608000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.610000] io scheduler noop registered
[4294669.610000] io scheduler anticipatory registered
[4294669.610000] io scheduler deadline registered
[4294669.610000] io scheduler cfq registered
[4294669.611000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.636000] EISA: Probing bus 0 at eisa.0
[4294669.636000] Cannot allocate resource for EISA slot 2
[4294669.636000] Cannot allocate resource for EISA slot 5
[4294669.636000] Cannot allocate resource for EISA slot 6
[4294669.636000] EISA: Detected 0 cards.
[4294669.637000] NET: Registered protocol family 2
[4294669.646000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294669.646000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294669.646000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.646000] TCP: Hash tables configured (established 131072 bind 65536)
[4294669.646000] NET: Registered protocol family 8
[4294669.646000] NET: Registered protocol family 20
[4294669.646000] ACPI wakeup devices: 
[4294669.646000] VBTN PCI0 PCI4 PCI2 PCI3 PCI1 PCI5 PCI6 USB0 USB1 USB2 USB3 
[4294669.646000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.647000] Freeing unused kernel memory: 224k freed
[4294669.662000] vga16fb: initializing
[4294669.662000] vga16fb: mapped to 0xc00a0000
[4294669.786000] Console: switching to colour frame buffer device 80x30
[4294669.786000] fb0: VGA16 VGA frame buffer device
[4294670.929000] Capability LSM initialized
[4294670.940000] NET: Registered protocol family 1
[4294670.956000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.956000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.956000] ACPI: bus type ide registered
[4294670.961000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[4294670.961000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[4294670.961000] ICH7: chipset revision 1
[4294670.961000] ICH7: not 100% native mode: will probe irqs later
[4294670.961000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[4294670.961000] Probing IDE interface ide0...
[4294671.633000] hda: SONY DVD-ROM DDU1615, ATAPI CD/DVD-ROM drive
[4294672.347000] hdb: SONY CD-RW CRX217E, ATAPI CD/DVD-ROM drive
[4294672.398000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.398000] Probing IDE interface ide1...
[4294672.911000] Probing IDE interface ide2...
[4294673.423000] Probing IDE interface ide3...
[4294673.935000] Probing IDE interface ide4...
[4294674.447000] Probing IDE interface ide5...
[4294674.963000] hda: ATAPI 48X DVD-ROM drive, 254kB Cache
[4294674.963000] Uniform CD-ROM driver Revision: 3.20
[4294674.965000] hdb: ATAPI 48X CD-ROM CD-R/RW drive, 1536kB Cache
[4294675.360000] usbcore: registered new driver usbfs
[4294675.360000] usbcore: registered new driver hub
[4294675.360000] USB Universal Host Controller Interface driver v2.2
[4294675.360000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294675.360000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.360000] uhci_hcd 0000:00:1d.0: Intel Corporation I/O Controller Hub UHCI USB #1
[4294675.422000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.422000] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[4294675.422000] hub 1-0:1.0: USB hub found
[4294675.422000] hub 1-0:1.0: 2 ports detected
[4294675.425000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 22
[4294675.425000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.425000] uhci_hcd 0000:00:1d.1: Intel Corporation I/O Controller Hub UHCI USB #2
[4294675.487000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.487000] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[4294675.487000] hub 2-0:1.0: USB hub found
[4294675.487000] hub 2-0:1.0: 2 ports detected
[4294675.490000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294675.490000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.490000] uhci_hcd 0000:00:1d.2: Intel Corporation I/O Controller Hub UHCI USB #3
[4294675.552000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.552000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[4294675.552000] hub 3-0:1.0: USB hub found
[4294675.552000] hub 3-0:1.0: 2 ports detected
[4294675.555000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
[4294675.555000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294675.555000] uhci_hcd 0000:00:1d.3: Intel Corporation I/O Controller Hub UHCI USB #4
[4294675.617000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294675.617000] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[4294675.617000] hub 4-0:1.0: USB hub found
[4294675.617000] hub 4-0:1.0: 2 ports detected
[4294675.646000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 21
[4294675.646000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.646000] ehci_hcd 0000:00:1d.7: Intel Corporation I/O Controller Hub EHCI USB
[4294675.646000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.657000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294675.657000] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[4294675.660000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294675.660000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.661000] hub 5-0:1.0: USB hub found
[4294675.661000] hub 5-0:1.0: 8 ports detected
[4294675.709000] SCSI subsystem initialized
[4294675.710000] libata version 1.11 loaded.
[4294675.711000] ahci version 1.00
[4294675.711000] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 20
[4294675.849000] usb 5-4: new high speed USB device using ehci_hcd and address 2
[4294675.923000] hub 5-4:1.0: USB hub found
[4294675.923000] hub 5-4:1.0: 2 ports detected
[4294676.191000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[4294676.626000] usb 5-4.1: new high speed USB device using ehci_hcd and address 4
[4294676.671000] hub 5-4.1:1.0: USB hub found
[4294676.671000] hub 5-4.1:1.0: 4 ports detected
[4294676.910000] usb 5-4.2: new high speed USB device using ehci_hcd and address 5
[4294677.175000] usb 5-4.1.1: new low speed USB device using ehci_hcd and address 6
[4294677.366000] usb 5-4.1.2: new low speed USB device using ehci_hcd and address 7
[4294680.023000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294680.023000] ahci(0000:00:1f.2) AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[4294680.023000] ahci(0000:00:1f.2) flags: 64bit ncq pm led clo pio slum part 
[4294680.023000] ata1: SATA max UDMA/133 cmd 0xF887ED00 ctl 0x0 bmdma 0x0 irq 20
[4294680.023000] ata2: SATA max UDMA/133 cmd 0xF887ED80 ctl 0x0 bmdma 0x0 irq 20
[4294680.023000] ata3: SATA max UDMA/133 cmd 0xF887EE00 ctl 0x0 bmdma 0x0 irq 20
[4294680.023000] ata4: SATA max UDMA/133 cmd 0xF887EE80 ctl 0x0 bmdma 0x0 irq 20
[4294680.224000] ata1: dev 0 cfg 49:2f00 82:746b 83:7f01 84:4023 85:7469 86:3e01 87:4023 88:207f
[4294680.224000] ata1: dev 0 ATA, max UDMA/133, 312500000 sectors: lba48
[4294680.224000] ata1: dev 0 configured for UDMA/133
[4294680.224000] scsi0 : ahci
[4294680.426000] ata2: no device found (phy stat 00000000)
[4294680.426000] scsi1 : ahci
[4294680.627000] ata3: no device found (phy stat 00000000)
[4294680.627000] scsi2 : ahci
[4294680.828000] ata4: no device found (phy stat 00000000)
[4294680.828000] scsi3 : ahci
[4294680.828000]   Vendor: ATA       Model: WDC WD1600JS-75N  Rev: 10.0
[4294680.828000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294682.896000] usbcore: registered new driver hiddev
[4294682.899000] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.7-4.1.1
[4294682.902000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.7-4.1.2
[4294682.902000] usbcore: registered new driver usbhid
[4294682.902000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294682.923000] Initializing USB Mass Storage driver...
[4294682.929000] scsi4 : SCSI emulation for USB Mass Storage devices
[4294682.929000] usb-storage: device found at 5
[4294682.929000] usb-storage: waiting for device to settle before scanning
[4294682.929000] usbcore: registered new driver usb-storage
[4294682.929000] USB Mass Storage support registered.
[4294682.949000] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[4294682.949000] SCSI device sda: drive cache: write back
[4294682.949000] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[4294682.949000] SCSI device sda: drive cache: write back
[4294682.949000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 >
[4294683.003000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294683.679000] ACPI: CPU0 (power states: C1[C1])
[4294683.938000] Attempting manual resume
[4294683.938000] swsusp: Suspend partition has wrong signature?
[4294683.947000] kjournald starting.  Commit interval 5 seconds
[4294683.947000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.753000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.932000]   Vendor: SMSC      Model: 223 U HS-CF       Rev: 3.60
[4294687.932000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294687.943000] Attached scsi removable disk sdb at scsi4, channel 0, id 0, lun 0
[4294687.947000]   Vendor: SMSC      Model: 223 U HS-MS       Rev: 3.60
[4294687.947000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294687.958000] Attached scsi removable disk sdc at scsi4, channel 0, id 0, lun 1
[4294687.984000]   Vendor: SMSC      Model: 223 U HS-SM       Rev: 3.60
[4294687.984000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294687.995000] Attached scsi removable disk sdd at scsi4, channel 0, id 0, lun 2
[4294687.999000]   Vendor: SMSC      Model: 223 U HS-SD/MMC   Rev: 3.60
[4294687.999000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294688.056000] Attached scsi removable disk sde at scsi4, channel 0, id 0, lun 3
[4294688.057000] usb-storage: device scan complete
[4294688.079000] Adding 867468k swap on /dev/sda6.  Priority:-1 extents:1
[4294688.327000] EXT3 FS on sda5, internal journal
[4294690.226000] lp: driver loaded but no devices found
[4294690.302000] mice: PS/2 mouse device common for all mice
[4294694.361000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294695.081000] cdrom: open failed.
[4294695.084000] cdrom: open failed.
[4294697.125000] Linux agpgart interface v0.101 (c) Dave Jones
[4294697.132000] agpgart: Detected an Intel 945G Chipset.
[4294697.163000] agpgart: AGP aperture is 256M @ 0x0
[4294697.259000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294697.363000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294697.363000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294697.953000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294697.953000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294698.577000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294698.577000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294698.658000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294698.658000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294698.749000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294698.749000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294699.063000] hw_random hardware driver 1.0.0 loaded
[4294701.211000] input: PC Speaker
[4294701.249000] Real Time Clock Driver v1.12
[4294701.435000] ts: Compaq touchscreen protocol output
[4294708.472000] ACPI: Power Button (FF) [PWRF]
[4294708.472000] ACPI: Power Button (CM) [VBTN]
[4294708.578000] ibm_acpi: ec object not found
[4294714.640000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294714.640000] apm: overridden by ACPI.
[4294715.233000] Bluetooth: Core ver 2.7
[4294715.233000] NET: Registered protocol family 31
[4294715.233000] Bluetooth: HCI device and connection manager initialized
[4294715.233000] Bluetooth: HCI socket layer initialized
[4294715.245000] Bluetooth: L2CAP ver 2.7
[4294715.245000] Bluetooth: L2CAP socket layer initialized
[4294715.267000] Bluetooth: RFCOMM ver 1.5
[4294715.267000] Bluetooth: RFCOMM socket layer initialized
[4294715.267000] Bluetooth: RFCOMM TTY layer initialized

```

---

### Post by mips on 2006-02-11
**What does the output from lspci look like ?**

What happens if you boot with the apci=off or apic=off options ?

I suspect that card might not have support for it in the kernel and you would have to compile your own but I could be wrong.

Do you not have spare ethernet card lying around you can plug in, connect to the network and get a updated kernel ?

Alternatively you can search this forum on how to get your wireless working, sorry i'm not to clued up in that area.

[http://www.ubuntuforums.org/showthread.php?t=102793](http://www.ubuntuforums.org/showthread.php?t=102793)
[http://www.ubuntuforums.org/showthread.php?t=102083](http://www.ubuntuforums.org/showthread.php?t=102083)
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2198&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2198&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng)
[http://support.intel.com/support/network/sb/cs-012904.htm](http://support.intel.com/support/network/sb/cs-012904.htm)
[http://support.intel.com/support/network/sb/CS-009209.htm](http://support.intel.com/support/network/sb/CS-009209.htm)

---

### Post by mips on 2006-02-13
From a terminal try **sudo modprobe e1000** and see what happens.

---

