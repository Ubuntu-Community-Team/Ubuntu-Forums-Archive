---
title: "Bridge not working"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by FORCED-INDUCTN on 2011-07-25
Hello

I know this is a bit strange but I have heard (and seen) that you can setup linux as a bridge/switch of sorts.

I tried the fallowing:

ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0
brctl addbr mybridge
brctl addif mybridge eth0
brctl addif mybridge eth1
ifconfig mybridge up

And connected two laptops but they can not ping each other. Am I missing something?

--Forced

---

### Post by jmoorse on 2011-07-26
Do the laptops have valid IP addresses?  Can you post the output of:

```

brctl show
brctl showmac br0

```

When the laptops are running and trying to ping.

What OS are the laptops?  What are their IPs/masks?

---

