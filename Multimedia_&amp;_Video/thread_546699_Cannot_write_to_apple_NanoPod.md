---
title: "Cannot write to apple NanoPod"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by jnorthr on 2007-09-09
here is my dmesg after attaching the nano - looks like writing to hfs format pods is risky:

> [439094.504000] usb 1-1: USB disconnect, address 3
[476115.068000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[476115.244000] usb 1-1: configuration #1 chosen from 2 choices
[476115.248000] scsi2 : SCSI emulation for USB Mass Storage devices
[476115.248000] usb-storage: device found at 4
[476115.248000] usb-storage: waiting for device to settle before scanning
[476120.248000] usb-storage: device scan complete
[476120.256000] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[476120.276000] SCSI device sda: 1999871 512-byte hdwr sectors (1024 MB)
[476120.280000] sda: Write Protect is off
[476120.280000] sda: Mode Sense: 68 00 00 08
[476120.280000] sda: assuming drive cache: write through
[476120.292000] SCSI device sda: 1999871 512-byte hdwr sectors (1024 MB)
[476120.296000] sda: Write Protect is off
[476120.296000] sda: Mode Sense: 68 00 00 08
[476120.296000] sda: assuming drive cache: write through
[476120.296000]  sda: [mac] sda1 sda2 sda3
[476120.320000] sd 2:0:0:0: Attached scsi removable disk sda
[476120.320000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[476124.552000] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.

so how/where do we specify the -force (?) option, which command ?

---

### Post by donmarone on 2007-09-09
Hi there, you need to disable journaling on your iPod as the kernel driver mounts journaled hfs volumes read-only.

[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling]("http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling")

Don Marone

---

