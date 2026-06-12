---
title: "Weak Signal"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by bolenjx1 on 2010-04-14
Hi,

I'm very new to Ubuntu (9.10) and I just finished installing it. I have a problem with my wireless connection - I'm getting a weak signal ~50-60%. In windows, signal strength is usually 80%+. So far, I'm not getting disconnected or anything, just that the signal is pretty weak. 

I've tried doing 

> sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-genericBut nothing happened. BTW, if it matters, I've done an OS update first before running the above commands.

Here's the output of **lshw**

>            *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: xxxxxx
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.xxx.x.xxx latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f0100000-f010ffff

---

### Post by mark bower on 2010-04-14
i operate through 3 walls at anywhere from about 45 to 60% (2 to 3 bars).  60% is plenty of signal strength.  in fact, i would say that 60% is actually "pretty strong".  just for fun, i am still planning to make some parabolic reflectors to see if i can get to 65 or 70%.  i saw online a neat way to do it with styrofoam and wire mesh or aluminum foil.  i have already drawn my parabola.  

and if you have a detachable antenna on 5 feet of cable or so, be sure to move it around to different locations while observing signal strength.  it can make a big difference.  in may case where the computer is 3 walls away from the router, the signal can vary by 10 as i move it horizontally on a self, eg, between 40 and 50.

another edit, you're going to love Ubuntu.  the only tasks i cannot do are taxes, and Nikon IV slide scanner.  all else has moved to linux to include a print server(one printer for 3 house computers).

mark

---

