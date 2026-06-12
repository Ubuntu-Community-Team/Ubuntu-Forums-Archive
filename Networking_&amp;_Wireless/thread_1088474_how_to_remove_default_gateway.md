---
title: "how to remove default gateway"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-03-06
Someone told me to do this

sudo route add default gw 192.168.123.1 

whereas 192.168.123.1 is my router's ip

Now I want to undo it because I cannot access any other sites except google. How can I do it?

here's my ip table

route
Kernel IP routing table 
Destination  gateway  genmask          flags metric ref use iface
192.168.123.0  *      255.255.255.0     u     0      0   0   eth0
default      192.168.123.1  0.0.0.0     ug   0       0    0   eth0

Many thanks!

Ok I just do
sudo route del default gw 192.168.123.1 

but still cannot access the internet. what to do?

that's strange. only google search work. but cannot visit any sites.

edit: i can nslookup too

What's wrong/? I can access the admin page of the router but not the internet?
Is that something wrong with dns??

---

### Post by afeasfaerw23231233 on 2009-03-06
I can visit gmail too. whats wrong???

---

### Post by afeasfaerw23231233 on 2009-03-06
ok I reboot it and everything is normal again. But it is the the first time to have this problem. ????

---

### Post by RayVad on 2009-03-06
You fixed it already, but you can remove the default gateway by doing:

sudo route del default gw 192.168.123.1

---

