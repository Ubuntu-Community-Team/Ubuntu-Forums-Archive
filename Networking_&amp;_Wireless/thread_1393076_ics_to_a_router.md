---
title: "ics to a router"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by grundlestain on 2010-01-28
i have a desktop running 9.10 that recieves internet thru a wireless connection, i want to share the connection thru the lan card to a router. i cant seem to get it to work. in vista it was easy (but vista sucked) so that was all i used it for... i have looked all over and find all sorts of stuff that dosnt work for me, can anyone point me somewhere that will help please...

---

### Post by chewearn on 2010-01-29
Right-click on Network Manager icon (in Notification Area), select "Edit connections", under "Wired" tab, click Add, select "IPv4 Settings" tab, change "Method" to "Shared to other computers".

---

### Post by grundlestain on 2010-02-03
i have tried that, however it does not work, i dont know if it would make a difference to set up the dhcp some other way, but on vista it was able to plug in and work (about the only thing that worked dependably) without changing anything in the router... i tried following everything i could find in here but it all seems to end up sharing the other direction...

---

### Post by dmizer on 2010-02-03
In addition to the above directions given by chewearn, you'll also have to install dnsmasq-base and disable DHCP on your router.

---

