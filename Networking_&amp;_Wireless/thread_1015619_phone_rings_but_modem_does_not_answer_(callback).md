---
title: "phone rings but modem does not answer (callback)"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by kaos_frack on 2008-12-19
i connect to the internet using a dial-up modem with callback
it works on windows but i'm having some problems on ubuntu
authentication succeeds and the server calls back but the modem does not answer the ring
i tried to add ATS0=1 init string but not working
/var/log/ppp.log says something like:
```
send (ATS0=1^M)
expect OK
ATS0=1^M
OK
--got it
...
expect RING
SIGINT
```
i also tried to different values like ATS0=2 and ATS0=3, but no change

---

