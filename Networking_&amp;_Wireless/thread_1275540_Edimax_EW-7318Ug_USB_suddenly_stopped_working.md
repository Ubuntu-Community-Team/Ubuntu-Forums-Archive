---
title: "Edimax EW-7318Ug USB suddenly stopped working"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by Unkuiri on 2009-09-25
Hi, I've been using Edimax EW-7318Ug USB wireless for some time and it was working fine but today I take it off while it still working and since then there's no way I can make ubuntu detect it...:(... using lsusb it doesn't detect it:
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


using dsmeg:
> [11425.541074] usb 2-2: new full speed USB device using ohci_hcd and address 22
[11425.724043] usb 2-2: device descriptor read/64, error -62
[11426.012047] usb 2-2: device descriptor read/64, error -62
[11426.292053] usb 2-2: new full speed USB device using ohci_hcd and address 23
[11426.476057] usb 2-2: device descriptor read/64, error -62
[11426.765081] usb 2-2: device descriptor read/64, error -62
[11427.044054] usb 2-2: new full speed USB device using ohci_hcd and address 24
[11427.452051] usb 2-2: device not accepting address 24, error -62
[11427.628045] usb 2-2: new full speed USB device using ohci_hcd and address 25
[11428.037037] usb 2-2: device not accepting address 25, error -62
[11428.037075] hub 2-0:1.0: unable to enumerate USB device on port 2


Can someone please help with this?
Maybe it's a driver problem, or a file may have been corrupted...:(...

---

