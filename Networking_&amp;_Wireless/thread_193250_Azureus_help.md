---
title: "Azureus help"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by piracyrocks on 2006-06-09
ok so i have my ports forwarded in my routers config. but i do not know how to open them up on my comuter's firewall.  how do i do this?

also, my router is running dhcp but i want to keep a static address all the time, i did this with windows just by configuring my wireless card to use a static address however i do not know how to do this on linux, could u help?

---

### Post by mlind on 2006-06-09
By default, iptables that's firewall for linux kernel, doesn't have any rules
defined on Ubuntu. So there's no software firewall blocking the traffic.

If you have installed firestarter, use it's gui to open ports for Azureus.

---

### Post by piracyrocks on 2006-06-10
ok, so how do i assign a specific ip address for my wireless card to use

i would do this in windows normally by configuring the TCP/IP properties of my card

how do i do this in linux

---

### Post by piracyrocks on 2006-06-10
any help?? i just wanna know how to assign my wireless card an ip

---

### Post by mlind on 2006-06-10
[QUOTE=piracyrocks]any help?? i just wanna know how to assign my wireless card an ip[/QUOTE]

I guess you can do it using Networking admin tool, or by manually editing
/etc/network/interfaces. see man interfaces. I dunno about configuring wireless
nic, but if you search the forums, you should find answer for that.

---

