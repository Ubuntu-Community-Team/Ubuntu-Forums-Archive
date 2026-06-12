---
title: "Internet stops working when torrent app is active"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by 98cwitr on 2010-04-18
This holds true in Transmission and NOT in Vuze. UPnP is enabled, ports are randomized and open each time. Pings to outside still work fine, but I cannot browse to websites (404 errors) when the app is running. Any ideas? I'm stumped, is Transmission locking all other in bound traffic/ports except the one it wants to use?

---

### Post by donato roque on 2010-04-18
Hi,
I've been puzzled by this same 'phenomenon' for two weeks myself.  The symptoms are the same but they coincidentally started when my isp 'upgraded'.  So I start transmission and network monitor one after the other to measure my total upload and every time the symptoms appear it's the same total upload number.  Which leads me to conclude that my isp is capping my upload which impacts browsing first and most and then finally bittorrent.

Bittorrent connections are not terminated at least not right away.  But every time I open a browser--'server not found'.

I reset my lan, that's what I do, gives best result.  I figured it resets the counter or something.

---

### Post by 98cwitr on 2010-04-19
how does upload capping affect browsing? I mean honestly all the overhead would be hitting the ISPs DNS, and the requested URL hitting the host, download would be all the way back, containing all the web content, right? Seems really light to me...even if you're on a 200k upload or something (that would be me :D 30M down and 200k up). I close Transmission and it's back flying again. 

When Vuze is open my internet is pretty slow, but not "down" like in Transmission. I always blame the ISP for everything though :) Time Warner cable blows....

---

