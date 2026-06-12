---
title: "Can't browse other samba hosts using nautilus (via &lt;servername&gt;)"
date: 2008-06-07
forum: Mandriva/Mageia
---

### Post by pelle.k on 2008-06-07
I can't connect, or browse another samba server via it's netbios name nor hostname (which is the same on this particular server im trying to reach). Using the server *ip* works, but that kind of defeats the purpose of using a host/netbios name.

[I]As it turns out, I'm a retard. Apparently, since i set "interfaces" in smb.conf using (old syntax) "192.168.1." instead of using (new/correct syntax) "192.168.1.0/24" the nmbd daemon on that machine didn't start, thus the name resolution failure.
Run along, nothing to see here! ;)[/I]

---

