---
title: "IP address no longer available"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by risby on 2011-03-21
Hi peeps

I don't know if I've given correct title or not but this is what's happening:

I have Ubuntu Lucid Lynx with a D-Link WDL G122 USB wireless device connecting to a Netgear GDN2200 router. This has all been set up and working for over a year and I have nine devices' MAC addresses with reserved IP addresses set up in the router for its DHCP functionality.

One day about a week ago I had no internet connectivity and ipconfig showed no IP address for the wlan0 interface. The network device is not dead; its led flashes every minute or so. The router's log does not show any rejected dhcp requests. I haven't intentionally changed anything to do with the network configuration but I suspect there may have been an automatic update that wasn't compatible with my set up.

I've moved the computer into the room next to the router and connected it with an ethernet cable and added the network card as another reserved IP address on the router but that also fails to establish a connection.

Any ideas what I should try nexr?

TIA, Ris

---

### Post by risby on 2011-03-23
I have tried setting the ipaddress (and netmask and gateway) manually. First for the wireless device and then for the cable device but that didn't work; ipconfig still shows no ip address for either interface.

It puzzles me that under System->Preferences->Network Connections, where I set the manual options, the Last Used column says "never" as though this management tool was redundant and some other software has been handling the connection.

---

