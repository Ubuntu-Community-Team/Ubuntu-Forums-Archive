---
title: "MultiConnect for linux"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by shababhsiddique on 2009-11-26
Is it possible to combine two or more network connection as one? and thus increase the bandwidth. I have heard of MultiConnect for windows-
[http://asurasoft.awardspace.com/abtmulticonnect.html](http://asurasoft.awardspace.com/abtmulticonnect.html) 
I havent tried yet. I dont have XP in my PC
is there anything similar for ubuntu?

---

### Post by scorp123 on 2009-11-26
> **shababhsiddique said:**
> Is it possible to combine two or more network connection as one? This is called "bonding" and e.g. on servers with multiple interfaces we do that all the time.

[http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

Those instructions are for an older Ubuntu release but still valid.

Debian instructions (should be valid for Ubuntu as well):
[http://www.5dollarwhitebox.org/wiki/index.php/Howtos_NIC_Bonding_Debian](http://www.5dollarwhitebox.org/wiki/index.php/Howtos_NIC_Bonding_Debian)

Detailed instructions from the Ubuntu wiki:
[https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation)

---

### Post by shababhsiddique on 2009-11-26
Thanks for the reply, I shall check those out. Does it cover using multiple GSM modems?

---

### Post by scorp123 on 2009-11-26
> **shababhsiddique said:**
> Does it cover using multiple GSM modems? ?? :D

No idea if that will work.

---

### Post by shababhsiddique on 2009-11-26
Thanks again- but I am afraid it is only applicable with ethernet--
> shabab@shabab-desktop:~$ mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
no MII interfaces found
shabab@shabab-desktop:~$ sudo mii-tool

eth0: no link
 

---

### Post by scorp123 on 2009-11-26
> **shababhsiddique said:**
> Thanks again- but I am afraid it is only applicable with ethernet  That's the idea.

What are you trying to achieve? Bonding Internet connections (because that's technically what you are trying to achieve here it seems?) is quite more complex ....

[http://linux-ip.net/html/adv-multi-internet.html](http://linux-ip.net/html/adv-multi-internet.html)
[http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/](http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/)

.
.
.
.

---

### Post by scorp123 on 2009-11-26
And I just found this one too:

"Routing for multiple uplinks/providers"
[http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html)

---

### Post by shababhsiddique on 2009-11-26
> **scorp123 said:**
> That's the idea.

What are you trying to achieve? Bonding Internet connections (because that's technically what you are trying to achieve here it seems?) is quite more complex ....

[http://linux-ip.net/html/adv-multi-internet.html](http://linux-ip.net/html/adv-multi-internet.html)
[http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/](http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/)

.

I am trying to use two mobile connection (using 2 GSM modems connected to USB), The service provider may be same or different.

---

### Post by umar_zulfiqar on 2010-01-19
hi i am new to ubuntu but very much know about what do to if you guide me
here is the story 
i have two pc using two internet connections with same isp
iboth have lan cards or ethnet internet connected with wan(pppoe)
there is lan ip address auto asign by isp dhcp server(he use mikrotik router os)
for example:192.168.12.40 lan1 ip   172.169.12.40 wan1 or pppoe ip

there is no default gate way with lan and wan

2nd connection 192.168.12.41 lan2 ip 172.169.12.41 wan2 or pppoeip

no dns for lan

dns server for wan1 example 172.169.0.1 and 223.49.169.140
dns server for wan2 are same as above

i am using rp-pppoe for connecting to the internet i create two pppoe connection both connect but drop by one to browse or downloading meanwhile i can only use one connection at a time

i want to combine or bonding or load and balancing with these connection without using any router

ubuntu 9.10 help to do above or not >>>>>?or other  method>>>>>?

if you guys say yes then plz help me
thanks to all those who has the ability to solve this  ;)

---

### Post by shababhsiddique on 2010-03-06
> **umar_zulfiqar said:**
> hi i am new to ubuntu but very much know about what do to if you guide me
here is the story 
i have two pc using two internet connections with same isp
iboth have lan cards or ethnet internet connected with wan(pppoe)
there is lan ip address auto asign by isp dhcp server(he use mikrotik router os)
for example:192.168.12.40 lan1 ip   172.169.12.40 wan1 or pppoe ip

there is no default gate way with lan and wan

2nd connection 192.168.12.41 lan2 ip 172.169.12.41 wan2 or pppoeip

no dns for lan

dns server for wan1 example 172.169.0.1 and 223.49.169.140
dns server for wan2 are same as above

i am using rp-pppoe for connecting to the internet i create two pppoe connection both connect but drop by one to browse or downloading meanwhile i can only use one connection at a time

i want to combine or bonding or load and balancing with these connection without using any router

ubuntu 9.10 help to do above or not >>>>>?or other  method>>>>>?

if you guys say yes then plz help me
thanks to all those who has the ability to solve this  ;)

have u tried scorp's solution with ethernet?? tell me if it worked

---

