---
title: "Bluetooth USB adapter"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by scubascooby on 2012-02-04
I bought a BlueNext Bn01 USB BT dongle because it allegedly works with Linux but it doesn't even seem to be detected.

>sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

>hcitool dev
Devices:

System/Preferences/Bluetooth says that there is no BlueT adapter.

I tried restarting the service but I think that isn't going to do anything if the dongle is not detected.

What should I try next to get this detected and configured ?

---

### Post by scubascooby on 2012-02-16
Anyone have any ideas ?  The machine is a 1.5GHz Jetway mini. Other USB devices work fine like the HP printer and logitech webcam.

One of the reviewers on amazon seems to have had no problems.

[http://www.amazon.co.uk/Micro-Super-Bluetooth-Dongle-Adaptor/dp/B0018V6JGE](http://www.amazon.co.uk/Micro-Super-Bluetooth-Dongle-Adaptor/dp/B0018V6JGE)

---

### Post by scubascooby on 2012-03-04
Could this be a file permissions issue ?

---

