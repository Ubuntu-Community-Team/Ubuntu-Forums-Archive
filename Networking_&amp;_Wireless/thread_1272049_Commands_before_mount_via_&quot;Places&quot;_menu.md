---
title: "Commands before mount via &quot;Places&quot; menu"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by oscar69 on 2009-09-21
Is possible to add a wake-on-lan before an nfs mount?

I made a bookmark in "Places" menu to mount the shared fs, but it works just if it is already started. To power up the Nas it is sufficient a wake-on-lan packet, and a little sleep.

The Nas have a power switch with "auto" position. It stay on while receive wol packets. When stared, I can send regular wol packet, while share is present: I think to see if exist dir $HOME/.gvfs/share 
When the dir disappears, the loop exits, end the NAS shutdown.

But, when powered off, I cannot startup again other than with another command.

I'd like to simple call the bookmark.

Thanks

---

