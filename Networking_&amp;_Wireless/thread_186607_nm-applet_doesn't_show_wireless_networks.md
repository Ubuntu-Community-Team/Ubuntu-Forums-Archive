---
title: "nm-applet doesn't show wireless networks"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Hilbert Schraal on 2006-06-02
Upgraded from 5.10 to Dapper yesterday. In 5.10 networking was working perfectly. The wired connection works fine, but the wireless doesn't. The NetworkManager applet doesn't show the wireless networks, just the wired network.

eth1 does exist. I have an Intel Centrino laptop (Acer TravelMate 660), which has an Intel PRO/Wireless LAN 2100 card (ipw2100).

Any one having the same problems?

Hilbert

---

### Post by SqRt7744 on 2006-06-02
[QUOTE=Hilbert Schraal]The NetworkManager applet doesn't show the wireless networks, just the wired network.
Hilbert[/QUOTE]

does your /etc/network/interfaces file only contain references to lo?  network-manager only handles those interfaces not mentioned in the interfaces file.

i.e. it should look something like this:
```

# The loopback network interface
auto lo
iface lo inet loopback

```

---

### Post by Hilbert Schraal on 2006-06-02
ok, that was it. My interfaces file said:

--------------------------------------
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid any
--------------------------------------

I removed the eth0 and eth1 lines. NetworkManager works correctly now (as it did in 5.10)

Thanks! Hope this helps others as well.

---

### Post by jessedyer on 2008-01-24
Thank you, SqRt7744!  I had the same problem.

---

