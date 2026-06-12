---
title: "Listen to wlan instead of eth"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by hectorh30 on 2009-12-05
Hey there, 
I've been using Ubuntu for a while now and I feel very comfortable. The reason of this post is the following:
I'm in a network where there is free access to the internet through wireless, but theres a proxy in the wired connection. I need to make up some configurations on a pc which I can only access through the wired, but when I plug in the RJ-45 programs like firefox or pidgin stop working and I need to set up the proxy settings. Is there any way I can set these programs to 'listen' to the wlan instead of the eth so theres no need to configure the proxy on them?
Thanks in advice

---

### Post by Yoann Juet on 2009-12-05
> **hectorh30 said:**
> Is there any way I can set these programs to 'listen' to the wlan instead of the eth so theres no need to configure the proxy on them?
Thanks in advice

Well, your default gateway seems to be on the wired lan. To bypass the proxy, you just have to adjust your default route.

Print the routing table :

```
ip route
``` 

Delete your current default gateway

```
route del default gateway <@IP_YOUR_WIRED_LAN_ROUTER>
```

Add a new default gateway to the wireless lan

```
route add default gateway <@IP_YOUR_WIRELESS_LAN_ROUTER>
```

---

### Post by hectorh30 on 2009-12-07
Thanks! That absolutely did the trick.

---

