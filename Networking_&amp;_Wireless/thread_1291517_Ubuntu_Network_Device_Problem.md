---
title: "Ubuntu Network Device Problem"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by therussianjig on 2009-10-14
Hi, every time I restart my computer, a new ethernet device is created and added into my UDEV rules. (Im up to eth13) This poses a problem because each new device has a unique MAC address, and I need my device and MAC to be static in order to access the school network.

---

### Post by Iowan on 2009-10-14
You can delete the extras from */etc/udev/rules.d/70-persistent-net.rules*, but that doesn't solve the issue of the MAC address changing. Dunno if [this]("http://www.debianadmin.com/change-your-network-card-mac-media-access-control-address.html") might help.

---

### Post by therussianjig on 2009-10-14
I already have deleted the extras, the problem is they just re add themselves every reboot. I have also tried the mac changer without any luck. Since then I am trying to edit the UDEV rule generator such that every time it "re recognizes" my Ethernet card, it will create the same rule every time. I'm not sure exactly how to do this or if its a good idea.

---

