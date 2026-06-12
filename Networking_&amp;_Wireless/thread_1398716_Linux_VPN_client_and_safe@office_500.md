---
title: "Linux VPN client and safe@office 500"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by ebaniz on 2010-02-04
Hi, has anyone been able to connect a Linux VPN client to a safe@office 500 using pre-shared keys?  From windows, I can establish a IPSec/L2TP  (also PSK) connection with no issues(No third party software. Just created a new connection in XP).   I have tried using StrongSwan and xl2tpd on Karmic without success.  The ipsec part appears to work as shown below:

```

002 "masdi" #1: initiating Main Mode
104 "masdi" #1: STATE_MAIN_I1: initiate
003 "masdi" #1: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n]
002 "masdi" #1: enabling possible NAT-traversal with method RFC 3947
106 "masdi" #1: STATE_MAIN_I2: sent MI2, expecting MR2
003 "masdi" #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike-02/03: i am NATed
108 "masdi" #1: STATE_MAIN_I3: sent MI3, expecting MR3
002 "masdi" #1: Peer ID is ID_IPV4_ADDR: 'x.x.x.x'
002 "masdi" #1: ISAKMP SA established
004 "masdi" #1: STATE_MAIN_I4: ISAKMP SA established
002 "masdi" #2: initiating Quick Mode PSK+ENCRYPT+UP {using isakmp#1}
003 "masdi" #2: NAT-Traversal: Transport Mode not allowed due to security concerns -- using Tunnel mode
003 "masdi" #2: NAT-Traversal: Transport Mode not allowed due to security concerns -- using Tunnel mode
112 "masdi" #2: STATE_QUICK_I1: initiate
002 "masdi" #2: sent QI2, IPsec SA established {ESP=>0x7e9329d9 <0x7540f8c8 NATOA=0.0.0.0}
004 "masdi" #2: STATE_QUICK_I2: sent QI2, IPsec SA established {ESP=>0x7e9329d9 <0x7540f8c8 NATOA=0.0.0.0}


```

Then I issue:
```
echo "c masdi" > /var/run/xl2tpd/l2tp-control
```

But xl2tpd fails with:

```

Feb  4 21:17:32 laptop xl2tpd[26175]: setsockopt recvref[22]: Protocol not available
Feb  4 21:17:32 laptop xl2tpd[26175]: This binary does not support kernel L2TP.
Feb  4 21:17:32 laptop xl2tpd[26176]: xl2tpd version xl2tpd-1.2.4 started on laptop PID:26176
Feb  4 21:17:32 laptop xl2tpd[26176]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Feb  4 21:17:32 laptop xl2tpd[26176]: Forked by Scott Balmos and David Stipp, (C) 2001
Feb  4 21:17:32 laptop xl2tpd[26176]: Inherited by Jeff McAdams, (C) 2002
Feb  4 21:17:32 laptop xl2tpd[26176]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Feb  4 21:17:32 laptop xl2tpd[26176]: Listening on IP address 0.0.0.0, port 1701
Feb  4 21:17:40 laptop xl2tpd[26176]: get_call: allocating new tunnel for host x.x.x.x, port 1701.
Feb  4 21:17:40 laptop xl2tpd[26176]: Connecting to host x.x.x.x, port 1701
Feb  4 21:17:40 laptop xl2tpd[26176]: **control_finish: message type is (null)(0).  Tunnel is 0, call is 0.**
Feb  4 21:17:40 laptop xl2tpd[26176]: control_finish: sending SCCRQ
Feb  4 21:17:41 laptop xl2tpd[26176]: network_thread: select timeout
Feb  4 21:17:45 laptop xl2tpd[26176]: last message repeated 4 times
Feb  4 21:17:45 laptop xl2tpd[26176]: **Maximum retries exceeded for tunnel 6991.  Closing**.

```


PPPd never gets launched.  To me it seems like this should work given I can create a vpn connection directly from WinXP without installing any checkpoint clients.

Any ideas?

---

### Post by bernz on 2011-01-14
Hi! I am having the same exact problem. Did you ever resolve this?

---

### Post by bernz on 2011-01-14
Hi! I am having the same exact problem. Did you ever resolve this?

---

### Post by bernz on 2011-01-14
Hi! I am having the same exact problem. Did you ever resolve this?

---

