---
title: "Disabling compiled in ethernet driver?"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by trapper- on 2009-11-09
Ok here's my situation. After discovering some major samba slowdown issues with the stock intel e1000 driver I downloaded and installed the latest version of this driver from intel and installed it. Works great now, only problem is that upon reboot the system is reverting to the earlier driver. I need to unload and reload it each time to get back to my updated one. I can't find any sign of the earlier driver on my system so think it must be compiled into the kernel? Can I stop this from loading somehow so that the updated one will be picked up later when the modules are loading?

dmesg shows the following on reboot, which I assume is the driver loading very early in the boot process (compiled in?)
```

[    3.154001] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    3.388777] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    3.388783] Copyright (c) 1999-2006 Intel Corporation.
[    3.703335] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection

```then after boot `ethtool -i eth0` confirms the default 7.3.21-k3-NAPI driver has loaded
```

driver: e1000
version:  7.3.21-k3-NAPI
firmware-version: N/A
bus-info: 0000:01:0c.0

````modprobe -r e1000` then `modprobe e1000` drops the older driver and loads in my updated version and `ethtool -i eth0` now reveals everything is good
```

driver: e1000
version: 8.0.16-NAPI
firmware-version: N/A
bus-info: 0000:01:0c.0

```So back to the inital question. Can I stop this 'compiled in' driver from loading in the first place using some kind of boot parameters. Or is my only option to run the unload and reload in a post boot script?

Oh btw: running ubuntu 9.10

---

### Post by trapper- on 2009-11-09
any ideas?

---

