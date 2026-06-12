---
title: "OpenVPN"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by ExemplarUbuntu on 2008-12-16
I've set-up OpenVPN on our server. I had some difficulty with the HowTo because several small steps are missing but eventually got it working.

The server is currently running from the cli and is logging this very frequently:

```

Tue Dec 16 09:27:20 2008 MULTI: multi_create_instance called
Tue Dec 16 09:27:20 2008 215.xx.yy.zz:1560 Re-using SSL/TLS context
Tue Dec 16 09:27:20 2008 215.xx.yy.zz:1560 LZO compression initialized
Tue Dec 16 09:27:20 2008 215.xx.yy.zz:1560 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Tue Dec 16 09:27:20 2008 215.xx.yy.zz:1560 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Tue Dec 16 09:27:20 2008 215.xx.yy.zz:1560 Local Options hash (VER=V4): '530fdded'
Tue Dec 16 09:27:20 2008 215.xx.yy.zz:1560 Expected Remote Options hash (VER=V4): '41690919'
Tue Dec 16 09:27:20 2008 215.xx.yy.zz:1560 TLS: Initial packet from 215.xx.yy.zz:1560, sid=457dd4c0 d6e721fe
Tue Dec 16 09:27:21 2008 215.xx.yy.zz:1530 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Tue Dec 16 09:27:21 2008 215.xx.yy.zz:1530 TLS Error: TLS handshake failed
Tue Dec 16 09:27:21 2008 215.xx.yy.zz:1530 SIGUSR1[soft,tls-error] received, client-instance restarting
Tue Dec 16 09:27:22 2008 MULTI: multi_create_instance called
Tue Dec 16 09:27:22 2008 215.xx.yy.zz:1561 Re-using SSL/TLS context
Tue Dec 16 09:27:22 2008 215.xx.yy.zz:1561 LZO compression initialized
Tue Dec 16 09:27:22 2008 215.xx.yy.zz:1561 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]

```

During the set-up I ran with TCP for a short time and that doesn't report the same problem.

The set-up is pretty much the same as the HowTo. The clients can connect and it seems to work fine.

My next step is to try to get the clients to see the dumb HP fileserver box on the LAN.

---

