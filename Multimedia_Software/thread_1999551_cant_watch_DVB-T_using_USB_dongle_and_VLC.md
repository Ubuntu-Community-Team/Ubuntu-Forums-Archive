---
title: "cant watch DVB-T using USB dongle and VLC"
date: 2012-06-08
forum: Multimedia Software
---

### Post by razor1 on 2012-06-08
Hello
i am trying to watch tv using DVB-T USB dongle APEX T328B
when i am connecting the usb in dmesg:

> 
[  463.084037] usb 1-3: new high-speed USB device number 4 using ehci_hcd
[  463.588745] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in cold state, will try to load a firmware
[  463.623863] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[  463.692130] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[  463.692228] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  463.693290] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)
[  463.695117] af9013: firmware version:4.95.0.0
[  463.699746] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[  463.700867] af9015: command failed:2
[  463.700872] qt1010 I2C read failed
[  463.700885] Registered IR keymap rc-empty
[  463.701003] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-3/rc/rc1/input19
[  463.701095] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-3/rc/rc1
[  463.701100] dvb-usb: schedule remote query interval to 500 msecs.
[  463.701105] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
[  463.712081] Geniatech AF9015: Fixing fullspeed to highspeed interval: 16 -> 8
[  463.713492] input: Geniatech AF9015 as /devices/pci0000:00/0000:00:04.1/usb1/1-3/1-3:1.1/input/input20
[  463.713690] generic-usb 0003:15A4:9016.0005: input,hidraw0: USB HID v1.01 Keyboard [Geniatech AF9015] on usb-0000:00:04.1-3/input1
and in lsusb
> 
Bus 001 Device 004: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
and in lsmod:
> 
dvb_usb_af9015         35117  0 
dvb_usb                24490  1 dvb_usb_af9015
dvb_core              110619  1 dvb_usb
when i am looking for tv station in vlc
it doesnt find any (works ok on windows)
what can be the problem?
Thank you

---

### Post by razor1 on 2012-06-09
someone?

---

### Post by howefield on 2012-06-09
How are you creating the scan file ?

---

### Post by razor1 on 2012-06-09
i tried using the commande:
w_scan -ft
i have also tried with kaffein and Digital TV

i have also tried using specific parameters in VLC

i am from israel the parameters are:
514 mghz, 8 mb bandwith

in windows (same computer) it works without any problem.

---

### Post by Jose Catre-Vandis on 2012-06-09
I have the same/similar device. Believe it only works properly if connected before a cold boot. So switch off, plug it in, start up and test.

---

### Post by razor1 on 2012-06-09
> **Jose Catre-Vandis said:**
> I have the same/similar device. Believe it only works properly if connected before a cold boot. So switch off, plug it in, start up and test.

hmm what do you mean "before cold boot"?

i tried using it when it was connected and than turned on pc,
and also when i have pluged it in after system operation was up allready

are you using ubuntu 12.04?
what exactly did you install in order to make
the device operate?

---

### Post by Jose Catre-Vandis on 2012-06-09
You should have installed the restricted drivers dvb firmware.

