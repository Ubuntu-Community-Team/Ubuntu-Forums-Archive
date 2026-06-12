---
title: "Network Manager connection to &quot;(none)&quot;"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by csete on 2009-01-04
I'm testing out a new Netgear WNDR3300 Dual Band router (firmware V1.0.29_1.0.29NA) with my Dell Inspiron E1505.  My laptop has Broadcom Draft N wireless card:

```
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.0.2 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

```

I'm using the Broadcom STA wl driver and things are working ok when connected to the G network SSID (using wpa/tkip).  When I switch over to the N network, I get a message that "You are now connected... " showing the correct SSID.  Once connected, Network Manager shows no connection in the icon and the hover text says: "Wireless network connection to '(none)'".  The network is still alive (I'm posting this via the N network) and yet it doesn't appear to be quite right.  I'm not sure what, if anything, I can do to fix this up.  The speed is double that of the G network, so it seems to be working at least to some extent.

```

> iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
eth0      no wireless extensions.

pan0      no wireless extensions.

```

```

> iwlist eth1 rate
eth1      no bit-rate information.

```

What other information could be helpful in debugging?  I see Broadcom just released a new version of the driver a few days ago, but I also see from reading the forums that this is non-trivial to add to Ubuntu.  Would it help?  Does anyone have an idea if/when this new driver might be available as a deb?

I appreciate any help that people could provide.  I need to decide if this router is worth keeping or if I should return it.

Thanks,
Craig

---

### Post by pcjunkie on 2009-03-12
I am getting this message too now.

3 days ago I attempted to browse to Localhost/xampp while offline and Fire fox locked me out.

After attempting a few things I set /etc/dbus-1/system-d/NetworkManager

 <policy at_console="true"> to  <policy at_console="false">

In an attempt to get FF to go to localhost and it worked. However going back to a wireless enevironment failed and the network manager failed.

I reset it back to true and while the network connected, the notify and connection information was lost and not replaced. Connecting to LAN produces a "connecting" icon that sticks but never shows connected. Its like the icons have hit time warp...


It now states: wireless network connection to ("none")
No information is available through this system. Accessing another network is going to be difficult I imagine..

---

### Post by csete on 2009-03-12
I created a bug in launchpad for this problem quite some time ago, but there have been no changes or information added to the bug.

---

