---
title: "Slow transfer speeds Ubuntu 10.04 &gt; XP"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by Hevydani on 2010-08-04
Hi I've just managed to access my windows share from Ubuntu but am now getting write speeds (to xp share) of only 9MB/s over my wired network, anyone have any ideas as to why this may be? I've googled but can find no specific answer.

My NIC is: 

Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

(from lspci) on a Dell studio 1737)

---

### Post by cj.surrusco on 2010-08-04
9MB/s is just about where you should be for a 100mbit connection. You may have gigabit on your ethernet controller, but you need to make sure all of the connections to your XP machine are gigabit. I'm talking about all cables (cat5e or cat6), hubs, router, and ethernet controller on the XP machine. They all need to have gigabit speeds in order for you to get faster transfer rates.

---

### Post by Hevydani on 2010-08-04
Ah ok thank you for the quick reply :) I shall check it out.

---

### Post by Quintus77 on 2010-09-20
Hi, Hevydani, i'm looking to do exactly what you've done with the file share. I have a few questions if you could help me out. I have a similar ethernet controller and was wondering what driver you have to have it working? Also did you connect the computers direct with a single cable?

thanks

---

