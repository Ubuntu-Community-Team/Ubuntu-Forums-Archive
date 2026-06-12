---
title: "WPN111 has stopped working"
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by TheBigH on 2012-12-22
Hi all,
My Netgear WPN111 adapter was working fine for months under ndiswrapper, but then it suddenly died. I am still able to detect the network, it just won't connect.

Here is the output of lsusb

```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and ndiswrapper -l

```

netwpn11 : driver installed
    device (1385:5F01) present

```

I've done some googling and the (no firmware) bit seems to imply that the driver is not installed. However, that can't be the case because the thing was working properly for a long time, and ndisgtk confirms that the netwpn11 driver is present and the hardware is detected.

Can someone help?

---

### Post by TheBigH on 2012-12-23
I solved it by uninstalling network-manager and installing wcid.

---

