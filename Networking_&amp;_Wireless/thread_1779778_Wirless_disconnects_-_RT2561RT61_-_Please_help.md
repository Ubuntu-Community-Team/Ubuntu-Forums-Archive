---
title: "Wirless disconnects - RT2561/RT61 - Please help"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by ratibars on 2011-06-10
I badly need help. I have been struggling with wireless  disconnection problem for a long time. It will randomly disconnect  particularly while I'm watching youtube videos. Got a MSI PC60G card.


Looking at your other replies I have added a these items to the  blacklist.conf file. But it still doesn't seem to solve the issue:

blacklist rt2800pci
blacklist rt2x00usb
blacklist rt3390sta
blacklist rt2860sta
blacklist rt2800lib

And here are some commands' results:

[SIZE=3]**lspci -v | less**[/SIZE]

03:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Micro-Star International Co., Ltd. Device b834
        Flags: bus master, slow devsel, latency 32, IRQ 21
        Memory at fdcf0000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
        Kernel driver in use: rt61pci
        Kernel modules: rt61pci


**[SIZE=3]sudo lshw -C network[/SIZE]**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:dd:20:a1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
       resources: irq:41 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdae0000-fdaeffff memory:fda00000-fda0ffff
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 00
       serial: 00:24:21:8c:53:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci  driverversion=2.6.38-8-generic firmware=0.8 ip=192.168.0.101 latency=32  link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:fdcf0000-fdcf7fff

[SIZE=3]**sudo lshw -C network**[/SIZE]
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:dd:20:a1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
       resources: irq:41 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdae0000-fdaeffff memory:fda00000-fda0ffff
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 00
       serial: 00:24:21:8c:53:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci  driverversion=2.6.38-8-generic firmware=0.8 ip=192.168.0.101 latency=32  link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:fdcf0000-fdcf7fff

**[SIZE=3]lsmod | grep rt2[/SIZE]**
rt2x00pci              13986  1 rt61pci
rt2x00lib              39075  2 rt61pci,rt2x00pci
mac80211              257001  2 rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211

[SIZE=3]**iwconfig**[/SIZE]

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"kanini"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:BF:0E:6D   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:2213   Missed beacon:0

```

---

### Post by chili555 on 2011-06-11
There is not much you can do. The rt2500-, rt61- and rt73-series have always been a bit twitchy and troublesome. I suggest you install compat-wireless. Here is the procedure: [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

In order to compile this, you will first need to install the prerequisites:```
sudo apt-get install linux-headers-generic build-essential
```In the driver-select section in the link I provided, you will select rt61pci.

After it's all done, reboot and let us have your report. If you don't understand or get stuck, post back. I will respond as soon as I can.

---

### Post by ratibars on 2011-06-11
Thanks Chili. Going out for the weekend. Will try once I come back and post the results.

---

### Post by ratibars on 2011-06-11
Chili,I did all that you suggested but the driver-select did not list rt61pci. So I went ahead with install and rebooted but the problem still persists.

Here is what I did:

Downloaded compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2cd compat-wireless-2011-06-01

make

sudo make install

---

### Post by chili555 on 2011-06-12
Let's see:```
modinfo rt61pci
```I'd like to see if the module built as expected.

---

### Post by ratibars on 2011-06-12
I forgot to mention two commands that I executed which are:

sudo apt-get install linux-headers-generic build-essential

sudo modprobe rt61pci (or something similar - this was instructed at the end when I ran the sudo make install command)


Here is the result for

modinfo rt61pci

```
modinfo rt61pci
filename:       /lib/modules/2.6.38-8-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B83AB64D509586953986FF9
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6,crc-itu-t
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```

---

### Post by chili555 on 2011-06-14
It looks like it compiled perfectly. If it's still not performing correctly, I suggest we write a conf file:```
sudo gedit /etc/modprobe.d/rt61pci.conf
```Add one line.```
options rt61pci nohwcrypt=1
```Proofread carefully, save and close gedit. After a reboot, is the performance better, the same or worse? If it's worse, remove the file:```
sudo rm /etc/modprobe.d/rt61pci.conf
```

---

### Post by ratibars on 2011-06-14
Thanks Chili. I did that and even after that the performance is same (doesn't seem to be worse until now). 

One thing I want to mention is that whenever the Internet disconnects the whole wifi connection to all the computers at my home gets disconnected. In other words the router or cable modem itself seems to gets disconnected (and then connects again). But there is nothing wrong with the router or modem as they work perfectly if I don't use the Ubuntu machine (that too only when that machine is being used to watch youtube or for file downloading).

---

### Post by chili555 on 2011-06-15
I have no further ideas. I'm sorry I could not be of more help.

---

### Post by ratibars on 2011-06-17
Chili, not a problem. Thanks very much for your help.

---

