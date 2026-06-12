---
title: "Cannot establish pppoe connection when eth0 is bridged"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by meekamoo on 2011-10-13
Hey all,

Not sure why this is not working...

I have my server dial up my adsl pppoe account through the adsl modem plugged in via switch.

Now I'm trying to set up openvpn under a bridge so that the networks are transparent. That works no problem.

Only problem is when I have the bridge set up I have to use the router to dial up, the server no longer can access the modem directly.

I'm getting the timeout for PADO packets in logs.

Soon as I remove the bridge and turn eth0 back on, I can pppoe again.

- I ensured the right interface was in the provider file (br0, not eth0)
- I replaced eth0 for br0 in my firewall rules for NAT

Is there something I'm missing?

---

