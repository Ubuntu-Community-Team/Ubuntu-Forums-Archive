---
title: "Hardy wireless stopped connecting."
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by Pde on 2008-12-18
Yesterday (December 16th) when I turned my computer on at work the wireless did not automatically connect like normal.  I restarted the computer and it connected when it came back on.  However, this morning it did the same thing, so I restarted and it still didn't connect.  I ended up restarting several times and I got it to the point where it recognizes the access points, but when I try to connect to one it just sits there "Attempting to join."  It does this on both WPA and unsecured connections, while Windows Vista has no problem connecting to same access point.  

My wireless card is a Linksys Wireless-G PCI adapter with RaLink RT2561/RT61 chipset 
Ubuntu version 8.04.1
kernel version 2.6.24-19-generic i686

dmesg returned ADDRCONF(NETDEV_UP) wlan0: link is not ready

I also tried sudo /etc/init.d/networking restart but no change.

---

### Post by Pde on 2008-12-18
I tried a bunch of stuff from different sources and as best I can tell the driver (rt61pci) is place and working, I did modprobe -r  rt61pci and then modprobe rt61pci which didn't change anything.

lshw -C network, ifconfig and iwconfig all seem to indicate that everything is fine, which makes sense because it can see the available connections; it just can't connect.

Do you think upgrading to Intrepid will fix it?  That's the only thing left I can think of.

---

