---
title: "Can't access servers in the .local domain on corporate LAN"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by dcrooke on 2011-02-07
In case others have this problem ...

Our corporate network has some internal servers whose host names are e.g. **foo.companyname.local** ... these do not work in Ubuntu.

This is because Ubuntu installs, by default, the AVAHI Zeroconf mDNS system, configures it to "own" the .local domain, and prioritizes it ahead of regular DNS in the hostname resolution order.

Solutions:

1. De-install AVAHI by removing the **avahi-daemon** and **libnss-mdns** packages and their dependents, using either Synaptic Package Manager from the UI, or **dpkg** from the command line

or,

2. Edit the file /etc/nsswitch.conf and change the hosts line to:

hosts:     files dns

---

