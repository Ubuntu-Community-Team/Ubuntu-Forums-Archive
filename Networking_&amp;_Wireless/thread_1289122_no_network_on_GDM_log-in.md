---
title: "no network on GDM log-in"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by guitar_man on 2009-10-12
I have two computers at home and they are on the same network.
Before I use to log-in on my server computer through SSH with-out users log-in on the GDM.

How can I start the Networkmanager without any user log-in??
Its a file server and it would be a pain if every time I want to access file I need to physically log-in on the server...:confused::confused::confused::confused:

---

### Post by Iowan on 2009-10-12
Seems like NM usually requires login to work. (I *could* be mistaken...) For a server, you might consider setting up the network via */etc/network/interfaces*. Interfaces defined there seem to activate on startup (if defined with "auto").

---

### Post by guitar_man on 2009-10-13
here is my setting....



> auto lo
iface lo inet loopback

is this it?

---

### Post by shredder12 on 2009-10-13
lo is the loopback interface..
you need to add a similar line for the interface you need to connect to internet..
eg. if the interface is eth0..
then 
```
auto eth0 
iface eth0 inet auto
```

---

### Post by guitar_man on 2009-10-13
Sorry for late reply...I'll try it later and post back what happen....Thanks in advance..

---

### Post by Iowan on 2009-10-13
"auto" isn't a valid method on the "iface" line, but it gives you an idea how the interface definition should look. You can check **man interfaces** for some samples.  Will you be setting up a static address, or using DHCP (maybe letting the DHCP server issue a static lease based on MAC address)?

---

### Post by shredder12 on 2009-10-14
Thanks Iowan, my fault it should have been either dhcp or a static address..

---

