---
title: "Forcing a few commands upon USB Device"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by beastrace91 on 2009-05-01
I am currently fighting with making a Cricket USB Modem act how I need it too... The following are two different methods I am using, the first almost works and the second works just fine.

Here are the dmesg out puts from each different method:

Using modeswitch: [quote="modeswitch"][ 2090.297149] usb 5-1: USB disconnect, address 7
[ 2095.381087] usb 5-1: new full speed USB device using uhci_hcd and address 8
[ 2095.542716] usb 5-1: configuration #1 chosen from 1 choice
[ 2095.561887] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
[ 2095.584503] scsi14 : SCSI emulation for USB Mass Storage devices
[ 2095.593182] usb-storage: device found at 8
[ 2095.593189] usb-storage: waiting for device to settle before scanning
[ 2100.595227] usb-storage: device scan complete
[ 2100.598272] scsi 14:0:0:0: Direct-Access     Cricket  T-Flash Disk     2.31 PQ: 0 ANSI: 2
[ 2100.612027] sd 14:0:0:0: [sdb] Attached SCSI removable disk
[ 2100.612266] sd 14:0:0:0: Attached scsi generic sg2 type 0[/quote]

Using a VM:
[quote="VM"][ 2222.481109] usb 5-1: USB disconnect, address 9
[ 2227.644444] usb 5-1: new full speed USB device using uhci_hcd and address 10
[ 2227.808783] usb 5-1: configuration #1 chosen from 1 choice
[ 2227.821393] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
[ 2227.842551] scsi16 : SCSI emulation for USB Mass Storage devices
[ 2227.856703] usb-storage: device found at 10
[ 2227.856713] usb-storage: waiting for device to settle before scanning
[ 2232.861221] usb-storage: device scan complete
[ 2232.864160] scsi 16:0:0:0: Direct-Access     Cricket  T-Flash Disk     2.31 PQ: 0 ANSI: 2
[ 2232.878730] sd 16:0:0:0: [sdb] Attached SCSI removable disk
[ 2232.879350] sd 16:0:0:0: Attached scsi generic sg2 type 0
[b][ 2326.952077] usb 5-1: reset full speed USB device using uhci_hcd and address 10
[ 2327.162365] scsi17 : SCSI emulation for USB Mass Storage devices
[ 2327.166525] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
[ 2327.166552] usb-storage: device found at 10
[ 2327.166557] usb-storage: waiting for device to settle before scanning[/b][/quote]

Excluding a few ID numbers (from the device getting added/removed from different tests) the are identical outputs up until after "type 0" (I put the added lines from the method that works in bold) Is there a way I can run commands on the USB device to get the out put the second method gives? While using a VM to mount the device is a handy bandaid for now, it does not work on slower system that I need this device to work on thus I am trying to make modeswitch work. Any help/suggestions would be welcome at this point.

~Jeff Hoogland

---

