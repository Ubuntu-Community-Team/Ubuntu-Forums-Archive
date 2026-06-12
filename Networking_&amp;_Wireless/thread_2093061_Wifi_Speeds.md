---
title: "Wifi Speeds"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by GuitarHero on 2012-12-09
For some reason my lenovo laptop with Ubuntu(up to date) only gets 0.48 Mbps while my girlfriend's macbook gets 22.54 Mbps on the same wifi network.  Same location/distance from router.

Does anyone know why this would happen and what I can do about it??

---

### Post by Bucky Ball on 2012-12-09
*Thread moved to **Networking & Wireless***

---

### Post by EmmEight on 2012-12-09
Sounds like a hardware/driver issue?

Have you checked the broadcom 43xx thread?

What wifi card do you have?

---

### Post by ZippyUbu on 2012-12-09
Hi,

Post the terminal output of: iwconfig

--
Zu

---

### Post by Bucky Ball on 2012-12-09
... and the output of:
```

sudo lshw -C network
```

... thanks.

---

### Post by GuitarHero on 2012-12-09
I remembered that I had a windows partition, tested it on that and it was 22 Mbps.

iwconfig:
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"NETGEAR59"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 84:1B:5E:71:9A:8C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:653   Missed beacon:0





sudo lshw -C network:

PCI (sysfs)

---

### Post by ZippyUbu on 2012-12-09
```
iwconfig:
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"NETGEAR59"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 84:1B:5E:71:9A:8C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:n
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:653   Missed beacon:0
``` This line might cause issues with speed: Bit Rate=1 Mb/s

Open the terminal and try:

```
 sudo iwconfig wlan0 rate 54M
```Then try your speed test again...

---

### Post by GuitarHero on 2012-12-09
The ping went down to 40 from 70, the dl speed stayed the same, and the upload speed actually went down from 3.5 to 2.46

---

### Post by Bucky Ball on 2012-12-09
You  didn't wait long enough.
```

sudo lshw -C network
```... and wait for the output, please. Then post here.

Switching off wireless N and power management will possibly solve the problem I'm thinking ...

---

### Post by GuitarHero on 2012-12-09
Sorry, here's the result:

 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:c8:1d:42
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 64:27:37:7e:0d:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-19-generic firmware=0.34 ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0100000-f010ffff

---

### Post by GuitarHero on 2012-12-13
Any idea?

---

### Post by ZippyUbu on 2012-12-13
```
description: Wireless interface
product: RT3090 Wireless 802.11n 1T/1R PCIe
vendor: Ralink corp.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 00
serial: 64:27:37:7e:0d:27
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-19-generic firmware=0.34 ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
resources: irq:18 memory:f0100000-f010ffff
```I think the driver you are using is incorrect. ```
driver=rt2800pci
```You should be using rt3090 wireless driver. 

Open the Terminal and copy and paste each line:
```
$ sudo add-apt-repository ppa:markus-tisoft/rt3090
$ sudo apt-get update
$ sudo apt-get install dkms rt3090-dkms
```To stop the other drivers loading you will need to blacklist them:
```
$ sudo nano /etc/modprobe.d/blacklist.conf
```Add the below to the end of the blacklist.conf
> 
# Blacklist other Ralink drivers
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usbSave, exit and reboot your system - Let us know.

--
Zu

---

### Post by Bucky Ball on 2012-12-14
+1. Give ZippyUbu's ideas a try ...

---

