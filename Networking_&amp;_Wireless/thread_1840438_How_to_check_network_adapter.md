---
title: "How to check network adapter"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by Fake51 on 2011-09-07
I have a problem with my ubuntu 10.10 install. A couple of days ago the network was working just fine, then today I boot up the computer and I get no connection.

The computer is connected to a modem-router through ethernet.
I've tried changing the cable, no luck.
I tried the cable in another computer, works fine.
The router is blinking the light for the ethernet connection, but on the computer I see no lights for the adapter.

I've pinging the router - all I get is "Destination Host Unreachable".

I set up the computer to use a static address, my /etc/network/interfaces looks like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
 address 192.168.1.38
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 gateway 192.168.1.1
```

I'm currently thinking the network adapter died. How would I go about checking that, and how would I go about diagnosing the problem in general?

Any and all pointers very welcome
Fake

---

### Post by praseodym on 2011-09-07
Hi,

do you use the network-manager? If not: is it disabled in "Autostart"? Can you show:

```
cat /etc/NetworkManager/nm-system-settings.conf
```

You may also try to take all components totally off the current for about 10 minutes. Does the router work with DHCP?

---

### Post by Fake51 on 2011-09-08
Apparently, leaving my computer offline over night solved the issue. I have no idea what went wrong earlier (several restarts had no effect) but it's working now. Question is just for how long.

Thanks for the help :)

---

### Post by praseodym on 2011-09-08
The idea behind "off the current" is, that all firmware is completely unloaded. Maybe something was "stucked"?!

---

### Post by Fake51 on 2011-09-08
Seems you're right - I'm guessing the router somehow didn't acknowledge the computer in the network. Turning the computer off for a good long while meant the router forgot about it.

---

### Post by praseodym on 2011-09-08
Router-firmware is up-to-date?

---

### Post by Fake51 on 2011-09-08
Newest I can find. It's a rock solid Netgear DG834G that's never failed me before. Replaced a very crappy Zyxel with it, so I'm somewhat annoyed to see a failure like this, but hey - it's pretty much the first time.

---

