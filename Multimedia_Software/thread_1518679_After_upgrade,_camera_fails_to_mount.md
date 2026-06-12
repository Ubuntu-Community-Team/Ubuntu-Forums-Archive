---
title: "After upgrade, camera fails to mount"
date: 2010-06-26
forum: Multimedia Software
---

### Post by senning on 2010-06-26
I have a DSC-W120 that worked fine with Jaunty and Karmic, but now that I'm trying to load my photos under Lucid, I can't seem to get it to mount.

After I plug it in and power it on, F-spot recognizes it as a **USB PTP Class Camera**, but when I select it I get a dialog box saying "*Could not lock the device*"

It appears under lsusb:
```
Bus 001 Device 010: ID 054c:033e Sony Corp. 
```

And here's my dmesg output:
```

[17650.450025] usb 1-5: new high speed USB device using ehci_hcd and address 10
[17650.591287] usb 1-5: configuration #1 chosen from 2 choices
[17650.591724] scsi14 : SCSI emulation for USB Mass Storage devices
[17650.591830] usb-storage: device found at 10
[17650.591831] usb-storage: waiting for device to settle before scanning
[17651.060032] usb 1-5: reset high speed USB device using ehci_hcd and address 10
[17655.590179] usb-storage: device scan complete
[17655.590782] scsi 14:0:0:0: Direct-Access     Sony     DSC              1.00 PQ: 0 ANSI: 0 CCS
[17655.592232] sd 14:0:0:0: Attached scsi generic sg3 type 0
[17684.630862] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 710
[17691.588217] sd 14:0:0:0: [sdc] Spinning up disk.....===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 562
[17776.601261] .

```

When I try mounting **sg3** manually, the command just sits there.

Any ideas?

---

