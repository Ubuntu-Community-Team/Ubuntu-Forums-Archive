---
title: "Setting up Gateway Router"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by donldmn on 2013-05-23
I have a computer running Ubuntu 13.04 desktop that's set up as a media server with sickbeard and xbmc. I would like to set up a gateway router on it to connect the household to the Internet. I have two ethernet cards and a docsis 3.0 modem. I have been searching the Internet for a solution and found nothing that worked. I am relatively new to Ubuntu and have been trying to do this for two days. Can someone explain how to do this with webmin, pfsense in virtualbox, or any other ideas? I have linked some things that I couldn't get to work:

[http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001)
[http://rbgeek.wordpress.com/2012/05/14/ubuntu-as-a-firewallgateway-router/](http://rbgeek.wordpress.com/2012/05/14/ubuntu-as-a-firewallgateway-router/)

---

### Post by forrestgowland on 2013-05-23
So are you wanting to connect one ethernet interface to your modem and the other ethernet interface to a switch that connects the other devices in your house, allowing them to access the internet?

---

### Post by forrestgowland on 2013-05-23
If thats the case then this will work:



Create the following file and save it somewhere like /etc/network/firewall
What it does:
  -Allows packets to be forwarded from your devices to the intenet and vice versa
  -Simple firewall
  -Translates your household devices private IPs to your public IP so they can use the internet


This is setup so eth0 is the interface that connects to your home lan and eth1 is connects to your modem.
If its the other way round then youll have to swap them round in the following script.
Also if your home network isnt 192.168.1.0/24 then change that too.  But its probably that or 192.168.0.0/24


```
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
iptables -A INPUT -i eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -s 192.168.1.0/24 -j ACCEPT

#Forward rules
iptables -A FORWARD -i eth10 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

# clear NAT rules
iptables -t nat -F
iptables -t nat -X
# NAT
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE[/FONT]
```

Once you have done that you need to make it executeable with  **[FONT=courier new]sudo chmod +x /etc/network/firewall[/FONT]**  (or whatever you saved it as)

Then allow ip forwarding:
[B]sudo gedit /etc/sysctl.conf
[/B]
scroll to the line that says:[B]
[FONT=courier new]#net.ipv4.ip_forward=1[/FONT][/B]
and remove the hash so it reads:     **[FONT=courier new]net.ipv4.ip_forward=1[/FONT]**

Last but not least edit your /etc/network/interfaces file:
[B]sudo gedit /etc/network/interfaces

[/B]Make sure your eth0 and eth1 interfaces are set correctly.
add  the preup line to your eth stanza that connects to the modem  (eg eth0)  so your firewall starts.  It should look something like:

[B][FONT=courier new]auto eth0
iface eth0 inet dhcp
          pre-up   /etc/network/firewall[/FONT][/B]

then reboot your pc and it should be working :)

---

### Post by donldmn on 2013-05-23
I tried this but could not get the Internet working. I know this is probably going to sound really sad but is there an easier way to do this like with some kind of software or in the ui? It's just that I feel like this should be really simple and I just can't figure it out. ](*,)

---

### Post by gordintoronto on 2013-05-23
Why don't you let the router do what it is supposed to do?

---

### Post by donldmn on 2013-05-23
I have the media server set up in the basement and i figured that it could work as a router cause it's always on. I have two gigabit switches set up down there too and I wanted to put both of my wireless routers on the ground floor and the upstairs to improve the connection. I figured it out thanks to this thread and this tutorial I just found. It works really well and I am going to start playing with some of the features.

---

### Post by forrestgowland on 2013-05-23
So its all working now?  Good job  :)

---

