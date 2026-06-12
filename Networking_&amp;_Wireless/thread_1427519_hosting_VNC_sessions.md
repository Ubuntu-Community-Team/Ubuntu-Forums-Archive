---
title: "hosting VNC sessions?"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Wilbefast on 2010-03-11
Hi there,

I'm collaborating on a piece of code with a guy who uses windows: he can host VNC sessions and I can look at what he's doing using the Remote Desktop viewer. However, he can't ever see what I'm doing because I can't seem to host VNC sessions :(

Is there any way of doing this on Jaunty?


William

---

### Post by sparky-steve on 2010-03-11
I'm relatively sure that in System, Preferences you'll find Remote Desktop. Thats a GUI for what is, in effect, a vnc server (im on Karmic, so cant be 100% certain).

Of course, assuming you're behind a router and have a private IP address, you'll need to forward port 5900 to your machine at your router, and if necessary adjust your machines firewall.

If your machine connects directly to the net (has a real IP) then you'll just need to open port 5900.

All of that said, VNC over the net is not secure. You could establish a tunnel through VPN or SSH, but thats another story.

Good luck

SS

---

