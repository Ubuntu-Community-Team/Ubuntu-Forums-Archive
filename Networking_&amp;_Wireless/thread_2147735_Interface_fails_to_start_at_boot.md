---
title: "Interface fails to start at boot"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by forrestgowland on 2013-05-22
Hi all

I have a seirra 4g mobile hotspot which I use to access the internet at home.  I have it tethered to my pc via USB.  It works fine, I can bring the interface (named **[FONT=courier new]wwan0[/FONT]**) up manually no dramas. But for some reason it wont come up at boot properly.  I say properly becuase when I boot, I cant access the internet but when I **[FONT=courier new]sudo ifup wwan0[/FONT]** it says the interface is already configured, so I have to **[FONT=courier new]ifdown wwan0 && ifup wwan0[/FONT]** Its not a huge problem but still annoying, but more annoying that I cant figure out why its doing it!

Details:

I have uninstalled network manager.  Network Manager failed to recognise **[FONT=courier new]wwan0[/FONT]** and Im more comfortable just configuring /etc/network/interfaces
Im using Ubuntu 13.04.  I was using Ubuntu Quantal Server(or maybe it might have been Precise... Think it quantal) on the same PC with the same setup and **[FONT=courier new]wwan0[/FONT]** always started properly on boot...
My /etc/network/interfaces reads:
[FONT=courier new]auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0

auto wwan0
iface wwan0 inet dhcp
    pre-up /etc/network/firewall
    dns-nameservers 8.8.8.8 8.8.4.4[/FONT]

My firewall reads:
[FONT=courier new]#load modules
modprobe ip_tables
modprobe iptable_nat
modprobe iptable_filter
#clear Rules
iptables -F
iptables -X
#Defualt filter chain actions:
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
# Input Rules
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i wwan0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -s 192.168.1.0/24 -j ACCEPT
#Forward rules
iptables -A FORWARD -i wwan0 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o wwan0 -j ACCEPT
# clear NAT rules
iptables -t nat -F
iptables -t nat -X
# NAT
iptables -t nat -A POSTROUTING -o wwan0 -j MASQUERADE[/FONT]

(I use the PC as a gateway for my other devices)
Let me know if theres any other info I should give.

Thanks

---

