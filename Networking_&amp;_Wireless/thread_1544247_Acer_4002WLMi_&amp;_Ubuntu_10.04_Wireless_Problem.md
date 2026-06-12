---
title: "Acer 4002WLMi &amp; Ubuntu 10.04 Wireless Problem"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by johng4etm on 2010-08-02
I am trying the Live CD on the above laptop. Everything seems OK except the wireless networking.
The wireless switch/LED on the front of the machine is flashing (as it does under XP when no connection can be made).

The machine use the Intel PRO/Wireless 2200BG chip set.

lspci finds the chip set.
iwconfig finds it as eth1
lsmod finds ipw2200
dmesg shows
[  852.860208] ipw2200 0000:02:04.0: PCI INT A disabled
[  870.411738] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  870.411744] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  870.411829] ipw2200 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[  870.411907] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  870.411957] ipw2200 0000:02:04.0: firmware: requesting ipw2200-bss.fw
[  870.528661] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  880.884036] eth1: no IPv6 routers present
[  936.875798] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  937.899086] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[  938.908081] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[  939.916052] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 1272.204059] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 1272.874877] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1542.875257] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1543.896071] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[ 1544.912050] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[ 1545.920064] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 1643.000195] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1643.000205] b44: eth0: Flow control is off for TX and off for RX.
[ 1643.000840] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1653.516039] eth0: no IPv6 routers present
[ 1861.000112] b44: eth0: Link is down.
[ 1882.000191] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1882.000201] b44: eth0: Flow control is off for TX and off for RX.
[ 6161.182520] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6161.384041] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 6730.514630] ipw2200: Failed to send TX_POWER: Aborted due to RF kill switch.
[ 6740.181542] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6741.204052] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[ 6742.212060] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[ 6743.220072] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 7439.178489] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7439.452079] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 8575.436051] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 8576.181293] ADDRCONF(NETDEV_UP): eth1: link is not ready

lshw -C network shows
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:6f:d7:b7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.7 latency=64 multicast=yes
       resources: irq:6 memory:d0204000-d0205fff memory:84000000-84003fff(prefetchable)
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:96:3f:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:10 memory:d0208000-d0208fff

iwlist scan shows NOTHING


Does it not work because I am running from the Live CD ?

Or is there some other explanation ?

Any help would be appreciated.

---

