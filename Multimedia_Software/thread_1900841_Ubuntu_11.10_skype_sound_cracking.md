---
title: "Ubuntu 11.10 skype sound cracking"
date: 2011-12-27
forum: Multimedia Software
---

### Post by qpens on 2011-12-27
Hi,
I have problem with skype 2.2.0.35 any sound from skype  (ringing, mic...) is cracking. In Ubuntu every thing is working fine  like youtube or mp3 only sounds In skype are buzzing. How can I solve  this problem?

---

### Post by qpens on 2012-01-04
Problem solved change the following line in /etc/pulse/default.pa

    load-module module-udev-detect

    with :

    load-module module-udev-detect tsched=0

---

