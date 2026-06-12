---
title: "Wired LAN down by default - how to auto connect"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by zi99y on 2006-02-24
Hi,

I have to admit I've done some tweaking and now use static ip, instead of dhcp. Also I've got a local dns server, which is working fine from ubuntu.

However, when I boot up into Gnome or KDE, eth1 is down by default, so I have to run ```
sudo ifup eth1
``` every time.

What used to happen is this would be up automatically if the cable was plugged in, and if I plugged the cable was plugged in later then it would bring the interface up - but this no longer works.

Any help on this would be appreciated

---

### Post by bikeboy on 2006-02-24
Can you post the contents of /etc/network/interfaces please?

---

### Post by zi99y on 2006-02-24
here you go: ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
##mapping hotplug
##	script grep
##	map eth1

#echo connects eth1 when device is hotplugged. using echo instead of grep #allows any device to be brought up when hotplugged. Note this could cause a #problem if a device is active and another one that is mapped is plugged in.
mapping hotplug
script Echo
map eth1

# The primary network interface
iface eth1 inet static
gateway 192.168.1.1
address 192.168.1.12
netmask 255.255.255.0

```

---

### Post by bikeboy on 2006-02-24
Can't say I've seen that Echo script used before. Mine runs off the grep script just fine.

It's like this:

> # This file describes the network interfaces available on your system
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
iface eth0 inet static
        address 192.168.1.7
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 210.15.254.240 210.15.254.241

So as you can see my static setup has a few more options specified. Could be the extra things I have in or it could be a problem with using Echo for hotplug, I don't know.

---

### Post by zi99y on 2006-02-24
Thanks bikeboy, I made some changes and it's working fine now. It must be the different hotplug command I was using - can't remember why I changed it now.

Don't think the network and broadcast parts are necessary unless you're on an unusual subnet or custom job, but they can't hurt so I've put them in too.

thanks again

---

