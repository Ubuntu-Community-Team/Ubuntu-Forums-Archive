---
title: "Atheros AR928X Went Down Today"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by MikeyDL on 2011-02-14
I've had this working for a while but my wireless Atheros AR928X went down today.  I'm connecting currently with a D-Link USB wireless adapter but hoping to troubleshoot my AR928X problems.  My card specific info is:

```
sudo lshw -C Network
```

  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:ce:90:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f4600000-f460ffff

```
dmesg | grep -e ath -e wlan
```

[    0.663880] device-mapper: multipath: version 1.1.1 loaded
[    0.663883] device-mapper: multipath round-robin: version 1.0.0 loaded
[   20.528540] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.528552] ath9k 0000:03:00.0: setting latency timer to 64
[   20.969130] ath: EEPROM regdomain: 0x65
[   20.969133] ath: EEPROM indicates we should expect a direct regpair map
[   20.969137] ath: Country alpha2 being used: 00
[   20.969139] ath: Regpair used: 0x65
[   20.997751] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   20.998301] Registered led device: ath9k-phy0::radio
[   20.998317] Registered led device: ath9k-phy0::assoc
[   20.998335] Registered led device: ath9k-phy0::tx
[   20.998350] Registered led device: ath9k-phy0::rx
[   22.100122] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.410488] ath: EEPROM regdomain: 0x3a
[   23.410491] ath: EEPROM indicates we should expect a direct regpair map
[   23.410494] ath: Country alpha2 being used: CA
[   23.410495] ath: Regpair used: 0x3a
[   24.592181] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   38.594365] wlan1: authenticate with c8:4c:75:20:e7:c7 (try 1)
[   38.596914] wlan1: authenticated
[   38.596951] wlan1: associate with c8:4c:75:20:e7:c7 (try 1)
[   38.601501] wlan1: RX AssocResp from c8:4c:75:20:e7:c7 (capab=0x431 status=0 aid=1)
[   38.601506] wlan1: associated
[   38.661598] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   48.732521] wlan1: no IPv6 routers present

If anyone has any ideas on what I might be able to do to get my onboard wireless up it would be much appreciated.

---

### Post by MikeyDL on 2011-02-15
So did some more testing today.  Was concerned that maybe the onboard wireless component failed.  So I booted Ubuntu from a 10.10 USB stick.  The wireless adapter worked fine off the stick.

So I'm guess that the drivers some how got messed up on my main HDD OS build.  How do you fix (i.e. reinstall) drivers in ubuntu?  For my wireless adapter they worked out of the box with Ubuntu and I don't have any external drivers showing up in the "install additional drivers" admin program.

Any ideas or tips on how to reinstall base drivers?

---

### Post by MikeyDL on 2011-02-15
Okay finally figured it out!  I had messed up my own wireless card.  A day or so earlier I had been manually IP'ing my eth0 adapter using the /etc/networking/interfaces file.  I changed the eth0 back to:

     auto eth0
     iface eth0 inet dhcp

Well, for some reason I figured I should do that for wlan0 as well so I added:

     auto wlan0
     iface wlan0 inet dhcp

I guess that messes up the automatic connections when you manually add lines to the interfaces file.  Took me a couple of days to figure out.

---

