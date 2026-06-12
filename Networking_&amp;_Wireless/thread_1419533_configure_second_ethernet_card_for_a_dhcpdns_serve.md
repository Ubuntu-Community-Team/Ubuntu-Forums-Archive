---
title: "configure second ethernet card for a dhcp/dns server"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by pavel989 on 2010-03-02
i already have an eth0 configured to automatically get its info from dhcp.

but i wanna configure eth1 to be able to serve dhcp and dns. i havent configured either dns or dhcp server on the server box since i have not configured the serving interface. 

so far my interfaces file is: 


```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet static
address 123.221.52.68
netmask 255.255.255.240
network 123.221.52.64
broadcast 123.221.52.69
gateway 123.221.52.79
```

i think my issue is my gateway. i dont know what i can make it to make this work. when i restart my networking, eth0 configures fine, and before i changed the netmask and following ip addresses, eth1 was working. now i get the error:

```
SIOCADDRT: No such process
Failed to bring up eth1.
```

---

### Post by Iowan on 2010-03-02
For a quick/dirty test, try commenting out the "network" and "broadcast" lines - then restart networking. Your subnet looks OK, but the "standard" broadcast address would be .79

---

