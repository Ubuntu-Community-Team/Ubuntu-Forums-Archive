---
title: "VPN connection failed"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by hc1785 on 2010-11-19
Hi, 
I am trying to set up a VPN connection from Ubuntu 10.10, but keep getting the "VPN connection failed" message or "VPN service failed to start". I have tried a few suggestions found on other threads (such as enabling MPPE or putting the domain name before the ip address) but without any luck. I really have no idea what is going wrong - if anyone has any tips I would be most grateful. The relavent part of the /log/messages file is included below.
Thanks. 


Nov 19 13:29:48 henry-Presario-V5000-ES273EA-ABU pppd[2174]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Nov 19 13:29:48 henry-Presario-V5000-ES273EA-ABU pppd[2174]: pppd 2.4.5 started by root, uid 0
Nov 19 13:29:48 henry-Presario-V5000-ES273EA-ABU pppd[2174]: Using interface ppp0
Nov 19 13:29:48 henry-Presario-V5000-ES273EA-ABU pppd[2174]: Connect: ppp0 <--> /dev/pts/1
Nov 19 13:29:49 henry-Presario-V5000-ES273EA-ABU pppd[2174]: LCP terminated by peer (^TM-+N'^@<M-Mt^@^@^CM-.)
Nov 19 13:29:52 henry-Presario-V5000-ES273EA-ABU pppd[2174]: Connection terminated.
Nov 19 13:29:53 henry-Presario-V5000-ES273EA-ABU pppd[2174]: Modem hangup
Nov 19 13:29:53 henry-Presario-V5000-ES273EA-ABU pppd[2174]: Exit.
Nov 19 13:31:27 henry-Presario-V5000-ES273EA-ABU pppd[2204]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Nov 19 13:31:27 henry-Presario-V5000-ES273EA-ABU pppd[2204]: pppd 2.4.5 started by root, uid 0
Nov 19 13:31:27 henry-Presario-V5000-ES273EA-ABU pppd[2204]: Using interface ppp0
Nov 19 13:31:27 henry-Presario-V5000-ES273EA-ABU pppd[2204]: Connect: ppp0 <--> /dev/pts/1
Nov 19 13:31:58 henry-Presario-V5000-ES273EA-ABU pppd[2204]: LCP: timeout sending Config-Requests
Nov 19 13:31:58 henry-Presario-V5000-ES273EA-ABU pppd[2204]: Connection terminated.
Nov 19 13:31:59 henry-Presario-V5000-ES273EA-ABU pppd[2204]: Modem hangup
Nov 19 13:31:59 henry-Presario-V5000-ES273EA-ABU pppd[2204]: Exit.

---

