---
title: "editing squid.conf errors"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by tdawg on 2009-04-23
Hi all, completely new, trying to edit squid.conf to get a proxy going..I'm on a router

i followed these directions:

[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

I uncommented and changed acl internal_network src 192.168.0.0/24 to 192.168.0.100

that is my ip when i type ifconfig

then I uncommented http_access allow internal_network

then i typed this into terminal:
```
sudo chown -R proxy:proxy /var/log/squid/
sudo chown proxy:proxy /etc/squid/squid.conf
```

then i tried to restart squid and this error message came up

```
 * Restarting Squid HTTP proxy squid                                                                                                                                                                            * Creating squid spool directory structure
2009/04/23 19:44:37| parseConfigFile: line 3040 unrecognized: '  TAG: test'
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.008 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted
2009/04/23 19:44:37| parseConfigFile: line 3040 unrecognized: '  TAG: test'
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.008 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted

```

as you can see i uncommented a line that read TAG visible_hostname and gave it an arbitrary name...I'm guessing this is wrong. HALLP!

---

### Post by tdawg on 2009-04-24
:confused:

---

