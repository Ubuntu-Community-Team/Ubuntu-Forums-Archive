---
title: "Broadcom bcm4311 st wl driver not working after last update"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by majikins on 2009-01-12
Hello

Running hardy 8.04.1 with the latest update kernel 2.6.24-23-generic and corresponding restricted modules.

When working on 2.6.24-22-generic my broadcom driver worked perfectly with the restricted sta driver. 

Now even tho the driver is enabled and card detected I get 

"Failed to read scan data : Invalid argument" when I do sudo iwlist eth1

I tried logging in with the previous kernel but that does not work anymore.

Please can someone help?

D

---

### Post by shafi on 2009-01-12
> **majikins said:**
> Hello

Running hardy 8.04.1 with the latest update kernel 2.6.24-23-generic and corresponding restricted modules.

When working on 2.6.24-22-generic my broadcom driver worked perfectly with the restricted sta driver. 

Now even tho the driver is enabled and card detected I get 

"Failed to read scan data : Invalid argument" when I do sudo iwlist eth1

I tried logging in with the previous kernel but that does not work anymore.

Please can someone help?

D

After kernel upgrade you need to install the driver again,
then the problem will be solved.

---

### Post by majikins on 2009-01-15
Hi

This does not work for me.  In order to install the driver again, I disabled the driver in the hardware-restricted utility, rebooted and enabled again.

Same problem.  What am I doing wrong?

D

---

### Post by majikins on 2009-01-24
Ok its now working - I'm not sure what changed as I rebooted the last time and it still did not work.  I had to reboot again and I tested just in case ---- it works!

---

