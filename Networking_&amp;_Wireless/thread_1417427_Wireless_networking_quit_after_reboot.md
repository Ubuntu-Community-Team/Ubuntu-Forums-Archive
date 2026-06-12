---
title: "Wireless networking quit after reboot"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2010-02-27
I've had my wireless networking (on an Acer Aspire laptop) working perfectly well for at least six months.  Now, quite suddenly, after a reboot I get the message from **wicd**, "No wireless networks found".  I probably was running a week or so before that without needing a reboot.  Windows wireless is fine (I'm using it to send this post).

In addition, my sound stopped working and I see a fleeting message to the effect that the sound system is reverting from analog to digital.

I'm running Kubuntu 9.10.  My guess is that something in a recent round of updates knocked me out of the box. How can I proceed to set things aright?

---

### Post by pwabrahams on 2010-02-28
I found the proximate cause: a kernel update that apparently killed the madwifi drivers.  Reverting to the previous kernel version solved the problem, though that's no real solution.  There's another thread on this subject; apparently the madwifi drivers need to be recompiled.  Looks like a bug to me!

---

