---
title: "ZTE MF100 Stopped Working around 26/10/2010"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by SquirrelOfDoom on 2010-05-27
Hi all,

Bit of an odd one this. My ZTE MF100 (on O2) had been working happily on my 10.04 laptop, but today is not recognised - e.g. no device listed by lsusb, nor error messages in dmesg at boot.

Re-plugging the device after boot gives me dmesg errors:
[ 1691.680162] usb 5-2: new full speed USB device using uhci_hcd and address 9
[ 1691.810163] usb 5-2: device descriptor read/64, error -71
[ 1691.990379] hub 5-0:1.0: unable to enumerate USB device on port 2
[ 1693.381839] usb 5-2: new full speed USB device using uhci_hcd and address 10
[ 1693.511559] usb 5-2: device descriptor read/64, error -71
[ 1693.750289] usb 5-2: device descriptor read/64, error -71
[ 1693.980081] usb 5-2: new full speed USB device using uhci_hcd and address 11
[ 1694.110155] usb 5-2: device descriptor read/64, error -71
[ 1694.350282] usb 5-2: device descriptor read/64, error -71
[ 1694.580184] usb 5-2: new full speed USB device using uhci_hcd and address 12
[ 1695.009565] usb 5-2: device not accepting address 12, error -71
[ 1695.061592] hub 5-0:1.0: unable to enumerate USB device on port 2

I can't see any suspicious entries in /var/log/dpkg, but I'm attaching a copy of the recent anyway, along with output for lsusb -vv.

Any help/suggestions on what I need to do to get this working again would be greatly appreciated.

Phil

---

### Post by alexfish on 2010-05-27
hi

this is the second post I have seen concerning laptop with this problem

going to be hard to resolve if no usb devices can be seen , does it recognise any other usb devices.

can you also check in the system monitor and see if  "hald" is running

thanks in advance

alexfish

---

### Post by alexfish on 2010-05-28
hi

done same upgrade, I think 

network manager fails to connect ,then modem not recognised

As a workaround ,try disconnect the modem and re-connect then use gnomeppp , wvdial 
or ppp . ppp should be on the system , to set up 

Code:

sudo pppconfig

does this help

regards

alexfish

PS your you living in the future , look at your title date

---

### Post by SquirrelOfDoom on 2010-05-29
Well, there's good and bad news... this was a faulty dongle.

So the good news is a replacement dongle of the same make works.

The bad that this seems to be a very flimsy bit of kit, that annoyingly shows the same status LED when working as when broken....

Thanks for the suggestions.

Phil

---

