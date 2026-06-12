---
title: "interface renaming after hardware change"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by Jive Turkey on 2009-12-31
I replaced a dead motherboard yesterday with a different brand.  Everything works fine except I really want my interfaces to be named eth0 and eth1 to keep from having to edit a bunch of other things.  I've edited /etc/network/interfaces to include them with the proper parameters but the network manager and ifconfig both seem to reference eth2 and eth3 which doesn't really exist anywhere that I can find.  

Where else is the NIC info stored?

Bonus points for fixing it with one terminal command :)

---

### Post by lloyd_b on 2009-12-31
> **Jive Turkey said:**
> I replaced a dead motherboard yesterday with a different brand.  Everything works fine except I really want my interfaces to be named eth0 and eth1 to keep from having to edit a bunch of other things.  I've edited /etc/network/interfaces to include them with the proper parameters but the network manager and ifconfig both seem to reference eth2 and eth3 which doesn't really exist anywhere that I can find.  

Where else is the NIC info stored?

Bonus points for fixing it with one terminal command :)

Okay, your terminal command is ```
sudo nano /etc/udev/rules.d/70-persistent-net.rules
``` :)

This file associates the MAC address of the ethernet device (which is usually fixed in the device's hardware) with the "eth..." logical name for the interface.  Just delete the lines for the old "eth0" and "eth1", and edit the lines for "eth2" and "eth3" to make the "eth0" and "eth1", and then reboot.

Lloyd B.

---

### Post by Jive Turkey on 2009-12-31
I'm reluctant to give you the bonus points because the solution also included editing the file.  I tried the proposed edits and found that I actually had to delete all of the rules pertaining to the interfaces (i cleared the lines from /etc/network/interfaces for good measure) and reboot.

The one line command might have looked like this:```
touch interfaces && touch 70-persistent-net.rules && cat "auto lo
iface lo inet loopback" >> interfaces && sudo mv ...
```

or I was hoping for a "sudo reconfig or purge so and so"

but hey its NYE so here are your bonus points!

*** <-- 3 of 'em!

---

