---
title: "Deactivate/Activate wireless network device"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by knahrvorn on 2006-02-28
Using the ndiswrapper I have (almost) succesfully made my wireless network on my laptop funtion properly. I only have a minor issue left.

During boot, I see three network related lines appear:
```
Setting up networking...
Configuring network interfaces...
Waiting for network interfaces to come up...

```
The former and the latter go straight through, but the middle one halts the boot process, and I have to press Ctrl-C before it continues. Apparently there isn't any network access during boot, since the NTP line fails.

When the boot is completed and I've logged into Gnome, I have to enter the network settings and Deactivate, then Activate the wlan0 device. After that, everything works fine, but until that there's no connection.

My wireless connection gets its IP by DHCP (and I really wouldn't want to change that). I have two network cards in the machine, a wireless and a wired (which is unplugged). If I boot with a cable in the wired network card, I still have to press Ctrl-C during boot, and the NTP line fails, but the connection is there immediately after I log in to Gnome.

Here's my /etc/network/interfaces:
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
iface wlan0 inet dhcp
wireless-essid [removed]
wireless-key [removed]

auto wlan0

iface eth0 inet dhcp


auto eth0

```

---

### Post by bikeboy on 2006-02-28
Try adding "map wlan0" so that it looks like this...

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
        map wlan0

# The primary network interface
iface wlan0 inet dhcp
wireless-essid [removed]
wireless-key [removed]

auto wlan0

iface eth0 inet dhcp


auto eth0

```

Mine works the way you want and is basically the same as what's above, except that I don't use dhcp.

edit: you may want to comment out eth0 if you don't have an ethernet cable plugged in by default. Make the line...

```

# map eth0

```

Mine is this way and I never have problems with the ntp as long as the internet is working.

---

