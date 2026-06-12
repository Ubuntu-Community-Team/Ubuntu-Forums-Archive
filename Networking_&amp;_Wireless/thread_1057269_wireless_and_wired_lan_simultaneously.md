---
title: "wireless and wired lan simultaneously?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by parkerault on 2009-02-01
I have my wireless and wired connections working, but what I'd like to do is use the wireless for internet access and the wired connection just for LAN.  I was able to do this in windows by giving the wired connection a static ip and no gateway, which forces all external ip requests to use the wireless gateway.  When I attempt to do the same thing in kubuntu, no connection is made.  Any help?

(What I really need is a wireless bridge, but until I scratch up a few hundred bucks I'll have to figure this one out) ;)

---

### Post by nixscripter on 2009-02-03
That's not too hard to set up. But first, please post the output of these two commands (in ```
 forum tags):

[code]ifconfig -a
``` and ```
route
```

---

