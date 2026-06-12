---
title: "Rt2870 injection problems,10.04"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by spikeofdoom on 2010-09-09
hello there ive searched for a while now and cant seem to find anything. unfortunately i have the Bcm4312 with that 14e4:4315 i believe it is so i cant do injection with my internal card on my laptop (dell studio 1535) so i had this linksys wusb600n laying around, has an Rt2870 chipset from what ive read, i havent found anything saying it doesnt support injection, but i start airmon, goes into mon mode, and i start airodump set to the bssid and channel of the test router i set up. i see it in the top part of airodump but no packets in the bottom, so i start aireplay set to the bssid of the router and use the arpreplay attack, it runs and suggest i run airodump to capture (already running) and aireplay reads increasing read packets 0 arp and 0 acks, and sent 0 packets

in airodump no packets show up, but the beacons continusly go up not sure what that means

any help would be great

---

### Post by gallifrey on 2010-09-09
Hi!
I have the exact same setup as you, with a 14e4:4315 and an rt2870. I managed to get injection working on the Broadcom by using the b43-fwcutter firmware extractor instead of the BCMWL proprietary driver, at the expense of bluetooth. With the rt2870, simply use the rt2800usb driver. Aircrack-ng site has a good guide on patching them to work, as you will need to install compat-wireless (google Aircrack + compat-wireless, link should be near the top). 

Hope this helps.

---

