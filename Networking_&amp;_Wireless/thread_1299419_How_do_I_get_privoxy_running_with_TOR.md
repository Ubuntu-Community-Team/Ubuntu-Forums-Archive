---
title: "How do I get privoxy running with TOR??"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by ucal on 2009-10-23
Okay, I have privoxy up, and seemingly running (the process shows up in process manager, but there's no window or anything to show it.  The config file from the TOR site is being used.  But when I check my IP with TOR on and with TOR off, it's unchanged.  I'm using [http://www.whatismyip.com/](http://www.whatismyip.com/) to check my IP.  

Any ideas on what's up?  I'm using torbutton as well.

---

### Post by ucal on 2009-10-23
Ran TOR in terminal (privoxy already running, it only shows errors about a logfile.
```
Oct 23 22:22:20.648 [notice] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Oct 23 22:22:20.650 [notice] Initialized libevent version 1.3e using method epoll. Good.
Oct 23 22:22:20.650 [notice] Opening Socks listener on 127.0.0.1:9050
Oct 23 22:22:20.650 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Oct 23 22:22:20.650 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Oct 23 22:22:20.650 [err] Reading config failed--see warnings above.

```

So I guess it's a TOR related problem, though I don't have any idea how to fix it.

---

### Post by ucal on 2009-10-24
Okay, so running tor in the terminal and then checking the system monitor reveals that those errors it's experiencing must be fatal errors, cause a tor process isn't showing up after them.  

Also, is there any way I can get the title changed?  I don't think privoxy is the problem anymore.

EDIT:  Managed to get TOR running properly with this post:

> **oracle2b said:**
> try killing tor with this:

sudo killall tor

Start tor again


Then, restart privoxy and polipo

sudo /etc/init.d/privoxy force-reload && /etc/init.d/polipo restart


But now upon testing there are still some issues:  It can't seem to make connections upon reviewing the output in the terminal.  It waits for 120 seconds then gives up.  IP address is regularly changed though, so we're halfway there :D

---

