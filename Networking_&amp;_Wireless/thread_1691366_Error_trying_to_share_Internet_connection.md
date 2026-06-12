---
title: "Error trying to share Internet connection"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by frisket on 2011-02-19
In the documentation at [https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29) it says

> Note: To clarify the above example here is an example configuration that will work - * 1. You are already connected to the internet using your wireless on port wlan0 * 2. The ethernet port eth0 is connected to the PC that needs to share your internet connection (or you could wire eth0 to a router for multiple machines) 

I am trying to do precisely this, with my laptop aready connected to the internet via my HTC Hero on port usb0, and the router needing to share the connection plugged into the laptop's port eth0. Port eth0 is set to "Shared" as the doc describes.

The router in question is an old WiFlyer pocket AP, which has a fixed and unchangeable IP address on its wired port of 192.168.7.77. What happens is that when I plug it into the laptop's eth0, NetworkManager pops up the "eth0 Connected" message...and then "Disconnected"...and then "Connected"...and then "Disconnected"...etc.

I want to be able to share my cellphone's Internet connection through the laptop and out into the WiFlyer so that others can get a wireless connection in a location that has no other form of connectivity.

[Rooting the Hero and making it an AP won't work: it can't run Froyo and it can't broadcast wireless.]

---

### Post by slooksterpsv on 2011-02-19
> **frisket said:**
> ...

The router in question is an old WiFlyer pocket AP, which has a fixed and unchangeable IP address on its wired port of 192.168.7.77. What happens is that when I plug it into the laptop's eth0, NetworkManager pops up the "eth0 Connected" message...and then "Disconnected"...and then "Connected"...and then "Disconnected"...etc.

...

Have you tried a different Ethernet port (if it has one)? I can't find any backside pictures of the WiFlyer pocket AP. Also try powercycling it, and if you have a reset button, try resetting it. Otherwise the WiFlyer could be bad. Or your ethernet is bad on the computer. Or both or a bad cable.

---

### Post by frisket on 2011-02-19
> **slooksterpsv said:**
> Have you tried a different Ethernet port (if it has one)? I can't find any backside pictures of the WiFlyer pocket AP.

The backside goes:
RJ11/phone, RJ45/"Internet", RJ45/(LAN icon), Power

I'm using the RJ45 socket labelled "Internet" which is where it expects to get its connection from when in LAN mode (as opposed to Phone mode: it has a dialer which can connect to a POTS dialup provider, and then rebroadcast the connection wirelessly ;-) The socket with the LAN icon is for when you want to use it as a plain ol' router, all wired.

> Also try powercycling it, and if you have a reset button, try resetting it. Otherwise the WiFlyer could be bad. Or your ethernet is bad on the computer. Or both or a bad cable.

Reset/Power has no effect. It's working perfectly: if I plug it straight into my home LAN, it connects and broadcasts its wifi just fine.

It's the NetworkManager that is messing things up, as far as I can see, because I have misunderstood something key and critical which the doc fails to mention (probably because it's so blindingly obvious to the authors that they felt it didn't need mentioning :-)

---

### Post by slooksterpsv on 2011-02-19
The Internet connection of it may require a patch cable. It's different from a regular Cat5 or Cat5e cable.

---

### Post by frisket on 2011-02-20
> **slooksterpsv said:**
> The Internet connection of it may require a patch cable. It's different from a regular Cat5 or Cat5e cable.

I'm using one...

---

### Post by frisket on 2011-02-21
Fixed. It turned out that 10.4 appears to have installed both dnsmasq *and* dnsmasq-base by default, so dnsmasq had to be removed and masquerading enabled manually. I have updated the wiki at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) to reflect this. Thanks for all the suggestions.

---

### Post by slooksterpsv on 2011-02-21
> **frisket said:**
> Fixed. It turned out that 10.4 appears to have installed both dnsmasq *and* dnsmasq-base by default, so dnsmasq had to be removed and masquerading enabled manually. I have updated the wiki at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) to reflect this. Thanks for all the suggestions.

I would not have even thought of that, congrats =D

---

