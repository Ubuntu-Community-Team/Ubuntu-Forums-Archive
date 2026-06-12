---
title: "Inconsistent Networking"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by guillec on 2009-09-08
I have a strange networking problem. It seems to be very inconsistent. 

If I ping my gateway, at first it will says
*Destination Host Unreachable*, but if I leave it pinging it will start working. 

The same with everything else. sometime pinging google works and sometimes it doesn't. I am getting an IP but seems like I can't get anything else consistently.

I have tried 3 different NIC cards.

I first noticed strange things happening during the installation. It was during the automatic configuration of the network. It would say, either I am not using DHCP or its too slow or something else...so I just disconnected the cable and re attached and then it worked.

Any ideas?

I am working with Ubuntu Server 8.04 and I also tried Server 9.04.
The NIC cards I used are first a Intel NIC, Linksys and Dynex.
I used to have Server 7.04 and although I didn't use the box soo much I didn't notice any networking problems then.

---

### Post by guillec on 2009-09-08
I believe I have found my solution! 
I just needed to do a **firmware upgrade** on my Linksys router!

---

### Post by ductiletoaster on 2009-09-08
I would suggest before u upgrade you firmware to look into replacing it with **DD-wrt**. its opensource and based very secure and adds alot of advanced features (if you need them). And switchin has acutally helped me fix some of my network problems

---

