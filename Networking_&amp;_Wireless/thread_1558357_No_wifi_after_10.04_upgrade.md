---
title: "No wifi after 10.04 upgrade"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by dadacamp on 2010-08-22
Hi all
I ran the upgrade from 9 to 10.04. So far I have everything but wifi. There is no wifi access even through a menu bar icon. Any others with this problem who've found a solution?

---

### Post by Iowan on 2010-08-22
Right-click Network Manager icon in upper right corner to verify Networking is enabled. A couple of other threads that might help:
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")

If these don't help, you might have a driver problem. **sudo lshw -C network** should reveal information about your interface(s).

---

### Post by LinuxHead on 2010-08-22
> **dadacamp said:**
> Hi all
I ran the upgrade from 9 to 10.04. So far I have everything but wifi. There is no wifi access even through a menu bar icon. Any others with this problem who've found a solution?


Install Wicd from synaptic manager.

---

