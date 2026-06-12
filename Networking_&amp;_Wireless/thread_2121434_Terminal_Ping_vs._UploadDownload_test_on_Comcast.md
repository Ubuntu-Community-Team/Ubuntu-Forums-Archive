---
title: "Terminal Ping vs. Upload/Download test on Comcast"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by idcrewdawg on 2013-03-01
I'm having doubts about our internet speed. After a discussing my concern with my cable provider they sent me to the site speedtest.net. When I use the site, I get vastly different results than what I would get with a ping test to the same URL through terminal.

My website result: [http://www.speedtest.net/result/2544057436.png](http://www.speedtest.net/result/2544057436.png)[ATTACH=CONFIG]239605[/ATTACH]
My ping result: -- speedtest.net ping statistics 4 packets transmitted, 4 received, 0% packet loss, time 3004ms rtt min/avg/max/mdev = 57.990/59.347/61.121/1.133 ms

The way I read the two results tell me I'm getting vastly different results. So I'm not trusting the site, as that's the site that Comcast referred me to for the test. If I use a site they don't recommend I get results closer to what my terminal ping results are.

My question. Are ping results done at terminal reflecting my upload/download speeds? The comcast rep tells me they are different, but I don't trust them, as Comcast has a horrible reputation in that regard.

---

### Post by pierceTN on 2013-03-01
Your upload/download speeds are different than your ping. 
Your ping is how many milliseconds it takes for the data packet to hit a defined server.  So your ping is not always going to be the same.
The ping on the speedtest.net said 15 ms, you should be able to ping the same server that the speedtest site used in a terminal, and get very close results.
Speed (usually measured in Mbps) is *how much data* can be transmitted per second
Ping is *how fast* data can get there. (in ms's)

so, for a fair test you would have to ping the same server that the speedtest is using.

hope that help,


-Pierce

---

### Post by idcrewdawg on 2013-03-01
Thanks! That answers my question!

---

