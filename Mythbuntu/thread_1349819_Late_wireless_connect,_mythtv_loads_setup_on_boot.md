---
title: "Late wireless connect, mythtv loads setup on boot"
date: 2009-12-08
forum: Mythbuntu
---

### Post by bgiannes on 2009-12-08
I have a mythbuntu box, with wireless N (which works good).

But

On startup just before the wireless connection can be made, mythtv starts (auto starts) can't find a network connection and the loads itself in setup mode!?!? Within a second the wireless connection is then made, doh!


please help

---

### Post by kja999 on 2009-12-09
Hi,

I'm guessing you are using NetworkManager to get your wireless connected?

There will always be this lag as the wireless only starts to connect after the user logs in.
You need to manually set up a wireless connection without using NM (potentially tedious and painful), but ultimately better for a static box.

Or you could try removing networkmanager and using wicd, then use a post connect command to launch myth.

I have been down the same path, and eventually just cut my losses and put a cable in ...

---

### Post by nickrout on 2009-12-09
Or just set up wireless networking in /etc/network/interfaces

finding the right invocation for some of the wireless options can be a pain, particularly if you are using encryption.

---

