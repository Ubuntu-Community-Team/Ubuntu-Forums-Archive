---
title: "Cannot Ping server from outside of the network"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by U2XS on 2012-05-09
I suspect it's a router issue, but I have to ask.  I have a DD-WRT router & a Kubuntu Zoneminder installation.  I am trying to ping the server's HTTP port from outside of the network.  It does work internally.  

On DD-WRT, I have forwarded the port correctly.  I have also unchecked 'Block Anonymous WAN Requests (ping)'.

If I go to [COLOR="YellowGreen"][Http://MyIPAddress.com:MyPortNumber](Http://MyIPAddress.com:MyPortNumber)[/COLOR] on my browser, I can see the web page.  However if I '[COLOR="YellowGreen"]PING MyIPAddress.com:MyPortNumber[/COLOR]', the request just times out and gives me an error message.

Is there something I can do on the serverside?  Or is this a router issue?

---

### Post by howefield on 2012-05-10
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by 2F4U on 2012-05-10
Two possibilities come to my mind:
1) A firewall on the router is blocking ping requests (for example, my router is configured intentionally to block ping requests from outside).
2) A firewall on the server is blocking the ping request.

---

