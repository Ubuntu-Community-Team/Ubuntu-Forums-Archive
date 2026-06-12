---
title: "Setting eth2 as default"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by radicaldreamer on 2005-12-19
I have a dell inspiron 8200 laptop and it has a built in wireless card, well it doesnt work by default and rather than screw around with getting it to work i just use my cisco card. The problem is every time i reboot i have to deactivate my built in card and then activate the cisco. Is there a way i can just set the cisco to default?

---

### Post by Lambert on 2005-12-19
edit your /etc/network/interfaces file

delete anything that is for the internal device and make sure your cards interface has an auto xxxx line at the end of it.

---

