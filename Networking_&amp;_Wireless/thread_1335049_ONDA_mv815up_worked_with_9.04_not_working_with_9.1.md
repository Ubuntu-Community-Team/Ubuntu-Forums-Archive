---
title: "ONDA mv815up worked with 9.04 not working with 9.10"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by vang1804 on 2009-11-23
Hi everyone,

   I am using a ONDA 3g stick (provided by Vodafone) to access internet. The stick was working just fine with 9.04 with the only conflict that I had was to umount the inside flash drive of the stick, before ubuntu could find the modem. After upgrading to 9.10 i had the following error:

```


[ 3620.651701] usb 2-6: USB disconnect, address 8
[ 3623.556555] usb 2-6: new high speed USB device using ehci_hcd and address 9
[ 3623.690597] usb 2-6: configuration #1 chosen from 1 choice
[ 3623.703905] scsi13 : SCSI emulation for USB Mass Storage devices
[ 3623.706929] usb-storage: device found at 9
[ 3623.706937] usb-storage: waiting for device to settle before scanning
[ 3628.704388] usb-storage: device scan complete
[ 3628.704973] scsi 13:0:0:0: CD-ROM            Onda     datacard_cd-rom  0001 PQ: 0 ANSI: 0
[ 3628.714914] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3628.715179] sr 13:0:0:0: Attached scsi CD-ROM sr1
[ 3628.715332] sr 13:0:0:0: Attached scsi generic sg2 type 5
[ 3628.860455] sr 13:0:0:0: [sr1] Unhandled sense code
[ 3628.860466] sr 13:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 3628.860475] sr 13:0:0:0: [sr1] Sense Key : No Sense [current] 
[ 3628.860486] Info fld=0x0
[ 3628.860490] sr 13:0:0:0: [sr1] Add. Sense: No additional sense information
[ 3628.860502] end_request: I/O error, dev sr1, sector 71856
[ 3628.860516] __ratelimit: 3 callbacks suppressed
[ 3628.860523] Buffer I/O error on device sr1, logical block 8982
[ 3628.864776] sr 13:0:0:0: [sr1] Unhandled sense code
[ 3628.864787] sr 13:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 3628.864798] sr 13:0:0:0: [sr1] Sense Key : No Sense [current] 
[ 3628.864810] Info fld=0x0

```

Any ideas?

Regards,
Evangelos

---

