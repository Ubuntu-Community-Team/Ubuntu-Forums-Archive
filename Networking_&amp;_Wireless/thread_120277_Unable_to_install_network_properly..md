---
title: "Unable to install network properly."
date: 2006-01-21
forum: Networking &amp; Wireless
---

### Post by artix on 2006-01-21
I am not able to configure my network card and it all started at the installation when it said I probably didnt had a DHCP server available. I retried a few times but thought, what a heck.. I'll conf it static (I've tried that on debian, my router uses the mac adress to give me ip so I always get the same) but when I started up my newly installed Kubuntu I couldnt even access my router.

I tried manually setting it in a number of ways but nothing seems to work.
I can ping my ip address.. and localhost so the netcard itself should be installed I think? but i can't do anything "outside the card" so to speak.

The network card works perfectly under Debian 3.1.
Now im using Kubuntu 5.10

Anyone know what I can try? does (k)ubuntu use a different dhcp client then Debian 3.1 does?

---

### Post by cayamara on 2006-01-21
Your network card is probably not configured to use DHCP. Make sure your "/etc/network/interfaces" file looks somewhat like this:
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

# The primary network interface
**iface eth0 inet dhcp**

```
The last line tells eth0 to use DHCP (I hope thats what you want). After that, run ```
$ sudo ifup eth0
``` If it doesn't work, please post the output of ```
$ sudo ifconfig
```

Hope it works!

---

