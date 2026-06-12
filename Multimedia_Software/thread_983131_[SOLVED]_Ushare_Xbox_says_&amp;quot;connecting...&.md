---
title: "[SOLVED] Ushare: Xbox says &amp;quot;connecting...&amp;quot;. Times out."
date: 2008-11-15
forum: Multimedia Software
---

### Post by goldfish2 on 2008-11-15
When I activate Ushare, if I stare at my xbox for 5 minutes or so, the name of my share "Ushare" will appear.  But if I try to connect to it times out and tells me to check my firewall.  Otherwise it vanishes after a few minutes only to reappear later.  I don't think I have a firewall because of:
```
$ sudo ufw status
Firewall not loaded
```

When I start Ushare I get the following:

```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.0.6:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /mnt/raid/shows
Found 1052 files and subdirectories.
```

(my only network devices are lo and eth0, and also I've been told from people who have it working that they still get the "Interface eth0 is down." error, so I don't think that is a problem)

I've used synaptic to install ushare version 1.1a-0ubuntu1 (which installed both libupnp2 v1.4.3-2 and libdlna0 v0.2.3-0ubuntu1).  I am currently using Hardy. Here is my /etc/ushare.conf

```
USHARE_NAME=uShare
USHARE_IFACE=eth0
USHARE_PORT=49200
USHARE_TELNET_PORT=
USHARE_DIR=/mnt/raid/shows
USHARE_OVERRIDE_ICONV_ERR=
ENABLE_WEB=no
ENABLE_TELNET=no
ENABLE_XBOX=yes
ENABLE_DLNA=
```

Why can the xbox see my share, but not connect to it?

Thanks,
GoldFish

P.S.
If I turn on the WEB interface I can load the page [http://192.168.0.6:49200/web/ushare.html](http://192.168.0.6:49200/web/ushare.html) on any of the computers on my network without problem.

---

### Post by goldfish2 on 2008-11-18
Problem solved: I updated to Ubuntu 8.10

I wish I could give more detail than that.  I'm unsure what about upgrading to Ubuntu 8.10 fixed it, but it wasn't working before the update and then was after.

I still get the "Interface eth0 is down." message, but it works now, despite it.

GoldFish

---

