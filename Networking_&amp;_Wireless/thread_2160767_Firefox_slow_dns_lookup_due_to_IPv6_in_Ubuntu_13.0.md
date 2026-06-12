---
title: "Firefox slow dns lookup due to IPv6 in Ubuntu 13.04"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by ivlevkir on 2013-07-08
Just installed a fresh copy of Ubuntu 13.04 64 and ran into a very strange problem. Chrome is working fine but Firefox 22 sometimes connects to sites very slow. It can take around 10 seconds before Firefox starts to load something(I can see something like 'connecting to' or look up).
I actually found out how to fix it. Just went to about:config and set network.dns.disableIPv6 to true and Firefox started loading pages very fast
But my question is what's changed since Ubuntu 12.10. In my Ubuntu 12.10 network.dns.disableIPv6 is set to false and Firefox works properly.

---

### Post by praseodym on 2013-07-08
Check in the network-manager settings if IPv6 is on "Ignore"

---

### Post by ivlevkir on 2013-07-08
> **praseodym said:**
> Check in the network-manager settings if IPv6 is on "Ignore"

Sorry how do I launch network-manager? I don't seem to have a program named 'network-manager'.

---

### Post by praseodym on 2013-07-08
The "radar" icon in the top panel.

---

### Post by ivlevkir on 2013-07-08
> **praseodym said:**
> The "radar" icon in the top panel.
IPv6 is set to automatic.

---

### Post by praseodym on 2013-07-08
Try to "ignore" it.

---

### Post by ivlevkir on 2013-07-08
> **praseodym said:**
> Try to "ignore" it.
Thanks it actually helps but my question why it's changed now. In Ubuntu 12.10 it is set to automatic and Firefox works perfectly.

---

