---
title: "RT2561/RT61 Wireless Slow or Drops"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by esc1 on 2011-05-17
When I was on Intrepid this card worked flawlessly. Torrents downloaded over 1mb a second and had no problems surfing the net. Now on the last release and this release (10.04) my torrent speeds are nearly a fourth of what they were and at times browsing the net while not even downloading torrents is as slow as dialup. It also times out several times a day. I will post all the info I know a helpful hand may need.

dsmg
```
[   19.848627] CPU0 attaching NULL sched-domain.
[   19.848635] CPU1 attaching NULL sched-domain.
[   19.900179] CPU0 attaching sched-domain:
[   19.900183]  domain 0: span 0-1 level MC
[   19.900186]   groups: 0 1
[   19.900192] CPU1 attaching sched-domain:
[   19.900194]  domain 0: span 0-1 level MC
[   19.900196]   groups: 1 0
[   20.466257] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   75.311340] wlan0: deauthenticating from c4:3d:c7:a8:54:52 by local choice (reason=3)
[   75.320086] wlan0: direct probe to AP c4:3d:c7:a8:54:52 (try 1)
[   75.324288] wlan0: direct probe responded
[   75.324294] wlan0: authenticate with AP c4:3d:c7:a8:54:52 (try 1)
[   75.325907] wlan0: authenticated
[   75.325932] wlan0: associate with AP c4:3d:c7:a8:54:52 (try 1)
[   75.328435] wlan0: RX AssocResp from c4:3d:c7:a8:54:52 (capab=0x421 status=0 aid=1)
[   75.328437] wlan0: associated
[   75.329310] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   85.411262] wlan0: no IPv6 routers present
[ 2201.510024] No probe response from AP c4:3d:c7:a8:54:52 after 500ms, disconnecting.
[ 2203.100355] wlan0: direct probe to AP c4:3d:c7:a8:54:52 (try 1)
[ 2203.300025] wlan0: direct probe to AP c4:3d:c7:a8:54:52 (try 2)
[ 2203.501266] wlan0: direct probe to AP c4:3d:c7:a8:54:52 (try 3)
[ 2203.700021] wlan0: direct probe to AP c4:3d:c7:a8:54:52 timed out
[75831.270564] wlan0: direct probe to AP c4:3d:c7:a8:54:52 (try 1)
[75831.274555] wlan0: direct probe responded
[75831.274560] wlan0: authenticate with AP c4:3d:c7:a8:54:52 (try 1)
[75831.277930] wlan0: authenticated
[75831.277949] wlan0: associate with AP c4:3d:c7:a8:54:52 (try 1)
[75831.281517] wlan0: RX AssocResp from c4:3d:c7:a8:54:52 (capab=0x421 status=0 aid=1)
[75831.281519] wlan0: associated

```

lsmod
```
lsmod |grep -i -e rt61pci -e ndiswrapper
rt61pci                21414  0 
crc_itu_t               1715  1 rt61pci
rt2x00pci               6905  1 rt61pci
rt2x00lib              32133  2 rt61pci,rt2x00pci
eeprom_93cx6            1765  1 rt61pci
esc1@esc1-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:54:07:37
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:25 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdae0000-fdaeffff(prefetchable) memory:fda00000-fda0ffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 00
       serial: 00:1a:ef:07:57:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.2.19 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:fdcf0000-fdcf7fff

```

Something that jumps out at my is the IRQ thing in dmsg. I've read on here that the rt61pci driver is problematic and I should maybe go with the rt61 although I have no idea about configuring that.

I would really appreciate some help.

---

