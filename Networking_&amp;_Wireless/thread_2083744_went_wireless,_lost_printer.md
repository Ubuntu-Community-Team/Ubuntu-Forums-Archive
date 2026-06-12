---
title: "went wireless, lost printer"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by Subito Piano on 2012-11-13
Hi!  Running Lubuntu 12.04.  It networked beautifully as ubuntu always does; it discovered all three "workgroups" here and easily added the office copier, which plugs directly into a switch upstream.  Great!

Today i brought in a TrendNet Wireless N-router and hooked it up. I am using WPA2 encryption.   I also changed from "Network manager" to WiCD.  I am connected to the internet but now i can't see any of the workgroups; it won't discover any printers, and when trying to print to the office copier, it says "Processing - Unable to locate printer."

The device URI is dnssd://TOSHIBA%20e-STUDIO352-05225626._pdl-datastream._tcp.local/   -- i have not changed this from when i installed it (before going wireless).

I tried changing my print "Server Settings" by checking "Publish shared printers connected to this system" and "Allow printing from the internet," and i rebooted --- none of these helped.

???Any ideas??

---

### Post by Subito Piano on 2012-11-13
Solved - thanks to a network specialist.  It was NOT a Ubuntu problem.  It turns out i was trying to use a wireless router as an access point.  I went into the wireless router settings and disabled DHCP, then unplugged the incoming cable from the WAN   port and plugged it into one of the 4 computer ports.  Everything is fine now.

---

