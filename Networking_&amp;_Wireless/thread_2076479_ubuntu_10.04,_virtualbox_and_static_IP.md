---
title: "ubuntu 10.04, virtualbox and static IP"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2012-10-26
Hi,

i have ubuntu 10.04 as guest OS (virtual box) on a windows 7 host machine.
guest OS gets static IP from my wireless router and can ping host machine or other machine in local network.

however, when i try sudo apt-get update, ubuntu (guest os) returns me temporary failure resolving "us.archive.ubuntu.com".
it's like guest doesn't have access to internet :(

where is my mistake ?
thx

---

### Post by alain.roger on 2012-10-26
strange...i can't ping my own router :( whereas i have /etc/resolv.conf set with:
nameserver 192.168.1.1

---

### Post by Sergius14 on 2012-10-26
Hi,

Check your Virtual Network Configuration.


Should be Bridged for what you want. This option set aside your VM like a Physical from the Network point of view.

NAT may work, depending several things. Your host OS works like a router-firewall-nat.


Local-Only definetelly won't work :P. It is reserved for just creating a virtual network living online inside your host (for demoing, labs, etc.)

---

