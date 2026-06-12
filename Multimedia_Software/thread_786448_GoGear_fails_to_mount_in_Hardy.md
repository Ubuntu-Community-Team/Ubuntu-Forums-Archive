---
title: "GoGear fails to mount in Hardy"
date: 2008-05-08
forum: Multimedia Software
---

### Post by lexarrow on 2008-05-08
Hi all,

I've been using Hardy since alpha4 and had no major problem with it. After the final release, my Philips GoGear 1830/17 doesn't mount anymore; not in nautilus and not in Rhythmbox.
Here's what syslog is saying:
```
kernel: [ 2098.601312] usb 2-3: new high speed USB device using ehci_hcd and address 5
kernel: [ 2098.742965] usb 2-3: config 128 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 100, changing to 10
kernel: [ 2098.745444] usb 2-3: configuration #128 chosen from 1 choice
NetworkManager: <debug> [1210237406.232354] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_14c_______MNC800M20929RA'). 
NetworkManager: <debug> [1210237407.104949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_471_14c_______MNC800M20929RA_if0'). 
kernel: [ 2120.235244] rhythmbox[8960]: segfault at b3bd6000 eip b465c748 esp bfeb0760 error 4
```

Any suggestions?

THX!

---

