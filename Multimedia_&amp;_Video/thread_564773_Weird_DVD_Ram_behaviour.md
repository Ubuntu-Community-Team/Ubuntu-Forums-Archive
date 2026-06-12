---
title: "Weird DVD Ram behaviour"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by Marshall2day on 2007-10-01
I have a Panasonic DVD RAM camcorder. When I connect it trough USB, it mounts automatically and since gutsy, I can see the files on it (This didn't work in Feisty)

The problem however is that whenever I try to open or copy a file. The volume disconnects. 

This is the only thing that still forces me to use windows, so if anyone can help me with this one, I would be so grateful.

My dmesg output after a disconnect:

```

[49226.944000] usb-storage: device found at 7
[49226.944000] usb-storage: waiting for device to settle before scanning
[49231.944000] usb-storage: device scan complete
[49231.948000] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-CAMERA M5795 NA04 PQ: 0 ANSI: 0
[49231.956000] sr1: scsi3-mmc drive: 15x/15x dvd-ram tray
[49231.956000] sr 4:0:0:0: Attached scsi CD-ROM sr1
[49231.956000] sr 4:0:0:0: Attached scsi generic sg3 type 5
[49232.196000] cdrom: This disc doesn't have any tracks I recognize!
[49234.220000] cdrom: This disc doesn't have any tracks I recognize!
[49239.512000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'UDF Volume', timestamp 2005/07/23 08:36 (1078)
[49239.568000] cdrom: This disc doesn't have any tracks I recognize!
[49243.388000] cdrom: This disc doesn't have any tracks I recognize!
[49243.424000] cdrom: This disc doesn't have any tracks I recognize!
[49243.472000] cdrom: This disc doesn't have any tracks I recognize!
[49352.072000] cdrom: This disc doesn't have any tracks I recognize!
[49363.384000] cdrom: This disc doesn't have any tracks I recognize!
[49363.420000] cdrom: This disc doesn't have any tracks I recognize!
[49363.448000] cdrom: This disc doesn't have any tracks I recognize!
[50048.332000] Unable to identify CD-ROM format.
[50351.944000] usb 5-1: USB disconnect, address 7
[50351.948000] scsi 4:0:0:0: [sr1] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[50351.948000] end_request: I/O error, dev sr1, sector 1768
[50351.948000] printk: 126 messages suppressed.
[50351.948000] Buffer I/O error on device sr1, logical block 221
[50351.948000] Buffer I/O error on device sr1, logical block 222
[50351.948000] Buffer I/O error on device sr1, logical block 223
[50351.948000] Buffer I/O error on device sr1, logical block 224
[50351.948000] Buffer I/O error on device sr1, logical block 225
[50351.948000] Buffer I/O error on device sr1, logical block 226
[50351.948000] Buffer I/O error on device sr1, logical block 227
[50351.948000] Buffer I/O error on device sr1, logical block 228
[50351.948000] Buffer I/O error on device sr1, logical block 229
[50351.948000] Buffer I/O error on device sr1, logical block 230
[50351.948000] scsi 4:0:0:0: rejecting I/O to dead device
[50351.948000] scsi 4:0:0:0: rejecting I/O to dead device
[50351.948000] scsi 4:0:0:0: [sr1] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[50351.948000] end_request: I/O error, dev sr1, sector 2008
[50351.952000] scsi 4:0:0:0: rejecting I/O to dead device
[50351.952000] scsi 4:0:0:0: rejecting I/O to dead device
[50351.952000] scsi 4:0:0:0: rejecting I/O to dead device
[50351.952000] scsi 4:0:0:0: rejecting I/O to dead device
[50351.952000] scsi 4:0:0:0: rejecting I/O to dead device
[50351.952000] scsi 4:0:0:0: rejecting I/O to dead device
[50351.952000] scsi 4:0:0:0: rejecting I/O to dead device
[50352.084000] scsi 4:0:0:0: rejecting I/O to dead device
[50352.088000] scsi 4:0:0:0: rejecting I/O to dead device
[50352.088000] scsi 4:0:0:0: rejecting I/O to dead device
[50352.088000] scsi 4:0:0:0: rejecting I/O to dead device
[50352.088000] scsi 4:0:0:0: rejecting I/O to dead device


```

---

