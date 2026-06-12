---
title: "Firewall &amp; Virus Scan for XP Internet Sharing"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by mercenary on 2006-06-19
Ok, I FINALLY got DHCP and Firestarter working on my brother's "firewall" server servicing his 3 XP machines and he asks about virus scan to potect the XP machines so that he doesn't have to run virus scan software on the individual machines.  He said this is how his Windows 98SE internet connection server was set up.  I've been using UNIX for a while now to avoid virus issues.

Is there something available?

---

### Post by mips on 2006-06-19
There are several available.

AVG:
[http://free.grisoft.com/doc/20/lng/us/tpl/v5](http://free.grisoft.com/doc/20/lng/us/tpl/v5)
[http://www.ubuntuforums.org/showthread.php?t=136064](http://www.ubuntuforums.org/showthread.php?t=136064)
They also have have full commercial server versions.

Avast:
[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

ClamAV:
[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)
with havp  [http://www.server-side.de/features.htm](http://www.server-side.de/features.htm)

I dunno if all or any of the above will do realtime scans of downloads in progress. havp rproxy may be one way. I honestly have not seem a implementation of this nature. Even in a corporate environment every single desktop pc has it own av software installed and only centralised mail scanning and spam filtering.

---

