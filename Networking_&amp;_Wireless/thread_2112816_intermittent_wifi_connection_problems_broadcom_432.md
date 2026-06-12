---
title: "intermittent wifi connection problems: broadcom 4322 on ubuntu 12.04"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by intheseshoes on 2013-02-05
I am having intermittent wifi connection problems. Mostly my laptop is not connecting to wifi and just cycles through the available networks and fails to connect.

some probably relevant details
```
lspci -nn |grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
```This problem seems to have arisen on the last software update (this week) in which the following was updated:
```
Commandline: aptdaemon role='role-commit-packages' sender=':1.1872'
Install: linux-image-3.2.0-37-generic:amd64 (3.2.0-37.58), linux-headers-3.2.0-37:amd64 (3.2.0-37.58), linux-headers-3.2.0-37-generic:amd64 (3.2.0-37.58)
Upgrade: base-files:amd64 (6.5ubuntu6.4, 6.5ubuntu6.5), google-musicmanager-beta:amd64 (1.0.54.4672-r0, 1.0.55.7425-r0), linux-generic:amd64 (3.2.0.36.43, 3.2.0.37.44), libtelepathy-glib0:amd64 (0.18.0-1ubuntu1, 0.18.2-0ubuntu1), linux-headers-generic:amd64 (3.2.0.36.43, 3.2.0.37.44), linux-image-generic:amd64 (3.2.0.36.43, 3.2.0.37.44), initramfs-tools:amd64 (0.99ubuntu13, 0.99ubuntu13.1), jockey-common:amd64 (0.9.7-0ubuntu7.4, 0.9.7-0ubuntu7.7), jockey-gtk:amd64 (0.9.7-0ubuntu7.4, 0.9.7-0ubuntu7.7), linux-libc-dev:amd64 (3.2.0-36.57, 3.2.0-37.58), initramfs-tools-bin:amd64 (0.99ubuntu13, 0.99ubuntu13.1)
End-Date: 2013-02-04  10:16:51

```Any help for this inexperienced linuxer appreciated.

---

### Post by Hadaka on 2013-02-05
Hi, this may help..
[http://ubuntuforums.org/showthread.php?t=2107613&highlight=bcm4322](http://ubuntuforums.org/showthread.php?t=2107613&highlight=bcm4322)

---

