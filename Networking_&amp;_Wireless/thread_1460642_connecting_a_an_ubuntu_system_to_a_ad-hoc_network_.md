---
title: "connecting a an ubuntu system to a ad-hoc network with a sttic ip"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by 10ghost on 2010-04-23
Hi all,
I have been trying to connect my system to a ad-hoc created by a windows system. It requires me to assign a static ip to my system which i did by 

editing the file /etc/network/interface


adding this line to it

auto eth0
iface eth0 inet static
address 192.168.1.24
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.11


I am suspecting that i am assigning the staic ip for a wired connection not a wireless ad-hoc which is what i need.
How can i assign a static ip for a wireless ad-hoc network.

After adjusting the file I restarted the file

sudo /etc/init.d/networking restart

AFter restarting it. It gave me this error.

No such process 
Failed to bring up eth0
So what could be the problem and how can i resolve it.

---

