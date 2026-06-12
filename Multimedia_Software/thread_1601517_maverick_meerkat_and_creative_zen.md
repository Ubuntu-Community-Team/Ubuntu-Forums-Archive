---
title: "maverick meerkat and creative zen"
date: 2010-10-20
forum: Multimedia Software
---

### Post by tarini on 2010-10-20
Hi guys,
yesterday I upgraded of my ubuntu release from 10.04 to 10.10 and now, when I plug my mp3 creative zen player it doesn't work.
The same player works very well with 10.04 and I can upload my mp3s directly from rythmnbox using drag&drop.


Here my /var/log/syslog

```
Oct 20 15:58:20 tarini-laptop kernel: [25042.100344] hub 4-0:1.0: unable to enumerate USB device on port 2
Oct 20 15:58:38 tarini-laptop kernel: [25059.970030] usb 1-1: new high speed USB device using ehci_hcd and address 16
Oct 20 15:58:38 tarini-laptop kernel: [25060.102634] usb 1-1: device descriptor read/64, error -71
Oct 20 15:58:38 tarini-laptop kernel: [25060.340046] usb 1-1: device descriptor read/64, error -71
Oct 20 15:58:38 tarini-laptop kernel: [25060.570069] usb 1-1: new high speed USB device using ehci_hcd and address 17
Oct 20 15:58:39 tarini-laptop kernel: [25060.700067] usb 1-1: device descriptor read/64, error -71
Oct 20 15:58:39 tarini-laptop kernel: [25060.940048] usb 1-1: device descriptor read/64, error -71
Oct 20 15:58:39 tarini-laptop kernel: [25061.170055] usb 1-1: new high speed USB device using ehci_hcd and address 18
Oct 20 15:58:39 tarini-laptop kernel: [25061.592524] usb 1-1: device not accepting address 18, error -71
Oct 20 15:58:40 tarini-laptop kernel: [25061.711241] usb 1-1: new high speed USB device using ehci_hcd and address 19
Oct 20 15:58:40 tarini-laptop kernel: [25062.130050] usb 1-1: device not accepting address 19, error -71
Oct 20 15:58:40 tarini-laptop kernel: [25062.130077] hub 1-0:1.0: unable to enumerate USB device on port 1
Oct 20 15:58:40 tarini-laptop kernel: [25062.460044] usb 3-1: new full speed USB device using uhci_hcd and address 2
Oct 20 15:58:40 tarini-laptop kernel: [25062.589234] usb 3-1: device descriptor read/64, error -71
Oct 20 15:58:41 tarini-laptop kernel: [25062.820123] usb 3-1: device descriptor read/64, error -71
Oct 20 15:58:41 tarini-laptop kernel: [25063.052583] usb 3-1: new full speed USB device using uhci_hcd and address 3
Oct 20 15:58:41 tarini-laptop kernel: [25063.180051] usb 3-1: device descriptor read/64, error -71
Oct 20 15:58:41 tarini-laptop kernel: [25063.420054] usb 3-1: device descriptor read/64, error -71
Oct 20 15:58:42 tarini-laptop kernel: [25063.652544] usb 3-1: new full speed USB device using uhci_hcd and address 4
Oct 20 15:58:42 tarini-laptop kernel: [25064.072625] usb 3-1: device not accepting address 4, error -71
Oct 20 15:58:42 tarini-laptop kernel: [25064.192609] usb 3-1: new full speed USB device using uhci_hcd and address 5
Oct 20 15:58:42 tarini-laptop kernel: [25064.612540] usb 3-1: device not accepting address 5, error -71
Oct 20 15:58:42 tarini-laptop kernel: [25064.612561] hub 3-0:1.0: unable to enumerate USB device on port 1

```

Do you know which problem could be?

thanks :)

---

### Post by andreabiggi on 2010-11-11
Same problem and no solutions...

---

