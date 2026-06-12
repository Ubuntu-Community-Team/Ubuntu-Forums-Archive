---
title: "Ubuntu as Internet Router and DHCP Server"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by pdnail on 2013-05-13
Hello guys,
I'm trying to use my Ubuntu 13.04 workstation as an Internet Router + DHCP Server.

Basicaly, the Internet Routing (eth0 connected to internet and eth1 connected to 192.168.1.0 network - box ip address 192.168.1.1) is working fine (I've followed this guide: [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)). 
My unix box is connected to an Ethernet hub and an additional device (PC) connected to that hub with static ip is working fine (eg PC set with IP 192.168.1.10 - Subnet 255.255.255.0 - Router=unix_box= 192.168.1.1 - DNS IP provided by internet provider).


DHCP server service in not working. I've followed the steps here: [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server) but had no luck

**File: /etc/network/interfaces**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
   address 192.168.1.1
   network 255.255.255.0
   broadcast 192.168.1.255


**File: /etc/dhcp3/dhcpd.conf**

$ cat /etc/dhcp3/dhcpd.conf

# Sample /etc/dhcpd.conf
# (add your comments here)
ddns-update-style none;
log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
        option routers                  192.168.1.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        192.168.1.255;
        option domain-name-servers      85.18.200.200;
        option ntp-servers              193.204.114.232;
        default-lease-time 86400;
        max-lease-time 86400;
}


**File /etc/default/dhcp3-server**
INTERFACES="eth1"


**IP Route**
$ ip route
default via 89.96.xxx.xxx dev eth0 
89.96.xxx.xxx/28 dev eth0  proto kernel  scope link  src 89.96.xxx.xxx 
169.254.0.0/16 dev eth1  scope link  metric 1000 
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.1 


Please could anyone help with this DHCP server problem?

Thanks a lot

Danilo

---

