---
title: "Somebody. please."
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by tranzue on 2009-10-23
Hello all,

Somebody please help me with this problem.

I am dual-booting Windows 7 alongside the newest Ubuntu.  Well, when I installed Ubuntu, it correctly found my wireless card, and I downloaded it.  I can see internet connections, but it will not connect.  It used to sometimes connect, but now it seems like it wont connect at all.

Does anybody know why this is happening? When I run sudo lshw -C network, it says DISABLED but it isn't disabled.  I have a Dell Inspiron 1501.

Any help is greatly appreciated

---

### Post by rwt911 on 2009-10-23
What kind of wireless card is it? Is it a Dell 1390 Mini Wireless Card?

---

### Post by tranzue on 2009-10-23
The card is a Dell 1390 802.11g Mini Wireless Card

---

### Post by rwt911 on 2009-10-25
You may want to upgrade the kernel.

First try to see if there is already an update,

> sudo apt-get updateIf that doesn't fix it you can download a precompiled kernel from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/").

---

