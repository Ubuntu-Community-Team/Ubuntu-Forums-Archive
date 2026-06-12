---
title: "AR9285 problem with slow speeds"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by STUMPOFWAR on 2011-10-23
Alright....did a clean install of 11.10 64bit on a HP Pavillion G6.... 

At first my AR9285 worked at a snails pace....in Transmission I could only download torrent at 3kbs total! and I could not visit any webpage because I would time out.

I then did a few things I saw on here for other AR9285 sufferers:
1) ```
rfkill unblock all 
``` (appeared to do nothing)

2) ```
sudo gedit /etc/modprobe.d/blacklist.conf
```
and then
```
blacklist acer-wmi
``` (appeared to do nothing)

3) I also created /etc/modprobe.d/ath9k.conf and then:
```
options ath9k nohwcrypt=1
```

This greatly increased my speed but it is still running substantially slower then it did in 11.04.

I am at a loss on what to do here...I quickly installed Mageia and wireless worked fine (was curious after reading reviews)....so I then reinstalled 11.10 and same thing....

```
seliason@TELETRAAN-1:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
seliason@TELETRAAN-1:~$ uname -a
Linux TELETRAAN-1 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
seliason@TELETRAAN-1:~$ sudo lshw -C network
[sudo] password for seliason: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 05
       serial: 64:31:50:8e:3d:da
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 90:00:4e:4a:c7:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=10.130.170.220 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0200000-d020ffff


```

Any help would be appreciated!

~Shawn

---

### Post by STUMPOFWAR on 2011-10-23
Also on #2....

I saw one person had the code as

```
blacklist acer_wmi
```

rather then

```
blacklist acer-wmi
```

I did both to no avail.....

---

### Post by pastalavista on 2011-10-23
What kind of encryption do you run on wireless? I have the same wireless card in my Asus and had the same problem running under WEP security but worked almost normally after I changed it to WPA2. I still have the connection slow to almost nothing sometimes and fix it by disconnecting everywhere and reloading the driver.
```
sudo rmmod ath9k (wait a few seconds and then)
sudo modprobe ath9k
```.

---

### Post by STUMPOFWAR on 2011-10-23
Thanks for the reply.

I have WPA on the home router....I am seeing the same thing at Barnes and Noble on their free public WIFI...

Also did as you suggested:

```
sudo rmmod ath9k
```

which shut down the AR9285.....waited a minute then

```
sudo modprobe ath9k
```

....my machine immediately reconnected to Barnes and Nobles' free WIFI.... still running half-speed-ish

~Shawn

---

### Post by Nandu on 2011-10-28
Dear Folks,

I am having a similar problem with the same card AR9285. My computer connects to the wireless network at start up then drops out after a few minutes and fails to reconnect. 

It then tries to connect spending a fair amount of time trying to configure the wlan0 interface and get authorisation which it has. It then times out showing a red cross indicating failure to connect.

I look forward to any pointers on how to proceed. :-)

TIA

---

### Post by STUMPOFWAR on 2011-10-30
Sorry Tia...nothing new... it is usable but slower then before. No new news...

---

### Post by STUMPOFWAR on 2012-05-01
This issue still exists in 12.04....same work around works though.

---

