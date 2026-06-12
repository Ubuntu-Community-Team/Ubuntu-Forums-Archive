---
title: "Mythtv kills bluetooth?"
date: 2008-04-28
forum: Mythbuntu
---

### Post by jnorth on 2008-04-28
EDIT:  Nevermind - it was my lirc config.  A forum buddy just hit me up and reviewed it for me, for some reason some of my keys were listed multiple times in the config and it was dumping all keyboards after the lirc client within mythtv started up.

Don't ask me why - but it worked to delete the duplicates.
  Thanks!

===============================
Hi guys - I usually am the one assisting others in resolving problems, but I am at a loss on this one.

I have a working Mythbuntu/Mythtv setup on Hardy, and one on Gutsy.  In both, I also have a Dell Bluetooth Keyboard and Mouse set up.  This works great until I start Mythtv, at which point the bluetooth keyboard and mouse stop working.

I can shut down Mythtv and it does not restore service to the BT keyboard or mouse.  I have tried restarting the BT daemon also with no luck, as well as restarting GDM.  The only thing I have found so far that brings the BT devices back on line is a reboot.

I can see nothing in syslog or daemon logs that indicate what is going on.  The only thing I can think of is that lircd is interfering somehow, though I have no proof or evidence that that might be the case - it's just a hunch.

Anyone else run into this?

Thanks for any advice or pointers on where to look for a root cause!

---

