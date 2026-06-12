---
title: "permanently change transmit power when using NetworkManager?"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by robertbub on 2011-05-30
I'm using Network Manager on my laptop.  Works great.

This also works great:```
sudo iwconfig wlan0 txpower 10
```

So, my question is: how can I make this change permanent each time I boot and use my laptop?

I have a feeling that **/etc/network/if-pre-up.d/wireless-tools** may be the key, but I don't see any place where the configuration is obtained.

---

