---
title: "dial GPRS connection with pppd"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by pratik007 on 2009-07-16
Hi Experts,

I am trying to make GPRS connection from my linux (fc10 Linux localhost.localdomain 2.6.27.5-117.fc10.i686 #1 SMP Tue Nov 18 12:19:59 EST 2008 i686 i686 i386 GNU/Linux) machine.

I'm using kppp to dial GPRS connection.

I have connected my GPRS OEM module on /dev/ttyS0 of my linux desktop machine.


and configure kppp as per link [www.geocities.com/tru2oxid/index.html]("http://www.geocities.com/tru2oxid/index.html") (with neccesory modification for my GPRS service provider)

When I click on connect button of kppp I get following error messages in log window.
========================================
Jul 16 18:35:54 localhost pppd[32306]: pppd 2.4.4 started by root, uid 0
Jul 16 18:35:54 localhost pppd[32306]: Using interface ppp0
Jul 16 18:35:54 localhost pppd[32306]: Connect: ppp0 <--> /dev/ttyS0
Jul 16 18:35:56 localhost pppd[32306]: PAP authentication succeeded
Jul 16 18:35:57 localhost pppd[32306]: LCP terminated by peer
Jul 16 18:36:00 localhost pppd[32306]: Connection terminated.
Jul 16 18:36:00 localhost pppd[32306]: Modem hangup
Jul 16 18:36:00 localhost pppd[32306]: Exit.
========================================

Any idea what could be wrong?

Please let me know if any more information is required from myside.

Regards,
Pratik

---

