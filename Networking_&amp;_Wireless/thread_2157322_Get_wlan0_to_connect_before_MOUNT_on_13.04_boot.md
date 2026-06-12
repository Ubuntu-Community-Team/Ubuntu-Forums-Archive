---
title: "Get wlan0 to connect before MOUNT on 13.04 boot"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by EvilSupahFly on 2013-06-24
I have an old Toshiba Satellite laptop that I installed 13.04 on for my kids to play on. Normally boot time isn't an issue unless the ETH isn't connected and it falls back to WiFi.

The way I have it setup currently, during the boot, it loads network before running mount so that network shares are mounted by Automount during the boot sequence.

The problem is that if the eth isn't connected, I have to wait for the desktop to come up and the WiFi to connect, then manually run [FONT=courier new]**sudo mount -a**[/FONT] to get the NFS shares mounted from my internal server.

Is there a means by which I can get the WiFi to load, authenticate the WPA key and connect the shares for Automount on boot the way the ethernet does?

---

### Post by steeldriver on 2013-06-25
Not (afaik) using NetworkManager - you would need to do it via /etc/network/interfaces (and possibly disable NM) I think

Alternatively you could consider using autofs to mount the network shares on demand from 'userland'

---

### Post by praseodym on 2013-06-25
Hi,

change "false" to "true" in the /etc/NetworkManager/NetworkManager.conf and configure the interface in the respective file
```

auto wlan0
iface wlan0 inet dhcp
```
Did you check in your BIOS settings if the wireless is booted before the OS (if applicable)?

---

