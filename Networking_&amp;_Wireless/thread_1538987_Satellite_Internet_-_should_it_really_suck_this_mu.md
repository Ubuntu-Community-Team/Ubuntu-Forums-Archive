---
title: "Satellite Internet - should it really suck this much?"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by WinstonChurchill on 2010-07-26
So, I'm staying out at a friend's house in the middle of nowhere, and she's been complaining about how slow her satellite internet has been of late. So I decided I'd take a look...

If I ping my server at home, I end up with these statistics:
```

// @ 1 ping probe per second
60 packets transmitted, 36 received, 40% packet loss, time 59172ms
rtt min/avg/max/mdev = 639.915/799.882/1209.119/104.763 ms, pipe 2

```Compare that to driving 70 down the highway tethered to my cell phone: I  see latencies in the 3000's and out-of-order packets, but practically  none  get dropped.

If you ramp it up to 5 ping probes a second, the loss climbs to around 75%. To me, that seems quite excessive... The interesting thing is that all the packet loss seems to be occurring on download traffic - I set up tcpdump to monitor the packets on my server during the ping test, and all but 1 of the pings to got there, so the other 25 lost packets wondered astray on the return trip. I tested it with the client directly connected to the modem (it had the public IP), so I'm quite certain that it's the satellite link itself that is the issue here. I've attached the complete logs from the ping test for your enjoyment.

Of course, TCP corrects for the loss of packets, but with a latency of 800ms, resending packets takes a significant amount of time, not to mention services like DNS that just wait for a timeout to elapse (which is usually way too long). It can take 15 seconds to load a webpage.

So I guess my question is, should it be this bad? I know satellite is generally terrible, but I didn't expect to see such rampant packet droppage. Any thoughts?

---

### Post by iponeverything on 2010-07-26
No it should not be that bad. 40% packet loss borders on unusable. It should be close to 0% -- the latency also seem excessive, even for the packets going to space and back.

Check signal quality and re-align the dish if necessary.
Check that all the connections are good and also water tight.
Check the dish for obstructions and deformations. 
Check to see that nothing has moved into the line of sight.
Check the pole and dish mounts to make nothing has come loose that allows the dish to move.

---

