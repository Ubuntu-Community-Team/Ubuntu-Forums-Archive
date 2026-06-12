---
title: "share eth0's internet to eth1 and wireless"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Jungle_King on 2009-04-28
I've got a system running in my girlfriends uni room that were using as a storage/download server
 
It's on her uni network, so eth0 is connected to this and gets its IP from the uni DHCP
 
What i want to do is have her laptop or my laptop plugged in to eth1 and get the internet from the ubuntu box. I'd rather it be plug in and go, so preferebly have ubuntu running a dhcp server, but thats not too much of an issue, so setting her laptop's ip/dns manual isnt the end of the world if i need to and it saves headaches
 
this is where it gets tricky....
 
i have a wireless card in the ubuntu box also. I'd like to be able to setup a ad-hoc network to connect my itouch too and use when im there.
 
do i need to bridge eth1 and the wifi, and share the internet to br0?
 
I can get sharing working for eth1, but when it comes to setting up the wifi for ad hoc and sharing to both im well and truly lost!
 
so to clarify i have eth0 which is wired and goes to her uni lan, eth1 is also wired and will go to either my laptop or hers, and theres a wireless card.
 
I'm running intrepid desktop.
 
sorry for the bad pic! paint is all we have in work
 
cheers in advance guys!

---

### Post by Iowan on 2009-04-28
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page for ICS? There's a section near the bottom for [wireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless").

---

### Post by uBeer on 2009-04-29
To share your internet (wired or ad-hoc) you need to install dnsmasq-base on the internet pc.

Now when you plug in a laptop, you'll find that they do connect. Right click on the Network Manager icon and select "Edit Connections". There you'll see something like "Auto eth1" or "Ifupdown (eth1)". That should be the one you're connected to.

Select that one and click Edit and go to IPv4 Settings tab. Select from the Method drop down list: "Shared to other computers."
Now you're connected!!

Wireless it works almost the same but actually easier. Just create a new wireless network and connect to it with your phone. It should automatically configure it as "Shared to other computers".

I don't know yet how to let the wireless connected even if there is no other pc connected, so if you can ever figure that out: let me know!!

Have fun with ICS!

---

### Post by coutts99 on 2009-04-29
...

---

