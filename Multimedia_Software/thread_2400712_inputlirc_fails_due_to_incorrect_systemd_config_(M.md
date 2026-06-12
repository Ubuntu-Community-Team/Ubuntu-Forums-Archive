---
title: "inputlirc fails due to incorrect systemd config (MCE remote)"
date: 2018-09-09
forum: Multimedia Software
---

### Post by chrisallison2 on 2018-09-09
Hi, I'm having trouble logging into launchpad, so can't file this as a bug report.

inputlirc systemd service file has a line missing, as the start up file expects to be able to create a socket under /run/lirc

Package version:
```
[Unit]
Documentation=man:inputlircd(8)
Description=Zeroconf LIRC daemon using input event devices
After=udev lircd

[Service]
Type=simple
EnvironmentFile=/etc/default/inputlirc
ExecStart=/usr/sbin/inputlircd -f $OPTIONS $EVENTS

[Install]
WantedBy=multi-user.target
```

my version:
```
[Unit]
Documentation=man:inputlircd(8)
Description=Zeroconf LIRC daemon using input event devices
After=udev lircd

[Service]
Type=simple
RuntimeDirectory=lirc
EnvironmentFile=/etc/default/inputlirc
ExecStart=/usr/sbin/inputlircd -f $OPTIONS $EVENTS

[Install]
WantedBy=multi-user.target
```

This presumably affects all ubuntu flavours, not just ubuntu mate.

Can someone please file this as a bug report (and fix) on launchpad, as I am unable to at the moment, thanks.

---

