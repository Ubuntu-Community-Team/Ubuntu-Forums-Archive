---
title: "Changing MAC address freezes Ubuntu during boot-sequence"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by mycroft on 2006-04-12
This is my /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp
#hwaddress ether XX:XX:XX:XX:XX:XX
```

Notice the last line - if I uncomment it, Ubuntu freezes upon reaching the "configuring interfaces" stage, with nothing but the reset-button responding. Yet, as far as I can tell from reading the manual on interfaces, the syntax is correct. What am I doing wrong?

---

### Post by mycroft on 2006-04-13
Well - after studying the interfaces manual again I tried various combinations of enabling the hotplug initialisation of eth0 - but no matter what, adding the hwaddress command either appeared to have no effect, or it would freeze Ubuntu during startup.

Then I tried doing the next-best thing: making a script to assign the MAC address, and have Ubuntu execute that script instead. I tried to put this into the interfaces file too, using the pre-up option, but to no avail. As it turned out, I could not even invoke macchanger using the pre-up option.
Furthermore, I tried just making a script and have it executed at runlvl 5.

The results were pretty much the same whatever I tried, however - either it had no effect, or Ubuntu would freeze/crash during startup.
This lack of success during startup is puzzling, as my attempts were successful when testing within Ubuntu, using networking start/stop.

---

