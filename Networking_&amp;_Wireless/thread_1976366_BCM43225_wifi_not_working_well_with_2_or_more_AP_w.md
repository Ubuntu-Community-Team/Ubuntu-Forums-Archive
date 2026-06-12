---
title: "BCM43225 wifi not working well with 2 or more AP with same SSID"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by joningi on 2012-05-08
I've got the BCM43225 wireless card and I've been experiencing  problems (sometimes) with my wireless connection. 
My University has APs all over with the same SSIDs and usually i have no problem connecting to them and using the internet on good speeds. But... for the past year, I've been in 2 separate rooms where I've had problems with the wifi internet on my Ubuntu. I've got a Windows partition too and the the wifi works flawlessly when I'm running windows. But when running ubuntu 11.10 at the same spot, I either, have VERY slow internet or the internet works for the first 30 seconds after connecting to the AP and then it doesn't.
I've been google-ing around and cannot find a similar problem to mine. I think this has something to do with that 2 AP may be covering the same space and my computer can't decide which one too choose...

I've tried:
- to disable the additional STA drivers, rebooting...doesn't work
- blacklisting brcmsmac (this is the normal driver shown in the wireless connection info when I'm connected with wifi), rebooted - doesn't work, i.e. no wifi only cable available 
- tried to reinstall the STA drivers, reboot... didn't work.

Any other Ideas? What could be wrong? This is def related to the driver, because the wifi works fine on windows....

p.s. I haven't experienced any problems with other normal routers, where only one router/AP with one SSID is available - Only at the University. Which is rather irritating!
Thanks in advance!


*************EDIT****************
Looks like the problem has been solved. I updated to Ubuntu 12.04 this morning and it works great! Thank god for the new upgrade!

---

