---
title: "routing  and subnetting"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by ansingh on 2013-08-15
Hi all,

i wanted to understand a bit more about routing and if the config and results i have are right.

I currently am running a cable into my NIC and have a wifi dongle in to act as an access point mode using hostap having done that, i have set up hostapd and that part looks all
but what i am trying to do is create a subnet and assign that to the wifi dongle so that i can connect to that dongle to surf out to the net.

The issue is, after configuring the below files as displayed, i still can't surf out to the net.

i have so far

**/etc/network/interfaces **

iface lo inet loopback
iface eth0 inet dhcp
allow-hotplug wlan0
iface wlan0 inet static
address 10.1.0.1
netmask 255.255.0.0
gateway 10.0.0.138
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
[B]
/etc/dhcp/dhcpd.conf[/B]

subnet 10.1.0.0 netmask 255.255.0.0 {
range 10.1.0.2 10.1.0.15;
option domain-name-servers 10.0.0.138;
option routers 10.1.0.1;
interface wlan0;
}

i also run the forwarding command echo 1 > /proc/sys/net/ipv4/ip_forward

and when i run route -n  i get this


**Destination     Gateway         Genmask         Flags Metric Ref    Use Iface**
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.1.0.0        0.0.0.0         255.255.0.0     U     0      0        0 wlan0

Should i be expecting the gateway on line 3 to say 10.1.0.1 in order for me to go out to the net. If so have i missed the configuration somewhere?

Any help would be appreciated.

Thanks in advance

Anu

---

### Post by Doug S on 2013-08-16
Hi and welcome to Ubuntu forums.

I think you need some iptables rules to implement NAT (Network Address Translation).
Does the [Internet/Connection sharing wiki]("https://help.ubuntu.com/community/Internet/ConnectionSharing") give you enough information? If not, post back here.

---

