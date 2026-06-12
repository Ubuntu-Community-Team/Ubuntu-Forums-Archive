---
title: "Wireless problems after upgrading to 12.04"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by Jon30 on 2012-05-09
**Upgraded to 12.04 and wireless stopped working on Dell Inspiron**
Just thought I'd post my findings on the above problem that I experienced. Having searched through all the info out there I was utterly bewildered as to how to fix this. Everytime I tried to activate the Broadcom STA Proprietary Driver that was displayed in Settings / Additional Drivers it displayed an error message directing me to look in jockey log something or other. As you probably have guessed I'm a novice and so I got nothing from looking in the specified log file. I tried unblacklisting various things to no avail. 

Anyway, in the end the answer came easily. I went into Ubuntu Software Centre and searched for Broadcom. This brought up lots of things, none of which were installed except a Broadcom driver! I uninstalled the driver. I restarted my pc. I went back into settings > additional drivers and tried to activate the Brodcom STA Driver that it found. Hey presto! It worked!!

---

