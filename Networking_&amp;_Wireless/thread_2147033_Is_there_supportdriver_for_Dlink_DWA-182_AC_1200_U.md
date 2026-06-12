---
title: "Is there support/driver for Dlink DWA-182 AC 1200 USB wireless adapter?"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by levinth on 2013-05-20
I am trying to set up a small cluster interconnected by wireless. I got some AC1200 DWA-1200's. LTS 12.04 and 13.04 do not seem to recognize the device
lsusb displays
 2001:3101 D-Link Corp. 


any hope out there?
d

---

### Post by flash63 on 2013-05-21
No, it looks bad &#8594; try Ndiswrapper

[http://wikidevi.com/wiki/D-Link_DWA-182_rev_A1](http://wikidevi.com/wiki/D-Link_DWA-182_rev_A1)

---

### Post by Wally2512 on 2013-06-07
Have you had any success? I've been able to get the XP driver working on NDISWRAPPER. I can put up some instructions if you like. I am having some interesting things happen though. It works fine for a while but then appears to stop communicating. It still has an IP address and shows as connected but i can't ping the gateway or anything. I've found only a reboot fixes it. I'd be interested to see how you go.

---

