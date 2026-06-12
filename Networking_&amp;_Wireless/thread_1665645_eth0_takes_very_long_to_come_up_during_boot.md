---
title: "eth0 takes very long to come up during boot"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by [mm] on 2011-01-12
Hi, I've a server running Ubuntu 10.04 with a Realtek NIC (RTL8168C/8111C) which takes ten minutes or longer until it is ready during the boot process:

```

Jan 12 20:57:08 boxx kernel: [    2.523305] eth0: Identified chip type is 'RTL8168C/8111C'.
Jan 12 20:57:08 boxx kernel: [   12.847830] r8168: eth0: link down
Jan 12 20:57:08 boxx kernel: [   12.848953] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 12 21:09:45 boxx kernel: [  768.048386] r8168: eth0: link up
Jan 12 21:09:45 boxx kernel: [  768.050107] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 12 21:09:45 boxx kernel: [  768.905120] r8168: eth0: link up
Jan 12 21:09:55 boxx kernel: [  778.563136] eth0: no IPv6 routers present

```I also tried using a cronjob to bring the interface up much earlier:
```
@reboot  /sbin/ifup eth0
```However this failed with the message "interface eth0 already configured".

Has anyone an idea what the problem might be or what I could try to find out more about this problem?

---

### Post by [mm] on 2011-01-14
The problem was a faulty LAN cable...

---

