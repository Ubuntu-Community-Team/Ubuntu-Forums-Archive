---
title: "Philips GoGear SA3245/37 ( SA32XX ) 4GB - MTP not working"
date: 2009-04-20
forum: Multimedia Software
---

### Post by jpreston84 on 2009-04-20
I recently purchased a Philips GoGear SA3245/37 music player. It is my understanding that I need to connect this device via MTP to properly transfer music from Amarok, etc.

I'm running Kubuntu 8.10, Amarok 1.4.10 and the latest version of libmtp from the standard repositories.

I've modified my libmtp rules to add the device ID of my player (it wasn't in the default list), but still mtp-detect shows no devices.

Then I decided to check my syslog, where I noticed the following...

```
2009-04-20 20:51:05	JLAPTOP	kernel	[28652.256108] usb 4-1: new high speed USB device using ehci_hcd and address 17
2009-04-20 20:51:05	JLAPTOP	kernel	[28652.389899] usb 4-1: configuration #1 chosen from 1 choice
2009-04-20 20:51:05	JLAPTOP	kernel	[28652.392092] scsi16 : SCSI emulation for USB Mass Storage devices
2009-04-20 20:51:05	JLAPTOP	kernel	[28652.463580] usb-storage: device found at 17
2009-04-20 20:51:05	JLAPTOP	kernel	[28652.463595] usb-storage: waiting for device to settle before scanning
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.460460] usb-storage: device scan complete
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.461119] scsi 16:0:0:0: Direct-Access     Philips  GoGear SA32XX    0100 PQ: 0 ANSI: 4
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.463683] sd 16:0:0:0: [sdb] 1931008 2048-byte hardware sectors (3955 MB)
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.464178] sd 16:0:0:0: [sdb] Write Protect is off
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.464187] sd 16:0:0:0: [sdb] Mode Sense: 3e 00 00 00
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.464194] sd 16:0:0:0: [sdb] Assuming drive cache: write through
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.465805] sd 16:0:0:0: [sdb] 1931008 2048-byte hardware sectors (3955 MB)
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.466300] sd 16:0:0:0: [sdb] Write Protect is off
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.466308] sd 16:0:0:0: [sdb] Mode Sense: 3e 00 00 00
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.466313] sd 16:0:0:0: [sdb] Assuming drive cache: write through
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.466324]  sdb: sdb1
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.480630] sd 16:0:0:0: [sdb] Attached SCSI removable disk
2009-04-20 20:51:10	JLAPTOP	kernel	[28657.481542] sd 16:0:0:0: Attached scsi generic sg2 type 0

```

As you can see, it's loading it as a USB mass storage device. Is it supposed to do this in order to load up as an MTP device in Amarok?

If not, how do I force it not to?

If it is supposed to do this, can someone suggest other things I might try to make mtp-detect find my device?

Thanks, in advance.

---

