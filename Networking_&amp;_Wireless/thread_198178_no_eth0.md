---
title: "no eth0?"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by soongwoo on 2006-06-16
HDD is moved to another machine which has same hardware.
(Of course, MAC address of on-board NIC should be different.)
The HDD has Ubuntu 6.06 and NIC was configured as eth0.

After moving HDD, on-board NIC is eth1.
Is there a way to rename the NIC as eth0?

soongwoo

---

### Post by soongwoo on 2006-06-16
I found a solution from other thread.
Just edit /etc/iftab.

For my case, the file has defined eth0 with prevous machine's MAC.
So, I chnaged the MAC with current one.
That's it.

soongwoo

---

