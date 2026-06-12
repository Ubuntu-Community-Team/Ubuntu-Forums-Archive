---
title: "Bluetooth PAN stopped working in Maverick"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by alkach on 2010-10-27
Hi, gentlemen!

I had Bluetooth PAN network working fine in Lucid. For some reason (mainly hardware) I had to upgrade to Maveric. After that my Bluetooth PAN network stopped working at all. I found out that server host do not even expose any PAN or GN profiles. The only profile it exposes is "Hands-free audio". Setting PAND_ENABLE=1 in '/etc/default/bluetooth' did not have any affect. I attempted to start PAND in listening mode and it exposed PAN profile but any connection was unsuccessful. When I try to connect to any other PAN profile it also had no success with 'Permission denied' message.

I would be greatful for any commet of this problem.

---

### Post by spennig on 2010-10-30
[https://bugs.launchpad.net/bugs/654667](https://bugs.launchpad.net/bugs/654667)

Perhaps you'd like to add an 'Affects me too' in the (futile) hope that someone might notice it.

---

