---
title: "Latest ubuntu no wireless drivers"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by renegadeandy on 2011-08-06
Hi!

I had 10.04 and my wireless worked out of the box.

I just installed the latest and my wireless says "firmware missing"

The card is : 00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


Help!

---

### Post by westie457 on 2011-08-06
> **renegadeandy said:**
> Hi!

I had 10.04 and my wireless worked out of the box.

I just installed the latest and my wireless says "firmware missing"

The card is : 00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


Help!
Go to here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Follow the steps to install the correct drivers.
If you have already activated the STA driver via Additional Drivers you should deactivate it. 

Now reboot, if you installed the correct drivers wireless will be working. If not working choose the other driver and remove the incorrect one using ```
sudo apt-get remove --purge <name of driver>
``` substitute the <.....> with the correct name of the driver.

Reboot again.

---

