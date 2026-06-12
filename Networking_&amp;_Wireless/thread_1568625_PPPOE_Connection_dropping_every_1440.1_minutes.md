---
title: "PPPOE Connection dropping every 1440.1 minutes"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by lordyarox on 2010-09-05
After continuous connection hang ups and a lot of research I managed to set up my server so that it would reconnect - reestablish a PPPOE connection every time it dropped.

Seeing as it drops evers 1440.1 minutes (approximately once per 24 hours), that didn't pose an issue, up till now. I now require my server to run without any hangups whatsoever. Doing a bit of research, I came to realize that this may be a ubuntu specific issue.

I would like to know why this is being caused, and how to fix it. I have considered the option of my ISP reseting the connection every day, and I will test that, but I require answers based on the logs.

The following is a recurring part of the log from my messages, located in /var/log/messages
```

Aug 10 12:35:42 leon-server pppd[1051]: LCP terminated by peer
Aug 10 12:35:42 leon-server pppd[1051]: Connect time 1440.1 minutes.
Aug 10 12:35:42 leon-server pppd[1051]: Sent 690210218 bytes, received 460810804 bytes.
Aug 10 12:35:42 leon-server pppd[1051]: restoring old default route to eth0 [192.168.1.1]
Aug 10 12:35:45 leon-server pppd[1051]: Connection terminated.
Aug 10 12:35:45 leon-server pppd[1051]: Modem hangup
Aug 10 12:36:01 leon-server kernel: [259311.860655] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.5 DST=192.168.1.1 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=14465 DF PROTO=UDP SPT=60700 DPT=53 LEN=54 
Aug 10 12:36:01 leon-server kernel: [259311.860683] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.5 DST=192.168.1.1 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=14465 DF PROTO=UDP SPT=60700 DPT=53 LEN=54 
Aug 10 12:36:01 leon-server pppd[1051]: Terminating on signal 15
Aug 10 12:36:01 leon-server pppd[1051]: Exit.
Aug 10 12:36:02 leon-server kernel: [259312.693198] [UFW BLOCK] IN=eth0 OUT= MAC=00:1c:c0:f7:98:20:00:d0:50:5a:11:9b:08:00 SRC=70.55.96.32 DST=192.168.1.5 LEN=157 TOS=0x00 PREC=0x20 TTL=115 ID=26439 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.1.5 DST=70.55.96.32 LEN=129 TOS=0x00 PREC=0x00 TTL=49 ID=0 DF PROTO=UDP SPT=9985 DPT=60435 LEN=109 ] 
Aug 10 12:36:04 leon-server pppd[10135]: Plugin rp-pppoe.so loaded.
Aug 10 12:36:04 leon-server pppd[10135]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Aug 10 12:36:04 leon-server pppd[10137]: pppd 2.4.5 started by root, uid 0
Aug 10 12:36:04 leon-server pppd[10137]: PPP session is 6839
Aug 10 12:36:04 leon-server pppd[10137]: Connected to 00:90:1a:42:69:bb via interface eth0
Aug 10 12:36:04 leon-server pppd[10137]: Using interface ppp0
Aug 10 12:36:04 leon-server pppd[10137]: Connect: ppp0 <--> eth0
Aug 10 12:36:05 leon-server pppd[10137]: CHAP authentication succeeded
Aug 10 12:36:05 leon-server pppd[10137]: CHAP authentication succeeded
Aug 10 12:36:05 leon-server pppd[10137]: peer from calling number 00:90:1A:42:69:BB authorized
Aug 10 12:36:05 leon-server pppd[10137]: replacing old default route to eth0 [192.168.1.1]
Aug 10 12:36:05 leon-server pppd[10137]: local  IP address 89.143.141.78
Aug 10 12:36:05 leon-server pppd[10137]: remote IP address 213.250.19.90
Aug 10 12:36:05 leon-server pppd[10137]: primary   DNS address 193.189.160.13
Aug 10 12:36:05 leon-server pppd[10137]: secondary DNS address 193.189.160.23
Aug 10 12:36:13 leon-server kernel: [259323.721685] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=70.55.96.32 DST=89.143.141.78 LEN=157 TOS=0x00 PREC=0x20 TTL=116 ID=26589 PROTO=ICMP TYPE=3 CODE=3 [SRC=89.143.141.78 DST=70.55.96.32 LEN=129 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=9985 DPT=60429 LEN=109 ]
```

---

### Post by lordyarox on 2010-09-06
Confirmed as an ISP issue - dynamic IP's reset every 24 hours, if/when I change to a static IP the issues should be gone. 

Not Ubuntu-related.

---

