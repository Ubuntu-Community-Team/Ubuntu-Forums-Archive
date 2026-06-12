---
title: "My DNS servers are cleared from my network settings / resolv.conf on restart?"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by tominglis on 2009-03-23
Every time I restart my computer, my DNS servers are cleared from my network settings / resolv.conf.

I only have two in there: 208.67.220.220 and 208.67.222.222.

I have Kubuntu 8.04.2.

Does anyone know what might be wrong?

---

### Post by jonbuys on 2009-03-23
I would love to have this sorted out as well.  Right now, every time I move from one network to another, I need to sudo vi /etc/resolv.conf again to add my custom search domains.  I realize its a problem with our DNS, but is there some way to tell Ubuntu not to overwrite the existing DNS settings?

---

### Post by prshah on 2009-03-23
> **tominglis said:**
> Every time I restart my DNS servers are cleared 

> **jonbuys said:**
> is there some way to tell Ubuntu not to overwrite the existing DNS settings?

You can edit your /etc/dhcp3/dhclient.conf, and add the OpenDNS servers to the "prepend" line; this will ensure that the OpenDNS servers are used everytime.

From a terminal [Applications-Accessories-Terminal]:
```
sudo nano /etc/dhcp3/dhclient.conf
```

look for a line like ```
#prepend domain-name-servers 127.0.0.1;
``` and change it to read```
prepend domain-name-servers 208.67.220.220 208.67.222.222;
``` (Remember to remove the "#" commenting out the line in the beginning, or there will be no effect).

To test, you can either restart, or relogin, or just give the command```
sudo /etc/init.d/networking restart
```

---

