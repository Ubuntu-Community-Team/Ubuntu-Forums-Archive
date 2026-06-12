---
title: "Ubuntu 12.04 DNS problems"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by ebu on 2012-05-03
Hi,

After upgrading to 12.04 my company VPN stopped working, it connects, but then browsers can't find any site. Here is snippet from the syslog:

```

May  3 10:24:56 xxxwp400322 NetworkManager[1336]: <info> VPN connection 'VPN XXX' (IP Config Get) complete.
May  3 10:24:56 xxxwp400322 NetworkManager[1336]: <info> Policy set 'Auto ZZZZ' (eth1) as default for IPv4 routing and DNS.
May  3 10:24:56 xxxwp400322 NetworkManager[1336]: <info> VPN plugin state changed: started (4)
May  3 10:24:56 xxxwp400322 dbus[1296]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  3 10:24:56 xxxwp400322 dbus[1296]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  3 10:24:56 xxxwp400322 dnsmasq[15994]: nameserver 10.0.101.241 refused to do a recursive query
May  3 10:25:01 xxxwp400322 CRON[16048]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May  3 10:25:05 xxxwp400322 ntpdate[16028]: adjust time server 91.189.94.4 offset -0.000431 sec
May  3 10:35:01 xxxwp400322 CRON[16253]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)


```

is it "nameserver refused to do a recursive query" what causes all the troubles? Any help to fix it is highly appreciated!

Best regards, Eugene.

---

### Post by ebu on 2012-05-03
the problem was fixed by disabling dnsmasq as described in [here]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/"), but is there any way to fix it properly, i.e. without disabling dnsmasq?

---

### Post by yoblin on 2012-05-18
Same issue, works fine after the workaround.

---

### Post by jdthood on 2012-11-05
The problem seems to be with the peer. The VPN server is handing out an IP address for a nameserver which refuses to do recursive queries.

---

