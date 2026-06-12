---
title: "kaffeine won't launch"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by voided3 on 2007-10-29
I installed Kaffeine on Ubuntu Gutsy and it won't launch. When I click it, nothing happens, but there are two Kaffeine processes in the process manager. It also gives no terminal output when I run "kaffeine" in a terminal window. Any ideas? Thanks!

---

### Post by voided3 on 2007-10-29
Well, I think it's a KDE issue because K3B won't work either. In fact, when I opened K3B, it did nothing but crash and close firefox. What would cause this sort of thing?

---

### Post by voided3 on 2007-10-29
k3b give this output:

> ed@ed-2500LINUX:~$ k3b
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket

...then stops doing anything. Kaffeine doesn't give any terminal output though. Hmmm.....

---

### Post by PacShady on 2007-11-01
I found a very strange but effective (for me) workaround for the Kaffeine issue.

When Kaffeine fails to load for me, I load up KSysGuard and kill all Kaffeine processes. Now at first I then closed KSysGuard and tried Kaffeine again, and it would do the same thing again. HOWEVER, I found that if I leave KSysGuard OPEN before launching Kaffeine it seems to work fine. Very weird and stupid I know, but on my computer it seems to do the trick.

'Shady

---

