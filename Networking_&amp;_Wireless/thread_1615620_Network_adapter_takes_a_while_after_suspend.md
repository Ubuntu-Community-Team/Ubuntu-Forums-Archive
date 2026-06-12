---
title: "Network adapter takes a while after suspend"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by bprins on 2010-11-07
Hi guys,

After I wake-up my laptop (after suspended-mode) it takes a bit long to activate my wireless connection. It's only 20seconds, but still it's quite annoying, and for some reason windows is able to do it in 3-5 seconds.

I tailed my daemon.log during "suspend -> wake-up" activities. The action that seems to take long is in bold below:
```

Nov  7 14:07:51 ubuntu-laptop acpid: 1 client rule loaded
Nov  7 14:07:52 ubuntu-laptop avahi-daemon[1132]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::f27b:cbff:fe1f:ef74.
Nov  7 14:07:52 ubuntu-laptop avahi-daemon[1132]: New relevant interface eth1.IPv6 for mDNS.
**Nov  7 14:07:52 ubuntu-laptop avahi-daemon[1132]: Registering new address record for fe80::f27b:cbff:fe1f:ef74 on eth1.*.**
Nov  7 14:08:16 ubuntu-laptop NetworkManager[1130]: <info> Activation (eth1) starting connection 'Auto linksys'
N

```

Is there anything I can do to make this faster? 

Thanks a lot in advance!

Best regards, 

Bas Prins

---

### Post by bprins on 2010-11-07
sudo apt-get install wicd

sudo apt-get remove network-manager

applications>internet>wicd

all problems solved :)

---

