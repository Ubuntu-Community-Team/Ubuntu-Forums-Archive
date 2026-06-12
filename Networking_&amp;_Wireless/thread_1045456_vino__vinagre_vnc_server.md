---
title: "vino / vinagre vnc server"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by johnl on 2009-01-20
Hi guys,

I've setup vino VNC on my computer at home to listen for connections. I have the (windows) tightvnc client here at work.  I swear I used to have this working, but now I'm running into issues :(

Here's what I've done:

Forwarded ports 5900 tcp and udp in my router
Enabled vino server, do not prompt, ask for a password.
Attempt to VNC to <my-home-ip>:0, <my-home-ip>, or <my-home-ip>:5900.    

When I attempt to connect, TightVNC gets to "Protocol version negotiated."  and then stays there indefinitely.  

Anyone have any suggestions?

---

### Post by johnl on 2009-01-23
In case anyone else runs into this, re-starting GDM did the trick.

Probably some issue with enabling vino sever from an ssh-forwarded X session.

---

