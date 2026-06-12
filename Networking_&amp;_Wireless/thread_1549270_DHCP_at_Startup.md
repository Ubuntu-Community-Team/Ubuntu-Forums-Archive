---
title: "DHCP at Startup"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by zjagannatha on 2010-08-09
I'm having an issue on a few computers that share a filesystem server.
On boot, they attempt to mount the imported filesystem (on the server). The operating system gives an error and hangs at this point because they haven't bound to an IP address with DHCP yet. What I need to do is tell the system to start DHCP before trying to mount the imported filesystems.

Fyi, the imported filesystems are listed in fstab using nfs referenced by IP address.

I could add the dhclient call to some startup script. (Where is such a script?) but that removes the ability to alter network interfaces by gui, (in gnome's network manager, for instance).

Is there a better solution?

---

