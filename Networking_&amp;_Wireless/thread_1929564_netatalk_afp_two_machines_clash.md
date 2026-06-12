---
title: "netatalk afp: two machines clash"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by d2a on 2012-02-22
I'm running 10.04 on two different servers on the same LAN. I have netatalk 2.0.5-3 installed on both with identical configurations bar the share locations. These are advertised via avahi to a network of Macs (running 10.6X).

An example netatalk share config:

> ~/Public                "Public" options:nohex,usedots,invisibledots,upriv

The username is the same on both machines, but the password differs.

Both are visible to the Macs on the network, but when a share from server A has been mounted, selecting server B in the Finder displays the shares from s-A, and any attempt to mount a share from s-B is met with generic unable to connect errors. Once unmounted, either servers' share can be accessed, but only one can be mounted at any one time.

This may turn out to be an OS X fault but if someone can point me towards a log or something to help me diagnose this, i'd be really grateful

---

### Post by d2a on 2012-03-20
hmm - obviously no one has ever encountered this problem but me. Strangely, it's actually resolved itself. I've been wrangling with home dns setup, and some change i've made on the server must have resolved the issue. Perhaps it's a simple hostname conflict or something. either way, no longer an issue.

---

