---
title: "Can I permanently disable Wake-on-LAN?"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by donsy on 2012-04-02
I would like to permanently disable the Wake-on-LAN feature of my Ethernet connection. There's no option to do so in the BIOS so I'm resorting to placing the following command in /etc/rc.local

    ```
ethtool -s eth0 wol d
```That works fine the first time I suspend my system after booting up. After the first suspension, however, if I suspend again WOL is enabled. I also tried adding the the command to /etc/network/interfaces

```

auto lo
iface lo inet loopback
# The following two lines are added
post-up /sbin/ethtool -s eth0 wol d
post-down /sbin/ethtool -s eth0 wol d
```But that doesn't work either. I need to add the command to a script that executes with root privileges upon suspending the system. Or alternatively find another way to permanently disable WOL.

---

### Post by raja.genupula on 2012-04-02
i read in a post that this option is available in BIOS at PnP hardware settings and from there you can disable Wake-on-LAN

---

### Post by donsy on 2012-04-02
> **raja.genupula said:**
> i read in a post that this option is available in BIOS at PnP hardware settings and from there you can disable Wake-on-LAN
I just flashed the BIOS on my Dell Inspiron 17R to the latest version and it shows no such setting. There is a USB Wake Support setting but that's disabled by default.

---

### Post by Elfy on 2012-04-03
*Thread moved to **Networking & Wireless**.*

---

