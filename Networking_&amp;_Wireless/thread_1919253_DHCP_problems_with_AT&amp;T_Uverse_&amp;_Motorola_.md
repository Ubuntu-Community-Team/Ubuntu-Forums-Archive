---
title: "DHCP problems with AT&amp;T Uverse &amp; Motorola 2210"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by Clive McCarthy on 2012-02-02
I have a dozen Ubuntu 10.10 machines connected to a _wired_ LAN. The network is served by a Motorola 2210 VDSL modem and an AT&T (Edgewater) 250AEW router and various multi-port switches. The Edgewater 250AEW **HAS** to be the DHCP server (I think it's part of AT&T's lock-down on their VDSL modem interface).

Much of the time things work just fine. I'm able to access any of the Linux machine's Samba shares from my main workstation. I'm _always_ able to connect to the WAN.

However, periodically when I look for machines on the network via Nautilus I see almost nothing (except for my wife's MacBook!) and the Windows Network (it emits: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply.

Eventually, the system seems to heal itself and then runs for days without trouble. Then suddenly, nothing. Rebooting the modem doesn't seem to fix things.

Any help would be appreciated.

-- After awhile the Windows Network becomes accessible but the 'regular' list of Linux machines is still empty (except for the MacBook). Is Nautilus caching data and not refreshing? Why do (when things are operating normally) Linux machines appear in _both_ the Windows Network AND the 'other' Samba network? If my machine's wired connection is disabled and then re-enabled it makes no difference, but if the machine is rebooted it seems that Nautilus can again find the Samba shares. Is there some way of restarting Nautilus?

---

