---
title: "moblock killed web browsing"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by Forbees on 2012-11-20
[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

did the steps there, but when trying to test, or do anything. the command blockcontrol was not found.

so i purged it


now i can't get any internet traffic through  my browser, but still have LAN traffic


moblock probably killed port 80 or something, how can i get it back?

---

### Post by Forbees on 2012-11-20
blockcontrol isn't the command on my system apparently it's pglcmd


so that explains it all

---

### Post by jre on 2012-11-22
> **Forbees said:**
> blockcontrol isn't the command on my system apparently it's pglcmd

correctly. moblock, blockcontrol and mobloquer are only transitional packages to get you the current pgl.

I moved the updated wiki (pgl instead of moblock) to [http://sourceforge.net/p/peerguardian/wiki/pgl-Main/](http://sourceforge.net/p/peerguardian/wiki/pgl-Main/)

---

### Post by Forbees on 2012-11-28
cool, hopefully others won't run in to the same problems

i was initially going to use it for torrenting, used to peer block and windows


but after all this i found out transmission has a built in blocker - as long as you find a good list to update it with :)

---

