---
title: "xnetcardconfig and NetworkManager"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by oddiofile on 2009-05-16
I want to set a fixed IP address for a wired ethernet. 
Normally I either edit /etc/network/interfaces manually, 
or run "xnetcardconfig". But none of these approaches seems to "stick" after the next reboot.

I guess it's because of NetworkManager that is running instead of the old /etc/init.d/networking.

So I was wondering. If I want to use NetworkManager, what is the graphical wizard I can run to configure the interfaces?

I assume if I want to use xnetcardconfig, I must disable NetworkManager and use /etc/init.d/networking instead, correct?

---

