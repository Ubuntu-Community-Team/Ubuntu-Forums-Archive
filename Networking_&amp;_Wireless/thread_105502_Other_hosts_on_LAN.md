---
title: "Other hosts on LAN"
date: 2005-12-18
forum: Networking &amp; Wireless
---

### Post by hca on 2005-12-18
I need to know IP-addresses and hostnames of the other (active) hosts on my LAN. Which posibilities does Ubuntu linux offer?
I do know of one posibility given by my router's admin software. Here I can get hostname and ip-address of connected Win-XP hosts but only ip-addres of connected linux hosts. So this is not quite enough.
Can anybody help here?

---

### Post by tuxy on 2005-12-19
All the hosts are in /etc/hosts. If you know IP's of Linux machines then you can give names to the known IP's in the form-
For example *192.168.15.10 debianmachine* format.

If you want to ping 192.168.15.10. You can just ping with the machine name like *ping debianmachine* in our case here.

Or you can type in *who* and it will list the pc's connected to the server with their IP's and names.

---

### Post by alamba on 2005-12-19
Incase you don't have the IP addresses and hostnames of the machines you can run a utility called ntop. Just download and install and fire it up. You would find enough howto's on the subject. This is a network topology system that will over a few minutes listen on the LAN card on promotious mode and populate a table with all the hosts and IP addresses. It even has a web interface for reports that gives not only what you're looking for but also excellent details of active connections, protocol by protocol analysis, etc.

Akshay

---

### Post by tuxy on 2005-12-27
One other way is to broadcast through **ping x.y.z.255 -b**

---

