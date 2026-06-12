---
title: "Network Bridging"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by genericnumber1 on 2008-12-27
I've been googling for a few hours trying to fix my problem and haven't been able to find a solution to suit my problem... I'm trying to bridge a network through my ubuntu box while still permitting my linksys router to do all the DHCP work.

My desired network layout:
Computer 1 -> Ubuntu -> DHCP Router -> Cable Modem

But I would like for it to function for Computer 1 exactly as if it was like this...
Computer 1 -> DHCP Router -> Cable Modem

By this I mean I wish for the computer to act as if it's nothing other than another DHCP client to the router. Computer 1 is connected to the ubuntu box in eth0 and the ubuntu box is connected to the router through eth1. I've tried the feature built into firestarter, but regardless of the settings I get the error message "Failed to start the firewall. The device eth0 is not ready. Please check your network device settings and make sure your Internet connection is active."

I suppose a summary of my problem would be: 
"How do I use the ubuntu box as an over glorified network switch allowing both the ubuntu box and the single connected client (in eth0) to connect to the internet (in eth1)."

I'd be incredibly appreciative of any help you can give. I've been afraid to try many configurations I've seen  while googling that don't exactly match my problem out of fear of breaking my working internet connection for the ubuntu box on eth1.

---

### Post by joebeasley on 2008-12-28
You need to create a bridge interface, and add both of your interfaces to the bridge. (brctl is in the bridge-utils package)

manual way:
sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif bro eth1

ifconfig br0 x.x.x.x netmask x.x.x.x up   (or dhcp if that's what you use.)

The other pc is connected to the ubuntu box using a crossover cable. Configure it normally.

---

