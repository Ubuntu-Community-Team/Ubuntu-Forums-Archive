---
title: "Two interfaces in one host"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by amont on 2011-02-06
Hello,

Surely it's a silly question but I can't guess the answer.

I have a laptop "fura1" with two interfaces, eth0 (Ethernet) and eth1 (wifi), which I assign IPs 192.168.1.10 and 192.168.1.11 respectively. Then a desktop "fura2" with only one interface eth0 (Ethernet). Both are connected to a local network along with other appliances. My doubts arise on how to configure the /etc/hosts file of the desktop "fura2" taking in account that "fura1" has two interfaces, so two IP, but, obviously, only one hostname. 

My first attempt for /etc/hosts of "fura2" was:

127.0.0.1	localhost
127.0.1.1	fura2

192.168.1.10    fura1 fura1.workgroup
192.168.1.11    fura1 fura1.workgroup
192.168.1.102   PDA PDA.workgroup
192.168.1.103   MT MT.workgroup

But it seems to my that assigning two different IPs to the same host is not a good solution. On the other hand, if I give different name to each interface, I will got a host with two hostname (?). What is the correct approach? 

Thanks for your help

---

### Post by spiky001 on 2011-02-06
What do you want to do can you explain abit better plz, If it,s connect from desktp to lappy via host name? you need to edit etc/host in desktop

---

### Post by amont on 2011-02-07
Sorry, I'm afraid I can not express myself better. Can you?

---

