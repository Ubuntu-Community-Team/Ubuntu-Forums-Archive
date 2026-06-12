---
title: "[Firestarter, VPN] Closing dead connections after unexpected tunnel closure"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by placement80 on 2011-07-26
I like to look at my open connections in Firestarter. I connect through an OpenVPN tunnel, and sometimes my tunnel will die unexpectedly, and if I have an open connection when it happens, the connection will remain - presumably because it never gets the close signal or whatever it is that happens when connections close normally. If I have several connections open when it happens, I can end up with a whole list of dead connections, and neither restarting Firestarter nor the network-manager removes the dead connections. Is there any way for me to get rid of the dead connections?

---

