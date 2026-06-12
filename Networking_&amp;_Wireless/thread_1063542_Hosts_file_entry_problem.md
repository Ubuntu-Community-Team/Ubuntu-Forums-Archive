---
title: "Hosts file entry problem"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by meazz1 on 2009-02-08
What would be the right entry for /etc/hosts file entry.
My laptop name is john-laptop.
So, to use a full qualify domain name, what do I enter in /etc/hosts file?

Is this example correct? Do I need to change anything else under Network?


[PHP]127.0.0.1	localhost.localdomain localhost john-laptop
127.0.1.1	john-laptop 


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/PHP]

---

### Post by Gen2ly on 2009-02-08
> **meazz1 said:**
> What would be the right entry for /etc/hosts file entry.
My laptop name is john-laptop.
So, to use a full qualify domain name, what do I enter in /etc/hosts file?

Is this example correct? Do I need to change anything else under Network?


[PHP]127.0.0.1	localhost.localdomain localhost john-laptop
127.0.1.1	john-laptop 


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/PHP]

g, you need a valid address. use ifconfig den put in your right ip.

---

### Post by meazz1 on 2009-02-08
so, if my laptop is using 192.168.2.4, replace this with the 127.0.0.1 or 127.0.1.1 address?

---

### Post by meazz1 on 2009-02-09
bump

---

### Post by Iowan on 2009-02-10
I have one machine with actual IP address in that file, but most use similar to what you have...```
127.0.0.1    localhost.localdomain localhost 
127.0.1.1  john-laptop.localdomain  john-laptop  


# The following lines are desirable for IPv6 capable hosts 
::1     ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts  
```

---

