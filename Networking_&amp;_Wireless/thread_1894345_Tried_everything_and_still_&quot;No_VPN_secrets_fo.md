---
title: "Tried everything and still &quot;No VPN secrets found!&quot;\."
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by koohyar on 2011-12-12
I made a pretty pile of mess installing indicator-network then for switching back to network-manager, removing it and causing a huge load of dependency issues and...well I got around it and now I'm back and happy with network-manager except...
Well, two things have happened...
1 -My laptop doesn't detect wired connections (tried everything in the forums)
2 - And more importantly, I get the dreaded "No VPN secrets" Error when I try to connect through my VPN.
I've tried nearly everything found in the forums like "/etc/init.d/network-manager restart" but to no avail. I'm thinking maybe some packages are missing (?!)
Any help would be appreciated
Thank you\.

---

### Post by koohyar on 2011-12-13
Ok so I tracked down the problem to my libnm-glib-vpn package being outdated! (I must've 'manually' installed an outdated version before)..but completely fixed the VPN problem!
Don't know about the wired connection though, but I think that should be ok too! :)\.

---

