---
title: "Disable remote desktop auto-reconnect?"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by deepwater on 2009-05-26
I use the default RDP client in jaunty and find myself cursing it every time I get to work, log on, then 30 seconds later get locked out because my home pc has decided to auto-reconnect.  Thankfully, it takes less than 30 seconds for me to vnc to home and stop it.

Is there any way for disable the auto-reconnect function - or - is there an alternate rdp client I can use that does not have that "feature" ?  

Thanks!

---

### Post by Brandon Williams on 2009-05-26
Are you referring to the graphical "Terminal Server Client" (tsclient)? If so, it's really just a wrapper around the command line tool rdesktop. I think that it's tsclient auto-restarting your connection. Try running rdesktop directly instead.

---

