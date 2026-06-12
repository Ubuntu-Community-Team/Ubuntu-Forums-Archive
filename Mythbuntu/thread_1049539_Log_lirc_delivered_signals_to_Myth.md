---
title: "Log lirc delivered signals to Myth"
date: 2009-01-24
forum: Mythbuntu
---

### Post by mathog on 2009-01-24
Is there a way to get a log of the lirc events ("keys") delivered to Mythtv?  I can use irw to see what is coming out of the remote control raw, but not to see what lirc is in turn finally being delivering to mythtv.  This is a relevant distinction because once the mythfrontend is running, from the top menu:

 watch tv -> m -> guide

up/down/right/left arrows from the keyboard do not cause any issues, but after a small number of arrow events from the remote the guide freezes, and stops responding to the keyboard as well.  So the two are clearly not equivalent.  It seems likely that lirc is delivering not just ">" but maybe ">>>" in very quick succession, perhaps faster than the keyboard could generate it, and the fast series confuses myth.  Or it could be something else - it would be nice to see what is actually being delivered.

---

