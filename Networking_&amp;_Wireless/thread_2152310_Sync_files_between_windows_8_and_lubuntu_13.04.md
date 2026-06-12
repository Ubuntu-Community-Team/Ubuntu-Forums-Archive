---
title: "Sync files between windows 8 and lubuntu 13.04"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by mercast on 2013-06-07
Hi there. Does anyone know a way to sync files between widnows 8 and lubuntu 13.04 via network?
I don't know if this is the right section to ask this but it seemed the closest to my problem. Sorry for my bad english.

---

### Post by 2F4U on 2013-06-07
One possible option would be to setup a fileserver using Samba. This can be a dedicated machine, a NAS or even the Ubuntu machine. Samba allows Windows machines to connect to Linux boxes.
On the fileserver you would have shared folders, which are accessible from both Windows and Linux machines. There are several methods to keep local and remote folders in sync, for example rsync or Unison (quite functional GUI tool).

---

