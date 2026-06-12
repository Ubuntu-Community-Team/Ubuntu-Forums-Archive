---
title: "My internet wont work at all"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by missreckless on 2009-09-11
One day my internet just stoppped working it will not connecct via wired connection or wireless conecction. it's very frustrating seeing as how im not all tech savy like everyone else who runs this my ex put it non my computer and i love it but I need internet I'm tried automatic config with no luck... I've typed in the ip address and the subnet and the gateway under static ip and ive tried local zeroconf and nothing is working the internet here DOES work as im useing it on my mates computerb that runs windows right now i'd reinstall the cd but i dont want to end up deleting all 9000+ of the photos bi have on heere anyhelp? mind my typing my wrists are broken:confused::confused:

---

### Post by Iowan on 2009-09-13
How does your machine connect - router or modem (something else)? How/where did you enter static information - Network Manager, editing */etc/network/interfaces*? The static IP may require you to (also) manually enter DNS information in */etc/resolv.conf*. When machine was set for automatic IP address (DHCP), did it get address and was it similar to the one the Windows machine has? (**ifconfig -a** from a terminal will give information about Ubuntu's interfaces. 
By the way - what version do you have? CTRL-ALT-F1 should prompt with version number - CTRL-ALT-F7 should get yo back to Desktop.

---

