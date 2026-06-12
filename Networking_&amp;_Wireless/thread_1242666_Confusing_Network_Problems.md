---
title: "Confusing Network Problems"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by nuttycc on 2009-08-17
Hi,

When I installed Ubuntu on my system at first the network had no problems whatsoever. Then a few days ago when I turned on my system I could not connect to anything (although it said I was connected to my wireless network). If I remember correct I was unable to connect to my router (192.168.0.1) - but don't quote me on this.

I found that doing 'iptables -F' after bootup fixed the problem until I rebooted again. At every shut down I get the following

```
nm-system-settings: SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_15_f2_f2_11_bf)
nm-system-settings: SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_1d_0f_b7_9e_0e)
```

and shutdown stops. I cannot ctrl+alt+del out of it, and have to press the power button on my system.

Today after having been using the computer for awhile, the network went really really slow. The internet was unusable. I could not reconnect to IRC (although it got to a different point everytime, sometimes I'd get part way through the MOTD and sometimes I wouldn't get past it saying that it had found my hostname). I've tried iptables -F, ifdown -a then ifup -a, /etc/init.d/networking restart but I don't really know what else to do. I didn't want to start messing about with config files I didn't understand because I might just make the problem worse :P

Any help or suggestions would be greatly appreciated :)

---

