---
title: "disable wireless in network manager applet"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by User#32423 on 2012-01-02
I have Ubuntu lucid 10.04 on a netbook. The network manager applet setup works great for my usb broadband modem. The network manager doesn't support ad-hoc networks very well for my card. I wish to use the /etc/network/interfaces file to configure my wireless network. I therefore need to disable the wireless aspect of the network manager applet. However when I right click and untick the "Enable Wireless" box it disables temporarily. It is enabled again on reboot. 

I wish to disable the "enable wireless" permanently.

The following code on the command line disables the wireless:

dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false


Is there any way of putting this into a bootup script that gets read just before the /etc/network/interfaces file? or is there a simpler solution.

Thanks

---

