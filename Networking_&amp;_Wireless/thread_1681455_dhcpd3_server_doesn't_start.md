---
title: "dhcpd3 server doesn't start"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by phoenixpb on 2011-02-04
dhcpd3 server doesn't start for wlan0

/etc/default/dhcp3-server

INTERFACES="wlan0"

/etc/dhcp3/dhcpd.conf

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.254;
option domain-name-servers 192.168.0.1;
option domain-name "mydomain";

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.10 192.168.0.100;
range 192.168.0.150 192.168.0.200;
} 

iwconfig

wlan0     IEEE 802.11bg  Mode:Master  Frequency:2.437 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off

---

