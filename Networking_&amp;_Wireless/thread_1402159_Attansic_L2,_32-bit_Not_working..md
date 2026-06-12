---
title: "Attansic L2, 32-bit Not working."
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by DThurman on 2010-02-08
I have been able to use the Attansic L2 driver (atl2) for quite
some time (from 8.04 to 9.04) but with 9.10, the odd thing with
atl2 is that I can ping my local network, but I cannot reach the
Internet and yes, my gateway is properly set.  Also, my DNS
settings are resolving properly as well as I tested this manually
via nslookup.

BTW, I have two NICs, an MOBO network chip (Attansic L2)
and an Intel-Pro+ NIC the latter for testing when atl2
does not work as I have had this issue before in the
past w/ other distros, so I left the card in but disabled
the card only if atl2 works.

The Intel-Pro has no problems (locally/remotely).

Also, what seems odd is that I noticed that NetworkManager
does not seem to do anything after setting it via the
tray-tool and in /etc/init.d, NetworkManager is actually
named: NetworkManager-dpkg-backup if that means anything.
What I mean here is that NM for all entries shows 
Last Used: 'Never'

I tried to throw everything at it except the kitchen-sink,
as I could not resolve this atl2 Internet-access issue.

What can I do at this point to resolve this problem?

Thanks!
Dan

---