By cold boot I mean: Switch off PC. Remove DVB dongle. Put it back in. Boot PC. (you don't have to do this everytime, but be aware that just a reboot may not fix things). Check your dmesg. This is the important info for me:
```
[   15.221414] af9013: firmware version:4.95.0.0
[   15.227027] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   15.236805] Quantek QT1010 successfully identified.
``` You will see lots of stuff such as:```
[   15.011400] dvb-usb: found a 'KWorld USB DVB-T TV Stick II (VS-DVB-T 395U)' in warm state.
[   15.011743] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.238009] dvb-usb: schedule remote query interval to 500 msecs.
[   15.238021] dvb-usb: KWorld USB DVB-T TV Stick II (VS-DVB-T 395U) successfully initialized and connected.
[   15.260704] usbcore: registered new interface driver dvb_usb_af9015
``` but this doesn't necessarily mean it is completely fired up. You need the adapter to register.

Your outputs may be different to mine. Hope this helps

---

### Post by razor1 on 2012-06-09
tried that still not working :(

---

### Post by Jose Catre-Vandis on 2012-06-09
> **razor1 said:**
> tried that still not working :(

Need a bit more than that to help. Please post you dmesg output (in code or quote tags)

---

### Post by razor1 on 2012-06-09
dmesg after pc start up
```

[    0.596301] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.596348] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    0.596368] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfce7f000
[    0.654121] hub 2-0:1.0: USB hub found
[    0.654126] hub 2-0:1.0: 10 ports detected
[    0.654194] uhci_hcd: USB Universal Host Controller Interface driver
[    0.654242] usbcore: registered new interface driver libusual
[    0.654281] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.656466] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.656471] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.656601] mousedev: PS/2 mouse device common for all mice
[    0.656740] rtc_cmos 00:09: RTC can wake from S4
[    0.656875] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.656910] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.656982] device-mapper: uevent: version 1.0.3
[    0.657046] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.657054] cpuidle: using governor ladder
[    0.657056] cpuidle: using governor menu
[    0.657057] EFI Variables Facility v0.08 2004-May-17
[    0.657280] TCP cubic registered
[    0.657384] NET: Registered protocol family 10
[    0.657824] NET: Registered protocol family 17
[    0.657838] Registering the dns_resolver key type
[    0.657966] PM: Hibernation image not present or could not be loaded.
[    0.657979] registered taskstats version 1
[    0.678422]   Magic number: 0:534:809
[    0.678541] rtc_cmos 00:09: setting system clock to 2012-06-10 00:49:12 UTC (1339289352)
[    0.678894] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.678896] EDD information not available.
[    0.904032] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.904053] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.904068] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.904082] ata2: SATA link down (SStatus 0 SControl 300)
[    0.905050] ata1.00: ATA-8: ST3500418AS, CC37, max UDMA/133
[    0.905055] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    0.906233] ata1.00: configured for UDMA/133
[    0.906414] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC37 PQ: 0 ANSI: 5
[    0.906554] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.906585] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.906601] sd 0:0:0:0: [sda] Write Protect is off
[    0.906603] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.906624] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.907038] ata4.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL00, max UDMA/100
[    0.908033] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    0.910834] ata4.00: configured for UDMA/100
[    0.951336] ata3.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    0.951339] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    0.953463] ata3.00: configured for UDMA/133
[    0.953537] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    0.953631] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.953650] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.953675] sd 2:0:0:0: [sdb] Write Protect is off
[    0.953678] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.953698] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.956969] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL00 PQ: 0 ANSI: 5
[    0.962093] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.962098] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.962244] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    0.962299] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    0.962913]  sdb: sdb1
[    0.963183] sd 2:0:0:0: [sdb] Attached SCSI disk
[    0.967495]  sda: sda1 sda2 < sda5 sda6 >
[    0.967896] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.969356] Freeing unused kernel memory: 920k freed
[    0.969740] Write protecting the kernel read-only data: 12288k
[    0.974685] Freeing unused kernel memory: 1608k freed
[    0.979161] Freeing unused kernel memory: 1196k freed
[    0.994813] udevd[93]: starting version 175
[    1.064534] pata_amd 0000:00:08.0: version 0.4.1
[    1.064585] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.072175] scsi4 : pata_amd
[    1.074460] scsi5 : pata_amd
[    1.075307] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.075311] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.075992] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.076207] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.076221] forcedeth 0000:00:0f.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.076226] forcedeth 0000:00:0f.0: setting latency timer to 64
[    1.104225] Floppy drive(s): fd0 is 1.44M
[    1.124089] FDC 0 is a post-1991 82077
[    1.239126] ata6: port disabled--ignoring
[    1.239833] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 19
[    1.239847] firewire_ohci 0000:04:00.0: PCI INT A -> Link[LNED] -> GSI 19 (level, low) -> IRQ 19
[    1.239854] firewire_ohci 0000:04:00.0: setting latency timer to 64
[    1.243504] Geniatech AF9015: Fixing fullspeed to highspeed interval: 16 -> 8
[    1.243925] input: Geniatech AF9015 as /devices/pci0000:00/0000:00:04.1/usb1/1-4/1-4:1.1/input/input2
[    1.244046] generic-usb 0003:15A4:9016.0001: input,hidraw0: USB HID v1.01 Keyboard [Geniatech AF9015] on usb-0000:00:04.1-4/input1
[    1.244060] usbcore: registered new interface driver usbhid
[    1.244062] usbhid: USB HID core driver
[    1.300099] firewire_ohci: Added fw-ohci device 0000:04:00.0, OHCI v1.10, 4 IR + 0 IT contexts, quirks 0x10
[    1.348034] Refined TSC clocksource calibration: 2500.000 MHz.
[    1.348044] Switching to clocksource tsc
[    1.435687] EXT3-fs (loop0): recovery required on readonly filesystem
[    1.435691] EXT3-fs (loop0): write access will be enabled during recovery
[    1.460032] usb 2-6: new full-speed USB device number 2 using ohci_hcd
[    1.601053] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:85:5a:8b:42
[    1.601057] forcedeth 0000:00:0f.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.693361] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:04.0/usb2/2-6/2-6:1.0/input/input3
[    1.693462] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:04.0-6/input0
[    1.703738] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:04.0/usb2/2-6/2-6:1.1/input/input4
[    1.703848] generic-usb 0003:045E:0745.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:04.0-6/input1
[    1.732255] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:04.0/usb2/2-6/2-6:1.2/input/input5
[    1.732416] generic-usb 0003:045E:0745.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:04.0-6/input2
[    1.800147] firewire_core: created device fw0: GUID 0010dc000167afa3, S400
[   10.332940] kjournald starting.  Commit interval 5 seconds
[   10.333015] EXT3-fs (loop0): recovery complete
[   10.333147] EXT3-fs (loop0): mounted filesystem with ordered data mode
[   28.238355] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.250356] udevd[401]: starting version 175
[   28.395725] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[   28.395768] i2c i2c-1: nForce2 SMBus adapter at 0x4e00
[   28.485476] wmi: Mapper loaded
[   28.505536] parport_pc 00:06: reported by Plug and Play ACPI
[   28.505584] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   28.531994] cfg80211: Calling CRDA to update world regulatory domain
[   28.549030] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[   28.549050] ath5k 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   28.549116] ath5k 0000:01:07.0: registered as 'phy0'
[   28.563499] snd_hda_intel 0000:00:09.0: power state changed by ACPI to D0
[   28.563504] snd_hda_intel 0000:00:09.0: power state changed by ACPI to D0
[   28.563653] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   28.563658] snd_hda_intel 0000:00:09.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   28.563661] hda_intel: Disabling MSI
[   28.563687] snd_hda_intel 0000:00:09.0: setting latency timer to 64
[   29.012390] ppdev: user-space parallel port driver
[   29.064402] cfg80211: World regulatory domain updated:
[   29.064405] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.064407] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.064410] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.064412] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.064414] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.064417] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.143743] ath: EEPROM regdomain: 0x809c
[   29.143746] ath: EEPROM indicates we should expect a country code
[   29.143748] ath: doing EEPROM country->regdmn map search
[   29.143750] ath: country maps to regdmn code: 0x52
[   29.143752] ath: Country alpha2 being used: CN
[   29.143753] ath: Regpair used: 0x52
[   29.143756] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.143760] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143762] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.143764] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143766] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.143769] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143771] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.143773] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143775] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.143778] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143780] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.143782] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143784] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.143787] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143789] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.143791] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143793] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.143796] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143798] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.143800] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143802] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.143805] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.143807] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   29.143809] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   29.143811] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   29.143965] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.143968] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.143971] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.143973] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.143975] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.143978] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.143980] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.143982] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.143984] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.143987] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.143989] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.143992] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.143994] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.143996] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.144060] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.144063] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.144065] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.144067] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.144069] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.144072] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.144080] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.144082] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.144084] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.144087] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.144089] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.144091] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.144094] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   29.144096] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.147325] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   29.147877] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   29.148108] cfg80211: Calling CRDA for country: CN
[   29.149541] type=1400 audit(1339278580.965:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=641 comm="apparmor_parser"
[   29.149579] type=1400 audit(1339278580.965:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=579 comm="apparmor_parser"
[   29.149908] type=1400 audit(1339278580.965:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=641 comm="apparmor_parser"
[   29.149945] type=1400 audit(1339278580.965:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
[   29.150120] type=1400 audit(1339278580.965:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=641 comm="apparmor_parser"
[   29.150160] type=1400 audit(1339278580.965:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
[   29.161901] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.161906] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161908] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.161911] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161913] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.161915] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161917] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.161920] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161922] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.161924] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161926] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.161929] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161930] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.161933] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161935] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.161938] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161940] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.161942] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161944] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.161946] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161948] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.161951] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161953] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.161955] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161957] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.161960] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.161962] cfg80211: Disabling freq 2484 MHz
[   29.161965] cfg80211: Regulatory domain changed to country: CN
[   29.161966] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.161969] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.161971] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   29.177849] WARNING: You are using an experimental version of the media stack.
[   29.177852]     As the driver is backported to an older kernel, it doesn't offer
[   29.177853]     enough quality for its usage in production.
[   29.177853]     Use it with care.
[   29.177854] Latest git patches (needed if you report a bug to [email]linux-media@vger.kernel.org[/email]):
[   29.177855]     5472d3f17845c4398c6a510b46855820920c2181 [media] mt9m032: Implement V4L2_CID_PIXEL_RATE control
[   29.177856]     8d690c4a4e88297451edd027d37291676bc5b9c4 [media] mt9p031: Implement V4L2_CID_PIXEL_RATE control
[   29.177858]     0bc77f3f06fcf2ca7b7fad782d70926cd4d235f1 [media] mt9t001: Implement V4L2_CID_PIXEL_RATE control
[   29.380021] hda_codec: ALC888: BIOS auto-probing.
[   29.548241] WARNING: You are using an experimental version of the media stack.
[   29.548243]     As the driver is backported to an older kernel, it doesn't offer
[   29.548244]     enough quality for its usage in production.
[   29.548245]     Use it with care.
[   29.548245] Latest git patches (needed if you report a bug to [email]linux-media@vger.kernel.org[/email]):
[   29.548246]     5472d3f17845c4398c6a510b46855820920c2181 [media] mt9m032: Implement V4L2_CID_PIXEL_RATE control
[   29.548248]     8d690c4a4e88297451edd027d37291676bc5b9c4 [media] mt9p031: Implement V4L2_CID_PIXEL_RATE control
[   29.548249]     0bc77f3f06fcf2ca7b7fad782d70926cd4d235f1 [media] mt9t001: Implement V4L2_CID_PIXEL_RATE control
[   29.991909] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[   29.992211] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   29.992609] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)
[   30.018158] af9013: firmware version 5.1.0.0
[   30.020660] DVB: registering adapter 0 frontend 0 (Afatech AF9013)...
[   30.042531] Quantek QT1010 successfully identified.
[   30.042547] Registered IR keymap rc-empty
[   30.042850] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-4/rc/rc0/input6
[   30.042937] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-4/rc/rc0
[   30.042939] dvb-usb: schedule remote query interval to 500 msecs.
[   30.042944] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
[   30.050824] usbcore: registered new interface driver dvb_usb_af9015
[   30.119515] nvidia: module license 'NVIDIA' taints kernel.
[   30.119519] Disabling lock debugging due to kernel taint
[   30.326544] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 17
[   30.326562] nvidia 0000:02:00.0: PCI INT A -> Link[LNEB] -> GSI 17 (level, low) -> IRQ 17
[   30.326571] nvidia 0000:02:00.0: setting latency timer to 64
[   30.326575] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   30.327399] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.49  Mon Apr 30 23:46:33 PDT 2012
[   30.361023] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
[   30.382201] EXT3-fs (loop0): using internal journal
[   30.596170] input: HDA NVidia Line as /devices/pci0000:00/0000:00:09.0/sound/card0/input7
[   30.596267] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:09.0/sound/card0/input8
[   30.596359] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:09.0/sound/card0/input9
[   30.596470] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:09.0/sound/card0/input10
[   30.596542] input: HDA NVidia Line-Out Side as /devices/pci0000:00/0000:00:09.0/sound/card0/input11
[   30.596648] input: HDA NVidia Line-Out CLFE as /devices/pci0000:00/0000:00:09.0/sound/card0/input12
[   30.596727] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:09.0/sound/card0/input13
[   30.596804] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:09.0/sound/card0/input14
[   30.597379] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 16
[   30.597395] snd_hda_intel 0000:02:00.1: PCI INT B -> Link[LNEC] -> GSI 16 (level, low) -> IRQ 16
[   30.597398] hda_intel: Disabling MSI
[   30.597446] snd_hda_intel 0000:02:00.1: setting latency timer to 64
[   31.168913] init: failsafe main process (819) killed by TERM signal
[   31.226674] type=1400 audit(1339278583.041:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=874 comm="apparmor_parser"
[   31.228088] type=1400 audit(1339278583.041:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=874 comm="apparmor_parser"
[   31.228311] type=1400 audit(1339278583.045:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=874 comm="apparmor_parser"
[   31.231585] type=1400 audit(1339278583.045:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=872 comm="apparmor_parser"
[   31.273726] lp0: using parport0 (interrupt-driven).
[   31.276998] Bluetooth: Core ver 2.16
[   31.277088] NET: Registered protocol family 31
[   31.277090] Bluetooth: HCI device and connection manager initialized
[   31.277092] Bluetooth: HCI socket layer initialized
[   31.277095] Bluetooth: L2CAP socket layer initialized
[   31.279260] Bluetooth: SCO socket layer initialized
[   31.282761] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.282764] Bluetooth: BNEP filters: protocol multicast
[   31.293374] Bluetooth: RFCOMM TTY layer initialized
[   31.293381] Bluetooth: RFCOMM socket layer initialized
[   31.293383] Bluetooth: RFCOMM ver 1.11
[   31.342209] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.342875] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.346971] forcedeth 0000:00:0f.0: irq 43 for MSI/MSI-X
[   31.424420] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   31.448052] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   31.472084] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[   31.496033] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   31.496153] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:0b.0/0000:02:00.1/sound/card1/input15
[   31.496494] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:0b.0/0000:02:00.1/sound/card1/input16
[   31.496656] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:0b.0/0000:02:00.1/sound/card1/input17
[   31.496817] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0b.0/0000:02:00.1/sound/card1/input18
[   31.658882] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   31.939242] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   31.939245] vesafb: scrolling: redraw
[   31.939247] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   31.940689] vesafb: framebuffer at 0xcf000000, mapped to 0xffffc90011900000, using 1216k, total 1216k
[   31.941903] Console: switching to colour frame buffer device 80x30
[   31.941915] fb0: VESA VGA frame buffer device
[   31.957465] init: plymouth-splash main process (1211) terminated with status 2
[   34.762152] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   34.768010] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   34.781757] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   34.788012] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   35.556053] HDMI: detected monitor SAMSUNG
[   35.556056]       at connection type HDMI
[   35.556058] HDMI: available speakers: FL/FR
[   35.556062] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   36.481093] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   36.488008] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   36.497540] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   36.504011] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   36.514693] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   36.520008] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   37.288041] HDMI: detected monitor SAMSUNG
[   37.288043]       at connection type HDMI
[   37.288045] HDMI: available speakers: FL/FR
[   37.288049] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   42.192022] eth0: no IPv6 routers present

```

dmesg after usb plug out and in:
```

[  176.544337] usb 1-4: USB disconnect, device number 2
[  176.565974] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully deinitialized and disconnected.
[  178.992040] usb 1-4: new high-speed USB device number 4 using ehci_hcd
[  179.497398] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in cold state, will try to load a firmware
[  179.553426] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[  179.624850] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[  179.624947] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  179.626008] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)
[  179.626835] af9013: firmware version 5.1.0.0
[  179.628967] DVB: registering adapter 0 frontend 0 (Afatech AF9013)...
[  179.630218] af9015: command failed:2
[  179.630223] qt1010 I2C read failed
[  179.630239] Registered IR keymap rc-empty
[  179.630363] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-4/rc/rc1/input19
[  179.630458] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-4/rc/rc1
[  179.630463] dvb-usb: schedule remote query interval to 500 msecs.
[  179.630469] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
[  179.640796] Geniatech AF9015: Fixing fullspeed to highspeed interval: 16 -> 8
[  179.641252] input: Geniatech AF9015 as /devices/pci0000:00/0000:00:04.1/usb1/1-4/1-4:1.1/input/input20
[  179.641430] generic-usb 0003:15A4:9016.0005: input,hidraw0: USB HID v1.01 Keyboard [Geniatech AF9015] on usb-0000:00:04.1-4/input1

```

ls usb -v:
```

Bus 001 Device 004: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x15a4 Afatech Technologies, Inc.
  idProduct          0x9016 AF9015 DVB-T USB2.0 stick
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           71
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.01
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      65
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              16

```

---

### Post by Jose Catre-Vandis on 2012-06-09
Cropped from your dmesg
```
29.992609] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)
[ 30.018158] af9013: firmware version 5.1.0.0
[ 30.020660] DVB: registering adapter 0 frontend 0 (Afatech AF9013)...
[ 30.042531] Quantek QT1010 successfully identified.
[ 30.042547] Registered IR keymap rc-empty
[ 30.042850] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-4/rc/rc0/input6
[ 30.042937] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-4/rc/rc0
[ 30.042939] dvb-usb: schedule remote query interval to 500 msecs.
[ 30.042944] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
```

So it looks like it is configured OK.

Now we turn to signal and tuning. You say it worked OK under Windows, so guessing  signal is OK. I can't see a transmitter for Israel in the dvb-t folder so I guess we will have to do things manually.

What happens if you run:

This should scan for Israel and create mplayer compatible list (works in VLC)
```
w_scan -c IL -M > IL-VLC.conf
```
or

This should scan for Israel and create vdr channel list
```
w_scan -c IL > IL-dvb.txt
```

(you should get a file or files created with channel codes inside)

Here is the output I get from:```
w_scan -c GB > GB-dvb.txt
``````
5 USA;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6689:6690,6691=eng:0:0:12992:9018:12294:0
Channel 5+1;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6865:6866,6867=eng:0:0:13024:9018:12294:0
The Zone;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6817:6818:0:0:14532:9018:12294:0
ADULT Playboy;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6625:6626:0:0:15504:9018:12294:0
ITV3;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6881:6882,6883=eng:0:0:16048:9018:12294:0
QVC;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6049:6050:0:0:13120:9018:12294:0
bid tv;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6273:6274:0:0:14272:9018:12294:0
QUEST;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6929:6930:0:0:14498:9018:12294:0
Heart;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:0:6098:0:0:14720:9018:12294:0
Absolute Radio;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:0:6082:0:0:14688:9018:12294:0
Capital FM;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:0:6114:0:0:14752:9018:12294:0
ITV2 +1;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6529:6530,6531=eng:0:0:15952:9018:12294:0
ESPN;(null):634000:I999B8C34D0M64T8G32Y0:T:27500:6801:6802:0:100,180a:16096:9018:12294:0
BBC ONE;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:101:102,106=eng:0:0:4163:9018:4163:0
BBC TWO;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:201:202,206=eng:0:0:4287:9018:4163:0
BBC THREE;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:301:302,306=eng:0:0:4288:9018:4163:0
BBC NEWS;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:501:502:0:0:4352:9018:4163:0
BBC FOUR;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:401:402,406=eng:0:0:4544:9018:4163:0
BBC Parliament;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:601:602:0:0:4736:9018:4163:0
BBC R5L;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1402:0:0:5632:9018:4163:0
BBC R5SX;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1502:0:0:5696:9018:4163:0
BBC 6 Music;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1602:0:0:5760:9018:4163:0
BBC Radio 4 Ex;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1702:0:0:5824:9018:4163:0
BBC R1X;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1802:0:0:5888:9018:4163:0
BBC Asian Net.;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1902:0:0:5952:9018:4163:0
BBC World Sv.;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:2002:0:0:6016:9018:4163:0
BBC Radio 1;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1002:0:0:6720:9018:4163:0
BBC Radio 2;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1102:0:0:6784:9018:4163:0
BBC Radio 3;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1202:0:0:6848:9018:4163:0
BBC Radio 4;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:0:1302:0:0:6912:9018:4163:0
301;(null):666000:I999B8C23D0M64T8G32Y0:T:27500:901:951,952=eng:0:0:7168:9018:4163:0
ITV1;(null):642000:I999B8C23D0M64T8G32Y0:T:27500:520:521,522=eng:0:0:8271:9018:8207:0
ITV2;(null):642000:I999B8C23D0M64T8G32Y0:T:27500:530:531,532=eng:0:0:8325:9018:8207:0
Channel 4;(null):642000:I999B8C23D0M64T8G32Y0:T:27500:560:561,562=eng:0:0:8384:9018:8207:0
E4;(null):642000:I999B8C23D0M64T8G32Y0:T:27500:570:571,572=eng:0:0:8448:9018:8207:0
More 4;(null):642000:I999B8C23D0M64T8G32Y0:T:27500:590:591,592=eng:0:0:8442:9018:8207:0
Channel 4+1;(null):642000:I999B8C23D0M64T8G32Y0:T:27500:580:581,582=eng:0:0:8452:9018:8207:0
Channel 5;(null):642000:I999B8C23D0M64T8G32Y0:T:27500:540:541,542=eng:0:0:8500:9018:8207:0
ITV1 +1;(null):642000:I999B8C23D0M64T8G32Y0:T:27500:600:601,602=eng:0:0:8370:9018:8207:0
Sky News;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:101:102,104=eng:0:0:22080:9018:20544:0
Pick TV;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:301:302,304=eng:0:0:22208:9018:20544:0
Challenge;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:201:202,203=eng:0:0:22226:9018:20544:0
Dave;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:401:402,404=eng:0:0:22272:9018:20544:0
E4+1;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:501:502,504=eng:0:0:22336:9018:20544:0
ADULT smileTV3;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:601:602:0:0:22400:9018:20544:0
talkSPORT;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:0:1101:0:0:22592:9018:20544:0
Really;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:2111:2112,2114=eng:0:0:23712:9018:20544:0
ADULT PARTY;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:411:412:0:0:24256:9018:20544:0
Gems TV;(null):658000:I999B8C34D0M64T8G32Y0:T:27500:2401:2402:0:0:24448:9018:20544:0
4Music;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:101:102:0:0:25664:9018:24640:0
VIVA;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:201:202:0:0:25728:9018:24640:0
ADULT smileTV2;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:511:512:0:0:27520:9018:24640:0
Big Deal;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:2601:2602:0:0:27936:9018:24640:0
ITV4;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:601:602,604=eng:0:0:28032:9018:24640:0
Film4;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:701:702,704=eng:0:0:27136:9018:24640:0
Russia Today;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:2101:2102,2104=eng:0:0:27456:9018:24640:0
Q;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1901:0:0:26688:9018:24640:0
Magic;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1801:0:0:26624:9018:24640:0
The Hits Radio;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1701:0:0:26560:9018:24640:0
Kerrang!;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1301:0:0:26304:9018:24640:0
heat;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1201:0:0:26240:9018:24640:0
Kiss;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1101:0:0:26176:9018:24640:0
SMOOTH RADIO;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1401:0:0:26368:9018:24640:0
Yesterday;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:301:302,304=eng:0:0:25792:9018:24640:0
Sky Sports 1;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:2401:2402,2404=eng:0:100:27232:9018:24640:0
Sky Sports 2;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:2501:2502,2504=eng:0:100:27296:9018:24640:0
Smash Hits!;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1501:0:0:27040:9018:24640:0
Premier Radio;(null):682000:I999B8C34D0M64T8G32Y0:T:27500:0:1601:0:0:28160:9018:24640:0
```

---

### Post by razor1 on 2012-06-09
the file is empty

> elad@ubuntu:~$ w_scan -c IL > IL-dvb.txt
w_scan version 20111203 (compiled for DVB API 5.4)
using settings for ISRAEL
Country identifier IL not defined. Using defaults.
frontend_type DVB-T, channellist 4
output format vdr-1.6
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> DVB-T "Afatech AF9013": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.6
frontend 'Afatech AF9013' supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
FREQ (174.00MHz ... 860.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:01) 
184500: (time: 00:03) 
191500: (time: 00:06) 
198500: (time: 00:08) 
205500: (time: 00:11) 
212500: (time: 00:14) 
219500: (time: 00:16) 
226500: (time: 00:19) 
Scanning 8MHz frequencies...
474000: (time: 00:21) 
482000: (time: 00:24) 
490000: (time: 00:26) 
498000: (time: 00:29) 
506000: (time: 00:31) 
514000: (time: 00:34) 
522000: (time: 00:36) 
530000: (time: 00:39) 
538000: (time: 00:42) 
546000: (time: 00:44) 
554000: (time: 00:47) 
562000: (time: 00:49) 
570000: (time: 00:52) 
578000: (time: 00:54) 
586000: (time: 00:57) 
594000: (time: 00:59) 
602000: (time: 01:02) 
610000: (time: 01:04) 
618000: (time: 01:07) 
626000: (time: 01:09) 
634000: (time: 01:12) 
642000: (time: 01:15) 
650000: (time: 01:17) 
658000: (time: 01:20) 
666000: (time: 01:22) 
674000: (time: 01:25) 
682000: (time: 01:27) 
690000: (time: 01:30) 
698000: (time: 01:32) 
706000: (time: 01:35) 
714000: (time: 01:37) 
722000: (time: 01:40) 
730000: (time: 01:43) 
738000: (time: 01:45) 
746000: (time: 01:48) 
754000: (time: 01:50) 
762000: (time: 01:53) 
770000: (time: 01:55) 
778000: (time: 01:58) 
786000: (time: 02:00) 
794000: (time: 02:03) 
802000: (time: 02:05) 
810000: (time: 02:08) 
818000: (time: 02:11) 
826000: (time: 02:13) 
834000: (time: 02:16) 
842000: (time: 02:18) 
850000: (time: 02:21) 
858000: (time: 02:23) 

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!


---

### Post by Jose Catre-Vandis on 2012-06-10
Hmmmm, our outputs are much the same apart from the DVB api
```
~$ w_scan -c GB
w_scan version 20111203 (compiled for DVB API 5.4)
using settings for UNITED KINGDOM
DVB aerial
DVB-T GB
frontend_type DVB-T, channellist 6
output format vdr-1.6
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
	/dev/dvb/adapter0/frontend0 -> DVB-T "Afatech AF9013 DVB-T": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.4
frontend 'Afatech AF9013 DVB-T' supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
FREQ (174.00MHz ... 860.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:00)
``` I am on Xubuntu 12.04 running 3.2.0-24-generic
kernel. What system / OS / version are you running? Custom setup ? Do not know why your country code is not being used? Check w_scan -c ?, is it likely to be any other country than IL ? Are you able to copy all the parameters needed from your Windows setup for a channel? (I recognise this is where you may have started but this may help to debug. You can find this in VLC in the command string dialog )

This now looks like signal strength ? Do you have a booster?

---

### Post by errrn on 2012-07-10
try scanning using tvtime.

I'm in argentina and I've been playing around with a hauppage 900 dongle. I finally got it to work, and the only way I got useful scan results was with tvtime (it's in the software center - hassle free).

if you do, and just to save you some time, tvtime is going to use your webcam (if you have one) as a source, so you have to change it manually. 

this is the command as I used it. it scans from something like 40Mhz to 900Mhz

 tvtime-scanner -d /dev/video1 -n PAL-N

good luck!
hope it helps

---

