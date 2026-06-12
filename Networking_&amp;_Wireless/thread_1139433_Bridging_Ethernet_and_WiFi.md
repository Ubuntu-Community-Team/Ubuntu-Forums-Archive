---
title: "Bridging Ethernet and WiFi"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by CalcProgrammer1 on 2009-04-27
I use Windows (XP, Vista, and 7's) Network Bridging (or sometimes Internet Connection Sharing) to connect my Xbox 360 to the Internet when I only have my laptop.  It works fine in Windows on every PC I own, but I can't find any way to bridge easily in Ubuntu.  I tried bridge-utils, but that doesn't like bridging interfaces that aren't listed in /etc/network/interfaces.  I don't want my Ethernet line to be set up as a static IP, because sometimes I connect to the Internet via that line, but I want it to work both ways.  I also need Network Manager to keep control of wlan0 so that I can discover and connect to new networks.  How can this be done?  I have an Intel 4965 A/G/N WiFi card and a Realtek Gigabit Ethernet card in my laptop (HP dv9700t).

---

### Post by inobe on 2009-04-27
just set eth0 to "shared to all computers"

[IMG]http://www.itsyourpc.org/duane/files/networker.jpg[/IMG]

i have shared to other computers and never had any issues.

---

### Post by CalcProgrammer1 on 2009-04-27
Shared to other computers seems to be working on my PC (laptop sharing Internet to desktop) but I haven't tried the 360.  Does this only share the Internet or does it do a full bridge?  I noticed both PC's have the same IP address (whereas Windows bridging allows the attached devices to get new IP's from the router/DHCP server).  I don't know if that is an issue or not.

---

### Post by inobe on 2009-04-27
you have a router correct ?

plug the ethernet cable into the wan port and enable "share to all computer" no configuration needed.


done

---

### Post by CalcProgrammer1 on 2009-04-27
Wouldn't that involve 2 routers?

Cable modem -> Router ))) Laptop -> WAN Router -> Xbox/Computer/etc

That only works because the second router is creating its own sub-network and establishing its own clients.  Windows' bridging does not make the computer into a DHCP server (essentially what adding a router does) but instead forwards DHCP requests to the DHCP server that the computer itself is connected to, getting the device its own IP address.  The device acts as if it was not even connected to a computer but to the router itself.

---

### Post by inobe on 2009-04-27
i won't make this complicated.


say you have a wireless connection from "whatever" source........ or a usb modem, even an evdo card !


laptop> router> wired/ wireless computers.


plain and simple, no assigning this or that forwarding that and this, connect the hardware and make the change.

now if you want to bridge something to me only makes sense on virtual machines, but you want to connect and xbox and a pc from some unknown source.

----------------------------------------------------------------------------------------------------------------------

edit: you can also go threw ICS [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

or add hoc [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by CalcProgrammer1 on 2009-04-28
The reason is that the laptop is connected to a router that has other PC's on it.


Modem ----------> Router ))) Laptop -> Xbox

PC (Media Server) --^
Another Xbox -------^
If I want to connect to the media server using the Xbox, the laptop must bridge the entire connection and not just the Internet part.  My modem, router, and media server are in one room but I have no Ethernet ports in my living room, where I want to play the Xbox and stream my media.  That is why I need bridging and not just Internet sharing.  I also sometimes have friends over and we hook up multiple consoles to play multiplayer.  This also requires a functional LAN as other consoles may be connected directly or to other laptops.

---

### Post by inobe on 2009-04-28
ahh' it makes complete sense :)

sorry i sent you up the wrong path, well at least we learned something together.

now that we are getting advanced i see your need to bridge.

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

you did say you tried the util, i am sure there are ways to troubleshoot this.

edit: [http://onlyubuntu.blogspot.com/2008/08/howto-share-internet-connections-in.html](http://onlyubuntu.blogspot.com/2008/08/howto-share-internet-connections-in.html)

---

