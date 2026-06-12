---
title: "Dell Inspiron 640m wireless (?) problems"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by onebir on 2011-01-22
Dell Inspiron 640m laptop, running 10.04. It previously connected via wifi & now fails to connect, although the wireless indicator shows a connection. Connection via ethernet works.

Below there's some information that looked like might it be useful to diagnose the problem based on other posts in this forum. Thanks in advance!

> 
onebir@onebir-laptop:~$ **sudo lshw -C network**
[sudo] password for onebir: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:a8:81:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.4 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:dfdff000-dfdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:af:b7:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44  driverversion=2.0 duplex=half latency=64 link=no multicast=yes  port=twisted pair speed=10MB/s
       resources: irq:17 memory:df9fe000-df9fffff
onebir@onebir-laptop:~$ **sudo dhclient**
There is already a pid file /var/run/dhclient.pid with pid 2034
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/pan0/a6:7f:c3:1a:6a:0d
Sending on   LPF/pan0/a6:7f:c3:1a:6a:0d
Listening on LPF/wlan0/00:13:02:a8:81:4a
Sending on   LPF/wlan0/00:13:02:a8:81:4a
Listening on LPF/eth0/00:14:22:af:b7:b3
Sending on   LPF/eth0/00:14:22:af:b7:b3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 10.0.0.4 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPACK of 10.0.0.4 from 10.0.0.138
bound to 10.0.0.4 -- renewal in 41452 seconds.
onebir@onebir-laptop:~$ **ip address ls**
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:14:22:af:b7:b3 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::214:22ff:feaf:b7b3/64 scope link 
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 00:13:02:a8:81:4a brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.4/8 brd 10.255.255.255 scope global wlan0
    inet6 fe80::213:2ff:fea8:814a/64 scope link 
       valid_lft forever preferred_lft forever
4: pan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether a6:7f:c3:1a:6a:0d brd ff:ff:ff:ff:ff:ff
    inet6 fe80::a47f:c3ff:fe1a:6a0d/64 scope link 
       valid_lft forever preferred_lft forever
onebir@onebir-laptop:~$ ip route ls
10.0.0.0/8 dev wlan0  proto kernel  scope link  src 10.0.0.4 
default via 10.0.0.138 dev wlan0 
onebir@onebir-laptop:~$ **sudo cat /etc/resolv.conf**
nameserver 10.0.0.138
domain siemens
search siemens
onebir@onebir-laptop:~$ **dig google.com**

; <<>> DiG 9.7.0-P1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28581
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.            IN    A

;; ANSWER SECTION:
google.com.        85    IN    A    66.102.13.106
google.com.        85    IN    A    66.102.13.104
google.com.        85    IN    A    66.102.13.99
google.com.        85    IN    A    66.102.13.105
google.com.        85    IN    A    66.102.13.103
google.com.        85    IN    A    66.102.13.147

;; Query time: 34 msec
;; SERVER: 10.0.0.138#53(10.0.0.138)
;; WHEN: Sat Jan 22 11:58:02 2011
;; MSG SIZE  rcvd: 124

---

### Post by onebir on 2011-01-22
Weirdly it's now working. If anyone has any suggestions about what the problem might be &/ how to stop it recurring &/ resolve it quickly if there's no way to stop it recurring, they'd be much appreciated...

---

### Post by onebir on 2011-01-27
The problem seem to have recurred today. I could only connect after rebooting.

For the record, here's my chipset:

```
~$ lspci
...snip...
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

