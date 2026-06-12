---
title: "Wireless Control"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by windexh8er on 2009-04-16
So I am in the process of building a customized version of Ubuntu for a deployment.  The problem I'm running into is that these boxes have multiple wireless network interfaces of various sorts to collect data.  Each have 3-5 network cards in them, of varying drivers for different tasks.  Here's what I want to do:

1) Be able to very accurately configure each interface in the system no matter what order they happen to come up in.  Example: if a specific Atheros card is not in the box at boot, even though there are others those others will maintain their specific configurations based on the MAC of the individual cards.  When the missing interface is added then it will get it's unique configuration.

2) Some interfaces I don't want handled at all by NetworkManager.  These interfaces should not have any networking of any sort applied because they will be spun up in a monitor mode by a custom script.

I've looked through /etc/network/interfaces as well as /etc/NetworkManager/nm-system-settings.conf and I am not sure what the best way to approach this is...

NetworkManager has nothing for documentation other than a little bit on the live.gnome.org site.  They make it out to be that you can control the wireless interfaces with fine grained control but there is no documentation backing that up.

Anybody care to shed some light?  My next option is to start digging through source code to figure it out...  I would have thought someone would have already tackled this.

Thanks a ton in advance!

Oh and BTW -- this is on 9.04 because I need the mac80211 goodness apparent in 2.6.28.  :)
--windexh8er

---

