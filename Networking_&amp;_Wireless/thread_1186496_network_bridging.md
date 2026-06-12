---
title: "network bridging"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by Jcdlvsrbld on 2009-06-13
ive been trying to connect my 360 to xbox live through an ethernet port on my laptop. so basically: xbox->laptop->internet .  i cant seem to figure out how to do it. i did it when i had windows, and i know it can be done on mac. I saw one post that i thought would be helpful, but it involved firestarter, and i can't get it to run the firewall (it keeps saying "the device eth0 is not ready) im not sure how to fix this. can someone explain how to do this in firestarter, or provide a different method to bridging the connection?

---

### Post by Jcdlvsrbld on 2009-06-13
seriously? no help? not even one bit of spam? NOTHING??

---

### Post by Jcdlvsrbld on 2009-06-13
im just going to keep posting.  Will gadmin-squid help? how do i use it?
do i need to set up a dhcp/dns server?

---

### Post by Jcdlvsrbld on 2009-06-13
what about bridge-utils? will that work? someone please answer!

---

### Post by Belizeian on 2010-01-11
Gadmin-squid, want help it is suppose to be for administration and configuration of squid, and the package in the repo, well it breaks
squid so it doesn't work.  Now I'm sure you could futz around and get squid to work with it just sucks that it breaks that which works.

If I understand your orginal question it sounds like you have a laptop that connects to the internet wirelessly and you want to utilize the net port on the laptop to conect the xbox if that's the case then what you probaly need is a crossover cable, or adapter.

---

### Post by toosneaky on 2010-03-16
install squid, iptables, ebtables, bridge-utils.
then edit and run this.

this is assuming eth0 and eth1 are your network interfaces and 192.168.1.11 is the ip of your laptop. change this as neccesary.

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

echo "setting up bridge"
brctl addbr br0
brctl show
brctl addif br0 eth0
brctl addbr br0 eth0
brctl addif br0 eth1
brctl addbr br0 eth1
ifconfig eth0 0.0.0.0 promisc up
ifconfig eth1 0.0.0.0 promisc up
ifconfig eth1 0.0.0.0 promisc up
ifconfig br0 192.168.1.11 netmask 255.255.255.0 up
route add default gw 192.168.1.254 dev br0

echo "bringing bridge online"
ebtables -t broute -A BROUTING -p IPv4 --ip-protocol 6 --ip-destination-port 80 -j redirect --redirect-target ACCEPT
iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-ports 3128
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-ports 3128

---

