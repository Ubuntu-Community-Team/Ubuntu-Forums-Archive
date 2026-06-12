---
title: "Block a range of IP"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by Giorgis on 2006-06-13
What is the easyest way to block an IP address ?
I would also like to block a complete range like ... say ... Microsoft. 
I don't like how they are talking to my MS boxes for "our own good"
Also is there a service were I can share a blacklist to fight port scanning from potential "infiltrators" and spamers. I would like add a level of protection to my XP boxes on the network that are sitting behind an Ubuntu M/C

Kind Thanks for your help

Giorgis

---

### Post by rbalfour on 2006-06-13
Inside iptables in the "Chain INPUT (policy ACCEPT)"

You need something like this.

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  210.188.173.0/24     anywhere

---

### Post by frodon on 2006-06-13
To block an IP : ```
sudo iptables -A INPUT -s The_IP -j DROP
```

More on iptables there : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by Giorgis on 2006-06-14
[QUOTE=rbalfour]Inside iptables in the "Chain INPUT (policy ACCEPT)"

You need something like this.

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  210.188.173.0/24     anywhere[/QUOTE]
How do I block a range 
ie 134.28.*.* 

does that work ?

G

---

### Post by notequal on 2006-06-30
I am also interested in this.  However I would like to accept a range of IPs.

---

