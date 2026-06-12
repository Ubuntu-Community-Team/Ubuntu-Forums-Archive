---
title: "I can see the shared remote printer but can't print"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by perfectopresents on 2009-08-25
I have been making a bit of progress and I am stuck yet again. I have an old box I leave running, my server, and a personal machine as well. The older server has a printer attached to it, which I've managed to set up in cups 1.1, print test pages while SSHed into the server, and just today, I got the broadcast working and now I can SEE the printer on my personal machine. But I can't do anything with it. I can't print. Why can I see the printer on my personal machine but can't print to it? What simple setting could be preventing this?

Address of my personal machine: 192.168.2.150
Addresses of my server: 192.168.2.1  and  192.168.1.3

```

cupsd.conf

Port 631
Browsing On
BrowseProtocols cups
BrowseAddress 192.168.2.255

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.2.*
Allow From 192.168.1.*
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

```

---

