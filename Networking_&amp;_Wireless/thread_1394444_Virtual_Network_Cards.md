---
title: "Virtual Network Cards"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by trentw2323 on 2010-01-30
I am doing some testing and have created a few taps using the command
```
tunctl -t tap0 -u username
and tunctl -t tap1 -u username
```

I attempted to assign ip addresses to these interfaces using
```
dhclient tap0
```

This is failing because i do not think the traffic from the tap is being forwarded to the real interface.
How do I make this happen?
Also I want to bridge the virtual nics together. How do i bridge interfaces together?

The end state will be 1 physical interface, and 2 taps bridged together.
Any help is appreciated

---

