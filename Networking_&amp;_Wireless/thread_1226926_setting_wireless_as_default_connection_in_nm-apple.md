---
title: "setting wireless as default connection in nm-applet"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by Eraemaajaervi on 2009-07-30
hi,

I got a little home server so which I'm locally connecting with a crossover cord using my ethernet connection. Additional I'm connected to my wireless network.
It's possible to be connected to both at the same time, but the ethernet connection is set as default and as a result I can't access the Internet while being connected via ethernet.

how do I change the default connection preferences in ubuntu's default mn-applet?

ps: wicd is not an option because it doesn't support multiple connections

---

### Post by superprash2003 on 2009-07-30
hope this helps [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by thuynn on 2009-08-01
Hi Eraemaajaervi,
I'm a newbie and I still can not access the wireless network from my laptop. (In WinXP, I can access it normally, so I think the network is ok, the problem may be caused I have missed something). Please guide me how to access wireless network. My laptop is an Asus K40IJ T6400 and this is some information about it:

Intel Core 2 DuoT6400 (2x2.0Ghz, 800MHz FSB, 2MB L2 Cache)45nm /14.0" HD (1366x76 LED backlight Splendid /2GB DDR2/ 8001 x SO-DIMM socket up to 4GB /160GB5400 rpmSATAIntel® GMA 4500MHD /8X Super Multi DVDRW Double Layer /802.11 b/g/n6 Cell(2.3kg)/ Linux/China /Pin ~6hrs (SHE Technology) , Ice cool , Keyboard Chocolate , Loa AltecLancing hi&#7879;u &#7913;ng SRS ,1.3MP Camera , Card reader

Thank you in advance :D

---

### Post by Eraemaajaervi on 2009-08-03
> **superprash2003 said:**
> hope this helps [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

thanks, will try it as soon as I get access to my homesever again 

@thuynn: may be this can help you
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

---

### Post by Eraemaajaervi on 2009-08-10
well, couldn't be simpler...

for all fellow users: 
in the connection editor of your wired connection go to "Routes" and check "Use this connection only for resources on its network"
 
=)

---

### Post by firefly2442 on 2009-11-30
> **Eraemaajaervi said:**
> well, couldn't be simpler...

for all fellow users: 
in the connection editor of your wired connection go to "Routes" and check "Use this connection only for resources on its network"
 
=)

Thanks!  I was looking for this feature. :)

---

