---
title: "Wifi hotspot Ubuntu 11.10"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by mitasol on 2012-02-25
So I have installed Ubuntu 11.10 on an HP DV6 laptop and want to  setup a wifi hotspot so my Motorola Xoom can access the internet. I have  had this running under Windows 7 using a utility called Connectify.
 I have gone to System Settings/Network/Wireless Network and clicked  on Start Hotspot – it starts, shows connected, and is listed in the network list when I  click on the icon in the top bar but no devices can find it. Eventually after a few minutes it disconnects.


 Any ideas?

---

### Post by Darkness Des on 2012-02-25
I'm not 100% sure about this, but I believe that Ubuntu has to be connected to the internet through a wired connection for the hot spot to work.

---

### Post by mitasol on 2012-02-25
> **Darkness Des said:**
> I'm not 100% sure about this, but I believe that Ubuntu has to be connected to the internet through a wired connection for the hot spot to work.


oops, sorry missed that bit, the DV6 is connected to the internet via a wired connection.

---

### Post by Darkness Des on 2012-02-26
Hmmm... Personally, I haven't gotten the hotspot to work, but that's probably just because of my wireless card. Check around and see if yours will work. I'm not really up to speed on the details of the hotspot as I switched over to Kubuntu a long time ago, but last I recall it depended on certain functionality.

---

### Post by mitasol on 2012-02-28
It seems that I have to use hostapd to enable this functionality - now to try and nut out the conf file for this :)

---

