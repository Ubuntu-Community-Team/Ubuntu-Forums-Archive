---
title: "dhcp3-server"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by eaglecoth on 2011-10-22
Hi, I have this annoying problem with my dhcp3-server refusing to start. I thought I'd start with the relevant configuration that is available on the machine:

**[SIZE=2]Below is my ifconfig:[/SIZE]**
 
eth0 Link encap:Ethernet HWaddr 00:50:bf:da:2d:91
inet addr:82.182.xx.xx Bcast:82.182.96.255 Mask:255.255.255.0
inet6 addr: fe80::250:bfff:feda:2d91/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:11986 errors:0 dropped:0 overruns:0 frame:0
TX packets:7508 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:6912714 (6.9 MB) TX bytes:1269330 (1.2 MB)
Interrupt:11 Base address:0xd000
eth1 Link encap:Ethernet HWaddr 00:50:bf:db:49:16
inet addr:192.168.0.1 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::250:bfff:fedb:4916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:11965 errors:0 dropped:0 overruns:0 frame:0
TX packets:11276 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1679655 (1.6 MB) TX bytes:7437412 (7.4 MB)
Interrupt:12 Base address:0xdc00
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1080 (1.0 KB) TX bytes:1080 (1.0 KB)
 
**[SIZE=2]Below is my /etc/dhcp3/dhcpd.conf:[/SIZE]**
 
# Sample /etc/dhcpd.conf
# (add your comments here)
#default-lease-time 600;
#max-lease-time 7200;
#option subnet-mask 255.255.255.0;
#option broadcast-address 192.168.0.255;
#option routers 192.168.0.1;
#option domain-name-servers 81.26.226.3, 81.26.226.2;
 
ddns-update-style none;
log-facility local7;
authoritative;
subnet 192.168.0.0 netmask 255.255.255.0 {
#range 192.168.0.40 192.168.0.90;
range 192.168.0.211 192.168.0.215;
option routers 192.168.0.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option domain-name-servers 81.26.226.3;
default-lease-time 86400;
max-lease-time 86400;
}
 
[SIZE=2]**Below is the part of my /etc/services where I have currently no entry for port 67/68:**[/SIZE]
 
