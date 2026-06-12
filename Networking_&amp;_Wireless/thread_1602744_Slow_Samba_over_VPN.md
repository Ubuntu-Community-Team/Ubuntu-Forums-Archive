---
title: "Slow Samba over VPN"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by ccreese on 2010-10-21
Hello.

I have Samba on Ibex running over VPN, and am having problems with speed reading and writing from XP and 7 boxes. It takes, for example, 16 minutes to transfer four files for a total of 1.2MB.

I assume that this problem is due to SMB block size and the latency I'm dealing with, always between 200 and 500ms. 

How can I properly configure client and server to negotiate a suitable block size / tcp window to reduce the number of transactions and up the speed?

Thanks,
Colin

---

