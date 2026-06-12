---
title: "Gnome panel network-icon fake?"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by utnubuuser on 2009-09-03
Ubuntu 8.04 gnome

The network icon on my thinkpad's top panel works as prescribed in most instances, but yesterday I noticed that when right-clicked, to disable wired-networking, the icon changes to show the network is disconnected, but Firefox still accesses websites.

So, the icon is **not disconnecting** the computer from the internet. 

Any suggestions on where to start looking?

The only real difference on this machine is that I upgraded Firefox to 3.5.  -- Maybe something in one of the configuration files not linked properly?  

Thanks.

PS.  Network-manager has always been a little off with this particular machine.  ie, I have to choose my preferred wireless service twice, because it connects, then drops the connection, but upon re-selecting it's ok.

---

### Post by dbalascak on 2009-09-03
Not a fake.  There are 2 methods that can be used to configure the interface. First being the */etc/network/interfaces* file.  This is the first place that the Network Manager checks for config info.  

The second method is used if the file */etc/NetworkManager/nm-system-settings.conf* contains the following
```

[ifupdown]
managed=true

```
If this is set then the */etc/network/interfaces* should be very light as follows
```

auto lo
iface lo inet loopback

```
Then the icon on the desktop is enabled and all configuration can be done through it.  The config data is now placed into */etc/NetworkManager/system-connections* directory into interface specific files.  If you have config info in both locations strange interactions can occur.

---

### Post by utnubuuser on 2009-09-03
Thanks I'll check it out.  I think it might be my thinkpad acpi is not configured properly.

Turns out if I disable the wifi through the thinkpad specific buttons, as well as through the network manager, then the connection is actually stopped, otherwise the wifi is running in the background, so when the wired network is disabled, the wifi is still working in the background even when the icon says networking is disabled.

---

