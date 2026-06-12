---
title: "nfs not starting..."
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by knichel on 2009-11-04
I recently set up a proxy/gateway on my network.  I also run a DHCP server and NFS exports.  When I restarted the computer, I noticed that nfs-kernel-server would not start...  I examined /var/log/messages and notices gobs and gobs of messages like these...
ETH1 is my inside interface on 192.168.6.0/24
ETH0 is my outside interface on 192.168.15.0/24 that connects to my VoIP router

```

Nov  4 17:49:25 Peechie kernel: [ 1073.539367] IN=eth0 OUT= MAC=00:1d:7d:09:94:0f:00:13:10:24:f5:0b:08:00 SRC=69.59.248.136 DST=192.168.15.100 LEN=80 TOS=0x00 PREC=0x00 TTL=247 ID=31635 DF PROTO=UDP SPT=12258 DPT=10118 LEN=60                                                                                                                     
Nov  4 17:49:25 Peechie kernel: [ 1073.549845] IN=eth0 OUT= MAC=00:1d:7d:09:94:0f:00:13:10:24:f5:0b:08:00 SRC=69.59.248.136 DST=192.168.15.100 LEN=80 TOS=0x00 PREC=0x00 TTL=247 ID=31636 DF PROTO=UDP SPT=12258 DPT=10118 LEN=60                                                                                                                     
Nov  4 17:49:25 Peechie kernel: [ 1073.559650] IN=eth0 OUT= MAC=00:1d:7d:09:94:0f:00:13:10:24:f5:0b:08:00 SRC=69.59.248.136 DST=192.168.15.100 LEN=80 TOS=0x00 PREC=0x00 TTL=247 ID=31637 DF PROTO=UDP SPT=12258 DPT=10118 LEN=60                                                                                                                     
Nov  4 17:49:25 Peechie kernel: [ 1073.570013] IN=eth0 OUT= MAC=00:1d:7d:09:94:0f:00:13:10:24:f5:0b:08:00 SRC=69.59.248.136 DST=192.168.15.100 LEN=80 TOS=0x00 PREC=0x00 TTL=247 ID=31638 DF PROTO=UDP SPT=12258 DPT=10118 LEN=60

```

the SRC and DST do change and sometimes the SRC is something inside my network.  

I did lookup the address above...69.59.248.136 and it belongs to Vonage (my VoIP provider)

Also, what can I do to determine why I cannot start nfs?


I am just wondering if these are something to worry about?

---

### Post by knichel on 2009-11-12
Bump...
Anybody able to help?

---

