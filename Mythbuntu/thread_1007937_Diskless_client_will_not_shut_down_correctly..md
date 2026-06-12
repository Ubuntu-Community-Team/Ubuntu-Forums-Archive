---
title: "Diskless client will not shut down correctly."
date: 2008-12-10
forum: Mythbuntu
---

### Post by map7 on 2008-12-10
I'm running Mythbuntu 810 and I have a PXE client running off it (Toshiba TE2100 notebook).  This client is the only client I have working right now and it doesn't shut down.  

When I hit the power button it exits mythfrontend and X, then starts to shutdown and gets stuck on the Network Block Daemon with the error:

nbd0: Receive control failed (result -4)


The line before this is:
acpid: exiting

I haven't yet found what error code -4 means.

---

### Post by map7 on 2008-12-16
I've just got my eeepc to also be a diskless client with Mythbuntu 8.10 and it has the same error when shutting down.

---

### Post by map7 on 2008-12-16
Fixed, check out: [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-diskless/+bug/292319](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-diskless/+bug/292319)

---

### Post by stiev3 on 2008-12-19
How would I go about implementing the changes described?  Specifically applying the changes in mythbuntu-diskless-292319.debdiff ?

I've never applied a patch before, but if it's striaghtforward I'd give it a shot.  Then again, holding the power button isn't so bad if I have to jump through a lot of hoops that I'm not accustomed to.

---

