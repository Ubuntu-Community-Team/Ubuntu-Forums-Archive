---
title: "Connecting with ath9k produces &quot;Bad Password&quot;"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by davelbarton on 2011-04-14
I've been working on this for a while.  I have done the whole "install backports" thing, and that got me to the point where I can see the wireless connections; however, when I try to connect, I get a "Bad Password" message (which I don't believe, in the sense that I've checked the password back and forth several times).  I am using maverick on an HP Pavilion dv7-1120.  The relevant section of the lshw command is:

           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 01
                serial: 00:23:4d:24:87:24
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:18 memory:d1100000-d110ffff

If I do the trick of waiting until the "Bad Password" comes up and looking at the last messages in the dmesg log, I get the following:

[ 2534.170131] r8169 0000:0a:00.0: eth0: link down
[ 2535.700776] r8169 0000:0a:00.0: eth0: link down
[ 2535.701694] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2539.996320] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2540.198469] r8169 0000:0a:00.0: eth0: link down
[ 2540.199832] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2556.860391] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2557.042539] r8169 0000:0a:00.0: eth0: link down
[ 2557.044402] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2557.176565] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2559.681582] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 1)
[ 2559.880122] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 2)
[ 2560.080604] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 3)
[ 2560.280438] wlan0: authentication with c0:83:0a:3e:cb:01 timed out
[ 2573.587258] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 1)
[ 2573.784108] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 2)
[ 2573.984119] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 3)
[ 2574.184115] wlan0: authentication with c0:83:0a:3e:cb:01 timed out
[ 2587.489121] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 1)
[ 2587.688605] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 2)
[ 2587.888557] wlan0: authenticate with c0:83:0a:3e:cb:01 (try 3)
[ 2588.088599] wlan0: authentication with c0:83:0a:3e:cb:01 timed out
[ 2595.260272] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2595.503940] r8169 0000:0a:00.0: eth0: link down
[ 2595.505566] ADDRCONF(NETDEV_UP): eth0: link is not ready

Clearly something is wrong, but I don't know what and I don't know where to go from here.  Any help is appreciated!

---

### Post by davelbarton on 2011-04-15
Bump, in forlorn hope....

---

