---
title: "KVPNC hangs up after a minute"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by dumb_question on 2009-02-25
*I'm having a problem with KVPNC (Ubuntu Hardy): connection established properly, I am in, [http://www.whatismyip.com](http://www.whatismyip.com) sees the new IP address, but then it loses the connection after ~ a minute, and is unable to reconnect - error msg is "remote modem has hung up" so it seems like I'm missing a handshake to tell it I'm still here or something - any ideas? Tried pinging server so it doesn't lose track of me, but it won't respond to ping, tried leaving it pinging google so it stays active, but that still disconnects.*

Based on someone else's suggestion I tried turning **off** "Check connection status" in settings under Network / General, and that worked. Apparently if you keep bugging (some?) servers with these checks, they assume you are up to no good, and bounce you.

---

