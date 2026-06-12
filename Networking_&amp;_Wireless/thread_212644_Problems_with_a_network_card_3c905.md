---
title: "Problems with a network card 3c905"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by wendigox on 2006-07-10
Problems with a network card 3c905 

Hello to all! 

I am basically a mac user reason why I do not have much experience as far as the handling of commands and compilations, but for kubuntu 5,1 I will like to learn more of Linux, reason why sue is thanked for aid. 

The problem is: I found in the university a Fujitsu PII 400mhz with 128MB of ram and a card of network 3c905-C-TX/TX-M. 

Everything goes of wonder, everything except the network card. When I type: 
> $ discover Ethernet 
I get:
> com Corporation 3c905-TX/TX-m [Tornado]

I know att the module is installed because when type:
> $ lsmod | grep 3c59x
I get:
> 3c59x      37544 0
mii       5248 1 3c59x 
 I did also added the line ***3c59x*** in the file modules:
> $ kdesu /etc/modules the line 3c59x

And in interfaces too the line ***eth0*** and ***iface eth0 inet dhc***:
> $ kdesu /etc/network/interfaces

And efter reboot... nothing!

When I type ***ifconfig*** that only gives me details on ***lo*** nothing of ***eth0***. Some thing more I can do? thanks...

---

### Post by bikeboy on 2006-07-10
You could try ```
sudo modprobe 3c59x
```However it's a long shot since you tried adding it to /etc/modules anyway.

At least using modprobe doesn't require a restart, so it's good for testing.

---

### Post by wendigox on 2006-07-10
I did type ***sudo modprobe 3c59x*** but, efter type my password, give me nothing. I reboot again and nothing...

If I type ***lspci*** I get this in the 7 line:
***0000:00:14.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev74)***

Another idea?
thanks!

---

