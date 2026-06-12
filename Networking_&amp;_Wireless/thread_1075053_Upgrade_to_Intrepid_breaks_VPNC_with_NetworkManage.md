---
title: "Upgrade to Intrepid breaks VPNC with NetworkManager"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by which_dan on 2009-02-19
I have just upgraded to Intrepid and I find that NetworkManager is unable to log onto my work VPN.

vpnc is able to do this from the command line, but only if I set "Local port" to 0, so I imagine that this is the problem with NM.

Where can I make NM use a random local port in establishing a VPN connection?


EDIT: This has been resolved - racoon was using port 500, so uninstalling racoon fixed the problem.

---

