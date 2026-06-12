---
title: "Wirelss Not Working on 8.04 Server Edition"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by Valkhorn on 2009-02-09
So I went out to Best Buy and got this laptop:

[http://www.bestbuy.com/site/olspage.jsp?skuId=9167689&type=product&id=1218041150488](http://www.bestbuy.com/site/olspage.jsp?skuId=9167689&type=product&id=1218041150488)

It's an HP dv4-1225x

It's not a bad machine for Linux and everything seems to work fine except for one thing - and that's the wireless access.

I have 8.04 Server Edition installed with the Gnome Ubuntu Desktop.

Just so you guys know, this laptop has a wireless button at the top of the keyboard which allows you to enable/disable the wireless. In Windows, I can turn the wireless on and off without a problem and the LED goes from Red to Blue when it's inactive/active.

However in Ubuntu 8.04 I can not get the wireless to connect.

First, when I run lspci, I see that the Broadcom Wireless driver is listed. Second, I've tried checking the network status and wlan0 is not listed. Third, for the wireless adapter, it says Network Unclaimed when I run "lshw -C network".

I've attempted to install the ndiswrappers and I've attempted to connect to the device through the wrappers. The driver is installed but no matter what I cannot get the wireless network to become online.

Furthermore, the switch for wireless refuses to turn on - and I think this could be the culprit. Yet I can find no help anywhere on these particular laptops with this wireless button and why I can't seem to turn it on.

The other buttons for volume and muting work fine, but the wireless doesn't.

Any help?

---

