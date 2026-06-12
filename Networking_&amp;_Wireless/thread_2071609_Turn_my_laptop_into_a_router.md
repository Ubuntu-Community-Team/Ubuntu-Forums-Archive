---
title: "Turn my laptop into a router?"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2012-10-15
My home router uses WPA2 for my Wi-Fi, but I'm experimenting with homebrew programs on my Nintendo DS and it requires an internet connection.  However, the DS's current firmware (and even all the custom homebrew firmware I could find) only supports the WEP protocol.  I do not want to downgrade my router from WPA2 to WEP however.  So is there a way for me to turn my laptop into a Wi-Fi hotspot serving WEP, while being itself connected via WPA2?  I want it to be able to connect to my WPA2 router, but transmit WEP to my DS, preferably with a different passkey for security (I was able to crack a WEP key in under 40 seconds with aircrack on a laptop, so I don't trust WEP with the same key that I use for my router).  Is there a way for me to do this?

**Router**-------*WPA2*---*X*--->**DS**

**Router**-------*WPA2*------->**_Laptop_**-------*WEP*------->**DS**

---

### Post by ahallubuntu on 2012-10-15
You could buy a 2nd wireless card for your laptop, a little USB dongle you can get for under $10 on Amazon or eBay.  I think the newer versions of Ubuntu have a built-in feature in Network Manager to make a hotspot out of a 2nd wireless card in the way that you seem to want.

Can your Nintendo handle a wired/ethernet connection instead of WiFi?  Then you could turn an old router into a WiFi bridge of sorts (connected via WPA2) but you would plug an ethernet cable from one of the LAN ports into the Nintendo.

Or - just get a 2nd router that is dedicated to the Nintendo and is attached to the 1st router; 2nd router does only WEP.  Maybe you make it static IP with a weird subnet no one would be able to guess easily.  Unplug the spare router when you aren't on the Nintendo...

---

### Post by Stonecold1995 on 2012-10-16
I can't buy anything new (I have to use my laptop) and no, a Nintendo DS cannot connect to an Ethernet cable.  It supports WEP connections and unsecured connections.

---

### Post by griffinmt on 2012-10-16
If you are going to use your laptop as shown in your diagram, you will have to install a second wireless adapter in it somehow, or hardwire via enet to a dedicated wireless router. Either way you will have to spend some money or go scrounging with your freinds :)

---

### Post by Stonecold1995 on 2012-10-16
So there aren't any software solutions?

---

### Post by 1clue on 2012-10-16
You can create a virtual network interface to go on top of your physical one, to give the illusion of two cards.

I don't know the details of WEP or WPA2, whether your hardware can support both protocols, but the idea is sound at least for entertainment or education.

What is NOT viable is to separate security between the two networks.  The packets for both "networks" travel through the same space, and if they are routed by your laptop then those routed packets might be "secure" on the one side but not secure on the other, making your secure side no better than the less secure side.

So if your desire to not "downgrade" your router is for security reasons, your laptop router project will be the security hole you're afraid of, at least for the packets being routed and if your laptop can be compromised, the entire traffic can be had.

---

### Post by Stonecold1995 on 2012-10-22
So then is there a way to use a laptop to boost the signal strength of an unsecured hotspot and make its range longer?

---

