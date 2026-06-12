---
title: "UDP works; TCP doesn't (until it does...)"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by SoftwareMaven on 2012-10-24
I have a lenovo thinkpad running Ubuntu 12.04 with odd network behavior. After I reboot, UDP networking behaves fine but TCP networking doesn't work at all.  After some amount of time (variable from two to 10 minutes), TCP networking will re-engage except HTTP and HTTP/S won't work.  After some further variable amount of time, HTTP and HTTP/S will re-engage.

What I have looked at so far:

1. There are no messages related to eth0 or networking in general in dmsg. Everything looks nominal.
2. Wireshark shows no TCP messages being generated if I e.g. "telnet [www.google.com](www.google.com) 80". DNS messages are fine.
3. My router logs show no connection coming from the machine when I do the above.
4. There are no proxies set. When things decide to work, I make no particular steps.

If I turn the wireless on and off, the network becomes happy.

Ideas?

---

