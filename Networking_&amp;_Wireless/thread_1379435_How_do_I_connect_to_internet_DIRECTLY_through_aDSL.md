---
title: "How do I connect to internet DIRECTLY through aDSL modem?"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by s3a on 2010-01-12
How do I connect to internet DIRECTLY through my aDSL modem? I'm sure it's easy but I just don't know how to do it. I'd appreciate it if someone could at least point me in the right direction. I already have a router but I just want to connect it without using the router to confirm that my modem is defective because sometimes my internet works and sometimes it doesn't. In addition to testing my modem, I would also like to know how to do this for future practical reasons.

Any input would be GREATLY appreciated!
Thanks in advance!

---

### Post by adam814 on 2010-01-12
Why not just connect your computer via ethernet cable directly to the port on the back of the aDSL modem?

---

### Post by jmore9 on 2010-01-12
As was just posted connecting to your dsl modem via usb or ethernet is direct connection.  Connecting via router or switch is not.

---

### Post by efflandt on 2010-01-12
It depends whether your modem is just a bridge modem or in bridge mode (that requires doing pppoe on your computer), or if it is really a modem/router that handles PPPoE for you and gives you an IP address automatically.

In the latter case (modem/router) all you would have to do is connect it and have your PC configured for an automatic ethernet connection.

In the case of an old bridge modem, or a newer modem/router put into bridge mode, you would need to configure DSL in Network Connections with your pppoe login.  It does not really matter if ethernet to the DSL modem has an IP, unless your modem has an IP to check statistics (my old bridge modem never had an IP).

I am currently running a 2Wire 2701HG-B DSL wireless/modem/router that apparently runs a flavor of FreeBSD.  So I simply connect wired or wireless to it and I am on-line.  Although, I do some unusual things, like use a Zyxel P-330W in "wireless client bridge mode" to connect my wired desktop or old laptop (fried wireless PC card) to it remotely by wireless.

---

### Post by Quint_ishbuntu on 2010-02-10
what happens if ppppoe is not installed and it sugests at-get install pppoe however you need internet to install it ?

---

### Post by superprash2003 on 2010-02-10
its usually installed by default !!

---

