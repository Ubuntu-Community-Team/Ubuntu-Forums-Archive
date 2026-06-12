---
title: "Dual ethernet &amp; different subnet network @ office"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by bmanam on 2009-06-08
I have been tearing my hair out over this one:

I've decided to ditch M$ at the office and setup an Ubuntu box but I have unbeleivable problems getting the network setup correctly so that it work in Ubuntu.

Situation: I have 2 NIC's on the Ubuntu box setup in /etc/network/interfaces as:

auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.1.11
netmask 255.255.255.0
gateway 192.168.1.1

I've also got "dnsmasq" installed to issue dynamic IP's to employees connecting wirelessly to the server from their laptops while in the office. They access the "in-house" server to use a web application (PHP) runnig on Apache.

The DSL modem (192.168.1.1) feeds into eth1 and the DLink wireless router is connected to eth0. The DLink's IP is 192.168.0.1, thus DHCP issues IP from the range 192.168.0.50 to 192.168.0.150.

Now, I want the employees to access the web-app and also use the server for their internet connectivity (email, etc.) but I cannot seem to get the internet traffic to route through the server. They can access the web-app running on Apache just fine but they just cannot access the internet no matter what. I also have short-lasting little intervals where even the server itself seems to "lose" the internet connection....completely stumped on that one.

Can anyone offer advice? Should I just convert the entire network to the same subnet (i.e. 192.168.1.x) or am I missing some kind of routing record to get the server to let the employees' internet traffic through as well as serve them the web-app running on Apache?

A mouthful I know, but thanks in advance for any help.

---

### Post by superprash2003 on 2009-06-08
have you tried this for internet connection sharing [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by bmanam on 2009-06-08
Thanks a million superprash2003. I'll definately check it out...it looks exactly like what I've been after.

---

### Post by Iowan on 2009-06-08
There's a [link]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") near the bottom of that help page that goes to a wireless sharing help page - but I'm never sure if it goes the right direction (wireless to wired?).

---

### Post by brabo on 2009-06-08
i do not think that matters iowan, the wireless router does all the routing to wifi and back.
the PC will route ethernet-ethernet with that guide, and that's what he needs.

brabo.

---

