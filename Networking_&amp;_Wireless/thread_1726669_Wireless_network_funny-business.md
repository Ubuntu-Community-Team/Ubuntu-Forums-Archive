---
title: "Wireless network funny-business"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by confubar on 2011-04-11
Normally I connect to a wireless network by clicking the  network icon, clicking the desired network.  The system does not connect automatically.
But when I visit my mom, as soon as I boot up my laptop, the thing begins automatically trying to connect to a neighbor's wireless network. Oddly, this is the network that my laptop (Dell ubuntu) first connected to (to my surprise) the first time I booted up. I have done a clean install of 10.04 since then..... wtf is going on:roll:

---

### Post by adempewolff on 2011-04-11
A lot of home routers use the same name (ie: linksys, netgear, etc.)  chances are its not some ghost from a previous image of your computer, but rather you had successfully connected to another network on this install of ubuntu and that network had the same ssid (probably same exact brand/model of router and everyone just uses the default settings).

Just add your mom's network and move it above the neighbors in your network list in network manager. :)

edit: ubuntu by default will connect automatically again to any network (or network with the same ssid and settings) that it has connected to successfully before.

---

### Post by confubar on 2011-04-11
My system does  !NOT!!!! connect automatically to networks it has connected to before. It does not connect automatically to my own network at home. And, I have not connected to all that many networks... I count 7 connected to and 5 detected but not used.
My mom does not use a wireless network.

---

### Post by bkratz on 2011-04-11
> **confubar said:**
> My system does  !NOT!!!! connect automatically to networks it has connected to before. It does not connect automatically to my own network at home. And, I have not connected to all that many networks... I count 7 connected to and 5 detected but not used.
My mom does not use a wireless network.



If you want to autoconnect, simply right click on network manager and go to edit wireless then put a checkmark in connect automatically. If this is what you want.

---

### Post by Iowan on 2011-04-11
My laptop has individual settings for different wireless networks - I can enable it to connect to the library automatically, but not to my neighbor's (which it tried to do - after it connected once.)

---

### Post by confubar on 2011-04-12
Aha, and thanks folks. I checked the connections listed in network manager, edit , and, well well, that mynetwork was the only one with the automatic connect turned off. I deleted momsneighbors. But I am still wondering  why momsneighbors network connected automatically, since my system hadn't seen it since the clean install.

---

### Post by SeijiSensei on 2011-04-12
> **confubar said:**
> Aha, and thanks folks. I checked the connections listed in network manager, edit , and, well well, that mynetwork was the only one with the automatic connect turned off. I deleted momsneighbors. But I am still wondering  why momsneighbors network connected automatically, since my system hadn't seen it since the clean install.

Another good question is whether the neighbors' network required a password.  If not, and you and your mom are on good terms with them, you might suggest that they implement WPA2 or (the much less secure) WEP to keep nosy outsiders from browsing their computers and potential criminals from exploiting their network.

---

### Post by josephmills on 2011-04-12
> **seijisensei said:**
> another good question is whether the neighbors' network required a password.  If not, and you and your mom are on good terms with them, you might suggest that they implement wpa2 or (the much less secure) wep to keep nosy outsiders from browsing their computers and potential criminals from exploiting their network.
+1

---

