---
title: "port forwarding / redirection"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by Pvt_Ryan on 2008-12-17
Hi, 

I have 3 computers A, B and C
A is in the subnet 192.168.1.x
B & C are in the subnet 192.168.2.x

C has a mysql db running on it, but will only accept connections from its own subnet (this CANNOT be changed).

I need A to connect to the mysql DB on C. I would like to use B to forward the connection from A.

A connects to B on port 33306 B forwards the connection to 192.168.2.6:3306.

I think I need to use iptables to do this however I have never used iptables before and there is a lot of reading to do on it and I just don't have the time atm (though when I do I will read up on it). 

Can anyone help please?


Regards,

Ryan

EDIT:
I tried the following but it didn't work. 
```

iptables -t nat -D PREROUTING -i eth0 -p tcp --dport 33306 -j DNAT --to-destination 192.168.2.6:3306

```

---

### Post by albinootje on 2008-12-17
> **Pvt_Ryan said:**
> 
I tried the following but it didn't work. 
```

iptables -t nat -D PREROUTING -i eth0 -p tcp --dport 33306 -j DNAT --to-destination 192.168.2.6:3306

```

I'm not good at iptables, but i need to learn it anyway (for LPI exams):).

Here they use a second line for iptables in the 
"Port Forwarding using Iptables" section :
[http://www.hackorama.com/network/portfwd.shtml](http://www.hackorama.com/network/portfwd.shtml)

And you need to enable the packet forwarding.
check /etc/sysctl.conf

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

---

### Post by Pvt_Ryan on 2008-12-17
Do i need to restart a daemon in order to reload sysctl.conf? as it is still failing to connect. 

Here are my iptables and the rules i created.

```

iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 33306 -j DNAT --to 192.168.2.6:3306
iptables -A FORWARD -p tcp -i eth0 -d 192.168.2.6 --dport 3306 -j ACCEPT

```

```

iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             mysql.example.com tcp dpt:mysql

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

```

 iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             anywhere            tcp dpt:33306 to:192.168.2.6:3306

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by albinootje on 2008-12-17
> **Pvt_Ryan said:**
> Do i need to restart a daemon in order to reload sysctl.conf? as it is still failing to connect. 


see : man sysctl

sudo /sbin/sysctl -p /etc/sysctl.conf would do

---

### Post by albinootje on 2008-12-17
You can check whether it's working by using :
cat /proc/sys/net/ipv4/ip_forward

0 means disabled
1 means enabled

---

### Post by Pvt_Ryan on 2008-12-17
Sorry I should have said I did that as well. (it is set to 1)

---

### Post by Pvt_Ryan on 2008-12-18
bump

---

### Post by mpokrywka on 2008-12-21
You missed one important part:
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

It is very important because on "B" packets are DNATed to C, but without above rule, packet source will remain as "A". Above rule will change outgoing packets source to B. And C will get packet with "correct" source (same subnet) and will reply to B, and B will return this reply to A.

---

