---
title: "nm-applet gone and not automatically connected"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by amsterdamharu on 2011-01-26
I had to connect directly to the dsl modem do traceroute and now that I'm connected through the router it won't automatically connect.

Solved the auto connection by changing /etc/network/interfaces but the applet still don't show.
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Uninstalled and re installed the network-manager packet a couple of times but still nothing showing (yes I have the notification area on my panel).

Now installed wcd but I'm not sure what it's supposed to do.

My question is; is there a way to use pppoe and then not use it without borking up the network applet and or having to re install Ubuntu?

---

### Post by amsterdamharu on 2011-01-26
1. Uninstalled network-manager "sudo apt-get purge network-manager"
2. Changed /etc/network/interfaces  to:
```
auto lo
iface lo inet loopback
``` 
Using the command
```
sudo nano /etc/network/interfaces
```Then press control + x, y and enter
3. Installed network-manager
```
sudo apt-get install network-manager
```
4. rebooted

---

