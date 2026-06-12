---
title: "Ethernet Connection Dropping"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by 00b00nt00 on 2011-05-26
Ubuntu 11.04 64bit

So I built my first PC around a Gigabyte GA-880GM-USB3L AM3+ board: 

[http://www.gigabyte.com/products/product-page.aspx?pid=3828#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3828#sp)

It has a Realtek 8111E chip (10/100/1000 Mbit) LAN.

The problem is twofold; firstly, while I can connect to the internet / network, speeds are very slow, maybe 70KiB/s download speed at best, and secondly, the connection appears to stall and I can only resume it by enabling / disabling the network connection from the panel menu.

I dual boot Windows 7 64bit, which does not exhibit this problem.

Ideas? Wait for 11.10?

---

### Post by 00b00nt00 on 2011-05-30
bump

---

### Post by dandnsmith on 2011-05-30
Consider changing to a different linux Ubuntu 10.10 or Mint 10 release?

Look at [this thread](http://fossplanet.com/f10/failure-configure-wired-connection-realtek-8111e-boardlan-controller-121697/) in case it sparks any thoughts.

---

### Post by 00b00nt00 on 2011-06-11
Basically it's a bug: Ubuntu installs the r8169 driver instead of the r8168 driver. And it's an old one, too:


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252307](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252307)


The solution is to remove and blacklist the r8169 driver and download/build/install the r8168 driver from the realtec web-site. It's a bit of a pain in the butt, but the whole procedure shouldn't take more than 5-10 minutes.

---

