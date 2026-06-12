---
title: "Trouble setting up gateway Ubuntu 12.04"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by bobx on 2013-04-09
I am trying to set up my Ubuntu box as a router/gateway for my other computers. I have 2 network cards in the Ubuntu box. eth0 is for the LAN and eth1 is for the WAN (DSL connection). I have found several How-Tos and have tried most of them. The one that has come closest to working is at [http://www.mehrdust.com/archives/configure-your-ubuntu-desktop-as-an-internet-gateway](http://www.mehrdust.com/archives/configure-your-ubuntu-desktop-as-an-internet-gateway) . The Ubuntu box can access the internet with no problems. However my other computers have trouble with most web sites. I can ping all websites from the other computers. I have tried several browsers on the other computers and I can get to Google, Youtube and some other sites. But I can not get to Yahoo, msn, ...

I have uncommented the following line in the file /etc/sysctl.conf


#net.ipv4.ip_forward=1

I have changed the iptables as follows:

sudo iptables -A FORWARD -o ppp0 -i eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -F POSTROUTING
sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

eth0 is set up as

192.168.0.2
192.255.255.0


The browsers appear to be trying to get to the websites but eventually time out. It could be that there are certain elements on the web sites that can not load.

Any suggestions ?

Bob

---

### Post by Hadaka on 2013-04-09
Hi, I also have been recently looking into
gateway/port forwarding with this method
and am probably more of a newb than you
on this subject. here is a link that may help.
[http://www.fclose.com/b/linux/816/port-forwarding-using-iptables/](http://www.fclose.com/b/linux/816/port-forwarding-using-iptables/)
good luck !

---

### Post by bobx on 2013-04-10
I uncommented most of the ipv4 items in sysctl.conf .

Next I changed the mtu on the other computer to 1492 (it was 1500) and presto it worked. Now I have to go back to sysctl.conf and comment out things I do not need, if I can figure out which are needed and which are not.
ob
Thank you 
Bob

---

