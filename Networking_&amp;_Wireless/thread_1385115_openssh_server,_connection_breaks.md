---
title: "openssh server, connection breaks"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by bender1234 on 2010-01-19
Hi don't know if this is the proper place to put this thread, but I'll shoot anyways.

I'm runnig openssh server on karmic x86.

uname -a

```
 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
```

I haven't altered the ssh configfile. The box is behind a NAT, but I have properly forwarded ports to it. The problem is that the connection breaks constantly(when ssh-ing over internet). The computer is connected to a router through wifi(Dlink dwa usb dongle, and y I've blacklisted the rt2800 driver), and internet on it works like a charm.  

I know the question is rather vague, but any ideas what might cause this problem? I might add that this happens when try to connect from campus and at home. It happens both from karmic and in putty on this pc.

The router is a Tilgin Vood 452W_B. A typical cra**y all-in-one dsl modem, router, 802.11b/g thing.

I can't quite see what might cause this problem. It doesn't mather if the line is beeing used by other people, pcs or process or not.

Best regards,
Bender

---

### Post by bender1234 on 2010-01-20
*bump* :)

I suspect that the issue is in fact the router, as the configuration is correct and there isn't any hardware/driver issues on the computer.

Is it possible that when using filesharing apps such as rtorrent, and when having to many connections the router runs out of ram(I.E.), and then "crashes"? I've experienced that when I have to many open torrents in rtorrent, and the number of allowed connections is set to high it gets problems. Any thoughts on this? I might add that this also happens on other computers at the location.

regards,
Bender

---

