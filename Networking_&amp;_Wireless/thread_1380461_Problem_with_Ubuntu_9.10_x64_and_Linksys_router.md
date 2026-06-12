---
title: "Problem with Ubuntu 9.10 x64 and Linksys router"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by IgnacioRV on 2010-01-13
Hello everybody, I recently instaled Ubuntu 9.10 x64 on a Dell Inspiron 1545 (wireless card is a Broadcom BCM4312) after a couple of hours I managed to make the drivers work and the laptop was able to recognize and connect to networks. 

However I have this problem: when it connects to my wireless router (Linksys WRT54GL) I can access the desktop pc (running windows) and it's public folders, but I don't have internet connection on the laptop (the desktop has).


To put it simple:
-when I connect the laptop directly to the cable modem _it can_ access internet.
-when I connect the laptop to the Linksys router _it can_ access the lan and other devices, but _it can't_ access internet (firefox tells "Server not found", pings are never answered, it isn't able to trace routes, etc...).


I don't think it would be a router's problem, because with Jaunty x86 everything worked fine and I also run windows 7 in the laptop without connectivity problems.

Any idea?

Thanks for your time!

---

### Post by Leppie on 2010-01-13
apparently ff sometimes defaults to ipv6, try disabling it by going to the about:config page and look for the following key:
```
network.dns.disableIPv6
```
double click it to change the value to true.

alternatively you can try adding a kernel option at boot. edit the grub defaults file:
```
gksudo gedit /etc/default/grub
```
modify the following line like this:
```
GRUB_CMDLINE_LINUX="ipv6.disable=1"
```
run update grub:
```
sudo update-grub
```

---

### Post by IgnacioRV on 2010-03-11
Thanks for the help, but it didn't work, apparently the problem isn't with firefox because any application has internet access. And it neither is an  ipv6 problem because I get an ipv4 address. I also tried writing DNS servers by editing the network connection but it didn't work (so I discard a DNS problem).

Again, this is the situation:

-Connected wired directly to the cable modem -> internet: YES
-Connected wired to the linksys router -> ip: YES; lan access: pings to desktop machine work, pings to linksys router DON'T.
-Connected wireless to the linksys router -> same as above.

Any idea will be welcomed

Thanks!

---

