---
title: "Nautilus does not see network shares"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by Clive McCarthy on 2012-02-04
I have a dozen Ubuntu 10.10 machines connected to a wired LAN. Much of the time I'm able to access any of the Linux machine's Samba shares from my main workstation... the system runs for days without trouble, then suddenly, nothing.

When I look for machines on the network via Nautilus I see only my wife's MacBook! Eventually, the system partly heals itself and the **Windows Network** becomes visible but the 'regular' list of Linux machines remains empty.

Is Nautilus caching data and not refreshing? Why do (when things are operating normally) Linux machines appear in _both_ the Windows Network AND the 'other' Samba network? 

If my machine's wired connection is disabled and then re-enabled it makes no difference, but if the machine is rebooted it seems that Nautilus can again find the Samba shares. Is there some way of restarting Nautilus to force it to request the DHCP table?

The network is served by an AT&T (Edgewater) 250AEW router and various multi-port switches. The Edgewater 250AEW _HAS_ to be the DHCP server (I think it's part of AT&T's lock-down on their VDSL modem interface).

Any help would be appreciated.

I have noticed another discrepancy with Nautilus: I add an Ubuntu machine to the network but it ONLY shows up in the Nautilus **Windows Network** section and does _not_ appear in the regular list. I tried smbtree and it shows it fine enough. If I _refresh_ the Nautilus window nothing changes; if I _close_ the Nautilus window and re-open Places->Network it finds it. Why is Nautilus so sleepy?

---

### Post by Clive McCarthy on 2012-02-06
It looks like the answer might be here:
[http://askubuntu.com/questions/16966/what-causes-nautilus-to-restart-whenever-i-kill-it](http://askubuntu.com/questions/16966/what-causes-nautilus-to-restart-whenever-i-kill-it)

---

