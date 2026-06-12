---
title: "Anyone ever get hostap drivers up?"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by Steve Quezadas on 2006-01-19
I have a Senao 2511CD card. hostap drivers seems to detect the card, but whenever i run iwconfig, i get a:
Warning: Driver for device wifi0 recommend version 18 of Wireless Extension, but has been compiled with version 17, therefore some driver features may not be available...

error. I believe this is preventing me from associating with the AP. I have the latest upgrades of everything. I am using Breezey Badger with the following kernel modules:
linux-image-2.6.12-10-686
linux-tree-2.6.12

Anyone ever get this to work? I would imagine I would have to upgrade Wireless Extension to 18 or downgrade the wifi0 driver to version 17.

Does anyone know how to do this or find some other workaround? yes, I checked the forums and google. Can't find much.

---

### Post by mpvano on 2006-01-20
I got it to work OK using my Prism 2 once I disabled the other driver alternatives.

For what it's worth, I haven't seen any problems related to the wireless extension issues with this or any other driver so far....

HOWEVER - When using hostap, every time the interface is brought down and then back up after sleep, it had a DIFFERENT NAME! This was quite a problem for its use with a notebook that's put to sleep regularly!

If I recall correctly, the card would sometimes appear as eth0 and eth2 (My 100baseT is eth1), other times it would appear as eth0 and wifi0, and I even think I saw the expected "wlan0" a few times.

These device names would appear in mysterious combinations, rarely the same twice and while I could make each of them work (including scanning - which is why I was trying to use hostap), I'd have to bring the card up by hand each time, since the correct interface name to use never seemed to be the same twice!

Apparently there' s some kind of problem in whatever scripting Ubuntu uses to rename interfaces - I didn't have the energy to track it down and decided to wait for an update someday to fix it. What little hostap documentation there is becomes a comedy of errors on ubuntu because of the musical device names.

If you get far enough to figure out why the device names, aren't stable, please let us all know....

For what it's worth, the driver worked really well for me once I'd have it configured each time - it seemed to have significantly better throughput than the orinoco-xxx drivers I'm currently using (Of course, they have notoriously slow throughput to start with - I don't think their bus interface code is very efficient).

You'll ONLY get one or another interface name  to associate by sending it commands. The fact that even when the same names appeared as I was familiary with, I'd have to send the configuration commands to the OTHER interface was particularly confusing.

I know this didn't help much, but the additional info might help you figure out what's going on.

Mario

---

