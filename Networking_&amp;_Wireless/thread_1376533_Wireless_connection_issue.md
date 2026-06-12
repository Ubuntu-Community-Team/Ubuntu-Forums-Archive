---
title: "Wireless connection issue"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by arluijen on 2010-01-09
This one is troubling me for some time.

I have a cisco linksys wireless adapter (WUSB600n) which, most of the time, great when booting up. But....mostly after some time (1min- 1hr.) it disconnects. When checking the status I can see some of the networks around me, including mine. But selecting it doesn't do anything.

I searched the forums and tried:

sudo dhclient

and
sudo /etc/init.d/networking restart

But still no connection; the only thing that helps is rebooting.
Any sugestions would be helpful.

---

### Post by ushills on 2010-01-09
If you are using 9.10  then this seems to be a fairly common issue.  Wireless seems really unreliable in 9.10, 9.04 is rock solid.

---

### Post by arluijen on 2010-01-09
Thanks,
but how to solve it ?

Furthermore: this also was the case in 9.04, though I could most of the times reconnect by clicking the network symbol and selecting my network again...

By the way, ronning sudo dhclient after a while results in: 
No DHCPOFFERS received.

I'll query that too.

---

