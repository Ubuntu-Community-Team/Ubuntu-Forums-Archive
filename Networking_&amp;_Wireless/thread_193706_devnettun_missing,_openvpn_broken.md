---
title: "/dev/net/tun missing, openvpn broken"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by pestie on 2006-06-10
Well, I knew I'd have some frustrations when upgrading to Dapper...

So, here's the situation. /dev/net/tun does not exist, so openvpn cannot allocate a tun device for itself. This was all working great under Breezy, of course. The kernel isn't even auto-loading the module for some reason, so I did a "modprobe tun" and it loaded just fine. But the hotplug subsystem or udev or whatever is supposed to create /dev/net/tun isn't doing so any more. I'm sure I can go in and create it by hand with mknod, but that's not a proper solution. Does anyone know a proper solution?

The other thing that appears to have broken on breezy -> dapper upgrade is sound. For whatever reason, my sound drivers simply weren't loading at boot. I put them in /etc/modules, but again, this seems like it's a hack rather than a proper solution. It also seems like it could be related to the tun device problem. Any ideas?

---

### Post by pestie on 2006-06-10
Never mind - this is all related to hotplug being missing. I'm starting another thread about that.

---

### Post by steve.horsley on 2006-06-10
I have run openvpn on Dapper (fresh install of flight 4 and upgraded since then) without problems, so I suspect that any problems you have are related to the fact that you upgraded. However much that helps.

---

