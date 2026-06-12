---
title: "rt270 disconnects and no reconnects"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by jbcfarina on 2010-01-30
When I use all the band(transmission or browsing too many videos) it disconnects after few minutes and it doesn't connect again until I reboot.

lspci:

05:01.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus

```
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 90:e6:ba:64:59:36
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe9fc000-fe9fffff ioport:d800(size=256) memory:fe9c0000-fe9dffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: ra0
       version: 00
       serial: 00:1d:1a:06:04:d2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.2.11 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:febf0000-febfffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

``````

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"feo"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:1C:DF:E4:67:87   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-58 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

```I could use N and WPA2 by following this [thread]("http://ubuntuforums.org/showthread.php?t=1246960&highlight=rt2860+karmic"). If it is possible to reconnect without reboot would be a possible workaround :)

(I use Ubuntu Karmic x_64)

---

### Post by jbcfarina on 2010-01-30
Bump

---

### Post by jbcfarina on 2010-01-31
bump .....:( at least how to reconnect without reboot,a hint? pleease

---

### Post by jbcfarina on 2010-01-31
I find how to do it without reboot:
```
sudo stop network-manager
sudo start network-manager
```¿any suggestion to fix the disconnects?.......

---

### Post by jbcfarina on 2010-02-02
Bump, the problem is with the upload disconnects always with rhytmbox-daap,  any ideas?........................:confused:

---

