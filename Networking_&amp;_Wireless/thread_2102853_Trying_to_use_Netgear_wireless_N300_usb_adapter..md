---
title: "Trying to use Netgear wireless N300 usb adapter."
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by DatSik on 2013-01-08
Ok my dell's internal wifi card works fine, but i bought a usb adapter to obtain a stronger signal but i cant seem to get it to work and ditch my internal all togather, it has the proper drivers.

here is a little output if it helps
Bus 002 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

---

### Post by praseodym on 2013-01-08
Hi,

which Ubuntu-version do you use? Unfortunately, there are no working native Linux drivers for Broadcom-USB-devices. Please show:

```
lsb_release -a
```
For Ubuntu 12.04 install the packages
[LIST]
[*]ndisgtk
[*]linux-headers-generic
[*]dkms
[*]build-essential
[*]ndiswrapper-dkms
[/LIST]
via Software center. With Ubuntu 12.10 you need to compile "by hand". For this you need to install first:
```

linux-headers-generic
build-essential
```, but only these!

---

### Post by kurt18947 on 2013-01-08
Any chance of returning it?  There are better choices that are plug 'n' play.  As praseodym says, it *can* be made to work but may not be simple.

---

### Post by haqking on 2013-01-08
To the OP see here for Netgear WNA 3100 support [http://ubuntuforums.org/showthread.php?t=1965989](http://ubuntuforums.org/showthread.php?t=1965989)

---

