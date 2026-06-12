---
title: "Cannot access internet with updates or google"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by triplemaya on 2010-02-08
I have just installed netbook remix on a new acer.
No internet
I can ping [www.google.com](www.google.com) ok, but when I put a query into firefox google box it just hangs.
When I attempt to use update manager it fails, error message is
cannot initiate the connection to gb.archive.ubuntu.com ... network is unreachable.

Going by advice on other forum pages I have:

Checked etc/resolve.conf, but this already contains the address of my modem router, 192.168.1.1

Added three lines to /etc/modprobe.d/aliases
alias net-pf10 ipv6 off
alias net-pf10 off
alias ipv6 off

all to no avail

The wireless was also disabled, but adding 
blacklist acer_wmi
to
/etc/modprobe.d/blacklist
fixed this.

In case this was a problem I have undone this and rebooted but still cannot see webpages, now just connected straight to the router with cable.

Very disappointed at present! Would be very grateful for help to get this working.

---

