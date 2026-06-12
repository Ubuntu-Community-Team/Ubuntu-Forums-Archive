---
title: "ipod nano 4g won't mount in Dapper 6.06"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by dwhsix on 2007-01-24
My ipod video mounts just fine in Dapper 6.06 but my daughter's iPod Nano 4g won't... there do seem to be reports of Nanos not mounting properly in Edgy (see [launchpad bug]("http://https://launchpad.net/ubuntu/+source/hal/+bug/66068") and [this viciouslime post]("http://www.viciouslime.co.uk/index.php?option=com_content&task=view&id=14&Itemid=33").  Not sure if what I've got is the same problem, though.

Dmesg shows:
[18131751.636000] usb 5-8: new high speed USB device using ehci_hcd and address 83
[18131752.508000] hub 5-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[18131752.620000] usb 5-8: new high speed USB device using ehci_hcd and address 84
[18131753.492000] hub 5-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[18131753.604000] usb 5-8: new high speed USB device using ehci_hcd and address 85
[18131754.012000] usb 5-8: device not accepting address 85, error -71
[18131754.408000] usb 5-8: new high speed USB device using ehci_hcd and address 87
[18131754.928000] usb 5-8: device not accepting address 87, error -71
[18131755.040000] usb 5-8: new high speed USB device using ehci_hcd and address 88
[18131755.560000] usb 5-8: device not accepting address 88, error -71
[18131755.672000] usb 5-8: new high speed USB device using ehci_hcd and address 89
[18131756.080000] usb 5-8: device not accepting address 89, error -71
[18131756.192000] usb 5-8: new high speed USB device using ehci_hcd and address 90
[18131756.600000] usb 5-8: device not accepting address 90, error -71

Any thoughts?  Thanks!

---

