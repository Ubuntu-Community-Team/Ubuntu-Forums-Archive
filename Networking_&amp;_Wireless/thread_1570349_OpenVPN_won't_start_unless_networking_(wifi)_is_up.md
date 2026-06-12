---
title: "OpenVPN won't start unless networking (wifi) is up, how to fix?"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by agro666 on 2010-09-08
Ubuntu 10.04 LTS

OpenVPN is S19 in startup scripts.  It errors as the device doesnt have an IP until WiFi adapter connects to a network.  The network wont be connected until the user logs in and the keyring is loaded (it is enabled so it doesnt prompt for password).  How can I fix this so that networking comes up and the WiFi devices get's an IP so that OpenVPN can bind to it.  It is a static DHCP lease that is given by the router, I just need it to be up.

---

