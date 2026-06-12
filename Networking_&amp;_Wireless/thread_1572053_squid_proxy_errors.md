---
title: "squid proxy errors"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by biodunolans_netbook on 2010-09-10
Hi,
Can't seem to be able to get my squid proxy running on lucid Lynx to accept and allow secure http (https) traffic to pass through. It works well for all other services though.
My connection is via a ppp connection and clients are connected via my wireless link.
Alternatively, is there any firewall/ICS connection sharing software like Winroute for linux based OSes?

---

### Post by sikander3786 on 2010-09-10
There is [firestarter]("https://help.ubuntu.com/community/Firestarter") for ICS.

I believe squid is not running in transparent mode. Does the browser on the client show any error or it just doesn't browse the https page?

[COLOR="Red"]**Edit:**[/COLOR] Also look if you have included this line in your squid.conf file.

acl SSL method CONNECT

---

