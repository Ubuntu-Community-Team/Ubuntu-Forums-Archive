---
title: "rtl8187 many message DoRxHighPower(): RF_ZEBRA, Upper Threshold"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by mvdberg112 on 2009-04-11
I've replaced my rtl8187 (from kernel/drivers/net/wireless) driver with 
/lib/modules/2.6.24-24-generic/ubuntu/wireless/rtl8187-usb/rtl8187/r8187.ko

I get tons and tons of these messages in the log files:
```
[16380.212925] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[16382.212646] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[16382.912534] GetUpgradeTxRate(): Tx rate (36) is not in supported rates
[16384.212501] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[16386.224812] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[16387.711845] GetUpgradeTxRate(): Tx rate (36) is not in supported rates
[16388.211820] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[16390.211526] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[16392.211194] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[16392.511162] GetUpgradeTxRate(): Tx rate (36) is not in supported rates

```Why do they appear? I thiknk that appear every one or two seconds, so I have thousands of them.
They appear in these files (why not just in one log file? it is linux...):
/var/log/kern.log
/var/log/messages
/var/log/syslog
and also the command: dmesg | tail -n 100

What do the messages mean?
Why do they appear with the new driver?
How can I stop them?

PS: the driver works fine as far as I can tell.

---

### Post by desconocido on 2009-08-12
I have the same problem.

See [http://ubuntuforums.org/showthread.php?t=1238228]("http://ubuntuforums.org/showthread.php?t=1238228")

---

