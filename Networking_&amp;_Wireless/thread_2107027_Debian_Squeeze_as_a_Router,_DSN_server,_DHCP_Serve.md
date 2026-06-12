---
title: "Debian Squeeze as a Router, DSN server, DHCP Server and VPN Server"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by bshosey on 2013-01-20
I am trying to set up Debian as a router, vpn server and dhcp server. One machine with 2 NICS. Eth0 is the internal and Eth1 is external. Eth1 connected directly to AT&T DSL Modem. I installed dnsmasq, pptpd and arno-iptables-firewall

The lan computers can get on the internet and they do dns properly. Also can ping and dns lookup other internal computers. But when I try to vpn I can't get client to connect to pptpd server. 

In the code boxes are the config files for the installation.

/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# LAN
auto eth0
iface eth0 inet static
address 172.16.1.1
gateway 172.16.1.1
netmask 255.255.252.0

# WAN
auto eth1
iface eth1 inet dhcp 
```/etc/dnsmasq.conf
```
interface=eth0
except-interface=eth1
bind-interfaces
expand-hosts
domain=fpi.local
dhcp-range=172.16.1.2,172.16.1.254,255.255.252.0,24h
dhcp-option=6,172.16.1.1
dhcp-option=3,172.16.1.1
```/etc/pptpd.conf
```

option /etc/ppp/pptpd-options
logwtmp
localip 172.16.2.1
remoteip 172.16.2.2-254
connections 253
bcrelay eth0
```
/etc/ppp/pptpd-options
```
name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
proxyarp
lock
nobsdcomp
ms-dns 172.16.1.1
ms-wins 172.16.1.1
```

chaps-secrets is setup with user name and password.

/etc/arno-iptables-firewall/debconf.cfg
```
#######################################################################
# Feel free to edit this file.  However, be aware that debconf writes #
# to (and reads from) this file too.  In case of doubt, only use      #
# 'dpkg-reconfigure -plow arno-iptables-firewall' to edit this file.  #
# If you really don't want to use debconf, or if you have specific    #
# needs, you're likely better off using                               #
# /etc/arno-iptables-firewall/custom-rules.  Also see README.Debian.  #
#######################################################################
DC_EXT_IF="eth1"
DC_EXT_IF_DHCP_IP=1
DC_OPEN_TCP="500 1723 22"
DC_OPEN_UDP=""
DC_INT_IF="eth0"
DC_NAT=0
DC_INTERNAL_NET="172.16.0.0/22"
DC_NAT_INTERNAL_NET=""
DC_OPEN_ICMP=0
```

I am hoping some one else can see what I have over looked. I picked PPTPD so for simplicity of setting up on multiple windows version.

---

