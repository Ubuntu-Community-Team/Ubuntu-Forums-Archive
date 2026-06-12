---
title: "Wireless is disabled on 9.10"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by paw160 on 2010-07-16
Hi,

I cannot seem to enable my wireless connection in 9.10.  I know that the connection WAS WORKING maybe a month or so ago.  However, 99% of the time I am wired.

Here's the facts:

I am using a BCM4312
It shows up in lspci
The drivers are loaded (wl, lib80211, and lib80211_crypt_tkip)

If I look at System->Administration->Hardware Drivers the Broadcom STA driver is active.

dmesg says that the interface is eth1 but then moves it to eth2

If I click on the network icon in the panel I have options for connecting to eth0 (wired lan which works fine) but under "Wireless Networks" it says "Wireless is disabled" in gray.

This WAS WORKING!  What happened and how do I get my wireless back?

Thanks,
Pat

---

### Post by Metaljaz on 2010-07-16
check to make sure you did not accidentally turn off your wireless. its usually a function key like F2. Look at the keyboard for the antenna icon then turn it on. Or it could be another series of functions keys.

---

### Post by Iowan on 2010-07-16
[Here]("http://ubuntuforums.org/showthread.php?t=1527415")  is a similar thread. Anything show up as a result (from a terminal) of **rfkill list**

---

