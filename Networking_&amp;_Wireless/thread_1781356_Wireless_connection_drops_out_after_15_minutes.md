---
title: "Wireless connection drops out after 15 minutes"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by Don Vosper on 2011-06-13
Having struggled to get the wireless connection at least working I find it drops out after 15 minutes or so.
When I check for wireless connections I can see none at all and the "Disable/Enable wireless conncection" has disappeared, the Network one is still there.
I get an auto reconnection if I reboot and all is well for another 15 minutes.
Is there any way i can recover the situation without a reboot?
I am trying to install the hplip-3.11.5 driver for my new wireless printer,the program take a while to install and by the time it has started looking for the printer the connection has dropped out.
I can't be sure but I don't think it was dropping out before I connected the printer using my wired pc.
All good fun but I'd like to get it sorted so I can get the engine back in my motorbike, the sort of technology I prefer!
Cheers
Don

---

### Post by JethroGillgren on 2011-06-13
stab in the dark but this might help you reconnect without rebooting:
> sudo service network-manager stop

then

> sudo service network-manager start

---

### Post by Don Vosper on 2011-06-13
Thanks, Will give it a try next time it happens.

---

### Post by Don Vosper on 2011-06-18
Hasn't failed since. not sure what I did to fix it but it's now sovled.
Don

---

