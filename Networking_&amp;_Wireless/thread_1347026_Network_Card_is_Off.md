---
title: "Network Card is Off"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by emagine on 2009-12-05
Hello Linux Community,

I recently installed Ubuntu 9.10 on an old family laptop.  It is a Compaq Presario V2000.  Everything works perfectly except no wireless networks are recognized, even though I know there are available networks.  My network controller is detected but is not doing it's job, which is finding available wireless networks!  Using "system testing" I found this out about my network controller:

"Detecting your network controller(s):

Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)"

I know there are similar posts as mine, but I searched and none use the same netork controller.
Please Linux Community, help me out.
Than you.

---

### Post by bkratz on 2009-12-05
> **emagine said:**
> Hello Linux Community,

I recently installed Ubuntu 9.10 on an old family laptop.  It is a Compaq Presario V2000.  Everything works perfectly except no wireless networks are recognized, even though I know there are available networks.  My network controller is detected but is not doing it's job, which is finding available wireless networks!  Using "system testing" I found this out about my network controller:

"Detecting your network controller(s):

Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)"


I know there are similar posts as mine, but I searched and none use the same netork controller.
Please Linux Community, help me out.
Than you.


This pretty much explains adding b43-fwcutter

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by emagine on 2009-12-05
> **bkratz said:**
> This pretty much explains adding b43-fwcutter

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Thank you very much.  Everything works perfectly.  I knew the Linux community was good, but I did not realize I would get a reply right away and have the issue solved.  Thank you so much!

---

### Post by bkratz on 2009-12-05
Please go to the thread tools and mark it solved so other may benefit

---

