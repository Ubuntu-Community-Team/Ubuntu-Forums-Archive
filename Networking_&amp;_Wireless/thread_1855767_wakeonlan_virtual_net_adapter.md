---
title: "wakeonlan virtual net adapter"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2011-10-06
```
Cable Modem
`--Switch
  |--Desktop
  `--Laptop
```Desktop Ip address
eth0 68.XXX.XX.XX (Internet)
eth0:1 10.0.0.1 (used for router service)
eth0:2 192.168.100.2 (modem status is on this network and there is a dhcp server for it)

```
cat /etc/init.d/wakeonlanconfig
#!/bin/bash
ethtool -s eth0:2 wol g
exit
```would the ufw firewall be blocking the wakeup?

EDIT:
thought i had enabled it in bios when i did not, wish asus would call it "Wake On Lan" in there BIOSes
it was under power not boot it worked on eth0 as expected once enabled in bios

---

