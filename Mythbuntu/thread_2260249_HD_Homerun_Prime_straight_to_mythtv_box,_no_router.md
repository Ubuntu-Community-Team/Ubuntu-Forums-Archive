---
title: "HD Homerun Prime straight to mythtv box, no router"
date: 2015-01-10
forum: Mythbuntu
---

### Post by Senkoboy on 2015-01-10
I am wanting to connect my HD Homerun Prime straight to my mythtv box. I had everything working in Windows 7, and in mythtv when connected to my router. Wireless is not up to par for streaming, so I want to hook the prime straight to my (Mythtv version.25, Mythbuntu 12.04) box. When I hooked it up I get a flashing light on the left, ( This indicates that the HDHomeRun has a network connection but is not getting an IP address from your router. Check to make sure that the DHCP function is enabled on your router, and that either the allowed devices/access control/MAC filtering function on the router is disabled, or that the HDHomeRun is on the allowed list.) What I run the Homerun config program I can't find my box with the scan. I have had a myth setup for a few years, but I am not an expert with Linux. What needs to be done to make this work? I have a combonation backend/frontend with a wireless internet connection so my ethernet port is open.

Thanks

---

### Post by steeldriver on 2015-01-10
IIRC you just need to configure the interface on the computer as "Link local only" - you may need to reset the Homerun as well if it was previously configured for DHCP, I can't remember

---

### Post by Senkoboy on 2015-01-11
This is from the silicon dust website.

> The HDHomeRun can be connected directly to a PC via an Ethernet cable.

The HDHomeRun is auto-MDX so does not need a cross-over cable.

Software: This feature requires HDHomeRun software release 20070829 or later.

Network configuration: Configure the PC to use a static IP address in the 169.254.x.y range, e.g. 169.254.5.12, with a network mask of 255.255.0.0. No gateway address or DNS servers are needed.


In network manager I have tried local link only. I have also tried manual config with the above numbers, but I had to put in a gateway address (192.168.1.5) to save the configuration. I can't get anything to work, it just sits there waiting for (requesting a wired network address).  I did move my router, with no internet connection, to my mythbox, plugged in my homerun and it worked.  I might pick up an old router off of ebay and hook it up, that would solve my problem.  I only halfway know what I am doing, that doesn't help things any. Would a switch do the same thing as the router?  I still get my internet from my wireless.

---

### Post by hollywoodpete on 2015-01-12
I am not very computer savy but if you show your current /etc/network/interfaces file I might be able to help

---

### Post by Senkoboy on 2015-01-13
> Th network light will flash until one of two conditions is met:
1) The HDHomeRun gets a DHCP address
2) If there is no DHCP server on the network, the HDHomeRun will assign itself a 169.254.*.* address and wait for a command (light stops flashing after it gets a command)

You're attempting #2. If you can't find the HDHomeRun make sure that you've assigned a 169.254.*.* address to the computer; many computers will do this automatically when DHCP fails but you can speed up the connection process by manually configuring the IP address of the computer.

I have it working for now.  After waiting for a little while I did a search again and found it this time.  I did set the network manager to local link.  I still think I will try to hook up a router as a wireless bridge, it should help my internet connection, and get away from the usb wireless adapter. 

Thanks

---

