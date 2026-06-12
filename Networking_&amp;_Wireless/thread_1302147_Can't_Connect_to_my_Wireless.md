---
title: "Can't Connect to my Wireless"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by seoj113 on 2009-10-26
Hello everyone,
I am brand new to Linux.  So far, I like it.
My issue is not being able to connect to the internet.  The system is not recognising my wireless signal.  I tried looking up for help in the Help section, but the Network Manager does not appear in the  right hand side of the try, as the instruction says.

I found the Network Connections, and there I have the option to entre information manually, under the Wireless tab; but I don't have all the settings right apparently, because I've tried to do it that way, but it won't let me.

Am I doing something wrong?  Do I need to reinstall or install an additional tool?

---

### Post by Iowan on 2009-10-26
The Network Manager icon *should* be there (up near the clock) - it has a couple of different faces.  It looks like the wireless power graph when wireless is enabled, it looks like a couple of monitors when wired is active.  For troubleshooting, open a terminal and run **lshw -C network**. Post results here.  If you need help getting information transferred, please ask.

---

