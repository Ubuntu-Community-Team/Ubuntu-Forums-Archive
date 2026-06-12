---
title: "Static IP on a local network?"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by airspoon on 2011-08-27
Is there anyway to achieve a static IP on my local network? Often, when I have to reboot my Ubuntu machine, or when I have to reboot my routers, my computers will be assigned different IPs (the last digit). 

I'm running Ubuntu 11.04 and if it matters, I have the older Apple tear-drop g wireless router that is configured as a WDS with an Apple Express router. The apple express router is then connected to my Ubuntu machine through ethernet. 

My network has 3 Ubuntu machines (2 Desktops, 1 laptop), 3 Windows machines (1 desktop, 2 laptops) and one Mac (laptop) and various devices like a printer, PS3 and SlingBox -all on the same network, though I really only need one computer to retain the same ip address. Is this possible?

The purpose behind my need (in case there is a different or better solution), is to access my Ubuntu machine (databases, ftp, http, etc..)  from the other computers on my network and having to reconfigure everything every time my ip changes is quite cumbersome.

Surely, there has to be a solution, right? Any and all help would be greatly appreciated.

---

### Post by chili555 on 2011-08-27
You certainly can. Just be sure the IP addresses are outside the range used by the DHCP server in the router. Click the Network Manager icon, Edit Connections and set up like the attached. Post back if you need more details.

---

### Post by airspoon on 2011-08-27
So. the DHCP range being the 10.0.1.x that it is assigning each computer now? Also, due I set up an entirely different network connection? Thanks!

---

### Post by chili555 on 2011-08-27
> So. the DHCP range being the 10.0.1.x that it is assigning each computer now? Exactly. If the configuration pages of your router or other access point show the DHCP range is from, for example, 10.0.1.2 to 10.0.1.50, use static IP addresses from x.51 on up so there is no collision.

---

