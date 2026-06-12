---
title: "Setting up network for multi-OS"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by bigpayne69 on 2011-07-04
I have 4 computers in my house, all with different OS's. (XP, Vista, 7, and Ubuntu) They would all be on Linux but haven't found a way to get my wife to stop using Windows. Anyways, I'd like to set up a home network to connect all 4 computers that would provide filesharing and print server. Does anybody know if this is even possible?

---

### Post by aeiah on 2011-07-04
yea you'll be fine. windows filesharing is done through samba and is compatible with linux (the native linux way of doing it would be NFS, but windows doesnt support that).

since the majority of the machines are windows based, just concentrate on getting that part set up and then use samba to connect to the windows shares from your ubuntu machine.

---

