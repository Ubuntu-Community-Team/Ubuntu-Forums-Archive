---
title: "Simple solution for synchronising uids, homedirs etc?"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by JamesNeko on 2009-01-18
I'm looking to set up a small networked environment between our Ubuntu machines at work. I might also want to sync my two home machines - Debian and Ubuntu.

I don't care about Active Directory or all that nonsense. I really just want to make sure users, groups and passwords match up, and keep homedirs on the network in one place.

Opinions?

I'm not familiar with anything that syncs the uids; I've used simple smb and nfs setups before. CIFS could work better, I guess. NFS can be a bitch sometimes, and on the work setup I can't really trust the basic host-based authentication I've tried at home. Unless there's something I can do about that? It's been a while since I touched NFS.

---

### Post by nixscripter on 2009-01-18
My suggestion: LDAP. Here's a howto to get you started (also describes in more detail what it is): [http://tldp.org/HOWTO/LDAP-HOWTO/](http://tldp.org/HOWTO/LDAP-HOWTO/)

---

