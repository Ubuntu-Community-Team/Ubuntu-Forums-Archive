---
title: "Need help configuring iptables"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by BlueTemplar on 2010-12-06
I'm writing
```

sudo iptables -t nat -A OUTPUT  -p tcp -m tcp   --dport 1935 -j DNAT --to-destination localhost:8080

```
as the rtmp2rtmpt readme tells me, but then when I do
```
sudo iptables -L
```
nothing has changed... and the proxy doesn't work obviously. Please help!

---

