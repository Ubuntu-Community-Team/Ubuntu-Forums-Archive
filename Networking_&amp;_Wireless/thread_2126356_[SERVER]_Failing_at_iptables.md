---
title: "[SERVER] Failing at iptables"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by Nate_is_cool on 2013-03-16
I'm setting up a proxy server with Dansguardian to filter. I'm trying to block any access trying to bypass the proxy (IE not using proxy settings )
Now I have two problems
1. I can't get ubuntu to reapply my tables after a reboot. I have it set in /etc/network/interfaces:



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback




# The primary (EXTERNAL) network interface
auto eth1
iface eth1 inet dhcp


# The secondary (INTERNAL) network interface
auto eth0
iface eth0 inet static
pre-up iptables-restore < /etc/dansguardian/iptables.rules
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1
network 192.168.0.0
broadcast 192.168.0.255


# Network bridge
iface br0 inet static
bridge_ports eth1 eth0
address 192.168.0.1
netmast 255.255.255.0
gateway 192.168.0.1
bridge_stp yes
bridge_fd 0



Now here is the weird part, re-running "sudo /etc/init.d/networking restart" will apply my ip routes, but it has to be run manually.

Second problem,

My without my tables applied I can access the net, it filters ads and porn. With them enabled I get this error:

[http://i174.photobucket.com/albums/w118/pspcracka/error_zps54b482eb.jpg](http://i174.photobucket.com/albums/w118/pspcracka/error_zps54b482eb.jpg)

This is the tables I applied:

sudo iptables -A OUTPUT -m owner --uid-owner root -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -m owner --uid-owner privoxy -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -j DROP
sudo iptables -A OUTPUT -o lo -p tcp --dport 8118 -m owner --uid-owner dansguardian -j ACCEPT
sudo iptables -A OUTPUT -o lo -p tcp --dport 8118 -m owner --uid-owner nathan -j ACCEPT
sudo iptables -A OUTPUT -o lo -p tcp --dport 8118 -j DROP

Any ideas?

---

### Post by bodhi.zazen on 2013-03-18
Your networking is all off. Why are you assigning ip addresses to eth0 (dhcp) and eth1 (static) and then bridging them ?

---

### Post by Nate_is_cool on 2013-03-18
You are backwords good sir,
eth0 is static and eth1 is dynamic. Basically eth1 is my POP, it will get it's IP from my modem, while eth0 is on the inside of my network. I'm bridging them so that I may pass traffic from network 192.168.0.0 to my modem.

I'm guessing you already spot my error?

---

### Post by Nate_is_cool on 2013-03-23
Anyone have any ideas why this isn't working?

---

### Post by SeijiSensei on 2013-03-23
You don't want bridging.  Read this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by Nate_is_cool on 2013-03-27
You rock. This fixed it. I'll post the full config tomorrow so that anyone who comes across this will have it.

---

