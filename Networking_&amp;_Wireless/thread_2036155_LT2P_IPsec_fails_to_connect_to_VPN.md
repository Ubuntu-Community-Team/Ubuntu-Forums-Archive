---
title: "LT2P IPsec fails to connect to VPN"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2012-08-01
I am trying to set up a VPN access to an office router from home. I am using DGN220 Netgear router and set it up as a VPN gateway for a single remote PC. I have a remote access to the router from home so I am doing it remotely. However, when I am trying to connect using LT2P IPsec from my home laptop it fails. 

First of all, I configured the first page of the client (IPsec tab) see the screenshot and when I try to connect it asks me for a passphrase but I did not set up any passphrase only a p re-shared key. So I wonder if I did anything wrong? There is no option in the router to add a passphrase. I would really appreciate any help.

---

### Post by foxy123 on 2012-08-01
I think there is a trouble with authentication at some point:

Remote router's log:
```
Wed, 2012-08-01 13:08:09 - [Office] STATE_MAIN_R2: retransmission; will wait 20s for response 
Wed, 2012-08-01 13:08:29 - [Office] no suitable connection for peer '192.168.0.3' 
Wed, 2012-08-01 13:08:29 - [Office] sending encrypted notification INVALID_ID_INFORMATION to 2.101.29.13:500 
Wed, 2012-08-01 13:08:30 - [Office] STATE_MAIN_R2: retransmission; will wait 40s for response 
Wed, 2012-08-01 13:09:10 - [Office] max number of retransmissions (2) reached STATE_MAIN_R2 
```

L2PT's log
```
Aug 01 13:05:37.765 ipsec_setup: Starting Openswan IPsec U2.6.37/K3.2.0-27-generic...
Aug 01 13:05:38.066 ipsec__plutorun: Starting Pluto subsystem...
Aug 01 13:05:38.073 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Aug 01 13:05:38.088 recvref[30]: Protocol not available
Aug 01 13:05:38.088 xl2tpd[7123]: This binary does not support kernel L2TP.
Aug 01 13:05:38.088 xl2tpd[7126]: xl2tpd version xl2tpd-1.3.1 started on myasus PID:7126
Aug 01 13:05:38.088 xl2tpd[7126]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Aug 01 13:05:38.089 xl2tpd[7126]: Forked by Scott Balmos and David Stipp, (C) 2001
Aug 01 13:05:38.089 xl2tpd[7126]: Inherited by Jeff McAdams, (C) 2002
Aug 01 13:05:38.090 xl2tpd[7126]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Aug 01 13:05:38.090 xl2tpd[7126]: Listening on IP address 0.0.0.0, port 1701
Aug 01 13:05:38.090 Starting xl2tpd: xl2tpd.
Aug 01 13:05:38.115 ipsec__plutorun: 002 added connection description "Office"
Aug 01 13:06:48.886 104 "Office" #1: STATE_MAIN_I1: initiate
Aug 01 13:06:48.887 003 "Office" #1: received Vendor ID payload [Dead Peer Detection]
Aug 01 13:06:48.887 106 "Office" #1: STATE_MAIN_I2: sent MI2, expecting MR2
Aug 01 13:06:48.887 108 "Office" #1: STATE_MAIN_I3: sent MI3, expecting MR3
Aug 01 13:06:48.887 003 "Office" #1: ignoring informational payload, type INVALID_ID_INFORMATION msgid=00000000
Aug 01 13:06:48.888 003 "Office" #1: received and ignored informational message
Aug 01 13:06:48.888 010 "Office" #1: STATE_MAIN_I3: retransmission; will wait 20s for response
Aug 01 13:06:48.889 003 "Office" #1: discarding duplicate packet; already STATE_MAIN_I3
Aug 01 13:06:48.889 003 "Office" #1: ignoring informational payload, type INVALID_ID_INFORMATION msgid=00000000
Aug 01 13:06:48.889 003 "Office" #1: received and ignored informational message
Aug 01 13:06:48.889 010 "Office" #1: STATE_MAIN_I3: retransmission; will wait 40s for response
Aug 01 13:06:48.889 003 "Office" #1: discarding duplicate packet; already STATE_MAIN_I3
Aug 01 13:06:48.890 003 "Office" #1: ignoring informational payload, type INVALID_ID_INFORMATION msgid=00000000
Aug 01 13:06:48.890 003 "Office" #1: received and ignored informational message
Aug 01 13:06:48.890 031 "Office" #1: max number of retransmissions (2) reached STATE_MAIN_I3.  Possible authentication failure: no acceptable response to our first encrypted message
Aug 01 13:06:48.890 000 "Office" #1: starting keying attempt 2 of at most 3, but releasing whack
Aug 01 13:06:48.891 [ERROR  300]   'IPsec' failed to negotiate or establish security associations

```

---

