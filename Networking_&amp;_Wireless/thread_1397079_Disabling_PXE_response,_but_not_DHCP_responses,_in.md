---
title: "Disabling PXE response, but not DHCP responses, in dnsmasq?"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by CCKrause on 2010-02-02
I'm wondering if it is possible to set dnsmasq onboard my Linksys WRT54GL/Tomato 1.19-mp2 router to completely ignore PXE boot requests, but to still have the request broadcast over the network, and to still have dnsmasq function as a DHCP server for non-PXE requests.

The idea is that I'd like to create - and occasionally deploy - a PXE server virtual appliance from VirtualBox running on one of the network systems.

When the appliance is not running, PXE boot requests - which should not occur without prior notice and the launch of the appliance **anyway **- would just be dropped. When the appliance is active on the network it would intercept and serve the PXE request. It would **not** act as a general DCHP server.

I'm not married to the idea of using dnsmasq on the appliance, but unless I want to modify the Tomato firmware on my router (and I'd rather not), I can't really replace dnsmasq on the router - but I **can** set options for dnsmasq via the router's web interface.

Thoughts anyone?

---

