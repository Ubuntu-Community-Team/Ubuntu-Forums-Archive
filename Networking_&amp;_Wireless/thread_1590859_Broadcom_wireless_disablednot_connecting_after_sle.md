---
title: "Broadcom wireless disabled/not connecting after sleep in 10.04"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by cshirky on 2010-10-08
Apologies if this has been asked before.

I am running an ACER 1830T with Atheros ethernet and Broadcom 802.11, using LinuxMint 9, which is based on Ubuntu 10.04. 

Neither the Atheros or Broadcom card work out of the box. I followed pytheas22's excellent instructions at [http://ubuntuforums.org/archive/index.php/t-1505697.html](http://ubuntuforums.org/archive/index.php/t-1505697.html), first getting Atheros working using compat-wireless-2.6.tar.bz2, and then, when that disrupted the Broadcom driver, I re-activated it.

When I start up, wireless is always disabled. When I enable it, I can connect to wifi networks. However, when the machine sleeps, wireless is always re-disabled, and when I re-enable it, it will no longer connect, even if it is trying to connect to the same network it was previously connected to.

Any advise about setting wireless to default enabled, through both sleep and re-starts, would be much appreciated.

---

