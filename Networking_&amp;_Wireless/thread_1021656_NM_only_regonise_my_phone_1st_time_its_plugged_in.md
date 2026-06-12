---
title: "NM only regonise my phone 1st time its plugged in"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by it.henrik on 2008-12-25
Hi,

I have a Sony Ericsson p9i and Network Manager (NM) recognizes it perfectly the very first time I connect it, if I unplug it and reconnects it then it is not recognized by NM anymore.

Here is a dmesg printout:
```
[ 2365.288102] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 2365.490184] usb 3-1: configuration #1 chosen from 1 choice
[ 2365.497146] cdc_acm 3-1:1.1: ttyACM0: USB ACM device
[ 2365.506589] cdc_acm 3-1:1.3: ttyACM1: USB ACM device
[ 2365.517392] cdc_acm 3-1:1.5: ttyACM2: USB ACM device
```


If I connect another sony ericsson phone (K810) it works fine:
```
[ 2441.908076] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 2442.135912] usb 3-1: configuration #3 chosen from 1 choice
[ 2442.146555] cdc_acm 3-1:3.1: ttyACM0: USB ACM device
[ 2442.166194] cdc_acm 3-1:3.3: ttyACM1: USB ACM device
[ 2442.183122] usb0: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 02:80:37:0d:03:00
```


whats going on?

---

