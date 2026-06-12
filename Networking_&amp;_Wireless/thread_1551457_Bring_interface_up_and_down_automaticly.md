---
title: "Bring interface up and down automaticly"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by Tukanfan on 2010-08-12
Hi!
I have a Ubuntu Server I'm using as router.
Therefore I would like to have network interfaces brought up and down on certain events (when network cable is (un)plugged, loosing a dhcp lease, etc).

My current setup consists of two physical ethernet interfaces with ipv4 and ipv6 enabled and one tunnel-interface that relies on ipv4 connectivity through one of the ethernet interfaces.

I don't know whether i should use netplug and ifplugd or the event based Upstart init daemon to achieve my goals. Currently the Upstart daemon is doing nothing...

Can you help? :)

---

