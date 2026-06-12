---
title: "Ldirectord preventing updates"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by Shdwdrgn on 2011-10-25
I upgraded my firewall from lucid to natty over the weekend and ran into a problem with ldirectord 1.0.4-0.  When the ipvsadm rules are loaded, my firewall is unable to connect to the internet (most noticeable is that 'aptitude update' freezes).  This does not affect any of the servers or workstations behind the firewall, only the firewall itself.  If I install the deb package for ldirectord 1.0.3-3.1, everything works fine.

My ldirectord rules for ports 21 and 80 grab anything that comes into the firewall and distributes it between the internal apache servers, however somehow the older version of ldirectord was able to differentiate between packets meant for the firewall.

I can't seem to find any bug reports on this issue, so I don't know if I'm doing something wrong, or if its just an obscure issue that nobody else has run in to.  Any suggestions as to how I can troubleshoot this, other than freezing my build at the older version?

---

