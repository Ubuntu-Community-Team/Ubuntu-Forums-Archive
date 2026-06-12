---
title: "Wirelessly connecting your Ubuntu desktop with a Linksys Wireless Range Expander"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by heroofhyrule on 2010-09-30
After spending several months coming up with ideas (and ultimately failing), I have found the easiest and simplest way to connect your Ubuntu desktop (or laptop w/o a wireless adapter/card) to the Internet using only a Linksys Wireless Range Expander and an Ethernet cord.  

YOU WILL NEED:

[LIST]
[*]Linksys Wireless Range Expander (WRE54G)
[*]Ethernet cable
[*]Linksys wireless router (that is providing your home/office with wireless Internet)
[/LIST]
The WRE54G can be purchased online through various websites, including eBay.  They run anywhere between $10 and $40, but it's going to be cheaper than a USB Wireless Adapter (and no software needs to be installed, making it universal for most Linux distros).

HOW TO DO IT:

[LIST=1]
[*]Make sure your Linksys wireless router is fully operational (it is plugged into the modem and the wireless Internet is working properly).
[*]Turn on your Ubuntu rig and plug one end of the Ethernet cord into the Ethernet port of said rig.
[*]Plug the other end of the Ethernet cord into the front of the WRE54G.
[*]Plug the WRE54G into a wall outlet.
[*]You now have a (pseudo) hard-wired Internet connection to your Ubuntu rig.
[/LIST]
HOW IT WORKS:

[LIST]
[*]The WRE54G has an Ethernet port built in on the front of the unit so that one may connect a non-wireless machine to it.
[*]The WRE54G picks up the wireless signal coming from the wireless router, and not only amplifies it but duplicates it as well.
[*]Your Ubuntu rig is hard-wired to the WRE54G, which is connected to the router via a wireless connection, thus passing the connection from your router to your Ubuntu rig.
[/LIST]
TOUBLESHOOTING:

[LIST]
[*]If you do not get connected to the Internet right away, DON'T panic (this happened to me the first time).
[*]Wait a few minutes.  If there is a red flashing light on the WRE54G, push the "Connect" button on the right side of the device.  You should now have an Internet connection.
[*]If you still don't have an Internet connection and the red flashing light comes back, press the "Connect" button again and then make sure your network connection is set to "Auto eth0."
[*]If this fails as well, send me a message. :-D
[/LIST]

---

### Post by Miqueridosims on 2011-03-24
Here is my case:
I have just installed the same expander V2, I am able to connect in Windows and it works perfectly I can even reach signal in my further bedroom, however I cannot connect in Lubuntu, I have tried to connect using the static IP address, and then it seem fine, but again when I tried internet is not working.
 
any recomendation
 
Thanks.

---

