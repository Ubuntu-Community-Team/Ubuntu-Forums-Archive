---
title: "Setting Up Static IP Address"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by SultanOmar on 2012-11-15
I'm trying to make my IP address static. I did the following: I added

> 
auto eth0 
iface eth0 inet static 
address 192.168.1.4 
netmask 255.255.255.0 
gateway 192.168.1.1 
dns-nameservers 8.8.8.8 192.168.1.1
to /etc/networks/interfaces. It worked with me but it lasted for about 30 seconds. After that, it went to the dynamic mode. I'm using Ubuntu 12.04.

  

Any help is appreciated

---

### Post by mikewhatever on 2012-11-15
Do you have Ubuntu 12.04 server or desktop?

---

### Post by Laiquendi on 2012-11-15
Not sure if this is what you meant by "any help" ;) but:
You can make it in a more simple way in "network connections" and it usually worked for me.

---

### Post by SultanOmar on 2012-11-15
I solved through Network Tools

Thanks, :)

---

### Post by lisati on 2012-11-15
Another way is to reserve an IP address via your router.

If your problem is solved, please mark it as "[solved]" using the "thread tools" drop-down menu.

---

