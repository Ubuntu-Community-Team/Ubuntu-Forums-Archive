---
title: "Wirelessly share laptops Internet connection"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by Magma828 on 2010-12-08
My laptop is connected to the university network by Ethernet cable, and they provide no wireless network. We are also not allowed to connect routers to the network. This is annoying because I can't use the Internet on my iPod.

So yeah, obviously the wireless interface on my laptop is unused, so how can I "repeat" the connection?

I tried creating a new wireless network by clicking on the network list icon at the top, and the iPod can find it. Problem is, when I try to join it I get this error on the iPod: Unable to join the network "cremeegg". I'm sure that the problem lies with ubuntu, because I can connect to other networks fine.

---

### Post by alan2796 on 2010-12-08
Hey, not sure if this is the right way to do it or not but it worked for me.

Network Manager > Create New Wireless Network.

[ATTACH]178109[/ATTACH]

Right Click Network Manager > Edit Connections, Select Wireless tab then click on your connection and hit edit then IPv4 Tab then make sure it set to "Shared to other computers" 

[ATTACH]178110[/ATTACH]

Open up Firestarter or if you don't have it (It's in the software center)

Start it up and Then 

Edit > Prefrences.

Click Network Settings and then sort your connections out

eth0 should be your wired card which is connected to the Internet and eth1 or wlan1 or wlan0 something is probably your wireless card which is what is connected to your Local Network, select the correct interfaces in the drop down menus and then check "Enable Internet Connection Sharing"

[ATTACH]178111[/ATTACH]


now try connecting your iPod to your Ad-hoc network.

also make sure that the firewall isn't blocking the incomming connection from your iPhone or anyother device which you want to connect to your network.

---

