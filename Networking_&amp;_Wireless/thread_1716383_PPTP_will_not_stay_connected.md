---
title: "PPTP will not stay connected"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by landersohn on 2011-03-28
I need desperately some help. I need to connect to two separate VPN servers under Lucid 64bit (not simultaneously)
The first one connects OK if I use the commend line pptp (pon) but will not connect using network-manager, I can live with that.

The second behaves very odd: it appears to sometimes connect (most of the time it fails at the authentication stage), gives me a new IP and DNS names but then drops the connection a few seconds later.

the system log shows
Mar 28 10:16:51 lowpull2-lt pptp[2873]: anon log[ctrlp_disp:pptp_ctrl.c:788]: Received Stop Control Connection Request.
Mar 28 10:16:51 lowpull2-lt pptp[2873]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 4 'Stop-Control-Connection-Reply'
Mar 28 10:16:51 lowpull2-lt pptp[2873]: anon log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Mar 28 10:16:51 lowpull2-lt pptp[2873]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Mar 28 10:16:51 lowpull2-lt pptp[2873]: anon log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)

To my great chagrin, the VPN works very well under Windoze. It pains me that Lucid does not seem to be able to get a reliable pptp client going for me.

Can anyone help with that? Do I need to upgrade my kernel (I am running 2.6.32-25-generic #44) or other components?

Thanks

---

