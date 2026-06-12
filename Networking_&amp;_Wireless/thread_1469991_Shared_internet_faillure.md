---
title: "Shared internet faillure"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by Hophans on 2010-05-02
I have been running ubuntu now for a few years and it have been a fairly smooth ride.
As 10.04 LTS have been published i have descided to go straight for a clean install giving the beta2 a go a few weeks ago and finaly got the final release on another clean install the other day.
I run Ubuntu on my laptop and when at home this serves as my internet gateway as my desktop computer has no wireless card and that have worked flawlessly untill now.

My home network usualy looks like: Desktop(Opensuse) -> Laptop(Ubuntu) -> Wireless router(internet)

I have done the setup run a few times with ipmasq and dnsmasq on the laptop (ipmasq was only pre 9.10) through a wired connection with a class A ipv4 for the nat gate to the inet gate on wlan0 using a class C ipv4.

But with 10.04 the odds have changed as my wired connection refuses any kind of connection through a shared link.

Basicly i have been doing it like desciped here: 

> 
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

echo 1 > /proc/sys/net/ipv4/ip_forward

apt-get install dnsmasq

/etc/init.d/dnsmasq restart

iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

echo 1 > /proc/sys/net/ipv4/ip_forward

removeing the # net.ipv4.ip_forward = 1 from /etc/sysctl.conf

And set up the network manager with a new connection on eth0 to link via "Shared to other computers" and that have done the trick even on 10.04 beta2 but on the final release of 10.04 this is not the case.

What i end up with is a network connection that reject to connect by any means not even optaining an ip for dhcp offer. Basicly i end up with a connection that via network manager just cycles on auto connect on a endless loop.

After this i have tried to flush my iptables and disabeling dnsmasq to start over but this has no effect. I have also tried to manualy set my default network setting (via ifconfig) for the class a ip but that leaves me with a working eth0 connection but no NAT to the desktop computer.

This is most likely caused by missconfiguration from my side but at this point i have no idea on how to get the shared connection working and even with firestarter i have failed badly.

I am open to any ideas on how to fix this or a sucessfull way to get shared link to work without dhcp offer.

> 
For refrence purpose my ipv4 table looks like this:
Desktop gets ipv4 via auto dhcp: 10.42.43.10
Laptop gives ip on dhcp offer: 10.42.43.10
Laptop holds dhcp ip:10.42.43.1
laptop route via nat from 10.42.43.10 to 192.168.0.50
Laptop connects to router with ip: 192.168.0.104
router has ip:192.168.0.50



---

### Post by Hophans on 2010-05-04
Well as it turn out it seems that the function i was looking for is no longer supported from Network manager applet in 10.04.

Doing it all manualy seems to work rendering a gui for network management useless though.
With dnsmasq installed i have made a small shell with the following from a tutorial and it works perfectly:

ifconfig eth0 10.42.43.1
iptables -A FORWARD -i wlan0 -o eth0 -s 10.42.43.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 
sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

Where Wlan0 is my internet acess and eth0 the nat forwarder for the client. To make this work on the client either a manual setup is needed inside the scope or you prober dns server must be defined for resolving.
So now my table looks like the above description with a manual setup on the client to use my isp name server. 
But i still cant stop wondering why dnsmasq no longer should work with the gui.

---

