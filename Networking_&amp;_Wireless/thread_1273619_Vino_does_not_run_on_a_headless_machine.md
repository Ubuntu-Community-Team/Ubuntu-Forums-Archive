---
title: "Vino does not run on a headless machine"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by jgb2185 on 2009-09-23
(original title: Vino does not run on a headless machine)

I am configuring an Ubuntu 9.04 server for my brother's classroom. As he has no Linux experience whatsoever, I have installed the gnome-desktop package atop the server install.

In Gnome, I have enabled auto-login under my brother's username, and the default Remote Desktop server (vino). This permits remote access using a VNC client just fine, but only so long as a monitor is attached to the PC. It can be an unpowered monitor, but it has to be attached. If the monitor is detached and the PC rebooted, the VNC connection fails with "Connection Refused (111)".

The delivery date I promised is only a few days away. How can I enable the vino server on this machine when it does not have a monitor attached?

Thanks...

JGB

---

### Post by jgb2185 on 2009-09-24
Okay, I have resolved the initial issue: in xorg.conf, setting the video driver to "vesa" allows gdm and vino to run when the monitor is disconnected. (See [*Problem with X Window on headless server*]("http://forums.fedoraforum.org/archive/index.php/t-198660.html").)

Now, the new problem is that the remote desktop resolution is tuck at 640x480. I have tried several modifications to xorg.conf, without success. Attached is my current iteration.

The delivery date for this server is this Saturday 26 September. Any help gratefully accepted.

JGB

---

### Post by jgb2185 on 2009-09-24
I apologize... I just realized that this is no longer a "Networking and Wireless" issue. I'll go ask in another forum.

JGB

---

