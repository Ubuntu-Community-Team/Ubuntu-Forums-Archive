---
title: "Bridged Network/OpenVPN Server Setup Causes Slow Boot Up"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Z3ro3X on 2009-08-11
I managed to setup a OpenVPN server and a bridged network.  This is so my brother's laptop will connect to me from anywhere in the world at anytime so it's easy to admin his system when he needs help.  My only issue is this.  After setting up the bridged network, Ubuntu's boot-up time is slow as hell.  I used Starup-Manager to change the splash screen so that I can see the boot process.  It pauses for a long time (about 10-15 seconds) on I think it was called Configuring Network Interfaces.  My wifi (wlan0) is the Internet source and the bridge (br0) is for the virtual network adapter (tap0) and my on-board Ethernet port (eth0).  I used Firestarter for DHCP.  The bridge works fine and the laptop connects to my system when it gets online.  I'm guessing the reason it takes a long time to boot is because I don't use the Ethernet for anything so the bridge sits there waiting for eth0 to connect to something.  Is there a way to fix this?  It's not a real big deal.  I hardly ever boot my system and I leave it running 24/7.  So an extra 10-15 seconds on boot time isn't a real show stopper but it is annoying.

---

