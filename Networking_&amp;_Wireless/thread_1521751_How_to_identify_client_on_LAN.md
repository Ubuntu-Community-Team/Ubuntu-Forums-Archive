---
title: "How to identify client on LAN"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2010-07-01
Hi,

I have a client on my lan.  I know he's there b/c he shows up in syslog every three hours or so...

Jun 28 14:03:22 homapump dhcpd: DHCPACK on 192.168.0.111 to 00:1e:37:cc:25:ad (<xxx>) via eth1

And there are some strange entries in kern.log...

Jun 30 15:45:38 <xxx> kernel: [8649804.588279] Inbound IN=eth0 OUT=eth1 SRC=208.74.67.20 DST=192.168.0.111 LEN=68 TOS=0x00 PREC=0x80 TTL=49 ID=5931 PROTO=ICMP TYPE=3 CODE=10 [SRC=192.168.0.111 DST=208.74.67.20 LEN=40 TOS=0x00 PREC=0x00 TTL=114 ID=4482 DF PROTO=TCP SPT=2250 DPT=80 WINDOW=64512 RES=0x00 ACK FIN URGP=0 ] 

He seems to be communicating with 208.74.67.20 and another host.

And in apache2/error.log...

[Thu Jun 24 08:05:24 2010] [error] [client 192.168.0.111] File does not exist: /var/www/HNAP1
[Thu Jun 24 08:05:27 2010] [error] [client 192.168.0.111] File does not exist: /var/www/TEADevInfo

He's looking for web pages that don't exist.

I think this client may be running some sort of malware.

How can I identify this client?  Can I get his host name or something that might tip me off as to his identity?

Thanks,

Alex

---

