---
title: "Really slow wireless internet Ubuntu 12.04 LTS : Comcast Xfinity"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by cyclingchap on 2013-04-03
OK, so I am running Ubuntu 12.04 LTS on a Toshiba Satellite laptop. Until recently I had no problems with wireless connectivity and download speeds; at my old house or in cafes etc..

However, after moving to California and setting up Comcast Xfinity broadband in my home I've had TERRIBLE wireless download/upload speeds. Very intermittent, often down completely.

Testing on Windoze 7 showed it was not the ISP, I was getting good downoad speeds in Explorer. But in Ubuntu 12.04 with firefox or chrome thhings were terrible.

I was going nuts. I tried deactivating ipv6, but that didn't solve the problem. Then I came across this : [http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html](http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html) and it totally worked.

Basically install WiCD network manager in Ubuntu software center, deactivate the default network manager, and connect with WiCD (you'll have to play with the settings a bit to connect). Wehey, superfast internet is back!!

There is definitely some kind of bug with the default wireless network manager, coupled with my combination of hardware/wifi router?

Anyway, if like me you're pulling your hair out over slow wireless in Ubuntu 12.04, try the above remedy.

---

