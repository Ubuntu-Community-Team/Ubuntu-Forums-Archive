---
title: "Setting up a home network w/ all ubuntu workstations?"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by DeMartini on 2009-08-18
I have three machines that I can ssh into back and forth, have them bookmarked on each machine so we don't have to type in IP's when we want to get into a specific machine to file share, all is good there. My question is it seems a bit wide open, whickh is to say w/ windows you get on the machines in the same workgroup, but you only share what you want to share, with ssh it's wide open, can you share some folders and block others?

---

### Post by dmizer on 2009-08-19
Well, "wide open" is relative. Since SSH is encrypted, it's far more secure than something like samba.

If you want to restrict file sharing to a specific folder, I suggest you do research into NFS. There's a fine tutorial on NFS in the 4th link in my sig.

---

