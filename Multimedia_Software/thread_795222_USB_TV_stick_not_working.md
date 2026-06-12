---
title: "USB TV stick not working"
date: 2008-05-15
forum: Multimedia Software
---

### Post by njean on 2008-05-15
Hello,

I'm trying to install Terratec Cinergy Hybrid XS on Xubuntu, last version.

I followed a guide, I compiled v4l-dvb-kernel and extracted firmware (from this link: [http://konstantin.filtschew.de/v4l-firmware/](http://konstantin.filtschew.de/v4l-firmware/))

I extracted such firmware to /lib/firmware (I tried all versions), did a sudo modprobe em28xx and tried using the stick with Kaffeine. It doesn't work.

Here's my lsusb output:

```
crivill@pc-telecamera:/lib/firmware/2.6.24-16-generic$ lsusb
Bus 005 Device 002: ID 0ccd:0042 TerraTec Electronic GmbH
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

And my dmesg output:

```
[   20.595147] ehci_hcd 0000:02:03.2: new USB bus registered, assigned bus number 5
[   20.595235] ehci_hcd 0000:02:03.2: irq 20, io mem 0xe9001000
[   20.610697] ehci_hcd 0000:02:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.610990] usb usb5: configuration #1 chosen from 1 choice
[   20.611042] hub 5-0:1.0: USB hub found
[   20.611056] hub 5-0:1.0: 4 ports detected
[   20.687399] SCSI subsystem initialized
[   20.810467] libata version 3.00 loaded.
[   20.838541] ata_piix 0000:00:1f.1: version 2.12
[   20.838695] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   20.849077] scsi0 : ata_piix
[   20.874417] scsi1 : ata_piix
[   20.875548] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   20.875554] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   20.970332] Floppy drive(s): fd0 is 1.44M
[   20.990014] FDC 0 is a post-1991 82077
[   21.186620] ata1.00: ATAPI: HL-DT-ST RW/DVD GCC-4481B, 1.16, max UDMA/44
[   21.242563] usb 5-4: new high speed USB device using ehci_hcd and address 2
[   21.350022] ata1.00: configured for UDMA/44
[   21.383109] usb 5-4: configuration #1 chosen from 1 choice
[   21.514732] ata2.00: ATA-5: WDC WD200BB-75CLB0, 05.04E05, max UDMA/100
[   21.514741] ata2.00: 39102336 sectors, multi 16: LBA
[   21.530708] ata2.00: configured for UDMA/100
[   21.531524] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4481B 1.16 PQ: 0 ANSI: 5
[   21.531897] scsi 1:0:0:0: Direct-Access     ATA      WDC WD200BB-75CL 05.0 PQ: 0 ANSI: 5
[   22.885052] Driver 'sr' needs updating - please use bus_type methods
[   22.893464] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   22.893478] Uniform CD-ROM driver Revision: 3.20
[   22.893598] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   22.896040] Driver 'sd' needs updating - please use bus_type methods
[   22.907483] sd 1:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   22.907517] sd 1:0:0:0: [sda] Write Protect is off
[   22.907522] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.907564] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.907707] sd 1:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   22.907731] sd 1:0:0:0: [sda] Write Protect is off
[   22.907735] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.907774] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.907788]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   22.909615] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   22.932293]  sda1 sda2 < sda5 >
[   22.958170] sd 1:0:0:0: [sda] Attached SCSI disk
[   23.352806] Attempting manual resume
[   23.352816] swsusp: Resume From Partition 8:5
[   23.352819] PM: Checking swsusp image.
[   23.353162] PM: Resume from disk failed.
[   23.428985] kjournald starting.  Commit interval 5 seconds
[   23.429027] EXT3-fs: mounted filesystem with ordered data mode.
[   33.526262] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.580903] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.650015] iTCO_vendor_support: vendor-support=0
[   33.710651] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.711840] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   33.711900] iTCO_wdt: No card detected
[   34.030467] intel_rng: FWH not detected
[   34.317372] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   34.516993] input: Power Button (FF) as /devices/virtual/input/input3
[   34.528518] ACPI: Power Button (FF) [PWRF]
[   34.528785] input: Power Button (CM) as /devices/virtual/input/input4
[   34.540487] ACPI: Power Button (CM) [PWRB]
[   34.540795] input: Sleep Button (CM) as /devices/virtual/input/input5
[   34.552486] ACPI: Sleep Button (CM) [SLPB]
[   36.430047] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   38.336526] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 16
[   38.336565] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   38.657930] intel8x0_measure_ac97_clock: measured 54902 usecs
[   38.657943] intel8x0: clocking to 48000
[   39.057360] Linux agpgart interface v0.102
[   39.206491] parport_pc 00:0a: reported by Plug and Play ACPI
[   39.206574] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.100078] usbcore: registered new interface driver snd-usb-audio
[   43.863699] lp0: using parport0 (interrupt-driven).
[   43.991538] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[   44.612861] EXT3 FS on sda1, internal journal
[   46.320318] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.179833] No dock devices found.
[   49.361253] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   49.361266] apm: overridden by ACPI.
[   49.536426] ppdev: user-space parallel port driver
[   49.710610] audit(1210859882.044:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4777 profile="/usr/sbin/cupsd" namespace="default"
[   51.310388] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   51.430227] Bluetooth: Core ver 2.11
[   51.432511] NET: Registered protocol family 31
[   51.432522] Bluetooth: HCI device and connection manager initialized
[   51.432531] Bluetooth: HCI socket layer initialized
[   51.517797] Bluetooth: L2CAP ver 2.9
[   51.517807] Bluetooth: L2CAP socket layer initialized
[   51.666258] Bluetooth: RFCOMM socket layer initialized
[   51.667520] Bluetooth: RFCOMM TTY layer initialized
[   51.667532] Bluetooth: RFCOMM ver 1.8
[   54.688398] NET: Registered protocol family 17
[   57.473298] NET: Registered protocol family 10
[   57.475084] lo: Disabled Privacy Extensions
[   68.094956] eth0: no IPv6 routers present
[ 2024.971979] Linux video capture interface: v2.00
[ 2025.078107] em28xx v4l2 driver version 0.0.1 loaded
[ 2025.078228] em28xx new video device (0ccd:0042): interface 0, class 255
[ 2025.078238] em28xx: device is attached to a USB 2.0 bus
[ 2025.078241] em28xx: you're using the experimental/unstable tree from mcentral.de
[ 2025.078245] em28xx: there's also a stable tree available but which is limited to
[ 2025.078248] em28xx: linux <=2.6.19.2
[ 2025.078251] em28xx: it's fine to use this driver but keep in mind that it will move
[ 2025.078254] em28xx: to http://mcentral.de/hg/~mrec/v4l-dvb-kernel as soon as it's
[ 2025.078258] em28xx: proved to be stable
[ 2025.078263] em28xx #0: Alternate settings: 8
[ 2025.078267] em28xx #0: Alternate setting 0, max size= 0
[ 2025.078270] em28xx #0: Alternate setting 1, max size= 0
[ 2025.078274] em28xx #0: Alternate setting 2, max size= 1448
[ 2025.078277] em28xx #0: Alternate setting 3, max size= 2048
[ 2025.078281] em28xx #0: Alternate setting 4, max size= 2304
[ 2025.078284] em28xx #0: Alternate setting 5, max size= 2580
[ 2025.078287] em28xx #0: Alternate setting 6, max size= 2892
[ 2025.078291] em28xx #0: Alternate setting 7, max size= 3072
[ 2025.266386] input: em2880/em2870 remote control as /devices/virtual/input/input7
[ 2025.294319] em28xx-input.c: remote control handler attached
[ 2025.295462] attach_inform: eeprom detected.
[ 2025.324515] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 42 00 50 12 5c 03 6a 32 9c 34
[ 2025.324542] em28xx #0: i2c eeprom 10: 00 00 06 57 46 07 00 00 00 00 00 00 00 00 00 00
[ 2025.324558] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 31 00 b8 00 14 00 5b 00 00 00
[ 2025.324575] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00
[ 2025.324591] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2025.324607] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2025.324622] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 32 03 43 00 69 00
[ 2025.324638] em28xx #0: i2c eeprom 70: 6e 00 65 00 72 00 67 00 79 00 20 00 48 00 79 00
[ 2025.324654] em28xx #0: i2c eeprom 80: 62 00 72 00 69 00 64 00 20 00 54 00 20 00 55 00
[ 2025.324671] em28xx #0: i2c eeprom 90: 53 00 42 00 20 00 58 00 53 00 00 00 34 03 54 00
[ 2025.324687] em28xx #0: i2c eeprom a0: 65 00 72 00 72 00 61 00 54 00 65 00 63 00 20 00
[ 2025.324703] em28xx #0: i2c eeprom b0: 45 00 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00
[ 2025.324720] em28xx #0: i2c eeprom c0: 69 00 63 00 20 00 47 00 6d 00 62 00 48 00 00 00
[ 2025.324736] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2025.324751] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2025.324767] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2025.324782] EEPROM ID= 0x9567eb1a
[ 2025.324785] Vendor/Product ID= 0ccd:0042
[ 2025.324788] AC97 audio (5 sample rates)
[ 2025.324791] 500mA max power
[ 2025.324794] Table at 0x06, strings=0x326a, 0x349c, 0x0000
[ 2025.327650] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[ 2025.327738] attach inform (default): detected I2C address c2
[ 2025.327749] /home/crivill/v4l-dvb-kernel/v4l/tuner-core.c: setting tuner callback
[ 2025.327753] tuner 0x61: Configuration acknowledged
[ 2025.327757] /home/crivill/v4l-dvb-kernel/v4l/tuner-core.c: setting tuner callback
[ 2025.327923] /home/crivill/v4l-dvb-kernel/v4l/xc3028-tuner.c: attach request!
[ 2025.327929] /home/crivill/v4l-dvb-kernel/v4l/tuner-core.c: xc3028 tuner successfully loaded
[ 2025.334573] attach_inform: tvp5150 detected.
[ 2025.398548] tvp5150 0-005c: tvp5150am1 detected.
[ 2025.500047] Loading base firmware: xc3028_init0.i2c.fw
[ 2025.556554] xc3028-tuner.c: Unable to load firmware
[ 2025.556563] xc3028-tuner.c: ** PLEASE HAVE A LOOK AT **
[ 2025.556567] xc3028-tuner.c: http://linuxtv.org/v4lwiki/index.php/Talk:Em2880#Firmware
[ 2025.556576] ANALOG TV REQUEST
[ 2025.556580] Loading base firmware: xc3028_init0.i2c.fw
[ 2025.570656] xc3028-tuner.c: Unable to load firmware
[ 2025.570668] xc3028-tuner.c: ** PLEASE HAVE A LOOK AT **
[ 2025.570671] xc3028-tuner.c: http://linuxtv.org/v4lwiki/index.php/Talk:Em2880#Firmware
[ 2025.570678] xc3028-tuner: no firmware uploaded (tuning not possible)
[ 2025.582860] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[ 2025.587325] em28xx #0: V4L2 device registered as /dev/video0
[ 2025.587336] em28xx #0: Found Terratec Hybrid XS
[ 2025.587402] usbcore: registered new interface driver em28xx
[ 2025.875632] em2880-dvb.c: DVB Init
[ 2025.875659] Loading base firmware: xc3028_8MHz_init0.i2c.fw
[ 2025.888724] xc3028-tuner.c: Unable to load firmware
[ 2025.888735] xc3028-tuner.c: ** PLEASE HAVE A LOOK AT **
[ 2025.888738] xc3028-tuner.c: http://linuxtv.org/v4lwiki/index.php/Talk:Em2880#Firmware
[ 2025.989570] FIXME:em28xx_i2c_send_bytes(1e): write failed:
[ 2025.989583] ===============================
[ 2025.989588] 7f
[ 2025.989591] ================================
[ 2025.990072] zl10353_read_register: readreg error (reg=127, ret==-19)
[ 2025.990156] em2880-dvb.c: failed initializing zl10353 DVB-T demodulator
[ 2025.990160] em2880-dvb.c: retrying with mt352 DVB-T demodulator
[ 2025.990696] FIXME:em28xx_i2c_send_bytes(1e): write failed:
[ 2025.990701] ===============================
[ 2025.990705] 7f
[ 2025.990708] ================================
[ 2025.991329] mt352_read_register: readreg error (reg=127, ret==-19)
[ 2025.991463] em2880-dvb.c: no luck with mt352 demodulator, not attaching em2880-dvb
[ 2025.991467] em2880-dvb.c: DVB-T demodulator not reachable, did you try "modprobe em28xx device_mode=1"
[ 2025.991472] Em28xx: Initialized (Em2880 DVB Extension) extension
[ 2564.784610] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2582.442757] eth0: no IPv6 routers present

