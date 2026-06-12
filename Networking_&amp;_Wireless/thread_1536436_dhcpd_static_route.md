---
title: "dhcpd static route"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by Enf` on 2010-07-22
Hello, I have setup a dhcpd server on my lan with the following option to reflect the static route to my private LAN.

dhcpd.conf
```

option static-routes 10.0.0.0 192.16.5.0

```I've tested it on OpenSUSE, ArchLinux and even Windows dhcp clients and they've managed to pull the static route configuration. However, to my suprise on my ubuntu machines this doesn't seem to load. Is there anything that needs to be done on the client's side to get this to work? Thanks.

---

### Post by Enf` on 2010-07-26
No one has any input on this?

---

### Post by Iowan on 2010-07-26
I'll try to check a machine when I get home - in the meantime, check settings in */etc/dhcp3/dhclient.conf* There is a list of "request" options - I'm not sure what the option might be for static routes.

---

