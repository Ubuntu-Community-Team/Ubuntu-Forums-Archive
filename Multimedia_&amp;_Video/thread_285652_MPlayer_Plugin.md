---
title: "MPlayer Plugin"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by gerowen on 2006-10-27
I can't get the mplayerplugin to take over playing embedded media in Firefox in Ubuntu 6.10.  It's still keeping the totem plugin, even after I removed all of the libtotem.so files from /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins .  I can't remove the totem-mozilla package because for some reason when I try to remove it, it has to remove ubuntu-desktop as a dependency...  Can someone help me out please?

---

### Post by Balle-Larsen on 2006-10-31
Ubuntu-desktop is just an empty package. It is a meta-package. It exists to depend on other packages. You can remove it.
You may want to install it again when upgrading the distribution.
After totem-mozilla and ubuntu-desktop are removed the mplayerplug-in will work.

---

