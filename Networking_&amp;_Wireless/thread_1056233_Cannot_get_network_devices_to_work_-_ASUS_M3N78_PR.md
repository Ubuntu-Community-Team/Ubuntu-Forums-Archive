---
title: "Cannot get network devices to work - ASUS M3N78 PRO"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by cahumphrey on 2009-01-31
I recently purchased an ASUS M3N78 PRO to replace the motherboard that died in my wife's PC. Figured it would be pretty straight forward, but I was mistaken.

At this point I have spent several hours, 4 hdd wipe/reinstalls, 2 different versions of Ubuntu, and I still cannot my network adapters to cooperate.

Looking for a little help...

The strange part is this: When I first reformatted and installed 8.10 desktop 32bit, everything worked flawlessly. We downloaded and installed updates, and after restarting the onboard LAN no longer worked. I poked around online and found a few threads offering ideas on how to fix this issue. Since it seemed like a PITA and would have to be performed any time a Kernel update is issued, I opted to just use one of the handful of extra 10/100 NIC cards I have laying around. I didn't want my wife to be dead in the water with no internet after doing updates. ;-)

I installed a DLINK 530TX network card onto the board, booted up and it got an IP right away, and I was in business. However after restarting, the problem returned. Only this time I had eth0, eth0:avhi, and eth1 (the DLINK card). DHCP did not work and setting up the connection manually also did not work. I cleared the dhcp table on my router and that did not help.

Not sure where to proceed. My plan from here is to do the following:

Disable onboard LAN
Install 3Com NIC
Format HDD / Install 8.10 again (5ths time is the charm?)
See what happens and bump this thread...

I should have more detailed info soon.

---

