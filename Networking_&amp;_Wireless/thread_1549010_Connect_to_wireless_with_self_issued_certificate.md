---
title: "Connect to wireless with self issued certificate"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by InFro on 2010-08-09
Hi guys,

I could not find the answer to my problem, so I am posting here. If there is similar thread just give me a link and I will shut up.

At my work place we have wireless network, to which I connect by using client certificate. The problem is that certificate is self issued and we have to add root certificate to system. Of course, all instructions are for the Windows OS and no one has a clue what to do in linux.
On windows I just add root certificate as trusted one, then when connecting I point to the given client certificate and thats it.
On Ubuntu I tried moving root certificate to various system folders (like /etc/ssl/certs/) but with no luck.

Connection information:
WPA enterprice
TKIP.

There is no TKIP option in Ubuntu though (only TLS, LEAP, Tunelled TLS, EAP (PEAP)).

Any ideas would be appreciated. Thanks.

---

