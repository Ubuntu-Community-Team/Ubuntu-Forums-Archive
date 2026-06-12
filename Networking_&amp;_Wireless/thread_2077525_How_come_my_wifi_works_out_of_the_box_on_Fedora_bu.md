---
title: "How come my wifi works out of the box on Fedora but not Ubuntu?"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by Moose on 2012-10-28
I am a Fedorian at heart. But i like the simplicity of Ubuntu and want to switch. I tried it from live cd and it wouldn't connect to my wifi. When i used Fedora 16 i had no problems connecting to the internet. But whenever i try on Ubuntu 11.10 it tries to connect about 5 times and then it says "Wifi disconnected" and tries to connect again?
 
My wifi adapter is Ralink RT5390 Wireless b/g/n Adapter. I tried to install the linux version of these drivers but it was too complicated and i gave up pretty quickly.. Anyone got any ideas?
 
Thanks

---

### Post by dniMretsaM on 2012-10-28
I think I read somewhere that a driver for this card is included in 12.04's kernel. Not sure, though. You could try installing 12.04 (or 12.10) instead of 11.10. There is also [this]("http://www.techytalk.info/ubuntu-ppas/ralink-wireless/").

---

### Post by Moose on 2012-10-28
Thanks man, i will try that solution thats on techytalk on my Ubuntu 11.10. If that for some reason won't work i will upgrade.

---

### Post by gururug on 2012-10-28
Yep, driver most likely compiled into kernel or included in Fedora package as loadable module.

Either use a newer/different OS, a different card, or go the hard route;

-Find the chipset
-Find the source
-Compile a module assuming you can satisfy dependancies ( i've always had alot of trouble with this )...requires in depth Linux skills usually. 


Keep googling the model/os and driver...

i.e. Search "RALINKXXX Ubuntu 11 Driver"......you may run across someone who has found a nice solution or is willing to upload a precompiled driver module.

---

