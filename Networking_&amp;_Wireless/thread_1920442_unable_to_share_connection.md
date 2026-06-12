---
title: "unable to share connection"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by compiz addict on 2012-02-04
Both my desktop and server are running Ubuntu 10.04

My desktop is receiving internet via wireless.

My server needs to receive internet from my desktop. It has a static IP as configured in /etc/network/interfaces of 192.168.0.195, because that is the IP that goes on the routers DMZ, and the gateway is set to the router transmitting wireless (192.168.0.1).

Bridging wlan0 and eth0 doesn't seem to work on my desktop when I use /etc/network/interfaces. Maybe it's not effected by that configuration file - I have no idea how I got it working on my server if that's the case.

Using the simple method of sharing internet using Ubuntu's network manager with the GUI and whatnot, which is setting up a wired connection and changing the methd to shared, and has always worked for me, causes my desktop to not receive internet at all. It's still connected to WiFi though, and I don't understand why it would be trying to receive internet from the wired connection when I set it to shared.

---

### Post by compiz addict on 2012-02-05
*bump*
still don't have this figured out.

---

### Post by helgman on 2012-02-06
Are you trying to set up a bridge between the wireless and the server or is the goal to let the desktop route packages between the wireless network and the server?

As for the desktop trying to connect to the Internet via the connected network ... maybe your routing table would give some clues (route -n). Maybe it sees your wireless and cabled networks as the same subnet, favoring the cable for speed? But this is just speculation ...

Regards,
Helgman

---

