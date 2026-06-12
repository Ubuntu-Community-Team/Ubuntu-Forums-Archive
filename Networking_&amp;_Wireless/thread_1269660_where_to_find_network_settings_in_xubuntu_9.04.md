---
title: "where to find network settings in xubuntu 9.04"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by inearlygaveup on 2009-09-18
Just installed xubuntu-9.04-alternate everything is fine except -
If I don't start my internet router before I start xubuntu my internet connection won't start.
If I reboot it works fine - any help appreciated - can't even find the network settings.

---

### Post by jward3010 on 2009-09-18
I don't know if it's installed in Xubuntu but go to a terminal and type:
```
sudo dhclient
```
after your router is switched on.

This will make Xubuntu search for a DHCP server on your network, which would be your router and it should get you an IP address.

Bada Bing!

---

### Post by kerry_s on 2009-09-18
> **inearlygaveup said:**
> Just installed xubuntu-9.04-alternate everything is fine except -
If I don't start my internet router before I start xubuntu my internet connection won't start.
If I reboot it works fine - any help appreciated - can't even find the network settings.

right click the icon-> edit connections
you can also enable/disable to bring it up/down.

---

### Post by inearlygaveup on 2009-09-19
Thanks all

kerry_s  - yes found all that thanks but it just keeps playing up, sometimes it connects ok other times I have to reboot.
I was looking for some way of making it hold its settings (is this a bug - or is it just my setup)

---

### Post by kerry_s on 2009-09-19
> **inearlygaveup said:**
> Thanks all

kerry_s  - yes found all that thanks but it just keeps playing up, sometimes it connects ok other times I have to reboot.
I was looking for some way of making it hold its settings (is this a bug - or is it just my setup)

i have noticed on some machines, you have to set it more than once, meaning delete the connection & set it up again. i had to do that like 3 times on this machine cause the wireless was not auto connecting when i resume from suspend, once it took, it's been working perfectly.

---

