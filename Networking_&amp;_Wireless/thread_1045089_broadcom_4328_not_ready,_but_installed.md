---
title: "broadcom 4328 not ready, but installed"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by pimparello on 2009-01-20
Hi there and many thanks in advance,

I am using 
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03

with ubuntu 8.10

After the upgrade from 8.04 (where wifi was nt working) it offered me to acivate the sta-wifi driver. I did so, but now it says, that the driver is activated, but not in use. iwconfig does not find any wifi extensions. 

What can I do, to acitvate my wifi? (of course: it's turned on and I tried to reboot after the activation)

Thanks!

---

### Post by Ayuthia on 2009-01-20
> **pimparello said:**
> Hi there and many thanks in advance,

I am using 
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03

with ubuntu 8.10

After the upgrade from 8.04 (where wifi was nt working) it offered me to acivate the sta-wifi driver. I did so, but now it says, that the driver is activated, but not in use. iwconfig does not find any wifi extensions. 

What can I do, to acitvate my wifi? (of course: it's turned on and I tried to reboot after the activation)

Thanks!

Can you post the results of lshw -C network?  I just want to verify that the wl module is the driver that is being used.

---

### Post by pimparello on 2009-01-24
Thanks, that helped me. Together with blacklisting ssb I could solve it. Thanks!

---

