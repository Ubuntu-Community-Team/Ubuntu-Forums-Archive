---
title: "Setting which eth interface can set the default route"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by at165db on 2009-12-16
I have 2 network cards installed in my desktop.

eth0 goes to a lab running a DHCP server, and it has a default route set so that lab devices can hop around.  I'm not really interested anything other than the lab subnet my PC is on.

eth1 goes to the corporate LAN.  This network is also running a DHCP and it has a default route set.  This is the default route I need so that I can hit servers for work and get on the web.  My NIC that is eth1 also has a DHCP reservation so I always get the same IP, which I need for various things.

This used to be fine when I was running 8.04 and 8.10 because eth1 would get an IP last, and set the default gateway to the one I wanted.

However, with 9.10, when I run route, it shows my default route is on eth0, and the lab gateway.  I also noticed that the Knetwork-management plasmoid in 9.10 shows both eth0 and eth1, but has a little red heart (and a red X) next to the item that says "Auto eth0 Active".  I have a box that says "Auto eth1 Active" but no heart, just a red X to disconnect. 

I've poked around Knetwork-management plasmoid and can't seem to figure out how to change the Default (the tool tip under the red heart) interface.

I don't care if I use the plasmoid to change my default route interface to eth1, I just need to change it.  Any ideas?

Thanks,
Russell

---

### Post by at165db on 2009-12-16
I should also point out, I'd like to not have to manually run something every time I reboot.

There was a default gateway interface setting I used to use in Fedora, but the stupid Fedora network UIs would blow away the setting any time you used them.  That was no fun.

---

