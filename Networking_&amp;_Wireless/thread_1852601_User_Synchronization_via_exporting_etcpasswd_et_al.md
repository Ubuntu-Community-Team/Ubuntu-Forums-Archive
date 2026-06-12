---
title: "User Synchronization via exporting /etc/passwd et al?"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by lflindsey on 2011-09-30
I've got two servers on static IPs, and I'd like to synch their users/passwords. I only have two, and will probably only ever have two, and I don't really want to go mucking around with something like Kerberos or NIS.

I'm thinking of exporting /etc/passwd and friends from the backup server to the computational server, using NFS. I can't think of any overt reason why this would be a bad idea, beyond some security issues which I imagine would be taken care of through judicious use of ip tables. What do y'all think?

Caveats:
- Of course, if the backup server should ever go down, it would be complicated to log in to the computation server. This can be overcome by mounting backup:/exports/etc over a directory that contains a minimal set of those files (which would be pointed to by links in /etc/)

---

