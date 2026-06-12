---
title: "Bandwidth Management in Linux"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by amolredhat on 2013-09-03
Hi all,

I want  bandwidth controller device in office network,  I want to control Internet Bandwidth Usage for client. I have one server which have 2 NICs

_OS:-_ Centos 5.7 


_Configuration:-_


eth0 have Public Ip
eth1 have Internal Ip (192.168.1.100)


&


From **eth1** Network cable is connected to Non-Mangeable switch, and from where users are connected to Internet.




On above server, I have configured  Squid & Iptables rules. Here I want to control Internet Bandwidth, So that I can give less Internet Speed to those who are unwanted users, who are taking resources of the Internet.




I have tried with Squid delayed pools, but it is not working efficiently, what I was was expecting.
 
How can I control Internet Bandwidth for Internal user (192.168.1.XX)? Is there any hardware device for Bandwidth Management.?

Please help, I  don't have much knowledge on Networking.

Regards,
Amol

---

### Post by houstonbofh on 2013-09-03
It is much easier to just install a purpose built appliance.  I am partial to m0n0wall as I have been a contributor since 2005.  However, pfSense is also a very good option.  Both are foss and totally free, not crack ware trying to get you to pay for more options.

---

