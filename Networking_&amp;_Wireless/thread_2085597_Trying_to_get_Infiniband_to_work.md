---
title: "Trying to get Infiniband to work"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by GodAtum on 2012-11-18
Hi all,

I have two Mellanox infiniband cards, one on my Win 7 PC and one of my Ubuntu 12.04 64bit PCs. I have been following these instructions ([http://davidhunt.ie/wp/?p=2291](http://davidhunt.ie/wp/?p=2291)). I got up to:
> Then add the relevant entries for the interface into /etc/network/interfaces file: auto ib0 iface ib0 inet static address 192.168.1.1 netmask 255.255.255.0However when I try to restart the service it says it cannot find the ib0 device. The kernel recognises it: >                               05:00.0 Memory controller: Mellanox Technologies MT25208 [InfiniHost III Ex HCA Flash Recovery] (rev a0)                      . However is it not listed in ifconfig.

Any help will be greatly appreciated.

---

### Post by GodAtum on 2012-11-23
Anyone able to advise please?

---

### Post by markanders on 2013-01-09
Not sure if you ever solved your issue but I had something similar, try adding the following to/etc/modules:

mlx4_ib

I'm working with these cards (from `lshw -C network` ): 
product: MT27500 Family [ConnectX-3]
vendor: Mellanox Technologies

And the combination of making sure that I've got libmlx4 installed and the above module was what worked for me.

---

