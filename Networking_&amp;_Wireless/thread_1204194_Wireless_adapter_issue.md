---
title: "Wireless adapter issue"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by davbet82 on 2009-07-04
Hello to everybody. I'm new to Ubuntu. I have installed the last version Jaunty Jackalope and it works fine. The only thing does not work fine is wireless adapter. Ubuntu see the adapter but as "Not Ready". So the adapter isn't able to work and intercept wireless networks. Any solutions? I have an HP Pavillion dv8000 with Broadcom 4311 card.

---

### Post by t0mppa on 2009-07-04
Likely just a driver issue, those are fairly common with the latest versions. Open up terminal and run **lshw -C network** and post back with the output to find out what driver (if any) is getting associated with your interface.

---

