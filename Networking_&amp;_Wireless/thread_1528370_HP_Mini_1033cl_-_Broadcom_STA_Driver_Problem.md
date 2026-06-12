---
title: "HP Mini 1033cl - Broadcom STA Driver Problem"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by Antimatter47 on 2010-07-10
Hello all,

I have just installed Ubuntu 10.04 Netbook Edition on an HP Mini 1033cl.  Everything works great, except I can't connect to any wireless networks.  The network connections menu always shows "disconnected" under "Wireless Networks", with no networks detected.  If I choose "Connect to Hidden Wireless Network" and manually enter the details, it still is not able to connect.

The netbook hardware support wiki page mentions having to uninstall and reinstall the broadcom driver after every reboot with this model.  I have rebooted, uninstalled and reinstalled many times, with no luck.  I tried using Synaptic to "completely remove" the driver package.  After that, the next time I opened the hardware drivers app I got the option of installing the B43 driver, not just the STA driver.  I tried the B43 driver, but it didn't work either.

Any suggestions?

---

### Post by Antimatter47 on 2010-07-12
Anyone?

---

### Post by moteprime on 2010-10-25
I am helping my brother installing Ubuntu 10.10 on his hp 1033cl and we are having the same problem.
Can anybody help?

---

### Post by moteprime on 2010-10-26
We got it working, using ndiswrapper and the xp driver.

---

