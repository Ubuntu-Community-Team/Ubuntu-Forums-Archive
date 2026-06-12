---
title: "Cannot connect to PPTP VPN in Ubuntu 10.04"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by White1989 on 2013-04-07
Hi, could you please someone help me to resolve the issue that's occurring when I try to connect to VPN using PPTP protocol on Ubuntu 10.04? 
I have set all the parameters (gateway, username, password) correctly as obtained by my network admin but when applying to connect to VPN the connection failed. 
I've checked for logs using:   grep ppp /var/log/messages and found the following:

Apr  3 18:49:17 ubuntu pppd[4980]: pppd 2.4.5 started by root, uid 0
Apr  3 18:49:17 ubuntu pppd[4980]: Using interface ppp0
Apr  3 18:49:17 ubuntu pppd[4980]: Connect: ppp0 <--> /dev/pts/1
Apr  3 18:49:48 ubuntu pppd[4980]: **LCP: timeout sending Config-Requests**
Apr  3 18:49:48 ubuntu pppd[4980]: Connection terminated.
Apr  3 18:49:48 ubuntu pppd[4980]: Modem hangup
Apr  3 18:49:48 ubuntu pppd[4980]: Exit.
Apr  6 20:44:34 ubuntu pppd[8584]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr  6 20:44:34 ubuntu pppd[8584]: pppd 2.4.5 started by root, uid 0
Apr  6 20:44:34 ubuntu pppd[8584]: Using interface ppp0
Apr  6 20:44:34 ubuntu pppd[8584]: Connect: ppp0 <--> /dev/pts/1
Apr  6 20:45:05 ubuntu pppd[8584]: **LCP: timeout sending Config-Requests**
Apr  6 20:45:05 ubuntu pppd[8584]: Connection terminated.
Apr  6 20:45:05 ubuntu pppd[8584]: Modem hangup
Apr  6 20:45:05 ubuntu pppd[8584]: Exit.
Apr  7 11:40:50 ubuntu pppd[2032]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr  7 11:40:50 ubuntu pppd[2032]: pppd 2.4.5 started by root, uid 0
Apr  7 11:40:50 ubuntu pppd[2032]: Using interface ppp0
Apr  7 11:40:50 ubuntu pppd[2032]: Connect: ppp0 <--> /dev/pts/1
Apr  7 11:41:21 ubuntu pppd[2032]: LCP: timeout sending Config-Requests
Apr  7 11:41:21 ubuntu pppd[2032]: Connection terminated.
Apr  7 11:41:21 ubuntu pppd[2032]: Modem hangup
Apr  7 11:41:21 ubuntu pppd[2032]: Exit.

Is there something more that I have to set? Because connecting to the same VPN in Windows proceeds without any problem.
Thank you

---

