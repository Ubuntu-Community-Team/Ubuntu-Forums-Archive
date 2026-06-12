---
title: "Can't restart network"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by raelanne on 2012-01-06
[SIZE=2]Hey guys. I edited [/SIZE][FONT=Courier New][SIZE=2]/etc/networking/interfaces[/SIZE][/FONT][SIZE=2] and added one more ip address. But i couldn't restart the network. when i type [FONT=Courier New]sudo /etc/init.d/networking restart[/FONT], this error appears... does anyone know how to fix this? please and thank you[/SIZE]
[SIZE=2]
[/SIZE] [FONT=Courier New][SIZE=2]* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.[/SIZE][/FONT]

---

### Post by chili555 on 2012-01-06
> Hey guys. I edited /etc/network[COLOR="Red"]ing[/COLOR]/interfaces and added one more ip address.Did you mean /etc/network/interfaces, I hope?

In a few words, I believe that is telling you that we can't start eth0 automatically as you've directed in /etc/network/interfaces, because there is no eth0.

Is there?```
ifconfig
```Mind if we have a look?```
cat /etc/network/interfaces
cat /etc/networking/interfaces
```

---

