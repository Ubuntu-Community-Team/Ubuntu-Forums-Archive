---
title: "Network usage constant"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by quintok on 2010-01-05
My wireless usb network adapter is constantly using ~100bytes/s even when there is nothing I can think of that needs to talk to the internet.  Is there a way to find out what programs are using the internet?

---

### Post by iponeverything on 2010-01-05
An easy to see what is going on would to use wireshark.

```
sudo wireshark
```

You might need to install it first with the package manager.

---

### Post by chewearn on 2010-01-05
I could be wrong, but there is always a small amount of traffic in a wireless network, basically to maintain connectivity.  For instance, there is the beacon frame:
[http://en.wikipedia.org/wiki/Beacon_frame](http://en.wikipedia.org/wiki/Beacon_frame)

---

