---
title: "Why would this update 'break' my wifi connection?"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by TBerk on 2009-03-24
I updated (via Synaptics) the following files/components:

> Commit Log for Fri Mar 20 22:20:11 2009

Upgraded the following packages:
libcolamd-3.2.0 (1:3.2.0-1ubuntu1~intrepid1) to 1:3.2.0-4
lp-solve (5.5.0.13-3ubuntu1~intrepid1) to 5.5.0.13-4
openoffice.org-base-core (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-calc (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-common (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-core (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-draw (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-emailmerge (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-gnome (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-gtk (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-impress (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-math (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-style-human (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
openoffice.org-writer (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
python-uno (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
ttf-opensymbol (1:3.0.1-1ubuntu1~intrepid1) to 1:3.0.1-7ubuntu1~intrepid1
uno-libs3 (1.4.1+OOo3.0.1-1ubuntu1~intrepid1) to 1.4.1+OOo3.0.1-7ubuntu1~intrepid1
ure (1.4.1+OOo3.0.1-1ubuntu1~intrepid1) to 1.4.1+OOo3.0.1-7ubuntu1~intrepid1



The next time I rebooted into Ubuntu I couldn't connect to the router, I toggled back and forth between using a wext driver and a ralink legacy driver (supporting an rt2860 wifi pci card).

My temp fix was just that, but what I'm really trying to understand is, is there anything in the list of files posted above that shed any light on this trouble?

Thx,
TBerk

---

### Post by TBerk on 2009-03-27
I have found that I can run ```
 $sudo iwconfig ra
``` and/or I can run ```
 $sudo dhclient3 ra0
``` and/or then I can restart the Network manually and I connect to my router and get an IP address/lease.

Since then- 


Latest news: Booted from the beta 9.04 CD and everything just works.

I'm likely going to let **this** thread die off. (too)


TBerk

---

