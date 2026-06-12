---
title: "WG111v3 Dropping Connection"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by darsie on 2009-05-18
Hello,

I've been a Ubuntu user for about 3-4 years, and this is the first time I've had to raise an issue. Sadly I haven't been able to figure this one out, and I'm back using windows. Boo.

I have a Netgear WG111v3 USB adapter (RTL8187B chipset) and it connects to my WPA network, no problem. However, after about 30-60 minutes the connection drops. Network Manager / WICD still shows a 60-80% signal but I'm not even able to ping my router.

I'm using a clean install Jaunty 32bit on a HP dv6000. Not using ndiswrapper, as the adapter worked soon as I plugged it in. Here's the output of lshw, dmesg and lsusb. Output from iwconfig and iwlist attached.

Thanks!

```
lsusb: 
Bus 001 Device 002: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]

dmesg:
[   31.484651] eth0: no link during initialization.
[   31.485163] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.783412] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.856788] wlan0: authenticate with AP f61576b8
[   39.859548] wlan0: authenticated
[   39.859550] wlan0: associate with AP f61576b8
[   39.868789] wlan0: RX AssocResp from f5d4c01a (capab=0x431 status=0 aid=1)
[   39.868793] wlan0: associated
[   39.874063] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.448015] wlan0: no IPv6 routers present

sudo lshw -C network:
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:2a:b7:d5:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.5 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:1a:3b:8d:a6:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

