---
title: "Server go boom"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by wesg on 2009-07-26
I have a Ubuntu 9.04 CLI server connected to my network via gigabit. It has an uptime of about 70 days, but now it has vanished from my network. The ethernet plugs are showing connected, but I can't see the computer on any of the services I have running on it: HTTP, SSH, AFP, SMB and the like. 

What can I do? I have a monitor and keyboard connected locally, but I can't even see the command line. Is there a keystroke required to display it? I'd like to fix the problem without resorting to pulling the plug (I've disabled the power button).

---

### Post by bacil on 2009-07-26
try Ctrl+Alt+F1 .. F6 any of these should give you console

---

### Post by wesg on 2009-07-26
OK, it came back, but I had to hit the reset. :( Is there a way to retrieve the Ubuntu startup data to find out where potential problems are?

---

### Post by powertower on 2009-07-26
> **wesg said:**
> OK, it came back, but I had to hit the reset. :( Is there a way to retrieve the Ubuntu startup data to find out where potential problems are?

look under /var/log/

or go to System - Administration - Log file viewer

---

