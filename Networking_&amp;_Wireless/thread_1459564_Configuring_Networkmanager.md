---
title: "Configuring Networkmanager?"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by mma8x on 2010-04-21
Is there a config file for networkmanager somewhere? I'm having a problem with my wireless driver where it will hang after a while unless i disable power management; easy enough with "iwconfig wlan0 power off".  I need a way for this to happen whenever NM is initiated (resuming from suspend, computer restart)

---

### Post by Iowan on 2010-04-21
There is a config file, but it seems to "move". On my old Karmic box, it was */etc/NetworkManager/system-connections*. On another Karmic machine, that is an empty directory. On my Jaunty laptop, it was (alt-F2)- gconf-editor >System>networking.

---

