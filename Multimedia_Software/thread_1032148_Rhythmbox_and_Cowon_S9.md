---
title: "Rhythmbox and Cowon S9"
date: 2009-01-06
forum: Multimedia Software
---

### Post by sirlancelot on 2009-01-06
Greetings,

I'm curious if anyone knows anything about getting the [Cowon S9]("http://www.cowonamerica.com/products/cowon/s9/") to work with Rhythmbox.

When I plug it in, Ubuntu 8.10 recognizes it as a "Picture CD" but nothing shows up in Rhythmbox 0.11.6 even with the MTP plugin enabled.

Anyone sharing my struggle?

Here's the `$ dmesg` for anyone interested...```
[17071.000037] usb 8-1: new high speed USB device using ehci_hcd and address 4
[17071.147901] usb 8-1: configuration #1 chosen from 1 choice
[17071.148242] scsi12 : SCSI emulation for USB Mass Storage devices
[17071.148526] usb-storage: device found at 4
[17071.148530] usb-storage: waiting for device to settle before scanning
[17076.148617] usb-storage: device scan complete
[17076.149235] scsi 12:0:0:0: Direct-Access     COWON    S9               1.00 PQ: 0 ANSI: 0
[17076.150611] sd 12:0:0:0: [sdd] 32194560 512-byte hardware sectors (16484 MB)
[17076.162653] sd 12:0:0:0: [sdd] Write Protect is off
[17076.162661] sd 12:0:0:0: [sdd] Mode Sense: 37 00 00 08
[17076.162664] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[17076.168099] sd 12:0:0:0: [sdd] 32194560 512-byte hardware sectors (16484 MB)
[17076.179600] sd 12:0:0:0: [sdd] Write Protect is off
[17076.179606] sd 12:0:0:0: [sdd] Mode Sense: 37 00 00 08
[17076.179609] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[17076.179943]  sdd:
[17076.181318] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[17076.181544] sd 12:0:0:0: Attached scsi generic sg4 type 0
```

---

### Post by sirlancelot on 2009-01-06
I was able to get some sort of Rhythmbox functionality by following this howto: [http://www.joshuascotton.com/main/archives/18](http://www.joshuascotton.com/main/archives/18)

However, it doesn't do it via MTP, Rhythmbox just treats it like a Mass Storage Device.

I'm still looking for a way to do syncing...

---

