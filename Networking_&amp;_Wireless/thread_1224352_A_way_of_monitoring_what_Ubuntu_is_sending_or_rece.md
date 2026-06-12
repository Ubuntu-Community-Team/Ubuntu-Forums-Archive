---
title: "A way of monitoring what Ubuntu is sending or receiving?"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by candtalan on 2009-07-27
I know someone who is trying out Ubuntu, and they travel around from UK into Europe etc. Their internet access is usually phone network based so when abroad, their status is Roaming, which can be very costly.

My discussion with them so far has covered the possibility of unchecking software sources check for updates etc etc, but I do not know if this action stops *all* spontaneous data traffic, such as , say, firefox or another app trying to send out for check of latest version silently. 

They have asked me is there a way of monitoring what Ubuntu is sending or receiving? the reason is to see what the data traffic totals are I believe.

Comments appreciated

---

### Post by chrisinspace on 2009-07-27
A basic tool that works well for high-level analysis is iptraf.

To install:  

```
sudo apt-get install iptraf
```

To run: 

```
sudo iptraf
```

---

