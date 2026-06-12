---
title: "Intel Pro/Wireless 3945ABG stopped working"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by piojominero on 2011-08-08
HI:

I'm new to linux. I've just installed Ubuntu 11.04. It has all been going ok, but the wireless just stopped working all of a sudden. The indicator light turned off and when I tried to turn it back on (Fn+F2) nothing happens. 
In the menu on the upper right corner I see 'Enable Networking' is checked, but 'Enable Wireless' cannot be modified.
I have a Dell Inspiron 6400 and the wireless device is an Intel Pro/Wireless 3945ABG.
I have tried to follow some of the threads on this forum on similar cases, but the ones that were comprehensible to me did not work (or I actually might not have understood them either).
Please help

---

### Post by bkratz on 2011-08-08
> **piojominero said:**
> HI:

I'm new to linux. I've just installed Ubuntu 11.04. It has all been going ok, but the wireless just stopped working all of a sudden. The indicator light turned off and when I tried to turn it back on (Fn+F2) nothing happens. 
In the menu on the upper right corner I see 'Enable Networking' is checked, but 'Enable Wireless' cannot be modified.
I have a Dell Inspiron 6400 and the wireless device is an Intel Pro/Wireless 3945ABG.
I have tried to follow some of the threads on this forum on similar cases, but the ones that were comprehensible to me did not work (or I actually might not have understood them either).
Please help


Can you post the output of the following?

rfkill list all

---

### Post by piojominero on 2011-08-08
This is what I get:


0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by piojominero on 2011-08-08
Sometimes, when I restart the computer, the wireless works; but if the signal is lost the LED on my laptop turns off and I cannot reconnect. Also, in these strange cases that the wireless works when I restart I can manually turn it off (Fn+F2), but nothing happens when I try to switch it back on.

---

