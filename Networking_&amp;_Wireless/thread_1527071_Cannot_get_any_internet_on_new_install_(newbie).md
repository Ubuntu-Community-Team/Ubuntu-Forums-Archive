---
title: "Cannot get any internet on new install (newbie)"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by WeShallBurn90 on 2010-07-08
Hi, I am new to Linux. I'm running Ubuntu 10.04 Lucid Lynx.

I Have a HP Compaq nx6110 with a Intel PRO/Wireless 2200BG.

When I go into my network tools I have loopback interface, ethernet interface (eth0) & (eth1) but cannot connect in any way
and have no indicator on the panel.

Any help would be much appreciated.

Thanks

---

### Post by Iowan on 2010-07-08
I presume the machine is set up for DHCP address (unless you manually configured an address...).
From a terminal (Applications>Accessories>Terminal) check (post if possible) **ifconfig -a**. That should show if both/either of your interfaces has an IP address. **sudo lshw -C network** will provide more information about your interfaces (drivers, aliases, etc...).

---

### Post by nida520 on 2010-07-08
wow
 
i get here

---

### Post by cchhrriiss121212 on 2010-07-09
Studio does not come with network manager:
[http://ubuntuforums.org/showthread.php?t=1525705](http://ubuntuforums.org/showthread.php?t=1525705)

---

