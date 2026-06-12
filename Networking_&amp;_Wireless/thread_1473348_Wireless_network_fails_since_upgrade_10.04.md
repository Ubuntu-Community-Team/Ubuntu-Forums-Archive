---
title: "Wireless network fails since upgrade 10.04"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Lauwerier on 2010-05-05
My wireless network failed after the Kubuntu 10.04 upgrade. I had previously had problems with knetwork manager, so I removed it and configured manually. I finally found that deleting both Networking Manager and Wicd brought back my connection ONLY after I manually do a **/etc/init.d/networking restart** and a fixed network addres in **/etc/network/interfaces**.
Output of **dmesg** is shown below. I suspect the line containing /usr/lib/NetworkManager/nm-dhcp-client.action may be related to my problem. Were does it originate from ? Can I avoid it ?

...
[   10.947466] kjournald starting.  Commit interval 5 seconds
[   10.947692] EXT3 FS on sda4, internal journal
[   10.947699] EXT3-fs: mounted filesystem with ordered data mode.
[   11.936574] wlan0: direct probe to AP 00:50:18:4f:ff:e2 (try 1)
[   11.938372] wlan0: direct probe responded
[   11.938377] wlan0: authenticate with AP 00:50:18:4f:ff:e2 (try 1)
[   11.939993] wlan0: authenticated
[   11.940012] wlan0: associate with AP 00:50:18:4f:ff:e2 (try 1)
[   11.942058] wlan0: RX AssocResp from 00:50:18:4f:ff:e2 (capab=0x431 status=0 aid=1)
[   11.942061] wlan0: associated
[   11.942888] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.197669] type=1505 audit(1273044808.369:5):  operation="profile_replace" pid=990 name="/sbin/dhclient3"
[   22.198545] type=1505 audit(1273044808.369:6):  operation="profile_replace" pid=990 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   22.199015] type=1505 audit(1273044808.369:7):  operation="profile_replace" pid=990 name="/usr/lib/connman/scripts/dhclient-script"
[   22.213244] type=1505 audit(1273044808.385:8):  operation="profile_load" pid=995 name="/usr/bin/freshclam"
[   22.217638] type=1505 audit(1273044808.389:9):  operation="profile_load" pid=998 name="/usr/sbin/clamd"
[   22.221138] type=1505 audit(1273044808.393:10):  operation="profile_load" pid=1000 name="/usr/lib/cups/backend/cups-pdf"
[   22.222166] type=1505 audit(1273044808.393:11):  operation="profile_load" pid=1000 name="/usr/sbin/cupsd"
[   22.226772] type=1505 audit(1273044808.397:12):  operation="profile_load" pid=1002 name="/usr/sbin/mysqld"
[   22.229526] type=1505 audit(1273044808.401:13):  operation="profile_load" pid=1003 name="/usr/sbin/mysqld-akonadi"
[   22.232270] type=1505 audit(1273044808.405:14):  operation="profile_load" pid=1004 name="/usr/sbin/tcpdump"
[   22.431932]   alloc irq_desc for 27 on node -1
[   22.431937]   alloc kstat_irqs on node -1
[   22.431953] atl1 0000:01:00.0: irq 27 for MSI/MSI-X
[   22.432374] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.692009] wlan0: no IPv6 routers present
[   22.931695] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   22.931700] apm: overridden by ACPI.

---

