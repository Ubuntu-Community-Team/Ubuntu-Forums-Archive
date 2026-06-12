---
title: "Setting IP Address with out GUI help please"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by zOdeac on 2006-06-23
Ok I am not sure where to start is but this is what I have done.  I installed ubuntu 6.06 server.  I am able to see the server by,

Web, Ping SSH etc no problems at all until i attempt to set the ip address from DHCP to Static then I can ping the new ip address but no web so i cant get to webmin anymore.

So I read up on many people talking about setting there IP address so i did this 

sudo nano /etc/network/interfaces

this shows me my IP table or location for the eth0.

I replaced 

auto eth0
iface eth0 inet dhcp

with 
auto eth0
iface eth0 inet static
address 10.0.0.3
netmask 255.255.255.0
gateway 10.0.0.1

based on the instructions i seen then i do a command

sudo /etc/init.d/networking restart

This says it’s ok when I do it.  Now even after reboot I still can’t see webmin or even the sample apache pages.

Can anyone help me here I am going nuts its like every thing stops working after I enter the IP address.

---

### Post by halitech on 2006-06-24
here is the pattern I followed which is basically the same except the broadcast setting. Don't know if that would make a difference or not. 

auto eth0
iface eth0 inet static
              address 192.168.1.100 (or whatever ip you want)
              netmask 255.255.255.0
              network 192.168.1.0
              broadcast 192.168.1.255
              gateway 192.168.1.1

---

