---
title: "VPNC Connecting to Cisco IPSec VPN (Empty Domain Issue)"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by Kasuko on 2013-01-14
I am currently having an issue with Ubuntu 12.10 connecting to my work's VPN server.

Now I have installed network-manager-vpnc and when I tried to connect to the VPN it would just quickly fail.

So I tried to create a config file and connect manually from the terminal I got the error ```
vpnc: server requested domain, but none set (use "Domain ..." in config or --domain
``` then when I run it providing --domain "" it connects fine. However if I provide any other domain it does not authenticate correctly.

Now if I move the vpnc binary to vpnc.real 
UPDATE: I have been told by Andrey Bondarenko on the [bug page]("https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/1197313") that using dpkg-divert is better.
```

dpkg-divert --local --divert /usr/sbin/vpnc.real --rename /usr/sbin/vpnc

```
and write a wrapper script where /user/sbin/vpnc used to be
```

#!/bin/sh
exec /usr/sbin/vpnc.real --domain "" $*

```

I can now successfully connect to my office's VPN through the GUI.

So my question is ... is it possible to have Network Manager send an empty domain to VPNC? I don't like this hack because it is not update proof. If network-manager-vpnc updates this will blow up!

If not does anyone know of a cleaner way of implementing this workaround?

Thanks
Kasuko

---

### Post by abone2 on 2013-09-06
Hi,

No it's currently impossible to connect with empty domain using network-manager-vpnc.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/1197313](https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/1197313)

---

