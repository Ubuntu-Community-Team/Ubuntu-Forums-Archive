---
title: "mobidata 100EU usb edge modem"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by shantanu18 on 2010-04-27
I am using ubuntu 9.10. I recently bought a mobidata 100EU modem. It uses usb multimode(storage device and modem).So i have used to usb_modeswitch to change the mode of my modem from storage to modem. But failed to do the change.I got success with another modem (philips talktalk).
usb_modeswitch.conf file for philips talktalk modem:
```

########################################################
# Philips TalkTalk (NXP Semiconductors "Dragonfly")

DefaultVendor= 0x0471
DefaultProduct=0x1237

TargetVendor=  0x0471
[COLOR="Red"]TargetProductList="1206,1234"[/COLOR]

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000030000000000000000000000"

```

My question, what is the [COLOR="Red"]TargetProductList or TargetClass[/COLOR] of my modem(mobidata 100EU) to switch modem mode.

---

### Post by pdc on 2010-04-27
you tell us what

> lsusb

gives you with the mobidata plugged in

---

### Post by shantanu18 on 2010-04-28
> 
lsusb

This command gives only the the vendor id and  product id  of usb-storage mode(0x04fc:0x2140). But i need the product id of modem mode.
plz help...:(

---

### Post by pdc on 2010-04-29
> I got success with another modem (philips talktalk).
usb_modeswitch.conf file for philips talktalk modem:

hmmmmmmmmmmmmm

yes, that because it is recognised by usbmodeswitch

join their forum

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

seek Josh's help

---

