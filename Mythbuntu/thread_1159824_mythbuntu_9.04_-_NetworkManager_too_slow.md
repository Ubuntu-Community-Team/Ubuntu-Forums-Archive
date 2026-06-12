---
title: "mythbuntu 9.04 - NetworkManager too slow"
date: 2009-05-15
forum: Mythbuntu
---

### Post by thechump on 2009-05-15
I've just installed mythbuntu 9.04 on a system with Core2 Duo E8400 3Ghz on an Intel DG45ID motherboard and using an Nvidia 8400GS video card instead of the built-in video.

The issue is that NetworkManager is too slow in bringing up the network; this is regardless of whether it's configured to get an IP address for the built-in wired NIC through DHCP or static IP. It's so slow that auto-login and mythfrontend have already completed before the interface is up.  Consequently, mythfrontend cannot contact the backend and requests to be re-configured everytime the machine is rebooted.

As far as I am concern, NetworkManager is now a useless piece of turd; I worked around the problem by disabling it and setting up the network by modifying /etc/network/interfaces.

---

### Post by uncle hammy on 2009-05-15
Network Manager has been embarassingly abismal since it was "updated" in 8.10.  I have had to go the same route as you did to get things to work...

Disable Network Manager in Sessions / Startup in the XFCE Settings
Add manual entry to /etc/network/interfaces
Add manual entry in /etc/resolve.conf for DNS

How on God's green earth can the network manager take so long to bring up a static entry?  DHCP I can kinda get, but static?

---

### Post by djieno on 2009-06-19
Yep, same here... worked for me too. Disable network manager from xfce settings and add in:

/etc/resolv.conf:
```
domain [yourdomain_without_brackets]
search [yourdomain_without_brackets]
nameserver [dns_ip_without_brackets eg. 192.168.1.1]
```

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Gtzzz 

Djie

---

### Post by mjancola on 2009-06-23
I too was having a problem changing Myth to use a static IP.  I was excited to find this post, but it didn't work.  Namely, I unchecked the box for Network Manager in Sessions and Startup and restarted.  My old DHCP address is still being used even though the interfaces file specifies a static.

On a related note, how do I launch the Network Manager?

---

### Post by dmfrey on 2009-06-23
Uninstall NetworkManager and replace it with wicd.

---

### Post by uncle hammy on 2009-06-24
Another thing you can do is set the launch order for the mythbackend service in /etc/rc2.d right now I think it's something like S20myth-backend.  Rename it to S99myth-backend.

That has actually worked for me and allowed me to use network manager.

---

