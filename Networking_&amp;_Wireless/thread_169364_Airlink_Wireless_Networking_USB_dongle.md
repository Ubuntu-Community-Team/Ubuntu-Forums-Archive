---
title: "Airlink Wireless Networking USB dongle"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by LeFou on 2006-05-02
Okay, I don't want to mess this up so even though I have some ideas about how to get this device going I'd very much appreciate someone double-checking my work, since it has failed a few times on a few distros.

I found what seems to be a driver patch for the kernel:
[http://sourceforge.net/projects/ax88178](http://sourceforge.net/projects/ax88178)

I ran 'patch ax88178.patch' after extracting and it just sorta hung there.

I've gone the ndiswrapper route as well, but the device created that way never got usable. If that's preferred I'll try it again.

In the GNOME device manager it does show "USB 2.0 WLAN" but vendor and device are "Unknown". 
info.linux.driver = usb 

Under that is "USB Vendor Specific" which has vendor "ZyDAS" and device "USB Vendor Specific Interface"
info.linux.driver = zd1211

Now what?

---

### Post by LeFou on 2006-05-02
I think I'm good. I used another thread in here (there sure are a lot!)

key seems to have been the file /etc/network/interfaces altered the way sharingan did
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
iface eth0 inet dhcp

auto eth0

#auto wlan0
iface wlan0 inet dhcp
#iface wlan0 inet static
#       address 192.168.1.3
#       netmask 255.255.255.0
#       network 192.168.1.0
#       broadcast 192.168.1.255
#       gateway 192.168.1.1
       wireless_essid USRHOME
       wireless_mode Managed
       wireless_channel 11
       wireless_rate auto
#       name Wireless CardName
#       wireless_keymode restricted
#       wireless_key1
#      wireless_defaultkey 1
```

and run through

```

sudo ifconfig etho0 down
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

Seems to work great. I took some notes; I'm scared to touch anything now, or even restart the machine, because this took Many Hours :(

Oh well, learning experience and all

---

