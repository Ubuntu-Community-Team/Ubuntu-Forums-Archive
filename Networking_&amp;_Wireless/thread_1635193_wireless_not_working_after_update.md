---
title: "wireless not working after update"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by zebraneo on 2010-12-01
I had wireless and everything was working fine, till I did some updates and now I can't get wireless, the computer can see the connection to the wireless but tries to connect but can't connect. Help\Thanks

 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:36:e6:9a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.100 latency=0 multicast=yes
       resources: irq:26 ioport:3000(size=256) memory:90010000-90010fff(prefetchable) memory:90000000-9000ffff(prefetchable) memory:90020000-9002ffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:17:c4:a2:ad:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:94000000-9400ffff
juile@juile:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=56/100  Signal level:-81 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by grahammechanical on 2010-12-01
iwconfig says "Not-associated" That means that you are not connected to the router/modem. But you knew that. Access Point: should show 6 pairs of number - letter combinations. The hardware address of the modem.

Are you using the correct authentication key (password)? Not your login password but the WPS-PSK key. I am sorry if that sounds too simple to suggest but I have been caught out by that myself.

Regards.

---

