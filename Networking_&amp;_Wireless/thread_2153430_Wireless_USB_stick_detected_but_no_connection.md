---
title: "Wireless USB stick detected but no connection"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by xxlray on 2013-06-11
I have a USB WLAN stick which I would like to use in Ubuntu 12.04. It seems to be recognized when I put it into the USB port.

```
$ iwconfig
lo        no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11abgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: D8:24:BD:4E:96:25   
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

```
$ lsusb | grep WLAN
Bus 001 Device 010: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
```

It is even listed in the Network Tools' Devices Tab. I already tried "sudo ip link set wlan1 up" but somehow only wlan0 (the internal adapter) gets connected to a network.

---

### Post by xxlray on 2013-06-19
This is the output of "sudo lshw -C network"
 ```
*-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: d4:be:d9:1b:f7:2e
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:e2e00000-e2e1ffff memory:e2e80000-e2e80fff ioport:4080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 10:0b:a9:90:f1:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-45-generic firmware=18.168.6.1 ip=192.168.100.125 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:e2d00000-e2d01fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1.1.2
       logical name: wlan1
       serial: 00:87:31:35:3d:bc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=134.169.202.229 multicast=yes wireless=IEEE 802.11gn
```

---

