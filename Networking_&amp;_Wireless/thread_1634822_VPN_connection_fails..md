---
title: "VPN connection fails."
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by grypher on 2010-12-01
I've been trying to connect to the Ipredator VPN service for some time with no success, it always worked under 9.04. After moving to 10.04 the service would get disconnected after a few hours (Terminated on signal 15) now after getting 10.10, it dies directly after connecting.    

Dec  1 07:18:39 Panther pppd[12757]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Dec  1 07:18:39 Panther pppd[12757]: pppd 2.4.5 started by root, uid 0
Dec  1 07:18:39 Panther pppd[12757]: Using interface ppp0
Dec  1 07:18:39 Panther pppd[12757]: Connect: ppp0 <--> /dev/pts/0
Dec  1 07:18:41 Panther pppd[12757]: CHAP authentication succeeded
Dec  1 07:18:41 Panther pppd[12757]: MPPE 128-bit stateless compression enabled
Dec  1 07:18:41 Panther pppd[12757]: local  IP address 93.182.150.51
Dec  1 07:18:41 Panther pppd[12757]: remote IP address 93.182.150.2
Dec  1 07:18:41 Panther pppd[12757]: primary   DNS address 93.182.182.85
Dec  1 07:18:41 Panther pppd[12757]: secondary DNS address 93.182.182.85
Dec  1 07:19:21 Panther pppd[12757]: Terminating on signal 15
Dec  1 07:19:21 Panther pppd[12757]: Connect time 0.7 minutes.
Dec  1 07:19:21 Panther pppd[12757]: Sent 0 bytes, received 8345 bytes.
Dec  1 07:19:21 Panther pppd[12757]: Child process /usr/sbin/pptp vpn.ipredator.se --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-12755 (pid 12759) terminated with signal 15
Dec  1 07:19:21 Panther pppd[12757]: Connection terminated.
Dec  1 07:19:21 Panther pppd[12757]: Exit.

 Is there a fix/workaround/reason for this? Its not a server side issue as windows connects fine and my settings have always on this machine before 10.10.

---

