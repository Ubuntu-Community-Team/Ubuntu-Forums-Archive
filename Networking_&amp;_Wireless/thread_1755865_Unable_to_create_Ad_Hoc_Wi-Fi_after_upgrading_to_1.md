---
title: "Unable to create Ad Hoc Wi-Fi after upgrading to 11.04"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by kobie on 2011-05-11
Hi all,

So here's the deal: I was happily using 10.10 to create ad-hoc wifi networks on my Dell Vostro 3700 with Broadcom BCM4313.  Everything worked 100%

After upgrading to 11.04, I am still able to connect to existing Wi-Fi networks, BUT I can't create ad-hoc networks anymore for some reason!

Specifically, NetworkManager is failing with its association request to the driver.  Repeatedly.  Until I get another screen in the GUI prompting me for the password details.  Ad Ininitum.

Any ideas?  Syslog attached.

---

### Post by kobie on 2011-05-11
Oh, this  seems related:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/756482](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/756482)

---

### Post by jmiggal on 2011-05-12
Adhoc networks do work fine (your link refers to a post in which adhoc networks were not supported). The problem is that I do not know how to change the beacon interval.

Any idea?
Many thanks

---

### Post by kobie on 2011-05-12
Err, I'm not sure what you mean. Creating ad-hoc networks after upgrading to Natty is certainly not "fine", as I described in my post.

If you are having a problem with setting your beacon interval, please start a new thread.

---

### Post by kobie on 2011-05-14
Ugh, the problem seems to have resolved itself without any tinkering, so I can only assume it was due to some update which was released.   :guitar:

---

