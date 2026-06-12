---
title: "Wifi will only connect at 1mbit?"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by tez1982 on 2009-01-02
Advent 6000 with RALink 6164 miniPCI Wifi Card

Where ever I go my wireless only seems to connect at 1mbit? I've had a good search around but can't seem to find the problem? Everything else works fine? 

Anyone got any good suggestions?

Thanks!

---

### Post by tez1982 on 2009-01-02
Oh forgot to mention I'm running 8.10

---

### Post by frenkel on 2009-01-02
It's a bug in the driver. You should be able to run something like:
```
iwconfig wlan0 set rate 54M
```
to have it working at normal speed.

---

### Post by Rob_H on 2009-01-02
If that doesn't help and you're in a heavily populated area, you might try changing the wireless channel used by your access point. I used to have trouble with slow/spotty connections and that fixed it for me.

---

### Post by tez1982 on 2009-01-02
tried iwconfig wlan0 set rate 54M

then remembered my wireless is ra0 for some reason.

tried 
iwconfig ra0 set rate 54M

and it came back
iwconfig: unknown command "set"

Any other ideas - thanks for the help so far

---

### Post by tez1982 on 2009-01-02
got it

sudo iwconfig ra0 rate 54M

then restarted the network and worked brilliantly! Also the signal strength has nearly doubled (laptop has not moved!)

Thanks again!

---

### Post by tez1982 on 2009-01-02
quick update. Every time I restart my laptop it loses this setting and reverts back to 1mbit, is there anyway to make the change permenant?

---

### Post by Blis on 2009-01-19
Hi there.

I had the same issue, and I followed the instructions from here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515/comments/49](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515/comments/49)

nm-applet still shows 1M, but iwconfig shows 54.  Test with SpeedTest.net confirms it.

Good luck.

BB

---

