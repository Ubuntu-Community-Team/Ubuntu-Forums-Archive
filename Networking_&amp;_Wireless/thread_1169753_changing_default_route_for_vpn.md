---
title: "changing default route for vpn"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by RikoW on 2009-05-25
Dear all,

I use network manager to manage my network connection including establishing vpnc connections to my employers intranet. In principle that works ok for most applications for example firefox. However, one essential application will not connect to one of our servers. Under Ubuntu 8.04 that worked fine if I just changed the default route via the ip command to the vpn server:

```
sudo ip route change default via 131.169.11.30
```

In the mean time, I have upgraded to a new laptop (Dell Lat E4300 with Intel Corporation Wireless WiFi Link 5100) and installed the most recent version of Ubuntu. If I now try to change the default route, I get an error message:

```
> sudo ip route change default via 131.169.11.30
RTNETLINK answers: No such process

```

Needless to say, the connection to the intranet server is not possible. I assume, it is still/again a routing problem, but don't know how to fix it. 

Help would be greatly appreciated!

Cheers,

            Riko

---

### Post by RikoW on 2009-05-28
Hi again,

it seems to be a problem with network-manager or the vpn plugin. If I start the vpn connection from the command line, I can change the default gateway without any problems ...

Cheers,

             Riko

---

