---
title: "Networking problem with Ubuntu 8.04 new install"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by FalconMtn on 2009-01-22
I'm not seeing any response to my inquiry in the absolute beginner talk, so I'm hoping to get a response here. Problem I'm encountering is with connectivity on an HP Pavillion zx5000 ubuntu 8.04 new install, as described here:
[http://ubuntuforums.org/showthread.php?t=1047346]("http://ubuntuforums.org/showthread.php?t=1047346")

Help...please?

---

### Post by Loosewheel on 2009-01-22
> **FalconMtn said:**
> I'm not seeing any response to my inquiry in the absolute beginner talk, so I'm hoping to get a response here. Problem I'm encountering is with connectivity on an HP Pavillion zx5000 ubuntu 8.04 new install, as described here:
[http://ubuntuforums.org/showthread.php?t=1047346]("http://ubuntuforums.org/showthread.php?t=1047346")

Help...please?

FalconMtn, you might want to 'cat /etc/network/interfaces' and see whats in there. Should only have:

auto lo
iface lo inet loopback

If there are other lines, (ie auto eth0...), comment them out with '#'.

Then reboot and see if NM will find and set up eth0.
If not 'click on nm-applett>Manual configuration', 'unlock' and your passwd, click on 'Wired connections' select 'properties', and check the box 'Enable roaming mode'.

Back out of there and reboot.

---

### Post by FalconMtn on 2009-01-23
Solved; see original thread.

---