```

As you can see, I have this errors:

```
[ 2025.500047] Loading base firmware: xc3028_init0.i2c.fw
[ 2025.556554] xc3028-tuner.c: Unable to load firmware
[ 2025.556563] xc3028-tuner.c: ** PLEASE HAVE A LOOK AT **
[ 2025.556567] xc3028-tuner.c: http://linuxtv.org/v4lwiki/index.php/Talk:Em2880#Firmware
```

```
[ 2025.989570] FIXME:em28xx_i2c_send_bytes(1e): write failed:
[ 2025.989583] ===============================
[ 2025.989588] 7f
[ 2025.989591] ================================
[ 2025.990072] zl10353_read_register: readreg error (reg=127, ret==-19)
[ 2025.990156] em2880-dvb.c: failed initializing zl10353 DVB-T demodulator
[ 2025.990160] em2880-dvb.c: retrying with mt352 DVB-T demodulator
[ 2025.990696] FIXME:em28xx_i2c_send_bytes(1e): write failed:
[ 2025.990701] ===============================
[ 2025.990705] 7f
[ 2025.990708] ================================
[ 2025.991329] mt352_read_register: readreg error (reg=127, ret==-19)
[ 2025.991463] em2880-dvb.c: no luck with mt352 demodulator, not attaching em2880-dvb
[ 2025.991467] em2880-dvb.c: DVB-T demodulator not reachable, did you try "modprobe em28xx device_mode=1"
[ 2025.991472] Em28xx: Initialized (Em2880 DVB Extension) extension
```

I'm stuck here. 

in /lib/firmware/2.6.24-16-generic I don't have any files beginning with x* like xc3028-tuner.c

Here's the dir output in that folder: 

```
acx                                 dvb-usb-vp7045-01.fw
aic94xx-seq.fw                      dvb-usb-wt220u-02.fw
atmel_at76c502_3com.bin             dvb-usb-wt220u-fc03.fw
atmel_at76c502_3com-wpa.bin         dvb-usb-wt220u-zl0353-01.fw
atmel_at76c502.bin                  ipw2100-1.3.fw
atmel_at76c502d.bin                 ipw2100-1.3-i.fw
atmel_at76c502d-wpa.bin             ipw2100-1.3-p.fw
atmel_at76c502e.bin                 ipw2200-bss.fw
atmel_at76c502e-wpa.bin             ipw2200-ibss.fw
atmel_at76c502-wpa.bin              ipw2200-sniffer.fw
atmel_at76c503-i3861.bin            isl3877
atmel_at76c503-i3863.bin            isl3886
atmel_at76c503-rfmd-0.90.2-140.bin  isl3887usb_bare
atmel_at76c503-rfmd-acc.bin         isl3890
atmel_at76c503-rfmd.bin             isl3890usb
atmel_at76c504_2958-wpa.bin         iwlwifi-3945-1.ucode
atmel_at76c504a_2958-wpa.bin        iwlwifi-3945.ucode
atmel_at76c504.bin                  iwlwifi-4965-1.ucode
atmel_at76c504c-wpa.bin             iwlwifi-4965.ucode
atmel_at76c505a-rfmd2958.bin        ql2100_fw.bin
atmel_at76c505-rfmd2958.bin         ql2200_fw.bin
atmel_at76c505-rfmd.bin             ql2300_fw.bin
atmel_at76c506.bin                  ql2322_fw.bin
atmel_at76c506-wpa.bin              ql2400_fw.bin
dvb-fe-or51132-qam.fw               rt2561.bin
dvb-fe-or51132-vsb.fw               rt2561s.bin
dvb-fe-or51211.fw                   rt2661.bin
dvb-fe-tda10046.fw                  rt73.bin
dvb-ttpci-01.fw                     v4l-cx2341x-dec.fw
dvb-usb-avertv-a800-02.fw           v4l-cx2341x-enc.fw
dvb-usb-bluebird-01.fw              v4l-cx2341x-init.mpg
dvb-usb-dib0700-1.10.fw             v4l-cx25840.fw
dvb-usb-dibusb-5.0.0.11.fw          v4l-pvrusb2-24xxx-01.fw
dvb-usb-dibusb-6.0.0.8.fw           v4l-pvrusb2-29xxx-01.fw
dvb-usb-dtt200u-01.fw               zd1201-ap.fw
dvb-usb-tvwalkert.fw                zd1201.fw
dvb-usb-umt-010-02.fw               zd1211
dvb-usb-vp702x-01.fw

