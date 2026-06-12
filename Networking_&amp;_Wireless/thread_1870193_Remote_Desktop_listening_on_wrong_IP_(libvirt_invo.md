---
title: "Remote Desktop listening on wrong IP (libvirt involved)"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by RHAnthony on 2011-10-26
I have a server that is hosting 3 VM's.  I want the host machine to be remote controllable via VNC.  The Ubuntu remote desktop is setup to allow control, but it says it is only listening on 192.168.122.1, which is an IP given to it by default by libvirt.  I can ssh to it via it's normal 192.168.1.x IP from the rest of my network, but I can't VNC to it, because it refuses to listen on that address.

What am I missing?  Why is the host's remote desktop insisting on using the libvirt IP?  And where can I change that libvirt IP anyway?

---

