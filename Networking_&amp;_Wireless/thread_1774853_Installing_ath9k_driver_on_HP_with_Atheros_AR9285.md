---
title: "Installing ath9k driver on HP with Atheros AR9285"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by djkee on 2011-06-03
Hello everyone, i am pretty new to Ubuntu and i am trying to get aircrack-ng and specifically airmon-ng to recognize by wifi card which is Atheros AR9285.

When i type airmon-ng i get:

```

Interface    Chipset        Driver

wlan0        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)


```I have downloaded compat-wireless-2011-06-01 and i have ran:

./scripts/driver-select ath9k but apparently that didnt install the driver so i tried:

make
make install

I thought that did it and after restarting airmon-ng still shows the interface and driver as unknown, anyone know why ?
I would appreciate any help.

I have HP DV-6 2144NR

Here is some more information i saw people asked for in other posts around the forum:
```

root@VIC09:/home/djkee# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dd-wrt_vap"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:16:47:E5   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:110   Missed beacon:0

``````

root@VIC09:/home/djkee# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````

root@VIC09:/home/djkee# lshw
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 01
                serial: 90:4c:e5:27:66:9c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.32-32-generic firmware=N/A ip=192.168.69.128 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f1200000-f120ffff

```

---

### Post by amithbn on 2012-06-05
I have the same problem. Were you able to solve yours? Can you given an insight into how you did it?

Thanks!

---

