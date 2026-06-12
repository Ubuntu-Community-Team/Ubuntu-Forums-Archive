---
title: "SSH Failing at Router?"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by brickedone on 2011-08-29
Have installed ssh server on ubuntu with fixed lan ip x.x.x.10

Have tested functional ssh login to localhost and to fixed lan ip x.x.x.10 from another machine on the lan

Have setup port forwarding on two different lan routers (x.x.x.1 routes wan and lan traffic, the other at x.x.x.2 just routes lan traffic) to forward port 22 to x.x.x.10 (yes, i'm using std ssh port)

Ssh login attempts fail when pointed to either router, fail from both ubuntu box and from separate windows machine via putty (as mentioned, both boxes can connect just fine when pointed directly to x.x.x.10)

What am I missing?

Thanks

---

### Post by brickedone on 2011-08-29
One more detail:

Router at x.x.x.1 has firewall on (since it's facing wan traffic), but router at x.x.x.2 has no active firewall (not blocking anonymous requests, etc).

As mentioned, ssh connections fail when pointed at either router from lan machines.  Not that it matters much, but error message is "Network error: Connection refused"

---

### Post by brickedone on 2011-08-29
Have dyndns set up on my router, decided to try router url just for kicks (instead of router lan ip address).  Works like a charm.

Seems like ssh connection through router (port 22 forwarding to server lan ip addr) works when sent to the router's public addr, but not when sent to the router's lan addr.  (I'm guessing)  Definitely interested if anyone actually knows whether this is the case, and why...

Thanks

---

