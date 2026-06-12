---
title: "2 connections to the internet..."
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by fychan on 2010-12-01
I have a 10.04 (64 bit) server sat behind a DSL router with a pix firewall, that is serving webpages etc fine on its external IP.

What I want to do is add a second internet connection via a different router & different pix firewall so that it will respond on a different IP - because the main DSL line has been somewhat flakey recently & I'd like a backup route to the server.

I don't even know if it's possible - but I'm guessing it's got something to do with routes & metrics - but I'm not clear on what those mean (complete newbie to networking, but not Ubuntu).

Description of network:
Current external DSL line - working fine.
DSL external IP address: 81.X.X.X
DSL pix f/w IP address:  10.0.0.2
Local server IP address: 10.0.1.1

Second ADSL line - I'd like my server to respond on
ADSL external IP address: 82.X.X.X
ADSL pix f/w IP address:  10.0.0.3
I have a second network card that's unused that I could configure for this.

Current routing table:
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.0.0.2        0.0.0.0         UG    100    0        0 eth0
```

Any help really would be greatly appreciated...

---

