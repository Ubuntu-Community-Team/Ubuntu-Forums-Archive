---
title: "need help with linksys wusb54g v4"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by softwaregeeks on 2005-12-28
installed edubuntu 5.10 last night.  Tried installing linksys wusb54g v4 wireless adapter. I installed .inf file from serialmonkey site.  I have read the other threads and tried them.  Here is ndiswrapper -l info:
ndiswrapper -l
Installed ndis drivers:
rt2500usb       driver present, hardware present

It shows driver is installed. If I try to delete driver I get the following:

ndiswrapper -e rt2500usb.inf Driver rt2500usb.inf is not installed. Use -l to list installed drivers



$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

dmesg output

~$ dmesg
: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 10000000:eec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 1994.089 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.744000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294667.745000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294667.751000] Memory: 251012k/261588k available (1415k kernel code, 9940k reserved, 763k data, 224k init, 0k highmem)
[4294667.751000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.751000] Calibrating delay loop... 3948.54 BogoMIPS (lpj=1974272)
[4294667.773000] Security Framework v1.0.0 initialized
[4294667.773000] SELinux:  Disabled at boot.
[4294667.773000] Mount-cache hash table entries: 512
[4294667.773000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[4294667.773000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[4294667.773000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294667.773000] CPU: L2 cache: 512K
[4294667.773000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00000400 00000000 00000000
[4294667.773000] CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 07
[4294667.773000] Enabling fast FPU save and restore... done.
[4294667.773000] Enabling unmasked SIMD FPU exception support... done.
[4294667.773000] Checking 'hlt' instruction... OK.
[4294667.777000] Checking for popad bug... OK.
[4294667.777000] checking if image is initramfs... it is
[4294668.295000] Freeing initrd memory: 4822k freed
[4294668.302000] ACPI: Looking for DSDT in initrd... not found!
[4294668.367000]  not found!
[4294668.402000] ENABLING IO-APIC IRQs
[4294668.403000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.513000] NET: Registered protocol family 16
[4294668.513000] EISA bus registered
[4294668.513000] ACPI: bus type pci registered
[4294668.526000] PCI: PCI BIOS revision 2.10 entry at 0xfbe6d, last bus=2
[4294668.526000] PCI: Using configuration type 1
[4294668.526000] mtrr: v2.0 (20020519)
[4294668.527000] ACPI: Subsystem revision 20050729
[4294668.566000] ACPI: Interpreter enabled
[4294668.566000] ACPI: Using IOAPIC for interrupt routing
[4294668.570000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.570000] PCI: Probing PCI hardware (bus 00)
[4294668.570000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.570000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294668.584000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294668.584000] Boot video device is 0000:01:00.0
[4294668.585000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.622000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.630000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294668.649000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294668.650000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294668.651000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)[4294668.652000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)[4294668.653000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294668.653000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294668.654000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294668.655000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)[4294668.655000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.655000] pnp: PnP ACPI init
[4294668.685000] pnp: PnP ACPI: found 11 devices
[4294668.685000] PnPBIOS: Disabled by ACPI PNP
[4294668.685000] PCI: Using ACPI for IRQ routing
[4294668.685000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.701000] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[4294668.701000] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[4294668.701000] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[4294668.701000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[4294668.701000] Simple Boot Flag at 0x7a set to 0x1
[4294668.701000] audit: initializing netlink socket (disabled)
[4294668.701000] audit: initialized
[4294668.701000] VFS: Disk quotas dquot_6.5.1
[4294668.701000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.701000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.701000] devfs: boot_options: 0x0
[4294668.702000] Initializing Cryptographic API
[4294668.702000] isapnp: Scanning for PnP cards...
[4294669.055000] isapnp: No Plug & Play device found
[4294669.076000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294669.080000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.080000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.080000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.080000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.083000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.083000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294669.083000] io scheduler noop registered
[4294669.083000] io scheduler anticipatory registered
[4294669.083000] io scheduler deadline registered
[4294669.083000] io scheduler cfq registered
[4294669.084000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.084000] EISA: Probing bus 0 at eisa.0
[4294669.085000] EISA: Detected 0 cards.
[4294669.085000] NET: Registered protocol family 2
[4294669.094000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294669.094000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294669.094000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294669.094000] TCP: Hash tables configured (established 16384 bind 16384)
[4294669.094000] NET: Registered protocol family 8
[4294669.094000] NET: Registered protocol family 20
[4294669.094000] ACPI wakeup devices:
[4294669.094000] VBTN PCI0 USB0 USB1 USB2 PCI1  KBD
[4294669.094000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.095000] Freeing unused kernel memory: 224k freed
[4294669.111000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.116000] vga16fb: initializing
[4294669.116000] vga16fb: mapped to 0xc00a0000
[4294669.275000] Console: switching to colour frame buffer device 80x30
[4294669.275000] fb0: VGA16 VGA frame buffer device
[4294670.425000] Capability LSM initialized
[4294670.439000] NET: Registered protocol family 1
[4294670.457000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.457000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.457000] ACPI: bus type ide registered
[4294670.463000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294670.463000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294670.463000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294670.463000] ICH4: chipset revision 1
[4294670.463000] ICH4: not 100% native mode: will probe irqs later
[4294670.463000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294670.463000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[4294670.463000] Probing IDE interface ide0...
[4294670.727000] hda: ST380011A, ATA DISK drive
[4294671.339000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.339000] Probing IDE interface ide1...
[4294672.011000] hdc: Memorex 52MAXX 3252AJ, ATAPI CD/DVD-ROM drive
[4294672.623000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.623000] Probing IDE interface ide2...
[4294673.136000] Probing IDE interface ide3...
[4294673.648000] Probing IDE interface ide4...
[4294674.160000] Probing IDE interface ide5...
[4294674.676000] hda: max request size: 1024KiB
[4294674.677000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.677000] hda: cache flushes supported
[4294674.677000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294674.721000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294674.721000] Uniform CD-ROM driver Revision: 3.20
[4294675.057000] Attempting manual resume
[4294675.057000] swsusp: Suspend partition has wrong signature?
[4294675.086000] usbcore: registered new driver usbfs
[4294675.086000] usbcore: registered new driver hub
[4294675.087000] USB Universal Host Controller Interface driver v2.2
[4294675.087000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294675.087000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.087000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
[4294675.149000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.149000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[4294675.149000] hub 1-0:1.0: USB hub found
[4294675.149000] hub 1-0:1.0: 2 ports detected
[4294675.152000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294675.152000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.152000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
[4294675.214000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.214000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[4294675.214000] hub 2-0:1.0: USB hub found
[4294675.214000] hub 2-0:1.0: 2 ports detected
[4294675.217000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294675.217000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.217000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
[4294675.279000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.279000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[4294675.279000] hub 3-0:1.0: USB hub found
[4294675.279000] hub 3-0:1.0: 2 ports detected
[4294675.309000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[4294675.309000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.309000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
[4294675.309000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.309000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294675.309000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe300800
[4294675.313000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294675.313000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.313000] hub 4-0:1.0: USB hub found
[4294675.313000] hub 4-0:1.0: 6 ports detected
[4294675.404000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294675.404000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294675.404000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294675.427000] e100: eth0: e100_probe: addr 0xfe1fe000, irq 20, MAC addr 00:07:E9:B6:A8:EE
[4294675.515000] usb 4-1: new high speed USB device using ehci_hcd and address 2[4294677.929000] ACPI: CPU0 (power states: C1[C1])
[4294678.128000] Attempting manual resume
[4294678.152000] swsusp: Suspend partition has wrong signature?
[4294678.162000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294678.162000] EXT3-fs: write access will be enabled during recovery.
[4294682.856000] kjournald starting.  Commit interval 5 seconds
[4294682.856000] EXT3-fs: recovery complete.
[4294682.856000] EXT3-fs: mounted filesystem with ordered data mode.
[4294683.869000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.523000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1
[4294687.814000] EXT3 FS on hda1, internal journal
[4294693.166000] parport: PnPBIOS parport detected.
[4294693.166000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294693.254000] lp0: using parport0 (interrupt-driven).
[4294693.284000] mice: PS/2 mouse device common for all mice
[4294693.617000] input: PS/2 Generic Mouse on isa0060/serio1
[4294693.918000] ts: Compaq touchscreen protocol output
[4294696.864000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294697.666000] cdrom: open failed.
[4294700.307000] Linux agpgart interface v0.101 (c) Dave Jones
[4294700.318000] agpgart: Detected an Intel 845G Chipset.
[4294700.346000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294700.462000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294700.469000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294700.469000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294700.825000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294700.825000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294700.921000] hw_random hardware driver 1.0.0 loaded
[4294701.476000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294701.476000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294701.785000] intel8x0_measure_ac97_clock: measured 49022 usecs
[4294701.785000] intel8x0: clocking to 48000
[4294704.002000] input: PC Speaker
[4294704.056000] Real Time Clock Driver v1.12
[4294704.113000] Floppy drive(s): fd0 is 1.44M
[4294704.144000] FDC 0 is a post-1991 82077
[4294705.309000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294705.321000] NET: Registered protocol family 17
[4294711.067000] NET: Registered protocol family 10
[4294711.067000] Disabled Privacy Extensions on device c02eb280(lo)
[4294711.068000] IPv6 over IPv4 tunneling driver
[4294712.757000] ACPI: Power Button (FF) [PWRF]
[4294712.757000] ACPI: Power Button (CM) [VBTN]
[4294712.893000] ibm_acpi: ec object not found
[4294721.221000] eth0: no IPv6 routers present
[4294722.621000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294722.621000] apm: overridden by ACPI.
[4294722.870000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[4294740.677000] Bluetooth: Core ver 2.7
[4294740.677000] NET: Registered protocol family 31
[4294740.677000] Bluetooth: HCI device and connection manager initialized
[4294740.677000] Bluetooth: HCI socket layer initialized
[4294740.815000] Bluetooth: L2CAP ver 2.7
[4294740.815000] Bluetooth: L2CAP socket layer initialized
[4294740.875000] Bluetooth: RFCOMM ver 1.5
[4294740.875000] Bluetooth: RFCOMM socket layer initialized
[4294740.875000] Bluetooth: RFCOMM TTY layer initialized

---

### Post by Lambert on 2005-12-29
I see one other thread dealing with a v4. You may want to read through this as there was success in that thread.

[http://ubuntuforums.org/showthread.php?t=98299](http://ubuntuforums.org/showthread.php?t=98299)

Their success came from updating to the latest ndiswrapper. See this thread for doing that.

[http://ubuntuforums.org/showthread.php?t=104539&highlight=NDISWRAPPER](http://ubuntuforums.org/showthread.php?t=104539&highlight=NDISWRAPPER)

as far as your ndiswrapper -e command. don't use the .inf at the end. Just enter it exactly as the driver name prints out with the ndiswrapper -l command.

sudo ndiswrapper -e rt2500usb

One last thought. You can consider using the native driver for this chipset to see if you can get it to work.

[http://ubuntuforums.org/showthread.php?t=106846](http://ubuntuforums.org/showthread.php?t=106846)

---

### Post by jnorth on 2006-01-01
I had success with the rt2x00 drivers from [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) for this card.  Forget ndiswrapper- it caused so many issues for me so I just gave up on it, I can life with some of the monitoring glitches in the rt2570 driver.  
Just download [this one]("http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b1.tar.gz?download"), make sure you have your kernel-headers and development tools installed, and run these commands:
```
tar -zxf rt2570-1.1.0-b1.tar.gz
cd rt2570-1.1.0-b1/Module/
make
sudo make install
```
The only errors you should get will have to do with making the file modprobe.conf - Debian/Ubuntu does things a little different so we have to change 2 things and reload the module to fix it, and then you'll be set.
1.  Move/rename the modprobe.conf (it should only have one line saying 'alias rausb0 rt2570') to the appropriate location:
```
sudo mv /etc/modprobe.conf /etc/modutils/rt2570
```
2.  Move the driver file to the appropriate location: (replacing the x's with your uname info, the driver will be in the general directory but(on my system) would not be found correctly until moved to the specific directory.  I could be stupid though :)
```
sudo mv /lib/modules/2.6.xx/extra/rt2570.ko /lib/modules/2.6.xx-xx-xxx/kernel/drivers/net/wireless/rt2570.ko
```
3.  Update modprobe and reload:
```
sudo depmod -a
sudo update-modules
sudo modprobe rt2570
```
Good luck!  I had this working on Debian sid before I switched to Ubuntu for my desktop and found most of this on various boards.  Hope it works for you!

---

### Post by Lambert on 2006-01-01
Hey jnorth, welcome to ubuntu. My second link in my post is howto install rt2570 but I don't have a device to test that howto on. Your post suggest others steps are needed. Would you mind posting in that thread what you did for others to use if they decide to use the rt2570 driver?

---

### Post by wondering_jew on 2006-01-05
Wow I followed those few steps and it worked perfectly.... from other posts from other threads I thought I was taking on an impossible task setting the wifi up :) thanks a lot!

---

### Post by jnorth on 2006-01-08
wondering:  no problem - glad it helped out :)  I struggled with that stupid thing for about a week working with ndiswrapper, etc before getting the rt2570 driver to work on Debian.  Then I switched over to Ubuntu (actually Kubuntu - I hate Gnome) and works great here too.

Lambert:  thanks for the welcome!  Didn't mean to sort of hijack your answer, I just get excited sometimes when I find a question that I can answer - makes me think I'm smart or something :)  I'm copying that bit over to the thread you posted now.

---

### Post by EricD on 2006-01-18
jnorth, I tried your instructions and I keep getting errors on make because I don't have gcc 3.4 installed? how do I go about installing gcc 3.4?

---

### Post by jnorth on 2006-01-23
[QUOTE=EricD]jnorth, I tried your instructions and I keep getting errors on make because I don't have gcc 3.4 installed? how do I go about installing gcc 3.4?[/QUOTE]

EricD, - sorry for not getting back sooner - I've been rebuilding my home box and swapped out for a 64bit proc this week so I've been up and down playing with that.

For gcc3.4 - you will need to add I believe at least the universe sources in your apt sources list.  I'm going to assume you're using a gui in gnome(probably synaptic) to do this.  Go to the menu, package sources, and enable the lines that have the multiverse/universe source.  You should then be able to do a search for gcc 3.4 and install from there.

I apologize for the sketchy instructions but I'm not in front of my Ubuntu box right now.

---

### Post by roxas232 on 2007-04-01
hey i was wondering what you would need to compile this in ubuntu 6.10 because every time i try to make rt2570 compile i just get a lot of errors. Thanks.

---

### Post by jnorth on 2007-04-01
> **roxas232 said:**
> hey i was wondering what you would need to compile this in ubuntu 6.10 because every time i try to make rt2570 compile i just get a lot of errors. Thanks.

Such as?  You'll find that in most forums you'll need to post some sort of details on what's wrong for other's to be able to help :)

Attach a copy of your console text from the make and make install commands and maybe someone will see something wrong with it.

---

