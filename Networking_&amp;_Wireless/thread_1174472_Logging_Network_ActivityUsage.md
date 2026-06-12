---
title: "Logging Network Activity/Usage"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by Nate9009 on 2009-05-31
Earlier today, I had a guy park his car across the street from my house, pull out a laptop, and (presumably) use my wireless network.  I'm fairly certian because after I noticed him, I went and turned off my router and the guy drove away.  I turned it back on once he left, only to see him parked in the same spot 10 minutes later with his laptop out again.

Does anyone know anything that logs network usage?  I might just be paranoid, but the guy did look like he was up to no good.  I doubt there is any program installed by default, but I would like to have something installed in case this happens again.

Any help is greatly appreciated!  Thanks very much!

P.S I'm running Ubuntu Gutsy and using a open wireless network on a Linksys WRT54G router. (I know lots of people say this is terrible, but WEP gave me trouble in the past and WPA is just as crazy).

---

### Post by superprash2003 on 2009-05-31
i think if you use dd-wrt on your router it would perform such functions.. but there is no point in knowing how much that person is using , instead try stopping that person from using it , the best way to do it , is to use WEP or WPA , i understand WPA can be difficult at times to implement on ubuntu , but WEP should work well and thats good enough , unless that person would try cracking it using aircrack etc . THats only if he is that desperate to get into your network :)
  So try setting up WEP one more time , and try fixing that instead..

---

### Post by wadesmart on 2009-05-31
My $.02....

... set up mac filtering. Unless they are really willing to go the extra distance, that stops them right there.

If you feel the need, keep security set up. 

Turn off your ESSID. 

Change the number of IP addresses available to the number of computers in your home. For example, if you have computers, then allow ONLY 2 ip's. 

I use DD-WRT on a linksys wrt54gl and it has bandwidth monitoring. 

Bandwidth monitoring through the OS wont help you any if you are not running a server as the bandwidth cant be tracked back to the net.

Wade

---

