---
title: "One thing works everything else doesnt."
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by pojo87 on 2010-04-15
Hey guys I'm pretty new to the forum so bear with me please :)
Basically I've noticed that the first thing i start up that involves the internet or my wireless card works fine, it's just everything else that craps out. If i startup wlan manager and choose my network that im using wepbuster will give me this error.

Checking for mac filtering...Trying to associate...ioctl(SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.


Can't associate. aireplay-ng died!

I've ran the commands it tells me to run and it does nothing.

If i run wepbuster first before starting wlan manager then when i do finally feel like goin online i cant even see any networks. Please help this is extremely frustrating.
Also im running backtrack 4.

and

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
        Subsystem: Toshiba America Info Systems Device ff68
        Flags: bus master, 66MHz, medium devsel, latency 0
        Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: ce200000-ce3fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000c7ffffff
        Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
        Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff68
        Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc Device 7914
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=0a, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: cd200000-ce1fffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000c8ffffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+), MSI 00
:
dont exactly know which one is my Wireless card.

---

