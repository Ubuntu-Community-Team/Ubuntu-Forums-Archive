---
title: "Broadcom BCM4313 takes ages to connect"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by drazgo on 2011-01-26
Hi everyone,

I'm having issues with my broadcom BCM4313 wireless adapter. Everything works just fine when connected (with additional drivers & Connman), but it takes about 5 minutes to connect to my network when i just started my computer! When resuming from hibernation it goes very quick though, so just when I boot my pc it's taking forever...

This is what I found in the dmesg output:


```
[   16.778057] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
[   16.808768] type=1400 audit(1295859939.727:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=833 comm="apparmor_parser"
[   16.808815] type=1400 audit(1295859939.727:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=799 comm="apparmor_parser"
[   16.808825] type=1400 audit(1295859939.727:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=826 comm="apparmor_parser"
[   16.809367] type=1400 audit(1295859939.727:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=833 comm="apparmor_parser"
[   16.809415] type=1400 audit(1295859939.727:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=799 comm="apparmor_parser"
[   16.809435] type=1400 audit(1295859939.727:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=826 comm="apparmor_parser"
[   16.809705] type=1400 audit(1295859939.727:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=833 comm="apparmor_parser"
[   16.809755] type=1400 audit(1295859939.727:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=799 comm="apparmor_parser"
[   16.809769] type=1400 audit(1295859939.727:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=826 comm="apparmor_parser"
[   16.844083]   alloc irq_desc for 22 on node -1
[   16.844087]   alloc kstat_irqs on node -1
```

Thanks in advance!

---

### Post by drazgo on 2011-01-27
Anyone?

---

### Post by drazgo on 2011-02-02
bump

---

