---
title: "Connection between Android and Ubuntu"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by mihai722 on 2010-07-17
My laptop is connected to internet through a crossover cable (DHCP) and I want to share this connection with my HTC tattoo through wifi (my laptop has wifi, no need for router).Is this thing possible ? 
I installed dnsmasq and created a wireless connection from network manager, but my phone doesn't find this connection, why? 
Thanks

---

### Post by bankey on 2010-09-24
> **mihai722 said:**
> My laptop is connected to internet through a crossover cable (DHCP) and I want to share this connection with my HTC tattoo through wifi (my laptop has wifi, no need for router).Is this thing possible ? 
I installed dnsmasq and created a wireless connection from network manager, but my phone doesn't find this connection, why? 
Thanks

you'll need to setup at least an ad-hoc network..

although I never got it right with andoid.. otherway goes perfect (android as adhoc ap (tether)))

better way seems to be by usb and adb (look at google.code for android dev kit)
and make a tunnel over ssh from the android out (with adb)
but the cheap and fast solution is to spend 25 dollar for wifi enabled router or ap

---

