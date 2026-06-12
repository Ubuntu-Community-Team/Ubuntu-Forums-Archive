---
title: "Wireless Modem"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by sivadasanop73 on 2009-06-09
Can you help me to setup BSNL WLL modem HUAWEI EC325

---

### Post by prshah on 2009-06-09
> **sivadasanop73 said:**
> Can you help me to setup BSNL WLL modem HUAWEI EC325

Just plug it in, and it should be detected right out of the box (USB modems create a WAN PPPoE interface in the current version)

The use wvdial (or your favorite ppp dialer) to create a ppp connection: Open a terminal```
sudo wvdialconf /etc/wvdial.conf
```

When done, use ```
wvdial
``` to connect. You need to do this from a terminal; if you close the terminal, the connection will be terminated as well. To clean disconnect, activate the terminal, and issue a break (Ctrl-C).

Post back here with details if you have any troubles with wvdialconf's settings.

---

