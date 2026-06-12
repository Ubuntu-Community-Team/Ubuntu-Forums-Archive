---
title: "Wifi problem"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by inso_741 on 2010-09-07
My wifi card is [DWA-525]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI")
I found the [drivers]("http://www.ralinktech.com/support.php?s=2") and compiled them using make and make install
How do I remove the default driver rt2800pci and load the new one?

---

### Post by inso_741 on 2010-09-07
how long before it runs out of the box??

---

### Post by inso_741 on 2010-09-07
alright Its using the correct driver now
but the device is named as ra0 instead of wlan0
how do I make network man use ra0 instead of wlan0???

---

### Post by inso_741 on 2010-09-08
bump

---

### Post by bkratz on 2010-09-08
> **inso_741 said:**
> alright Its using the correct driver now
but the device is named as ra0 instead of wlan0
how do I make network man use ra0 instead of wlan0???



Don't really understand your question-- your wireless device can be named a lot of things--some of which are wlan0,ra0, eth1 etc. What are you trying to do?

---

### Post by inso_741 on 2010-09-08
I want to rename it to wlan0
as network manager doesnt recognize it

---

### Post by bkratz on 2010-09-08
> **inso_741 said:**
> I want to rename it to wlan0
as network manager doesnt recognize it



network manager shouldn't really care. Can you post the outputs of the following commands?


```
lshw -C Network
sudo iwlist scan
```

---

### Post by inso_741 on 2010-09-09
sorry but the driver I installed kept crashing the system after log on
I've currently commented it in the /etc/modules and my wifi adapter is sound asleep.........

lspci -v gives:
```

    06:02.0 Network controller: RaLink Device 3060
    Subsystem: D-Link System Inc Device 3c04
    Flags: bus master, slow devsel, latency 32, IRQ 18
    Memory at d3000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt3562sta, rt2800pci
```
rt2800pci is the default driver which doesnt seem to work
rt3562sta is the one I compiled.........
HELP!

---

### Post by inso_741 on 2010-09-09
alright I got it working somehow
here's the o/p for lshw -C Network
```
*-network
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=rt2860 latency=32 maxlatency=4 mingnt=2
       resources: irq:18 memory:d3000000-d300ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: "adapter's mac"
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 multicast=yes wireless=Ralink STA

```
and o/p for sudo iwlist scan
```
ra0       Scan completed :
          Cell 01 - Address: "router's mac"
                    Protocol:802.11b/g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-43 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

```
network man doesnt see wi-fi adapter
wicd crashes on connecting.....
YELP!!!!

---

### Post by samuel_m on 2010-10-11
How did you get it working? I have the same issue! Please help :(

---

### Post by inso_741 on 2010-10-11
I had to blacklist the default module-"rt2800pci"
then I recompiled the latest drivers using sudo su(just sudo make && make install doesnt work)
Follow this [link]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1045703") for details..

---

