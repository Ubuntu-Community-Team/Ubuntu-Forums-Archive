---
title: "Networking just disapeared? HELP!"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by 4am on 2011-01-12
OK, so I've been running 10.10 in VirtualBox for about 2 weeks now, no problems. The other day I noticed my network was erratic, and when I did ifconfig, it listed eth1 as the interface (as opposed to eth0, which was the original setting). Strange, it seemed, that this should just change without warning or explaination, but it worked after restarting (still on eth1) so I shrugged it off.

Today, the VM can't see the network, total black hole. dhclient is running, no error messages, eth1 has an address on my local network, and nothing at all has changed about the local network (no new firewalls or routing or anything whatsoever).

A few times I did `sudo dhclient` and although it warned me that it was already running (found a .pid file in /var/run) it brought the network back up.

but now that doesn't even work.

I haven't changed a single thing with my vbox settings, so this is (apparently) all happening inside Ubuntu. any thoughts? Other information I should post here?

---

