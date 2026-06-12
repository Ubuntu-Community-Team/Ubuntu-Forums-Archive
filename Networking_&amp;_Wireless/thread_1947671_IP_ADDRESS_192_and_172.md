---
title: "IP ADDRESS 192 and 172"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by CopyRiight on 2012-03-27
I am running ubuntu latest version on vmware on a my macbook pro, i've used ubuntu 3 years ago when i was in the UK, now i'm back home and all i wanted is to try whether (snort and ettercap) still work or not.

However both snort and ettercap will not alert anything related to the network , snort did but only actions that were made on UBUNTU itself , not with other systems on the network.

I then discovered that, the ubuntu running on vmware was give a 172.x.x.x IP address (eth0) while my real router distribued 192.x.x.x . Then i thought, NO wonder it doesnt sniff nor detect any network traffic but itself.


How can i fix this problem?

Thanks.

---

### Post by dandnsmith on 2012-03-27
You need to find where this address is being allocated as 192.168.x.x and 172.{10-31}.x.x are 'private IP addresses' (which don't get routed outside the local network).
I think you should be able to affect the choice of address which the vmware offers (but don't remember far enough back to guide you).

---

