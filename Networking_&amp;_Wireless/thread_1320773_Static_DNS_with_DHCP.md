---
title: "Static DNS with DHCP"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Lambchopper on 2009-11-09
All:

I'm running Ubuntu Server as a router at home.  I get my Public IP and DNS settings from my ISP.  I've found that the DNS servers for my ISP downright suck.  When I change my resolv.conf file to point to other public DNS servers, my internet performance improves significantly.  Obviously when my Ubuntu Router renews it's lease or I reboot the router for some reason, I loose the name server settings in resolv.conf.  My question:  How can I stop this behavior?  I want to assign my own DNS servers and ignore those delivered via DHCP.

Thanks!

---

### Post by Iowan on 2009-11-09
*/etc/dhcp3/dhclient.conf* has a "prepend" line that will put your preferred server(s) at the top of the stack.

---

### Post by Lambchopper on 2009-11-10
SWEET!  That was exactly what I was looking for!  Thank you!!!

---

### Post by ratcheer on 2009-11-10
How do you check which DNS servers are in current use on Ubuntu?

Thanks,
Tim

---

### Post by chili555 on 2009-11-10
```
cat /etc/resolv.conf
```

---

### Post by ratcheer on 2009-11-10
> **chili555 said:**
> ```
cat /etc/resolv.conf
```

Thanks. Mine is apparently using my network gateway, which in turn points to the DNS's I want it to use. Is that sufficient, or should I specifically point my Ubuntu PC to the DNS's?

Thanks,
Tim

---

### Post by chili555 on 2009-11-10
The gateway is a perfectly valid nameserver. If it works properly, I wouldn't change a thing.

---

### Post by ratcheer on 2009-11-10
> **chili555 said:**
> The gateway is a perfectly valid nameserver. If it works properly, I wouldn't change a thing.

Ok, thanks again!

Tim

---

