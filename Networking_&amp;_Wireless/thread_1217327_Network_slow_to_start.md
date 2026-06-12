---
title: "Network slow to start"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by spiregrain on 2009-07-19
When I start up my machine, the network doesn't come up for about 10 seconds after the boot process is finished.

Looking at the lights on the switch, the PCs port lights up when the PC is switched on, stays on until the kernel is loaded, and then goes off untill about 10secs after the Ubuntu logon prompt appears (ie. ON when grub is displayed, OFF as soon as grub is finished, ON a *long* time later).

What is causing this?

The end of dmesg sez:
```
[   13.321677] usb-storage: device scan complete
[   13.335660] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    2.00 PQ: 0 ANSI: 0
[   13.359722] sd 7:0:0:0: [sdh] Attached SCSI removable disk
[   13.359783] sd 7:0:0:0: Attached scsi generic sg8 type 0
[   22.350962] ppdev: user-space parallel port driver
[   26.754920] skge eth0: enabling interface
[   26.758134] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.478310] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   28.478439] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   38.684026] eth0: no IPv6 routers present

```

Note the 10 second lag between the last to items.

I'm running kernel ```
Linux gkar 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

```

---

### Post by spiregrain on 2009-07-26
(small bump)

---

### Post by spiregrain on 2009-09-08
any ideas?

---

