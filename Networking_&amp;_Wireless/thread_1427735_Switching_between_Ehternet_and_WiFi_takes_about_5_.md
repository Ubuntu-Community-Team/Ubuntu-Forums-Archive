---
title: "Switching between Ehternet and WiFi takes about 5 minutes to work correctly"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by BillRebey on 2010-03-11
I'm using Ubuntu 9.10 in console mode - no GUIS, etc.  NetworkManager is not installed.

I'm switching manually between eth0 and wlan0 via "ifup xxx" and "ifconfig xxx down" (ifdown don't work - it's necessary to use 'ifconfig xxx down' rather than 'ifdown' to bring the interfaces down).

When I switch between the two, it takes as many as 5 minutes before I can once again ping something that worked just fine before I switched interfaces.  In pseudo-code, the sequence looks something like this:

$ ifup eth0
$ ping MachineA
   <ping succeeds>
$ ifconfig eth0 down
$ ifup wlan0
$ ping MachineA
   <ping will fail repeatedly, often for up to 5 minutes>
...retry 'ping' repeatedly...
$ ping MachineA
   <eventually, ping will succeed, and the connection to 
    MachineA can be made>

It doesn't matter if I'm swithcing from eth0 to wlan0, or the other way around.  Either way, I get a "lag" before the newly configured interface will work correctly.

Any ideas?

---

