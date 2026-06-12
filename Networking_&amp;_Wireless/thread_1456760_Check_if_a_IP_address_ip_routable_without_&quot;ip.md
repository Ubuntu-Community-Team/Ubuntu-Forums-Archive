---
title: "Check if a IP address ip routable without &quot;ip route get&quot;"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by nunojpg on 2010-04-17
route(8) does not allow to add a default route if the gateway is not reachable first.

> NOTE: The specified gateway must be reachable first. This usually means that you have to set up a static route to the gateway beforehand.

I've been using the following code to get around this:

```
ip route get "$gateway" >/dev/null 2>/dev/null || route add -host "$gateway" dev "$iface"
route add default gw "$gateway" dev "$iface"
```

Now I would like to make it portable for other platafforms that don't have ip(8). 
What can I use to replace "ip route get "$gateway""?

Regards

---

