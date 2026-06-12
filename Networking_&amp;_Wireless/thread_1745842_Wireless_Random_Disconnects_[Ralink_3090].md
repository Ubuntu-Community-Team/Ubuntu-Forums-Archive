---
title: "Wireless Random Disconnects [Ralink 3090]"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by the pearly gates on 2011-05-01
Hi,

I've been having issues with random disconnects of my internet connection on my desktop machine.  They occur anywhere from 5 to 30 minutes.  I'm using a Ralink RT3090 pci wireless card.

What's even stranger is that I also have a laptop having a Broadcom BCM4312 card.  That machine runs Ubuntu (either 10.10 or 11.04) while my desktop machine runs Xubuntu (again, I've tried it on either 10.10 or 11.04).  Also, I have a USB internet adapter on my PC machine where and the problem persists there.  The router that I'm on is an Asus WL-500W, and is on DD-WRT v24-sp2 (08/07/10) std - build 14896.

Given that the problem exists for various permutations of wireless cards / versions of ubuntu / machines, would you suspect that this is a router issue?

Right now I'm trying to brainstorm any ideas as to why this is happening.  In my "/var/log/syslog" I receive a "CTRL-EVENT-DISCONNECT" message when the problem happens.  Also, it seems to disconnect when I initiate *something*, i.e., click on a link in a webpage, but this not always the case.

Any help someone could provide would be invaluable to me, and I would greatly appreciate it.

Here's some network info on my desktop running xubuntu 11.04 (but again, I want to emphasize that I don't believe this is a 11.04 issue because I was having issues primarily with 10.10).

lshw -C network

```

  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 1c:65:9d:22:bb:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.1.140 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: d4:85:64:11:93:09
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff

```

ifconifg

```
eth0      Link encap:Ethernet  HWaddr d4:85:64:11:93:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30744 (30.7 KB)  TX bytes:30744 (30.7 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:22:bb:02  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe22:bb02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45261279 (45.2 MB)  TX bytes:2662543 (2.6 MB)

```


iwconfig

```
eth0      Link encap:Ethernet  HWaddr d4:85:64:11:93:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30744 (30.7 KB)  TX bytes:30744 (30.7 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:22:bb:02  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe22:bb02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45261279 (45.2 MB)  TX bytes:2662543 (2.6 MB)

root@moedown:/home/tim# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dd-wrtim"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```



Thanks,
Tim

---

### Post by chili555 on 2011-05-01
How about letting us see:```
lspci -nn 
lsmod | grep rt2
```Feel free to strip away any lines not relating to your Ralink wireless device. Thanks.

---

### Post by the pearly gates on 2011-05-01
> **chili555 said:**
> How about letting us see:```
lspci -nn 
lsmod | grep rt2
```Feel free to strip away any lines not relating to your Ralink wireless device. Thanks.

Yes, sure:

lspci -nn

```
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

```

lsmod | grep rt2

```
rt2860sta             494649  0 
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci

```

---

### Post by chili555 on 2011-05-01
> rt2860sta             494649  0 
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pciMan, that is a big pile-o-drivers you have there! Let's kick some out and see if things improve. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and let us hear a status report. Are the disconnects gone?

---

### Post by the pearly gates on 2011-05-01
> **chili555 said:**
> Man, that is a big pile-o-drivers you have there! Let's kick some out and see if things improve. Please open a terminal and do:

Proofread carefully, save and close gedit. Reboot and let us hear a status report. Are the disconnects gone?


Interesting. Thanks for the reply.  I did as you suggested and will test this out in the next couple of hours.

Do you suspect that there are other drivers in the linux kernel that are conflicting with mine?  Also, do you know why didn't "3090" show up when I ran the "lsmod | grep rt2" command?  As I understand it, lsmod lists all the drivers being used by the machine.

---

### Post by chili555 on 2011-05-01
> Do you suspect that there are other drivers in the linux kernel that are conflicting with mine?Nope, or else I would have framed my response differently.> Also, do you know why didn't "3090" show up when I ran the "lsmod | grep rt2" command?Because there is no 3090xx module. The correct module for your card is rt2860sta.```

$ modinfo rt2860sta
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
[COLOR="Red"]alias:          rt3090sta[/COLOR]
license:        GPL
description:    RT2860/[COLOR="Red"]RT3090[/COLOR] Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       [COLOR="Red"]rt3090[/COLOR].bin
firmware:       rt2860.bin
srcversion:     C22EE7282F9A519D7E9A764
--- snip ---
```> As I understand it, lsmod lists all the drivers being used by the machine.Correct.

---

### Post by the pearly gates on 2011-05-02
> **chili555 said:**
> Man, that is a big pile-o-drivers you have there! Let's kick some out and see if things improve. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and let us hear a status report. Are the disconnects gone?

Unfortunately this did not solve my problem.

Again, running

lsmod | grep rt2
```

rt2860sta             494649  1 
crc_ccitt              12595  1 rt2860sta

```

It appears as though the other modules have been successfully blocked, but sometimes I still lose connection...

---

### Post by the pearly gates on 2011-05-03
The disconnects are less frequent now, but this is the error message that I get when it does disconnect:

in the file: /var/log/syslog,

```

May  3 07:36:40 moedown wpa_supplicant[899]: CTRL-EVENT-DISCONNECTED bssid=xx:xx:xx:xx:xx:xx reason=0

```

(I've removed the actual bssid with x's)

---

