---
title: "What's wrong with my ping?"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by sagex24 on 2009-06-20
[IMG]http://www.speedtest.net/result/499723242.png[/IMG]

Everything else about my connection seems pretty great, but I don't understand why my ping is so high?   Anything that I could do to lower it.  The main reason I am worrying about this is for xbox though, so will it probably already be lower on the xbox with ports forwarded, than this ubuntu laptop with a strict firewall?

---

### Post by Brandon Williams on 2009-06-20
What gives you the idea that 59ms is a bad ping score? In my experience, 59ms is relatively low, and does not indicate an OS level problem. What score are you expecting?

To give you a reference point, I live in Boston. If I use [www.speedtest.net](www.speedtest.net) to check my connectivity, I get a 43ms ping score to New York but 75ms to Clifton, NJ. Both are reasonable, given that I'm pinging within the same region of the country. However, it's also clear that something about the network path between me and the server in Clifton, NJ is adding 30ms of latency to the round trip time. I sometimes see differences that big when pinging two Boston-based machines on different ISPs.

Now, if I were running the same test from multiple machines on my network and seeing very different scores, _then_ I might look at the machine with the bad scores and try to figure out what's wrong with it.

So, have you run your ping tests from different machines on your local network? And have you run the same tests to servers on different ISPs but in the geographic area?

I assume that you're concerned about this for gaming. The only way to figure out what your effective ping score is for the game in question is to ping the gaming server itself. The ping scores you get from [www.speedtest.net](www.speedtest.net) are a useful general reference, but won't tell you a lot about the latency you'll get while palying a specific game.

---

### Post by lloyd_b on 2009-06-20
Ping time is primarily dependent on the number of "hops" (number of routers passed through) between you and the target.  How large this number is depends on who your ISP is, who the ISP of the target is, and of course, where the two of you are located.

Just for comparison, I get 79ms ping times using the Speed Test server here in Tucson, but 59 ms against the server in Phoenix, and 50ms against the server in Los Angeles...

Because these times are primarily a result of "network topology" (the way the network is organized), there is pretty much nothing you can do about your ping time.  Having or not having a firewall will make no detectable difference (the amount of time firewall processing would add to packets would be hard to measure in *microseconds*, let alone milliseconds...)

Lloyd B.

---

