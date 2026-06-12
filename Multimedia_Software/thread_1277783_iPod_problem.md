---
title: "iPod problem"
date: 2009-09-28
forum: Multimedia Software
---

### Post by Teh Fail on 2009-09-28
Hello all. I am having problems mounting my 1st gen iPod nano. Not only does it not show up in nautilus, it doesn't mount it period.

dmesg | tail -n 25 returns this when plugging it in :

[38637.449608] usb 1-3: device descriptor read/all, error -71
[38637.564082] usb 1-3: new high speed USB device using ehci_hcd and address 96
[38637.586500] usb 1-3: device descriptor read/all, error -71
[38637.588435] hub 1-0:1.0: unable to enumerate USB device on port 3
[38638.032066] usb 2-2: new full speed USB device using ohci_hcd and address 6
[38644.321110] hub 2-0:1.0: unable to enumerate USB device on port 2
[38962.860075] usb 1-3: new high speed USB device using ehci_hcd and address 97
[38962.993560] usb 1-3: device descriptor read/all, error -71
[38963.108775] usb 1-3: new high speed USB device using ehci_hcd and address 98
[38963.241722] usb 1-3: device descriptor read/all, error -71
[38963.356099] usb 1-3: new high speed USB device using ehci_hcd and address 99
[38963.764768] usb 1-3: device not accepting address 99, error -71
[38963.876094] usb 1-3: new high speed USB device using ehci_hcd and address 100
[38963.897828] usb 1-3: device descriptor read/all, error -71
[38963.900435] hub 1-0:1.0: unable to enumerate USB device on port 3
[38965.100065] usb 1-3: new high speed USB device using ehci_hcd and address 101
[38965.234669] usb 1-3: device descriptor read/all, error -71
[38965.348771] usb 1-3: new high speed USB device using ehci_hcd and address 102
[38965.481458] usb 1-3: device descriptor read/all, error -71
[38965.596102] usb 1-3: new high speed USB device using ehci_hcd and address 103
[38965.620230] usb 1-3: device descriptor read/all, error -71
[38965.740765] usb 1-3: new high speed USB device using ehci_hcd and address 104
[38966.148085] usb 1-3: device not accepting address 104, error -71
[38966.148121] hub 1-0:1.0: unable to enumerate USB device on port 3
[38966.520069] usb 2-2: new full speed USB device using ohci_hcd and address 7

Any help would be appreciated.

---

