---
title: "Unable to connect USB camera"
date: 2008-08-18
forum: Multimedia Software
---

### Post by Satsat on 2008-08-18
Hello all,

I've been searching the net, but havn't found a similar situation, so here I am.
I'm trying to connect my camera through USB, but cannot get very far.

For info:
```
 uname -a
Linux badger 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686 GNU/Linux

```


When I switch it on, I get the following (and only) in /var/log/messages:

```
usb 5-5: new high speed USB device using ehci_hcd and address 53
usb 5-5: configuration #1 chosen from 1 choice

```
After a while, the camera gives up and I get this:

```
usb 5-5: USB disconnect, address 53

```

The command lsusb correctly reports the camera:
```
Bus 005 Device 056: ID 04a9:30ef Canon, Inc. EOS 350D (ptp)

```

And, lastly, no device node is ever created in /dev.

Thanks++ for any ideas you may have;

---

### Post by kostkon on 2008-08-19
Try to change the camera's mode from *USB Mass Storage Device* to *PTP* or the opposite, whichever one applies, and see what happens.

You will be able to change it from your camera's preferences.

---

### Post by Satsat on 2008-08-19
Thanks kostkon,

My camera only offers a print or PTP modes, and it is already set to PTP.

It used to work through kdigicam (but doesn't anymore), but if the camera doesn't have a "mass storage" option, this might explain why ubuntu is not able to mount it ... ?

I'll try with another soft (gphoto), maybe that'll work then.

---

