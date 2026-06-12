---
title: "Maverick 64bit Atheros AR928X series not functionning"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by Cypher2 on 2010-09-09
Hello,

I just loaded the Ubuntu maverick AMD64 beta and to my regret I see that the wireless adapter isn't functioning, even after applying updates through wired connection.

Terminal lspci -v command tells me that the network adapter is present as Atheros AR928X Wireless Network Adapter on PCI-E - rev 01 and that the ath9k module is being used by the kernel.

whats going on?? HELP!

---

### Post by Cypher2 on 2010-12-06
Got a fix from the ubunutu bug crushers and devs:

run in terminal: "sudo rfkill enable all" (minus quotes)

(make sure that "rfkill list all" returns soft and hard switches as on for all selections)

Voila!

---

