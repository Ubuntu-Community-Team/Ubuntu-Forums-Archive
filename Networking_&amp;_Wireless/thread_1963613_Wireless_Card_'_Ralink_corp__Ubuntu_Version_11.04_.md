---
title: "Wireless Card ' Ralink corp / Ubuntu Version 11.04 / Laptop Brand Lenovo / Model Z575"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by John Merlyn on 2012-04-22
Hello, 

I am a complete noob to linux/unix and have been a windows user, but due to certain programming and other projects i have started working on ubuntu. I have dual booted Ubuntu 11.04 after installing Windows 7 64 bit. Initially i had a problem with the wifi being auto disabled when Ubuntu would boot up(i referred other links in the forum and have resolved this by blocking the acer wireless stuff, not sure what that was). Immediately after this the wifi was working fine. But the next day i.e. today a very very peculiar problem has cropped up. I am not able to see one particular wifi network, i can see other networks (which is my home wifi network on this laptop and my room mates can see it so can i on my smartphone). However the connectivity to the network on Ubuntu is on and off. It works sometimes, sometimes it detects but cant connect , while other times i can connect and others where in the network connects and then disconnects. What could be the problem ? Please help, adding requested data for analysis

1 Model

**Lenovo Z575(Laptop)**

2 Wireless

[B]Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
    Subsystem: Lenovo Device f101
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0100000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2860sta, rt2800pci[/B]


3 interface

[B]wlan0     IEEE 802.11bgn  ESSID:"nhw-1"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 02:6F:81:FB:49:B0   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/B]

4 check for modules

$ lsmod | grep "wlan_module_name" --- doesnt work


5 kernel boot messages

$ dmesg | grep "wlan"
[   12.267029] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.364079] wlan0: authenticate with 02:6f:81:fb:49:b0 (try 1)
[   29.365490] wlan0: authenticated
[   29.365551] wlan0: associate with 02:6f:81:fb:49:b0 (try 1)
[   29.369073] wlan0: RX AssocResp from 02:6f:81:fb:49:b0 (capab=0xc21 status=0 aid=3)
[   29.369078] wlan0: associated
[   29.376408] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.336238] wlan0: no IPv6 routers present
[  709.488248] ieee80211 phy0: wlan0: No probe response from AP 02:6f:81:fb:49:b0 after 500ms, disconnecting.
[  710.756547] wlan0: authenticate with 02:6f:81:fb:49:b0 (try 1)
[  710.758089] wlan0: authenticated
[  710.758292] wlan0: associate with 02:6f:81:fb:49:b0 (try 1)
[  710.761710] wlan0: RX AssocResp from 02:6f:81:fb:49:b0 (capab=0xc21 status=0 aid=3)
[  710.761721] wlan0: associated
[  798.488177] ieee80211 phy0: wlan0: No probe response from AP 02:6f:81:fb:49:b0 after 500ms, disconnecting.
[  799.756557] wlan0: authenticate with 02:6f:81:fb:49:b0 (try 1)
[  799.758027] wlan0: authenticated
[  799.758205] wlan0: associate with 02:6f:81:fb:49:b0 (try 1)
[  799.761580] wlan0: RX AssocResp from 02:6f:81:fb:49:b0 (capab=0xc21 status=0 aid=3)
[  799.761591] wlan0: associated

6 network config

sudo lshw -C network
[sudo] password for merlyn: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:bd:bc:4e
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 64:27:37:54:c6:71
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.100.26 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0100000-f010ffff
7  
iwlist scan wlan0 ---iwlist: unknown command `wlan0' (check 'iwlist --help').


8  
lsb_release -d

Description:    Ubuntu 11.04

9 uname -mr

2.6.38-8-generic i686

---

### Post by chili555 on 2012-04-22
> $ lsmod | grep "wlan_module_name" --- doesnt workWhat is meant here is:```
lsmod | grep rt2800pci
```That comes from here:> *-network
description: Wireless interface
product: RT3090 Wireless 802.11n 1T/1R PCIe
vendor: Ralink corp.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 00
serial: 64:27:37:54:c6:71
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=rt2800pci[/COLOR] driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.100.26 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
resources: irq:18 memory:f0100000-f010ffffHowever, we know the module is loaded. We'd like to know if some other competing modules are loaded, so let's [COLOR="Red"]l[/COLOR]i[COLOR="Red"]s[/COLOR]t [COLOR="Red"]mod[/COLOR]ules with any name like rt2:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Let's also see:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```Thanks.

---

### Post by John Merlyn on 2012-04-23
> **chili555 said:**
> What is meant here is:```
lsmod | grep rt2800pci
```That comes from here:However, we know the module is loaded. We'd like to know if some other competing modules are loaded, so let's [COLOR="Red"]l[/COLOR]i[COLOR="Red"]s[/COLOR]t [COLOR="Red"]mod[/COLOR]ules with any name like rt2:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Let's also see:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```Thanks.

lsmod | grep rt2
rt2860sta             494649  0 
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci

  cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
minstrel_ht

Hope that helps 

Thanks in advance

---

### Post by chili555 on 2012-04-23
You do, indeed, have two conflicting modules loaded. Let's blacklist rt2800pci:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report.

---

### Post by John Merlyn on 2012-04-23
> **chili555 said:**
> You do, indeed, have two conflicting modules loaded. Let's blacklist rt2800pci:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report.

Hi, 

I did that and then the home network (named nhw-1) was not visible in either ubuntu nor windows 7, i remove that line from the config file and then i was able to connect to the network from ubuntu. What else could we try ?

Thanks in advance

---

### Post by chili555 on 2012-04-23
You could blacklist rt2860sta instead and reboot.

---

