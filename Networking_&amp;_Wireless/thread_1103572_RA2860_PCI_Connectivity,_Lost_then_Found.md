---
title: "RA2860 PCI: Connectivity, Lost then Found"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by TBerk on 2009-03-22
I had been toddling along with an Airlink101 300N (draft 'N' but connecting on a 80211g network.)

Well, a few days ago I ran either Update Manager and/or Synaptic Package Manager and it updated a few items; the only ones I recollected were the Open Office update that downloaded.

Well, the next day I was unable to connect via wireless but could see the same local networks I always do, including my own.

(btw I'm running wicd ver 1.5.9 and Ubuntu 8.10, the network is WPA2.)

In trying to understand what was going on I looked a the ra0 interface and in wicd it showed it was using the wext driver.

I was able to get past the failed authentication by choosing the ralink Legacy driver instead.

Poof- connection works now.  Lazy bones that I am I didn't do any command line verification/checking prior to 'fixing' the problem.

If I'm feeling brave enough later today I'll toggle back to the wext driver and see what happens.


TBerk

---

### Post by TBerk on 2009-03-23
Then LOST again...

So far this is what I have found to add to the initial post:

- Administrator: Network Tools shows ra0 only having IPv6 when I'm using the default 'wext' driver. But if I set the driver to use the ralink legacy driver I get an new entry in Network Tools; and it has both IPv6 and IPv4. 

If I dual boot back to WinXP I need to turn the (wifi) radio Off and back On again to get it to work.

My next step is to poke at the config files via a terminal window and look for the obvious, then reinstall the rt2860 drivers and (possibly) wicd from scratch.


TBerk

---

### Post by TBerk on 2009-03-27
Since I began diagnosing this;


Latest news: Booted from the beta 9.04 CD and everything just works.

I'm likely going to let **this** thread die off. (also)


TBerk

---