domain 53/udp
mtp 57/tcp # deprecated
tacacs-ds 65/tcp # TACACS-Database Service
tacacs-ds 65/udp
#bootps 67/tcp # BOOTP server
#bootps 67/udp
#bootpc 68/tcp # BOOTP client
##bootpc 68/udp
#dhcp3-server 67/tcp
#dhcp3-server 67/udp
#dhcp3-server 68/udp
#dhcp3-server 68/tcp
tftp 69/udp
gopher 70/tcp # Internet Gopher
gopher 70/udp
rje 77/tcp netrjs
finger 79/tcp
www 80/tcp http # WorldWideWeb HTTP
 
 
**[SIZE=2]Below is the output from "sudo ufw status" since I am using ufw[/SIZE]**
Status: aktiv
Till Ã
tgÃ¤rd FrÃ¥n
---- -------- -----
Samba ALLOW 192.168.0.0/24
22 ALLOW Anywhere
143 ALLOW Anywhere
25 ALLOW Anywhere
993 ALLOW Anywhere
80 ALLOW Anywhere
465 DENY Anywhere
10000 ALLOW Anywhere
67/udp ALLOW 192.168.0.0/24 68/udp
67/udp ALLOW Anywhere
67/tcp ALLOW Anywhere
68/udp ALLOW Anywhere
67 ALLOW Anywhere
 
 
[SIZE=2]**below is my ip-tables list:**[/SIZE]
Chain INPUT (policy DROP 4365 packets, 193K bytes)
pkts bytes target prot opt in out source destination
9969 1019K ufw-before-logging-input all -- * * 0.0.0.0/0 0.0.0.0/0
9969 1019K ufw-before-input all -- * * 0.0.0.0/0 0.0.0.0/0
4364 193K ufw-after-input all -- * * 0.0.0.0/0 0.0.0.0/0
4364 193K ufw-after-logging-input all -- * * 0.0.0.0/0 0.0.0.0/0
4364 193K ufw-reject-input all -- * * 0.0.0.0/0 0.0.0.0/0
4364 193K ufw-track-input all -- * * 0.0.0.0/0 0.0.0.0/0
Chain FORWARD (policy ACCEPT 774 packets, 40229 bytes)
pkts bytes target prot opt in out source destination
0 0 ACCEPT all -- eth0 eth1 192.168.0.0/24 0.0.0.0/0 ctstate NEW
13493 7172K ACCEPT all -- * * 0.0.0.0/0 0.0.0.0/0 ctstate RELATED,ESTABLISHED
774 40229 ufw-before-logging-forward all -- * * 0.0.0.0/0 0.0.0.0/0
774 40229 ufw-before-forward all -- * * 0.0.0.0/0 0.0.0.0/0
774 40229 ufw-after-forward all -- * * 0.0.0.0/0 0.0.0.0/0
774 40229 ufw-after-logging-forward all -- * * 0.0.0.0/0 0.0.0.0/0
774 40229 ufw-reject-forward all -- * * 0.0.0.0/0 0.0.0.0/0
Chain OUTPUT (policy ACCEPT 27 packets, 1188 bytes)
pkts bytes target prot opt in out source destination
4651 1243K ufw-before-logging-output all -- * * 0.0.0.0/0 0.0.0.0/0
4651 1243K ufw-before-output all -- * * 0.0.0.0/0 0.0.0.0/0
101 11309 ufw-after-output all -- * * 0.0.0.0/0 0.0.0.0/0
101 11309 ufw-after-logging-output all -- * * 0.0.0.0/0 0.0.0.0/0
101 11309 ufw-reject-output all -- * * 0.0.0.0/0 0.0.0.0/0
101 11309 ufw-track-output all -- * * 0.0.0.0/0 0.0.0.0/0
Chain ufw-after-forward (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-after-input (1 references)
pkts bytes target prot opt in out source destination
0 0 RETURN udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:137
0 0 RETURN udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:138
0 0 RETURN tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:139
0 0 RETURN tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:445
0 0 RETURN udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:67
0 0 RETURN udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:68
0 0 RETURN all -- * * 0.0.0.0/0 0.0.0.0/0 ADDRTYPE match dst-type BROADCAST
Chain ufw-after-logging-forward (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-after-logging-input (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-after-logging-output (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-after-output (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-before-forward (1 references)
pkts bytes target prot opt in out source destination
774 40229 ufw-user-forward all -- * * 0.0.0.0/0 0.0.0.0/0
Chain ufw-before-input (1 references)
pkts bytes target prot opt in out source destination
16 800 ACCEPT all -- lo * 0.0.0.0/0 0.0.0.0/0
5411 812K ACCEPT all -- * * 0.0.0.0/0 0.0.0.0/0 state RELATED,ESTABLISHED
51 2136 ufw-logging-deny all -- * * 0.0.0.0/0 0.0.0.0/0 state INVALID
51 2136 DROP all -- * * 0.0.0.0/0 0.0.0.0/0 state INVALID
0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0.0/0 icmp type 3
0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0.0/0 icmp type 4
0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0.0/0 icmp type 11
0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0.0/0 icmp type 12
2 56 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0.0/0 icmp type 8
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp spt:67 dpt:68
4489 204K ufw-not-local all -- * * 0.0.0.0/0 0.0.0.0/0
0 0 ACCEPT all -- * * 224.0.0.0/4 0.0.0.0/0
51 1428 ACCEPT all -- * * 0.0.0.0/0 224.0.0.0/4
4438 202K ufw-user-input all -- * * 0.0.0.0/0 0.0.0.0/0
Chain ufw-before-logging-forward (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-before-logging-input (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-before-logging-output (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-before-output (1 references)
pkts bytes target prot opt in out source destination
16 800 ACCEPT all -- * lo 0.0.0.0/0 0.0.0.0/0
4534 1231K ACCEPT all -- * * 0.0.0.0/0 0.0.0.0/0 state RELATED,ESTABLISHED
101 11309 ufw-user-output all -- * * 0.0.0.0/0 0.0.0.0/0
Chain ufw-logging-allow (0 references)
pkts bytes target prot opt in out source destination
Chain ufw-logging-deny (2 references)
pkts bytes target prot opt in out source destination
Chain ufw-not-local (1 references)
pkts bytes target prot opt in out source destination
4378 193K RETURN all -- * * 0.0.0.0/0 0.0.0.0/0 ADDRTYPE match dst-type LOCAL
51 1428 RETURN all -- * * 0.0.0.0/0 0.0.0.0/0 ADDRTYPE match dst-type MULTICAST
60 9224 RETURN all -- * * 0.0.0.0/0 0.0.0.0/0 ADDRTYPE match dst-type BROADCAST
0 0 ufw-logging-deny all -- * * 0.0.0.0/0 0.0.0.0/0 limit: avg 3/min burst 10
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0/0
Chain ufw-reject-forward (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-reject-input (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-reject-output (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-track-input (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-track-output (1 references)
pkts bytes target prot opt in out source destination
4 240 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 state NEW
70 9881 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 state NEW
Chain ufw-user-forward (1 references)
pkts bytes target prot opt in out source destination
Chain ufw-user-input (1 references)
pkts bytes target prot opt in out source destination
60 9224 ACCEPT udp -- * * 192.168.0.0/24 0.0.0.0/0 multiport dports 137,138 /* 'dapp_Samba' */
0 0 ACCEPT tcp -- * * 192.168.0.0/24 0.0.0.0/0 multiport dports 139,445 /* 'dapp_Samba' */
3 140 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:22
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:22
2 88 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:143
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:143
2 88 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:25
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:25
1 44 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:993
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:993
2 88 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:80
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:80
4 176 DROP tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:465
0 0 DROP udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:465
0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:10000
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:10000
0 0 ACCEPT udp -- * * 192.168.0.0/24 0.0.0.0/0 udp spt:68 dpt:67
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:67
0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:67
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:68
0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:67
0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0.0/0 udp dpt:67
Chain ufw-user-limit (0 references)
pkts bytes target prot opt in out source destination
0 0 LOG all -- * * 0.0.0.0/0 0.0.0.0/0 limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] '
0 0 REJECT all -- * * 0.0.0.0/0 0.0.0.0/0 reject-with icmp-port-unreachable
Chain ufw-user-limit-accept (0 references)
pkts bytes target prot opt in out source destination
0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0.0/0
Chain ufw-user-logging-forward (0 references)
pkts bytes target prot opt in out source destination
Chain ufw-user-logging-input (0 references)
pkts bytes target prot opt in out source destination
Chain ufw-user-logging-output (0 references)
pkts bytes target prot opt in out source destination
Chain ufw-user-output (1 references)
pkts bytes target prot opt in out source destination
 
 
 
**Below is the output of ip route:**
 
192.168.0.0/24 dev eth1 proto kernel scope link src 192.168.0.1
82.182.96.0/24 dev eth0 proto kernel scope link src 82.182.xx.xx
default via 82.182.96.1 dev eth0 metric 100
 
**[SIZE=2]When starting the dhcp3-server i get the following output:[/SIZE]**
 
sudo /etc/init.d/dhcp3-server start
* Starting DHCP server dhcpd3 * check syslog for diagnostics.
 
 
**[SIZE=2]Investigating the syslog gives the following error:[/SIZE]**
 
[SIZE=1]Oct 22 13:58:56 crona dhcpd: Copyright 2004-2008 Internet Systems Consortium.[/SIZE]
[SIZE=1]Oct 22 13:58:56 crona dhcpd: All rights reserved.[/SIZE]
[SIZE=1]Oct 22 13:58:56 crona dhcpd: For info, please visit [/SIZE][[SIZE=1]http://www.isc.org/sw/dhcp/[/SIZE]]("http://www.isc.org/sw/dhcp/")
[SIZE=1]Oct 22 13:58:56 crona dhcpd: Wrote 0 leases to leases file.[/SIZE]
[SIZE=1]Oct 22 13:58:56 crona dhcpd: Can't bind to dhcp address: Address already in use[/SIZE]
[SIZE=1]Oct 22 13:58:56 crona dhcpd: Please make sure there is no other dhcp server[/SIZE]
[SIZE=1]Oct 22 13:58:56 crona dhcpd: running and that there's no entry for dhcp or[/SIZE]
[SIZE=1]Oct 22 13:58:56 crona dhcpd: bootp in /etc/inetd.conf. Also make sure you[/SIZE]
[SIZE=1]Oct 22 13:58:56 crona dhcpd: are not running HP JetAdmin software, which[/SIZE]
[SIZE=1]Oct 22 13:58:56 crona dhcpd: includes a bootp server.[/SIZE]
 
**[SIZE=2]When using netstat to look for conflicting services I find the following:[/SIZE]**

[SIZE=1]Active internet connections (servers and established)[/SIZE]
[SIZE=1]Proto Recv-Q Send-Q Local Address Foreign Address State[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:53 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:3000 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:25 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 127.0.0.1:445 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 192.168.0.1:445 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:993 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:901 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 127.0.0.1:139 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 192.168.0.1:139 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:143 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:10000 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 0 0.0.0.0:80 0.0.0.0:* LISTEN[/SIZE]
[SIZE=1]tcp 0 52 192.168.0.1:22 192.168.0.123:49552 ETABLERAD[/SIZE]
[SIZE=1]tcp6 0 0 :::53 :::* LISTEN[/SIZE]
[SIZE=1]tcp6 0 0 :::22 :::* LISTEN[/SIZE]
[SIZE=1]udp 0 0 192.168.0.1:137 0.0.0.0:*[/SIZE]
[SIZE=1]udp 0 0 0.0.0.0:137 0.0.0.0:*[/SIZE]
[SIZE=1]udp 0 0 192.168.0.1:138 0.0.0.0:*[/SIZE]
[SIZE=1]udp 0 0 0.0.0.0:138 0.0.0.0:*[/SIZE]
[SIZE=1]udp 0 0 0.0.0.0:10000 0.0.0.0:*[/SIZE]
[SIZE=1]udp 0 0 0.0.0.0:53 0.0.0.0:*[/SIZE]
[SIZE=1]udp 0 0 0.0.0.0:67 0.0.0.0:*[/SIZE]
[SIZE=1]udp6 0 0 :::53 :::*[/SIZE]
 


[SIZE=1]Further, I am 100% sure that no other machine is running any bootp or dhcp server on the network, I have physically disconnected the machine from the network by removing the cables and the error persists.[/SIZE]

[SIZE=1]I can not understand what is blocking the service from starting. Anyone has experienced similiar errors?[/SIZE]

[SIZE=1]Any help is apprichiated.[/SIZE]

[SIZE=1]/Eaglecoth[/SIZE]

---

### Post by EtcGman on 2011-10-22
Check /etc/default/dhcp3-server if it is set: INTERFACES=eth0 - change it to INTERFACES=eth1

---

### Post by eaglecoth on 2011-10-24
> **EtcGman said:**
> Check /etc/default/dhcp3-server if it is set: INTERFACES=eth0 - change it to INTERFACES=eth1
 
 
 
Sorry, forgot to mention that the /etc/default/dhcp3-server looks as follows:
 
INTERFACES=eth1
 

I've tried both with and without this configuration.
 
/Eaglecoth

---

