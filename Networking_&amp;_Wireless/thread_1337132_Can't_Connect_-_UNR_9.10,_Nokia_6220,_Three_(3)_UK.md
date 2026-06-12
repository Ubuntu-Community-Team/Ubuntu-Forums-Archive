---
title: "Can't Connect - UNR 9.10, Nokia 6220, Three (3) UK"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by hoki_goujons on 2009-11-25
I'm trying to connect to the internet using my Nokia 6220, a cable and an Acer Aspire One using UNR 9.10. Everything's up to date regarding patches, firmware etc. I'm on 3 UK with an Internet add-on.

It used to work fine on 9.04 and it works fine on XP with Nokia PC Suite, choosing the 3 UK 'eseries' profile in One Touch Access, but I'm having no luck in Ubuntu now.

When I plug it in and choose 'PC Suite' mode from the phone, I can create a connection from the wizard on Ubuntu (choosing 'Handsets' as the 3 profile), then when I try to connect I get a popup saying 'GSM Network disconnected'.

Output from /var/log/messages is:

Nov 25 12:27:49 ben-laptop pppd[2251]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Nov 25 12:27:49 ben-laptop pppd[2251]: pppd 2.4.5 started by root, uid 0
Nov 25 12:27:49 ben-laptop pppd[2251]: Using interface ppp0
Nov 25 12:27:49 ben-laptop pppd[2251]: Connect: ppp0 <--> /dev/ttyACM0
Nov 25 12:27:49 ben-laptop pppd[2251]: PAP authentication succeeded
Nov 25 12:27:50 ben-laptop pppd[2251]: LCP terminated by peer
Nov 25 12:27:53 ben-laptop pppd[2251]: Connection terminated.
Nov 25 12:27:54 ben-laptop pppd[2251]: Terminating on signal 15
Nov 25 12:27:54 ben-laptop pppd[2251]: Modem hangup
Nov 25 12:27:54 ben-laptop pppd[2251]: Exit.

---

### Post by pdc on 2009-11-25
there have been many posts since 9.10 came out; folks reporting everything was fine and dandy under 9.04; and now, sadness with 9.10

older, wiser, folks have reported they do NOT install new software immediately; they let others explore the minefields of new software and install after 2-3 months as most bugs are sorted by then

---

### Post by hoki_goujons on 2009-12-04
> **pdc said:**
> there have been many posts since 9.10 came out; folks reporting everything was fine and dandy under 9.04; and now, sadness with 9.10

older, wiser, folks have reported they do NOT install new software immediately; they let others explore the minefields of new software and install after 2-3 months as most bugs are sorted by then

Other, less smarmy, folks needed some of the new features in 9.10 and, having read the write-ups, were willing to face the possibility of losing mobile internet for a while in exchange for them ;)

---

