---
title: "Tata Photo Card no longer detected after firmware upgrade"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by jdogzilla on 2010-05-14
Hello, I am using Ubuntu 10.04.  The Tata Photon+ card Huwai EC1260 was working flawlessly.  However, I recently did a firmware upgrade on the card that was provided by Tata Indicom for it to work on Windows 7.  After that, the card is no longer detected as a mobile modem in Ubuntu.  If I try to add a new connection, all options are disabled (whereas earlier Tata Photon card would appear automatically).  

The product ID has changed.  What change can I make to Ubuntu to enable it to detect the card again. 

used to be vendor=0×12d1 product=0×140b
now is vendor=0×12d1 product=0×1446

---

### Post by jdogzilla on 2010-05-17
Bump!!!

---

### Post by Tatateleserviceslimited on 2010-05-19
> **jdogzilla said:**
> Hello, I am using Ubuntu 10.04.  The Tata Photon+ card Huwai EC1260 was working flawlessly.  However, I recently did a firmware upgrade on the card that was provided by Tata Indicom for it to work on Windows 7.  After that, the card is no longer detected as a mobile modem in Ubuntu.  If I try to add a new connection, all options are disabled (whereas earlier Tata Photon card would appear automatically).  

The product ID has changed.  What change can I make to Ubuntu to enable it to detect the card again. 

used to be vendor=0×12d1 product=0×140b
now is vendor=0×12d1 product=0×1446



Hi, We would like   to inform you that currently the Photon+ devices are not compatible with   ubuntu.

---

### Post by alexfish on 2010-05-19
hi

[I]I think we would like to know why

[/I]also do you think you could supply the missing details highlighted in blue[I]

########################################################
# Tata Photon Card Huwai EC1260
#
# Contributor:** Possibly Tatateleserviceslimited**

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1446

;TargetVendor=  0x[COLOR=Blue]XXXX [/COLOR]
;TargetProduct= 0x[COLOR=Blue]XXXX[/COLOR]

;MessageContent="[COLOR=Blue]xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx[/COLOR]"

Serving you with best attention at all times

[/I]alexfish

---

### Post by jdogzilla on 2010-05-26
;DefaultVendor= 0x12d1
;DefaultProduct= 0x140b

;TargetVendor= 0x12d1
;TargetProduct= 0x1446

;MessageContent="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx xxxxxxxxxxxx"

I'm not quite sure where to get this Message Content text from?

---

### Post by alexfish on 2010-05-26
hi

I was not ask of you this info but that of tata ,  yes I know what you have posted is for the old device
but have just found
########################################################
# Huawei E270+  (HSPA+ modem)
# Huawei E1762
# Huawei E1820
#
# Contributor: Paranoid Paranoia

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1446

;TargetVendor=   0x12d1
;TargetProduct=  0x14ac

;MessageContent="55534243123456780000000000000011060000000000000000000000000000"

                                 according to the latest usb data this device is listed 

try to upgrade both the usb modeswitch and the modeswitch data at

 [Debian Repository]("http://packages.debian.org/usb-modeswitch").  

or

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by jdogzilla on 2010-06-02
Thanks much ... doing the update worked!:)

---

