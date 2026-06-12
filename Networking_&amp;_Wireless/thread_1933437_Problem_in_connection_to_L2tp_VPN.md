---
title: "Problem in connection to L2tp VPN"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by x53x6ex69x67x67x65x72 on 2012-02-29
Hi  
I'm trying to connect to a L2TP VPN account in Ubuntu Lucid Lynx.
I installed "l2tp-ipsec-vpn" But couldn't connect so I added Openswan's PPA and upgraded to 2.6.37 but still I can't connect!
VPN account itself has no problem; Windows 7 connects to it without any problem!
l2tp-ipsec-vpn's log is: 
 ```
Feb 29 02:35:09.691 xl2tpd[7020]: death_handler: Fatal signal 15 received
 Feb 29 02:35:09.691 Stopping xl2tpd: xl2tpd.
 Feb 29 02:35:09.828 ipsec_setup: Openswan IPsec apparently already active, start aborted
 Feb 29 02:35:09.906 recvref[22]: Protocol not available
 Feb 29 02:35:09.906 Starting xl2tpd: xl2tpd.
 Feb 29 02:35:09.907 xl2tpd[29080]: This binary does not support kernel L2TP.
 Feb 29 02:35:09.908 xl2tpd[29081]: xl2tpd version xl2tpd-1.2.5 started on ariyan-laptop PID:29081
 Feb 29 02:35:09.909 xl2tpd[29081]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
 Feb 29 02:35:09.909 xl2tpd[29081]: Forked by Scott Balmos and David Stipp, (C) 2001
 Feb 29 02:35:09.911 xl2tpd[29081]: Inherited by Jeff McAdams, (C) 2002
 Feb 29 02:35:09.911 xl2tpd[29081]: Forked again by Xelerance (www.xelerance.com) (C) 2006
 Feb 29 02:35:09.912 xl2tpd[29081]: Listening on IP address 0.0.0.0, port 1701
 Feb 29 02:35:49.542 Last command timed out
 Feb 29 02:35:50.582 whack: is Pluto running?  connect() for "/var/run/pluto/pluto.ctl" failed (111 Connection refused)
 Feb 29 02:35:50.622 whack: is Pluto running?  connect() for "/var/run/pluto/pluto.ctl" failed (111 Connection refused)
 Feb 29 02:35:50.638 [ERROR  300]   'IPsec' failed to negotiate or establish security associations
 
```

How can I fix it?
Thanks

---

