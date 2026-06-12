---
title: "iptables and captive portal"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by hm2075 on 2009-07-27
Hi, I am looking for some help on captive portals


i am happy with setting up wireless access points

what I want to do is create a script that will constantly check a txt file lets call it mac.txt  

if mac address of user is in this mac.txt file then allow access to internet, if it isn't then force user to go to captive portal on port 80


here is my iptable which allows anyone to surf the internet through my ap

iptables -t nat -A PREROUTING -p udp -j DNAT --to 192.168.1.1                        
iptables -P FORWARD ACCEPT
iptables --table nat --append POSTROUTING --out-interface wlan0 -j MASQUERADE

---

### Post by abeverley on 2009-08-20
Hi,

This page should help you:

[http://www.andybev.com/index.php/Using_iptables_and_PHP_to_create_a_captive_portal]("http://www.andybev.com/index.php/Using_iptables_and_PHP_to_create_a_captive_portal")

---

