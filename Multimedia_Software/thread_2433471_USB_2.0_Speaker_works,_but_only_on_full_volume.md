---
title: "USB 2.0 Speaker works, but only on full volume"
date: 2019-12-19
forum: Multimedia Software
---

### Post by dwater on 2019-12-19
Hi,

I bought a USB-2 speaker to fit under my monitor, and it works but only when the system is on full volume. If I reduce the volume using my keyboard's volume control even by one increment, then it goes silent. If I use the 'System Volume' slider in the Sound settings, then I can get more control and it seems like there is some 'range', but it seems like the 'zero' is at about 95% (visual guess cine the slider doesn't give a 'current' percentage, annoyingly).

I am using the 'Analogue Output - USB2.0 Device' option on the 'Output Device'. If I choose the 'Digital Output (S/PDIF) - USB2.0 Device', then the volume slider makes no different and it is on 'full' all the time.

Does anyone have any idea how to fix this so I can get a better control over the volume?

Max.

card 1: Device [USB2.0 Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

[ 1065.715167] usb 1-1.1: USB disconnect, device number 4
[ 1071.836736] usb 1-1.1: new full-speed USB device number 9 using xhci_hcd
[ 1071.951634] usb 1-1.1: New USB device found, idVendor=1908, idProduct=2070, bcdDevice= 1.00
[ 1071.951639] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1071.951643] usb 1-1.1: Product: USB2.0 Device
[ 1071.951646] usb 1-1.1: Manufacturer: Generic
[ 1071.951649] usb 1-1.1: SerialNumber: 20130100ph0
[ 1071.954432] usb 1-1.1: 1:1: cannot get freq at ep 0x2
[ 1072.018473] usb 1-1.1: 1:1: cannot get freq at ep 0x2
[ 1072.035034] usb 1-1.1: 1:1: cannot get freq at ep 0x2



[https://www.amazon.co.uk/gp/product/B07W1KN1XD/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B07W1KN1XD/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

Distributor ID:	Ubuntu
Description:	Ubuntu 19.10
Release:	19.10
Codename:	eoan

---

### Post by dwater on 2019-12-24
It seems no one has anything to say about this, so I opened a bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1857335](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1857335)

---

### Post by CelticWarrior on 2019-12-24
You should have perhaps tried it in another computer / different OS before reporting a bug.

---

### Post by dwater on 2019-12-25
Eh? Oh you mean I should have *mentioned* that I had tried the speaker on another device/os and it works fine...not sure how that makes any difference, but yeah, perhaps. I added a comment to that effect.

---

### Post by CelticWarrior on 2019-12-25
Yes, because you didn't mention such troubleshooting in the first draft, I assumed you didn't do it.

---

