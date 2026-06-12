---
title: "Cups server over network"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by reuben on 2006-01-15
Hello, I'm having trouble getting cups server working over the network.

Here is my setup:

DSL Modem
      |
      |
LinkSys Wireless Router ----wireless---- 192.168.1.103 Laptop
      |                                               
    ethernet
      |
      |
    192.168.1.100
    Guarddog firewall
    Desktop ----parallel---- printer


Hopefully the above is clear :) 

From my desktop, I can browse to 127.0.0.1:631 and view the cups panel. However, from the desktop OR the laptop, 192.168.1.100:631 does NOT work.

That probably makes sense from my desktop, but I can't figure out why the laptop cannot connect; here is my cups config:

<Location />
Encryption IfRequested
Satisfy All
Order deny,allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.103
</Location>
<Location /jobs>
AuthType Basic
AuthClass User
Encryption IfRequested
Satisfy All
Order allow,deny
</Location>
<Location /admin>
AuthType Basic
AuthClass System
Encryption IfRequested
Satisfy All
Order deny,allow
Deny From All
Allow From 127.0.0.1
</Location>
...
Listen 127.0.0.1:631

In guarddog, I have opened up IPP (631) on both the "local" AND "internet" zones (is this overkill?) but I don't think guarddog is the culprit here, as if I disable it completely I get the same non-behaviour.

Can somebody clue me in as to what's happening? Thanks

---

