---
title: "Weird problem with Audacious on fresh install of KUbuntu 20.04.2"
date: 2021-06-05
forum: Multimedia Software
---

### Post by LVDave on 2021-06-05
I use the Audacious music player to listen to a favorite music stream. It seems that on this new machine, with a new install of Kubuntu 20.04.2 that I cannot use the
domain name for the stream on Audacious. The stream url is [http://bestnewage.net:8000](http://bestnewage.net:8000) and resolves to 50.115.166.111:8000. If I enter "http://bestnewage.net:8000" in Audacious's "Open URL", the connection times out. I can reach the stream IF I use "http://50.115.166.111:8000". With a little judicious and quick use of "watch -n1 netstat -lna" I see an attempted connection to 3.223.115.185:8000, which appears to be an Amazon data services address in Northern Virginia. A ping of "bestnewage.net" returns 50.115.166.111. Apparently this weirdness is limited to Audacious, as I tried connecting to the stream url on the Deadbeef player and there the stream url works fine. I've tried purging Audacious and then reinstalling it, no change. This has me stumped... Any ideas??

Thanks
Dave

---

