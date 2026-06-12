---
title: "dongle daft"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by vmaxchick on 2009-06-28
hi there folks and hope all is well. I have just installed ubuntu and am now stuck sadly. I have a netgear wireless dongle which connects to an orange livebox router. 
I have no idea how to get this to work in ubuntu, its not showing the wireless dongle or the network. Aint got a clue where to start and also unsure of the SSID settings ect that may be required as there is only certain info available from the router.

hope someone can help or point me in the right direction
cheers
H

---

### Post by ajgreeny on 2009-06-28
Depending on the netgear adapter chipset, you may get it to work using ndisgtk, which will be the front end for ndiswrapper.  It may only work with wep security, but that may be sufficient if you are only using the machne for standard home type activities.  My Netgear WG511 v2 pcmcia card certainly works well in this way, but not with wpa, unfortunately.

Give it a try.  You will need to use the windows driver CD for the dongle and find the .INF file which ndisgtk will ask for in the setup.  I hope it works for you.  Ifnot I suspect it may be easier to get a linux-friendly card as replacement for your netgear.  Also have a look at [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) for further info.

---

### Post by vmaxchick on 2009-06-28
thanks for that not sure mind you on the ndisgtk  or how to use this, will give it a try either that or give up

---

