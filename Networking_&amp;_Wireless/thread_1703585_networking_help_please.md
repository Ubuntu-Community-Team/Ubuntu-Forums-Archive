---
title: "networking help please"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by cjells on 2011-03-09
Hi, I need some networking help. How do I change eth0 from dhcp to a static ip without re-instaling Ubuntu (which at this point appears easier)?

I have edited the /etc/network/interfaces file, where eth0 was not even listed, to add the following:

iface eth0 inet static
address 172.17.32.101
netmask 255.255.255.0
network 172.17.32.0
broadcast 172.17.32.255
gateway 172.17.32.1

so now the entire file reads:

#auto lo
#iface lo inet loopback
iface eth0 inet static
address 172.17.32.101
netmask 255.255.255.0
network 172.17.32.0
broadcast 172.17.32.255
gateway 172.17.32.1


Now ifconfig does not show eth0 but shows eth1, which is not in the interface file at all

yes, I have restarted networking , and rebooted the box. It doesnt want to take an ip.


In Windows or UNIX I would already be up and running. 


Thanks

---

### Post by An Sanct on 2011-03-09
You can use System > Preferences > Network Connections and then under wired edit the configuration...

---

### Post by tkelito on 2011-03-09
You've been given a response in your other thread.  It is much easier to get the answers you seek if you don't open multiple threads regarding the same issue.

---

### Post by An Sanct on 2011-03-09
Admins can also merge threads ...

---

