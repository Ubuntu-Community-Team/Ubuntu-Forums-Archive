---
title: "/etc/network/interfaces - allow-hotunplug"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by mafeuser on 2011-06-05
On my ubuntu 11.04, when plugging my usb wlan0 adapter I want hostapd be started automatically.
Thus in /etc/network/interfaces I add following wlan0 stanza:

auto wlan0
iface wlan0 inet static
  hostapd /etc/hostapd/hostapd.conf
  address 192.168.20.1
  netmask 255.255.255.0
  network 192.168.20.0
  broadcast 192.168.20.255

And it works fine, because hostapd deb package installs following:
/etc/network/if-pre-up.d/hostapd

I also want hostapd be stopped when I remove my wlan0 usb adapter, but this does not happen:(

Required file exists in the system:
/etc/network/if-post-down.d/hostapd

Is it a bug?

Note that `sudo ifdown wlan0' does the job when my wlan0 exists.

Do I have to hire udev REMOVE event for that? I hope not, because this is not so elegant as the above.

best regards,
Paul

---

