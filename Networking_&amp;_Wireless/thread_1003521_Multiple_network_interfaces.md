---
title: "Multiple network interfaces"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by PACSFerret on 2008-12-06
Hi.. Since upgrading to 8.10 I have a sub-optimal networking setup.  I have 3 possible interfaces - wired, wireless and mobile broadband. The optimal scenario is for Network Manager to bind the wired if available, if not then the wireless, and if not then the mobile broadband.

In fact, what is happening is even when the wired is plugged in, NM binds the wireless, and I need to disable wireless at NM but then go to a terminal to restart networking for it to pick up wired. Even then, NM doesn't see the wired connection.

That creates an issue when I have a different wired connection (home: DHCP, work:static) so I need to manually configure *interfaces* according to location.

This stuff should be transparent no? Or am I doing something particularly dim? 

PS NM upgrade is nontheless welcome. Wasn't able to get the mobile broadband working at all previously.

---

### Post by moore.bryan on 2008-12-06
for what it's worth, i was *never *able to get nm working on *any* of my machines, ever. my solution was to go to [wicd]("http://wicd.sourceforge.net/") and use that instead. wicd currently lets me do what you want to do, minus the mobile broadband, since i don't have it.

---

### Post by PACSFerret on 2008-12-06
> **moore.bryan said:**
> for what it's worth, i was *never *able to get nm working on *any* of my machines, ever. my solution was to go to [wicd]("http://wicd.sourceforge.net/") and use that instead. wicd currently lets me do what you want to do, minus the mobile broadband, since i don't have it.

Thanks Bryan.  Alas now I have it working the mobile broadband is important to me.  If anyone has notes on getting wicd to work with mobile I'd be grateful and certainly give it a go.

PS. Illustrious name given rugby connections.

---

### Post by moore.bryan on 2008-12-06
no worries... rugby is my religion. ;-)

you may still want to check-out the wicd page to see if anything mentions mobile broadband access; i just don't need it, so i don't know.

---

