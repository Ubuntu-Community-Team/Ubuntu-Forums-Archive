---
title: "Intermittent lack of networking"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Saraphim on 2009-08-14
Hi guys,

I'm having a problem on that has completely stumped me.

Upon startup of the machine I will sometimes have network, and sometimes not. It's easily tested by pinging my local gateway which will either work or not.

Trouble is: ifconfig, route and ethtool all give the same output whether ethernet is in a broken state or not. I diffed it. Until recently the only "fix" was to simply reboot the machine, but I just found out that ethtool -t will (sometimes) fix (or break) it. I have no idea where to go with my diagnostics from here on. Does anybody have a bright idea?

I'm running Ubuntu 9.04 with Edubuntu 9.04 on a Dell Optiplex GX280

---

### Post by Saraphim on 2009-08-14
This seems to stump everyone else just as much. :) I've made a really, really ugly workaround (ping gateway, if no answer, ethtool -t) but I would still love to figure out what's going on here if anyone has a suggestion.

---

