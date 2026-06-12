---
title: "Turning off avahi-daemon broadcasts to an interface"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by andrewc6l on 2009-06-08
I'm trying to set up an AX.25 interface over packet radio. Part of that involves turning off broadcasts to the interface.

I've found that avahi-daemon broadcasts to all interfaces pretty much constantly - not something I want to do with a 1200-baud interface. Is there a way to tell avahi-daemon not to broadcast on a specific interface (or alternately, a way to tell it to broadcast only on specific interfaces)?

What do I lose by turning avahi-daemon off? I'd rather not disable it entirely if I don't have to. I'm running 8.04.

Thanks!

---

### Post by andrewc6l on 2009-06-09
Found the answer (from the Avahi FAQ):
How can I tell Avahi to ignore certain network interfaces?

    * Right now Avahi will make use of all suitable network interfaces, there is no configuration option to restrict the interfaces used. However, there is a trick to make sure that Avahi ignores specific interfaces: remove the MULTICAST bit from the interface flags. You can do this with ifconfig like this:

      ifconfig eth1 -multicast

    * Keep in mind that this might disable multicasting for other applications, too. Since only very few programs make use of multicasting this is usally not much a problem, though.
    * To automatically remove the MULTICAST bit using udev on specific interfaces, add a file to /etc/udev/rules.d containing this (replace "RULE TO MATCH DEVICES" with correct rule):

---

