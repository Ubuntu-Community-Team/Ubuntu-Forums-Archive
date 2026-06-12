---
title: "FritzCard ISDN PCMCIA problems"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by jede on 2006-05-10
Hi,

I've been using successfully a FritzCard ISDN PCMCIA on my laptop with Ubuntu Breezy. After I upgraded to Dapper Drake the ISDN device has not been working anymore, the capiutils package seemed to be broken.
Have other people had the same problems and maybe solutions?

I also installed Ubuntu Dapper from scratch on another laptop and the FritzCard ISDN PCMCIA has not been working there too. I've followed the instructions from the ISDN Wiki page ([https://wiki.ubuntu.com/IsdnHowto)](https://wiki.ubuntu.com/IsdnHowto)), but this has not worked.
The strange thing on Dapper is that since I installed the ISDN packages the system tries to connect immediately via ISDN to internet. So the ethernet network device does not work then anymore (and ISDN also not). I need to start "/etc/init.d/networking restart" and the ethernet works again. 
How can I configure that ISDN dialup will only be started manually ?

Thanks,
Stefan

---

