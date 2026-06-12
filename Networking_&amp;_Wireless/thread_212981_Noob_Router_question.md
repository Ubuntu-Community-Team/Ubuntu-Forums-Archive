---
title: "Noob Router question"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by flub on 2006-07-10
I've got a Linksys Wireless Router which my Dapper laptop connects to.

On the Router itself (192.168.1.1) I've configured the DNS as follows.

208.67.222.222
208.67.220.220

Now the question I have, is do I need anything in my resolv.conf file?  If so what and why.

Also, how can I check what DNS servers I'm "REALLY" using?

Many thanks in advance.

---

### Post by tturrisi on 2006-07-10
The router should config the dns servers automatically when it grabs them from the modem.  If using a static ip address for your net card then use 192.168.1.1 as default gateway & dns server.

---

### Post by flub on 2006-07-11
Cheers thanks.

---

