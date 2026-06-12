---
title: "local DNS lookup"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by veehexx on 2010-05-04
i've been trying to worth this out for the last hour, and come to a dead end.

i'm having issues connecting to hostnames on the local network.
ie: 'nas1' does not resolve
'nas1.local' resolves & pings correctly.
direct IP pings ok also.

it seems I've been barking up the wrong tree with avahi, as i've both disabled it from starting, and removed it as per various threads on here, but no resolution.

windows machines can ping perfectly, but my ubuntu machine wont (10.04) so it looks like something local rather than network/router side.

---

### Post by veehexx on 2010-05-04
looks like it just affects the .local FQDN.

i've connected VPN into work, and it successfully picks up our work FQDN, just pinging the hostname.

---

