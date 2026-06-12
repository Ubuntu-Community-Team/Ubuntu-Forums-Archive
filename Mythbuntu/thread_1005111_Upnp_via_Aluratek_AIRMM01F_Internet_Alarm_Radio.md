---
title: "Upnp via Aluratek AIRMM01F Internet Alarm Radio"
date: 2008-12-07
forum: Mythbuntu
---

### Post by bob1234 on 2008-12-07
I was wondering if anyone has tried accessing Mythtv Upnp server via the Aluratek AIRMM01F Internet Alarm Radio. The manual states: 

Compatible with universal Plug-n-Play audio servers such as: Microsoft Media Player 11 (WMP11), Microsoft Media Connect, MusicMatch Jukebox

Does this work? Any thoughts are welcome before I take a gamble?

---

### Post by bob1234 on 2008-12-09
Bump, anyone...

---

### Post by dmfrey on 2008-12-10
bob1234,

If one of those apps or that device can talk to a UPNP server, then they should work.  Be sure to setup your IP Address in MythTV Setup to what your IP Address is on the box and not the loopback address.

If you want to test it out, setup, for example, a Windows VM to test out one of the apps against the Myth UPNP Server.  There are other means as well but it should be easily testable.

---

