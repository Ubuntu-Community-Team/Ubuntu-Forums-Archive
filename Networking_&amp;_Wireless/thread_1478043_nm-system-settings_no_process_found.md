---
title: "nm-system-settings: no process found"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by ToshoCorporation on 2010-05-09
Hi guys! First to say - I'm absolute newbie.
I'm with new version kubuntu 10.04
after changing *managed=true* in */etc/NetworkManager/nm-system-settings.conf*
I can't execute *killall nm-system-settings* it says:
*nm-system-settings: no process found*
Maybe I'm with the wrong command :confused:

---

### Post by Iowan on 2010-05-09
Moved to separate thread.
As I understand it, that line lets NM manage interfaces defined in */etc/network/interfaces*. The "standard" *interfaces* file has only two lines defining "lo".
*nm-system-settings* is not a process (check via **sudo ps -ef |grep nm**)- so it can't be killed.
Perhaps more details on what you need to accomplish?

---