```

What should I do now? What am I missing?

Thanks in advance!

---

### Post by njean on 2008-05-15
i found x* firmware files, I placed them inside /lib/firmware/2.6.24-16-generic

but still in dmesg I get the xc3028-tuner.c: Unable to load firmware

---

### Post by njean on 2008-05-15
ok dmesg works with no errors now after a reboot.

Kaffeine shows Digital tv section... but what if I want to see the analog composite signal ?

---

### Post by njean on 2008-05-15
up.

---

### Post by xc3RnbFO8P on 2008-05-15
Install Tvtime in Add/Remove (all available application)
Does your usb stick have composite jack?

---

### Post by njean on 2008-05-15
> **Ringi said:**
> Install Tvtime in Add/Remove (all available application)
Does your usb stick have composite jack?

It has a mini-usb connector and a strange cable with mini-usb male at one end, and 4 connectors on the other (including remote control sensor).. let me see if I can find a pic:

[IMG]http://damian.amherd.net/blogwerk/1-a.jpg[/IMG]

It's the one on the up-right.

---

### Post by njean on 2008-05-15
TVTIME WORKS!

Thanks!!

---

### Post by xc3RnbFO8P on 2008-05-15
Just try Tvtime, it has s-video, composite and analog Tv. 
OK :)

---

### Post by njean on 2008-05-15
> **Ringi said:**
> Just try Tvtime, it has s-video, composite and analog Tv. 
OK :)

Ok Tvtime works. But now, I need to use Mogulus.com flash plugin to stream my composite signal over the web. Mogulus window shows the Hybrid XS input, but it's set to digital.

Isn't it possible to set the composite input signal as default system-wise?

I don't know, maybe a parameter to set somewhere?

---

### Post by njean on 2008-05-16
up.

---

