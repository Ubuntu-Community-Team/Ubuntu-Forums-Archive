---
title: "Wired NIC used to work"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by Matt 6:27 on 2011-06-06
Possibly an obvious question, but here goes: I'm running Natty and trying to troubleshoot my ethernet problem.  An old laptop worked fine (including the ethernet) until a few days ago when we had a lightning strike relatively nearby.  It appears power went out briefly or there was a spike (all hardware, except the DSL modem/NIC, had surge protection).  The machine works fine now... except the network. I've run lshw -c network and it's showing "network: UNCLAIMED".  ifconfig shows only the loopback and no eth0 at all.  I've tried: ifup/ifdown, rebooting, live booting Natty off a USB drive, and tried on a network I know works... all to no avail.   One interesting bit of info is that I can see a MAC address when I view the 'network connections' via the applet in top panel.

Am I reasonable to conclude the ethernet port got fried by the lightning?  Any pearl of wisdom is welcome.  Thanks

---

### Post by sanderj on 2011-06-07
Did the ethernet initally just work after booting a Ubuntu CD?

And now the ethernet does not work after booting the same Ubuntu CD? 

And even not after turning off the machine, removing power + battery for a few minutes, and then booting again>


If Yes, I would also say the ethernet hardware is out of order.

---

### Post by Matt 6:27 on 2011-06-10
Ya, I tried all that and still can't get a connection.  Thanks for your thoughts.  I'm off to get a new NIC.

---

