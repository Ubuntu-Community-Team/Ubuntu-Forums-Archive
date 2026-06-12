---
title: "SSH + VNC + Matlab - what the hell..."
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by Zorgoth on 2010-07-19
When I start a vnc server using ssh, then as long as I'm logged in it's perfect.  When my ssh session ends, it's almost perfect.  But I need to use matlab, and for some reason, when I run matlab, certain actions seem to crash.

So far it's panel applets that are the problem; clicking on the system monitor, launchers (but not the ones inside menus) and icons in the system tray will all kill the vnc server.  This will not happen if there are no matlab windows open or if the ssh session is still logged in.

This only happens with graphical matlab windows (including figures and plots); just a matlab shell in a terminal won't do anything, although the full-fledged matlab gui (which I don't use) has the effect.

---

### Post by Zorgoth on 2010-07-19
Ok I have now seen it happen without matlab windows open, but the matlab windows make it much worse I guess.  I would actually be fine with a terminal equivalent of VNC since for viewing the final data I can use ssh -X; but I don't want the process on the server to be dependent on the network connection between the two computers.

---

### Post by Zorgoth on 2010-07-26
OK, I don't know why that was happening, but here's my solution;

Don't use VNC.  Use GNU screen.

---

### Post by SubCool on 2010-07-31
> **Zorgoth said:**
> OK, I don't know why that was happening, but here's my solution;

Don't use VNC.  Use GNU screen.

Whats GNU?

---

