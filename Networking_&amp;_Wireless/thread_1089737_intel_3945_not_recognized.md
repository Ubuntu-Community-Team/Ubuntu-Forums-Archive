---
title: "intel 3945 not recognized"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by jeremyjjbrown on 2009-03-07
In an attempt to get wep and wap working properly on my laptop I decided to replace my realtek 8187b with an Intel 3945 because the support is supposed to be much better. But, after installing two different cards in my laptop I cannot get the card recognised in either XP or Ubuntu. I tried to find it with lspci and lsusb but it does not show up. The realtek card shows up on lsusb when installed.

Any ideas would be appreciated.

---

### Post by jeremyjjbrown on 2009-03-10
Anyone...

Have I stumped all of you? I'm certainly stumped by this one.

---

### Post by mikewhatever on 2009-03-11
Did you check the module for intel 3945 is loaded?
<lsmod | grep iwl3945>

I think it's also a good idea to blacklist the module for the realtek by adding it to /etc/modprobe.d/blacklist.

---

