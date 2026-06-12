---
title: "i've tried b43 and sta driver for broadcom, no luck Please Help"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2011-04-23
hi, im using a hp pavillion entertainment pc dv2 1030us and have installed the b43 and sta wifi drivers with no luck.

the drivers say they work and are active, but no networks will pull up. i know for sure this network is setup fine, there has been another laptop connect to its wifi

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by josephmills on 2011-04-23
you have a bcm4322 it is not supported by b43 sorry googling.....

---

### Post by josephmills on 2011-04-23
did you try [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by josephmills on 2011-04-23
could we please see a ```
dmesg | grep b43 
```

---

### Post by slixz85 on 2011-04-26
02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

---

### Post by BertN45 on 2011-04-26
> **slixz85 said:**
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

According the synaptic package manager the BCM4322 is NOT in the list of supported hardware for the B43 drivers. So you probably have to stick to the STA driver.
I assume that you deactivated the STA driver when you did try the b43 driver and removed the b43 driver when you tried the STA driver.
I see two possibilities to get a working wifi:
- download the source from the broadcom side and follow their instructions to generate the driver.
- download ndiswrapper (synaptic package manager) and use the windows XP driver.

---

### Post by slixz85 on 2011-04-26
yes i have tried them one at a time, the sta says it works fine but i just see no networks and this laptop worked with windows vista wifi fine

i have tried ndiswrapper as well

the system is installed to a flash drive, the hard drive gave out in it and it has been take out.

lsmod | grep "b43\|ssb\|wl"
wl 1959565 0 
lib80211 5058 2 lib80211_crypt_tkip,wl

lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11 Access Point: Not-Associated 
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0



eth0 Link encap:Ethernet HWaddr 00:21:cc:3a:30:55 
inet addr:192.168.1.121 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::221:ccff:fe3a:3055/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1703 errors:0 dropped:0 overruns:0 frame:0
TX packets:1570 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1531676 (1.5 MB) TX bytes:303632 (303.6 KB)
Interrupt:43 Base address:0x4000 

eth1 Link encap:Ethernet HWaddr 00:25:56:39:81:27 
inet6 addr: fe80::225:56ff:fe39:8127/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:272 errors:0 dropped:0 overruns:0 frame:0
TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:20136 (20.1 KB) TX bytes:20136 (20.1 KB)

---

### Post by BertN45 on 2011-04-26
It looks like your system has two Ethernet LAN connections? Or did you install something related to P2P networking? 

In your last data I did see two Ethernet connections but absolutely no wifi, normally it should show wlan0 and eth0. It might be caused by your wifi card being seen as a wired Ethernet controller, looks that plausible?

Could you supply the complete lsmod list with the STA driver activated?

---

### Post by BertN45 on 2011-04-27
eth1 IEEE 802.11 Access Point: Not-Associated 
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

Just saw this info, so eth1 is your wifi controller, but I did not see a loaded driver module yet.

---

### Post by josephmills on 2011-04-27
please take out your ipaddress but could we see a ```
sudo lshw -C network
```
thanks

---

### Post by BertN45 on 2011-04-27
I've found next link seems to solve the issue:

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

---

### Post by slixz85 on 2011-04-27
thanks to your guys input so far, here is the network info joseph has the code for, i am also a newbie to linux as well. here is the network info joseph said to post

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:cc:3a:30:55
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.121 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:a000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff

---

### Post by josephmills on 2011-04-27
please click on this link it will download you firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``` then tell us when you get that far

---

### Post by slixz85 on 2011-04-27
ok if your certain this could work i will try it, and appreciate your help, however broadcom and other posters before in the forums have told me to use the sta only?

---

### Post by josephmills on 2011-04-27
> **slixz85 said:**
> ok if your certain this could work i will try it, and appreciate your help, however broadcom and other posters before in the forums have told me to use the sta only?

you dont have to do anything but please take a look at this [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by josephmills on 2011-04-27
> **slixz85 said:**
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller **[14e4:432b] **(rev 01)
important

---

### Post by slixz85 on 2011-04-27
this has been confusing with this wifi card, im about to try this b43 driver again but i have blacklisted b43,ssb and something else that broadcom said to do. so i dont know how to unblacklist. im new to linux commands so bear with me

---

### Post by josephmills on 2011-04-27
ok lets see what is loaded ```
lsmod b43 | grep 
``` ```
dmesg | grep b43
```

---

### Post by josephmills on 2011-04-27
also lets see whats blacklisted ```
cat /etc/modprobe.d/blacklist.conf

```

---

### Post by slixz85 on 2011-05-08
thanks so far everyone unfortunately no help. i have googled and found another site that had the wlan0 as eth1 which is what mine looks like to me, right?

sudo lshw -C Network
  *-network DISABLED      
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:39:81:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:cc:3a:30:55
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.117 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:a000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff

because iwconfig shows this 


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


^wlan0 is supposed to be in here right?

---

### Post by alfu on 2012-05-17
I just installed 12.04 on a dv2-1030us. No problem with wireless if you do this:

Boot from a 64 bit AMD 12.04 live CD.
From 'Dash Home' select 'Installed'.  Click on 'See 80 more results'
Click on 'Additional Drivers'.  Activate the STA Wireless driver.
On 'Close' you will be asked to re-boot.  

Since I had started from the live CD, I thought this installation would disappear on reboot, so I did a suspend, instead.  On re-awakening, clicking a combination of 'Enable Wireless' and 'Enable Networking' got the WiFi channels showing up.

I did the install with wireless enabled, and no problems with it after that. :)

---

