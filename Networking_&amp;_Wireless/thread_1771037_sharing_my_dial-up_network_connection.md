---
title: "sharing my dial-up network connection"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by ubun2warrior on 2011-05-30
hi

i connect to the internet on my laptop using a usb modem. i want to share this connection with other  computers. connected through lan cable. 

i want to manually assign ip on all computers. what should i do

---

### Post by ubun2warrior on 2011-05-30
i want to set the ip addressed manually for all pcs... 
from the network manager there is an option which says share the connection but that automatically sets the ip address to 10.42.43.1 for the system i don't want this, i want to manually set this ip and all the other ip for all systems

kindly explain as quickly as possible...

best regards

ubun2warrior

---

### Post by dandnsmith on 2011-05-30
Ive never heard of anyone doing it this way.
Since the 10.x.x.x is not routed outside the LAN, I wonder if it is prepared to set up the basic bits on the laptop, including the DHCP and routing for all the PCs.

Do you have an ethernet interface on the laptop, and what will you connect it to (router, switch, ...)?

---

### Post by dandnsmith on 2011-05-30
Just found [this exposition](https://help.ubuntu.com/community/Internet/ConnectionSharing) which may be what you really want to get it going

---

