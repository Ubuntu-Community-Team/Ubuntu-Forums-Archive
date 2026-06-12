---
title: "Can only get internet with DHCP not Static Ip"
date: 2006-05-19
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2006-05-19
Hey i have 2 computers wired to the hub and plugged into the hub i have a router it is a zyxel presteige 600 and internte works on both computer if i have it set in networking as dhcp but i need static ip so i can network can someone plz help me

---

### Post by Iowan on 2006-05-19
[QUOTE=CameronCalver]internte works on both computer if i have it set in networking as dhcp but i need dhcp so i can network [/QUOTE]What am I missing?  If it works in DHCP, but you NEED DHCP... you're good to go.

---

### Post by CameronCalver on 2006-05-19
lol loo at my edit]

fixed dont worry

---

### Post by spd106 on 2006-05-20
Hi,
As I understand you want to give your PCs static addresses so that they can talk to each other. But you also want them to access the Internet.
Have you checked that the IP addresses you are using are on the same subnet? 
For example:
router = 192.168.1.1 255.255.255.0
host 1 = 192.168.1.2 255.255.255.0
host 2 = 192.168.1.3 255.255.255.0

Make sure that you have either excluded these addresses or disabled DHCP on the router.
Can you ping the router? ie $ ping -c 4 192.168.1.1
or the other host?
Check that there are arp entries for the hosts and router. ie $ arp -a
Also look in the resolv.conf to see if you have dns servers listed. ie $ cat /etc/resolv.conf

If none of these work could you please post more information on what setup you have tried.
Good luck

---

### Post by CameronCalver on 2006-05-20
hey i have fixed it

---

