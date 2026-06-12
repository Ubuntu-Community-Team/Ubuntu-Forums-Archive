---
title: "UFW IP Masquerading Problems"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by sorling on 2009-04-06
Hey, I have a realy stange problems.
I have installed:
ipmasq, dnsmasq, ufw

Im useing the server to act like a router.
And the problem is that i get ALOT of UFW BLOCK FORWARD and UFW BLOCK INPUT in my log files from/to my local IP but the firewall doesnt block anything, every port is open and it doesnt matter if i make a rule like "sudo ufw allow from 192.168.0.0/24 to any"
the errors still accrue in the log.
The only rules i have now to that network is:
53/tcp                     ALLOW   192.168.0.0/24
53/udp                     ALLOW   192.168.0.0/24

Because the rules dont apply to that network anyhow.

Now my question is ther anythink I have overlooked or just missed? Im kinda new at the whole UFW/Unix thing. And how Im i suppose to conf my network so I can make rules for my LAN and WAN conn. (the WAN conn rules works great)

Example of an error in the log file:
[UFW BLOCK FORWARD]: IN=eth0 OUT=eth1 SRC=80.239.179.111 DST=192.168.0.152 LEN=236 TOS=0x00 PREC=0x00 TTL=51 ID=31223 DF PROTO=TCP SPT=3724 DPT=57671 WINDOW=8576 RES=0x00 ACK PSH URGP=0

Files I have changed/modifyed
**/etc/dnsmasq.conf**
dhcp-range=192.168.0.100,192.168.0.250,72h
interface=eth1

**/etc/network/interfaces**
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# LAN
auto eth1
iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        broadcast 192.168.0.255
ifup eth1

**/etc/default/ufw**
DEFAULT_FORWARD_POLICY="ACCEPT"

**/etc/ufw/sysctl.conf**
# Uncomment this to allow this host to route packets between interfaces
net/ipv4/ip_forward=1

**/etc/ufw/before.rules**
*nat
: POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
COMMIT

---

