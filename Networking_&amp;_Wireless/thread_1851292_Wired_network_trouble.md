---
title: "Wired network trouble"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by kylegio on 2011-09-28
Today my wired network started giving me trouble.

The network is functioning perfectly
my connection to it is not.

Network manager says connected
ifconfig says connected
browsing web doesnt work, 
accessing local devices/resources does not work
if wired interface is taken down then put back up it can not obtain an dhcp lease

syslog contains pages of the following
> 
Sep 28 02:51:28 kage-laptop NetworkManager[443]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Sep 28 02:51:31 kage-laptop NetworkManager[443]: <info> (eth0): carrier now ON (device state 8)
Sep 28 02:51:31 kage-laptop kernel: [  416.367153] jme 0000:09:00.0: eth0: Link is up at ANed: 1000 Mbps, Full-Duplex, MDI
Sep 28 02:51:46 kage-laptop kernel: [  431.260247] jme: Disable RX engine timeout
Sep 28 02:51:46 kage-laptop kernel: [  431.260932] jme 0000:09:00.0: eth0: Link is down
Sep 28 02:51:46 kage-laptop NetworkManager[443]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Sep 28 02:51:49 kage-laptop NetworkManager[443]: <info> (eth0): carrier now ON (device state 8)


there are also some unknown shutdown errors that started at the same time (sits at requesting all processes to end or something like that for about 5 mins... will try to find more info on that)

anyone have any thoughts, ive tried reconfiguring network manager and stuff but no joy.

wireless network works A1 100%

---

