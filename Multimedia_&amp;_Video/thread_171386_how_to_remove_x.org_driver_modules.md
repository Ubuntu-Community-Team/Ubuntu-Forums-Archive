---
title: "how to remove x.org driver modules?"
date: 2006-05-06
forum: Multimedia &amp; Video
---

### Post by ChrisC on 2006-05-06
My security update this week wants to update ~50 packages that I don't actually use (but apparently are installed) like "xserver-xorg-input-hyperpen" and "xserver-xorg-driver-tseng".  I've already gone through my /etc/X11/xorg.conf and /var/log/Xorg.0.log files to make absolutely sure that these drivers are not used, and now I just want to remove them so that they're not cluttering up my system.

When I go into synaptic and try to remove them, I get a popup warning that removing the selected package also requires that I remove "ubuntu-desktop", "x-window-system-core" and "xserver-xorg".  Uh, no, I don't think I'll be doing that, thanks :)

It seems the parent/child relationship there is backwards.  How do I just remove the modules that are installed but aren't actually ever used?  Or am I stuck with them?

- Chris

---

### Post by ChrisC on 2006-05-07
Meh.  I just reposted to the parent forum.

---

### Post by Reshin on 2006-05-09
Aren't those just meta-files? I think you can remove them safely.

---

