---
title: "setup to allow changing http proxy on the fly?"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by mikewse on 2012-11-05
Are there any solutions to "hot-swap" the system http proxy?
I'm moving every day between home (without proxy) and work (with proxy). The network connects fine as both spots are using DHCP, but I have to manually change proxy setting in /etc/environment and restart processes.

Is there f ex any solution that allows me to configure proxy settings to a local port, that is then forwarded to the appropriate destination for each network, so I don't have to restart processes?

Or at least a solution that automatically sets up the correct proxy at boot? (based on some config I've done)

Thanks
Mike

---

### Post by Lars Noodén on 2012-11-05
One way would be to install the Firefox add-on [Foxy Proxy](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/).  I don't know of options for other browsers or of a generic way to affect system-wide proxy settings in that manner.

---

### Post by mikewse on 2012-11-05
Tack Lars,
Interesting stuff, but I am looking for something system-wide so not just web browsers get affected :-)

---

