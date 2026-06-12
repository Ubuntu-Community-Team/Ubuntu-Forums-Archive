---
title: "Network Manager vs. WICD"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by Bradley Rowe on 2011-04-19
Howdy,

I've been having this wireless problem using Network-Manager where my network was dropping and spontaneously reconnecting every 11 seconds.  After troubleshooting for quite a while, I decided to give WICD a shot.

Well, things aren't fixed, but they certainly are different.  I find that the connection is much more consistent.  While there does seem to be intermittent dropping/reconnecting, it isn't happening every 11 seconds, usually going many hours between drops.  However, the connection quality is fairly consistently low, leading to fairly slow speeds.

So, here's some more information: when watching wireless status display on my DD-WRT router, I note that the signal strength behavior is quite different between Network-Manager and WICD.  With Network-Manager running, the signal-strength would oscillate widely between -30 and -70 dB.  In fact, the way I'd describe the pattern is that it would connect w/ a fairly strong signal, gradually decay, drop off the network entirely, and then repeat.  On the other hand, WICD just sits there at around -74 dB all the time.

I have no idea what's going on under the hood in either of these systems, so it impossible for me to know for certain why this behavior is occurring.  But, it seems like Network-Manager is spiking TX strength periodically (every 11 seconds) and then rolling it back until the connection is dropped, whereas WICD just leaves it where it is all the time, but is perhaps less finicky about signal quality.

At any rate, it would be really useful if someone had some thoughts they could share.  As things stand, neither of these situations are acceptable, but I'm at a loss as to what to do at this point.  I'd really love to just get one of these systems to transmit at a consistently high level so that this connection was useful.

Thanks for any insights.

Brad

---

### Post by matt_symes on 2011-04-19
Hi

Have you tried turning power saving off on your card if it has that ability ?

It has been known to cause frequent disconnections in certain cards/drivers.

```
sudo iwconfig wlan0 power off
```

The above assumes your wireless interface is wlan0. Enter password as usual.

Kind regards

---

### Post by Bradley Rowe on 2011-04-19
Hey Matt,

Thanks for the idea.  Unfortunately, that feature is not enabled in either the Network-Manager or WICD setup.  Alas.

I realize I haven't given much specific info in this thread (it's all in the other one I started about the incessant connect/reconnect on using Network-Manager).  If you think it would be helpful, I can repost it all here.  I'd love it if you could take a look at some of the specifics and flag anything suspicious.

Brad

> **matt_symes said:**
> Hi

Have you tried turning power saving off on your card if it has that ability ?



---

