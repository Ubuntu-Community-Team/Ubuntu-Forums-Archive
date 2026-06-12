---
title: "Information on dnsmasq with Ubuntu 12.10"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by codfather on 2012-12-04
Hi,

The way dnsmasq works with 12.10 has changed again, from 12.04. I have searched the Ubuntu documentation and Google for further info , without success.

Basically in 12.04 , dnsmasq moved the contents of /etc/resolv.conf to /var/run/nm-dns-dnsmasq.conf. You could see what the upstream DNS servers were. This file in 12.10 is empty, and with all the reading I have done, it appears to be being managed by dbus. I just need to know where this information is being stored, as it is causing us an issue with VirtualBox, not correctly passing through the DHCP information.

I know I could switch this service off , with the switch for the network manager service, but I would rather understand how the new system functions, and correct the issue there.

Any pointers to how this works gratefully received.

Cheers

---

### Post by codfather on 2012-12-06
In 12.10 dnsmasq and NetworkManager were changed to use dbus to
communicate instead of having to respawn dnsmasq for every change.

The result of that is that all the configuration is now passed over dbus
and there's no more configuration file used to provision dnsmasq.

You can query the current configuration with "nm-tool" or by looking at
your syslog where any dnsmasq configuration change is logged.

---

