---
title: "Connect eth0 and wlan0"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by chezerian on 2011-01-22
I would like to implement the following setup
           
clients<------->my router<---eth0---->desktop(ubuntu 10.04)<----wlan0---->internet router.


eth0 has an IP of 192.168.0.254
wlan0 has an IP of 192.168.2.200
the internet router has an IP of 192.168.2.254
I tried using this script but to no avail

sudo ifconfig eth0 192.168.0.254
sudo iptables -A FORWARD -o wlan0 -i eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"


I have setup a DHCP server on eth0 but cant get "my router" to ping 192.168.2.200 or 192.168.2.254
also this command doesn't work ping 192.168.2.200 -I eth0.

I thought i may have to bridge wlan0 and eth0 so i tried this [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge) but the internet stopped working so i cleaned up everything.

---

### Post by chezerian on 2011-01-22
bump

---

### Post by headvampyre@hotmail.co.uk on 2011-01-22
Firstly, what are you actually trying to do with this setup? internet connection sharing? if so, the id recommend a proxy like squid

---

### Post by chezerian on 2011-01-24
Yes for internet connection sharing

---

