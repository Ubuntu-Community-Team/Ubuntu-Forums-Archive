---
title: "Can i stop outgoing mail from my network"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by krishanthan on 2011-12-09
Dear Friend,

First thanks for your help. now i want another help, in my small company i was configure only squid proxy, now i can control or stop outgoing mail through my network. if it's possible how to make. (i think before i have to make transparent squid proxy)

---

### Post by jonobr on 2011-12-09
Quickest way is to block traffic on port 25, SMTP, however, AFAIK squid is atoamatically setup to do this by default

From the squid faq

> SMTP and HTTP are rather similar in design. This, unfortunately, may allow someone to relay an email message through your HTTP proxy. To prevent this, you must make sure that your proxy denies HTTP requests to port 25, the SMTP port.

Squid is configured this way by default. The default squid.conf file lists a small number of trusted ports. See the Safe_ports ACL in squid.conf. Your configuration file should always deny unsafe ports early in the http_access lists: 

---

