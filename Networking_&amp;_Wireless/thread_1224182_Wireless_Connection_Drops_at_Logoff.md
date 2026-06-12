---
title: "Wireless Connection Drops at Logoff"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by Surd on 2009-07-27
Hello, I have a server running **Ubuntu Server 9.04** (with XFCE, the xubuntu-desktop edition). Being my primary network server, the wireless connection is vital but whenever I logoff, the connection drops. Is there a way to make the connection stay active even after I log off. Im using a ZyXEL G-202 Wireless Adapter **without** ndiswrapper
This is my /etc/network/interfaces:
```
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
   address 192.168.2.1
   netmask 255.255.255.0
   broadcast 192.168.2.255
 
auto wlan0
iface wlan0 inet static
      wireless-essid netgear-m
      wireless-key [My network key]
      wireless-channel 06
      wireless-mode Managed
   address 192.168.1.2
   netmask 255.255.255.0
   broadcast 192.168.1.255
   gateway 192.168.1.1

```
Hope you can help, I am going away tonight so I will have to leave it logged on for the next week so I can still work on it. I have looked through man 5 interfaces and I didn't really understand it. I am quite new to Linux but I am getting the hang of it.

---

### Post by sebmaynard on 2009-11-25
Did you manage to fix this? I'm going through my usual bi-annual "let's install Linux on anything with a processor" phase, and my laptop has the same problem...

I'm actually rather happy with Ubuntu 9 so far; my only gripe is that when i connect via VNC, then logout of Gnome, the wireless connection goes with it, and I can't reconnect...

---

