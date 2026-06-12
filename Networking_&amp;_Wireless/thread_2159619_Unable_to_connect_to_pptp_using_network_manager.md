---
title: "Unable to connect to pptp using network manager"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by tichon on 2013-07-03
I see the following in the logs:

Jul  3 16:38:04 tichon pppd[10308]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jul  3 16:38:04 tichon pppd[10308]: pppd 2.4.5 started by root, uid 0
Jul  3 16:38:04 tichon pppd[10308]: Using interface ppp0
Jul  3 16:38:04 tichon pppd[10308]: Connect: ppp0 <--> /dev/pts/8
Jul  3 16:38:35 tichon pppd[10308]: LCP: timeout sending Config-Requests
Jul  3 16:38:35 tichon pppd[10308]: Connection terminated.
Jul  3 16:38:35 tichon pppd[10308]: Modem hangup
Jul  3 16:38:35 tichon pppd[10308]: Exit.

Doesn't appear that the connection is even initializing. Anyone have any thoughts on this? Thanks for your input.

Update (edit):
This appeared to have been the case while NAT within a network. While on a different network I connected just fine. Any ideas what could have been blocking my attempts?

---

