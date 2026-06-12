---
title: "How to Get Kismet to Recognize My Wireless"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by pizzaholic on 2010-12-03
I'm trying to get Kismet up and running with Ubuntu 10.10 and I'm using an Atheros AR928X, but I don't know what to put in the etc/kismet/kismet.conf file under the line **source=**

Do I need to install madwifi drivers, or are the drivers that come with Ubuntu sufficient enough? I've been reading other forums and on Google that I should put **source=madwifi_g,ath0,madwifi **but my device is not ath0, it's wlan0 as shown with the lspci command.

[B]Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (madwifi): Enabling monitor mode for madwifi_g source interface wlan0 channel 6...
ERROR:  Unable to create VAP: Operation not supported
ERROR:  Unable to create monitor-mode VAP
WARNING: wlan0 appears to not accept the Madwifi-NG controls. Will  attempt to configure it as a standard Madwifi-old interface. If you are  using madwifi-ng, be sure to set the source interface to the wifiX  control interface, NOT athX
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
Done.
[/B]
In some [other forum]("http://ubuntuforums.org/showthread.php?t=1186348")  on UbuntuForums someone said to make some changes under  SYSTEM>>ADMINISTRATION>>HARDWARE DRIVERS, but I don't have  HARDWARE DRIVERS under that submenu. I don't see an option for it  anywhere in my version of Ubuntu (Maverick 10.10).

Thanks.

---

### Post by chili555 on 2010-12-03
```
my device is not ath0, it's wlan0 as shown with the lspci command.
```Please show me. Also, please let us see:```
sudo lshw -C network
```You might take a look at:```
less /usr/share/doc/kismet/README.gz
```Especially see Section 12.

---

### Post by pizzaholic on 2010-12-03
[B]lspci

[/B]```
inkzoid@ZOIDDG-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```**sudo lshw -C network**

```
inkzoid@ZOIDDG-PC:~$ sudo lshw -C network
[sudo] password for inkzoid: 
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:03:7f:8e:5c:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-23-generic firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f1200000-f120ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:26:9e:55:f5:b0
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:45 ioport:2000(size=256) memory:f1004000-f1004fff memory:f1000000-f1003fff memory:f1010000-f101ffff

```I'm going through the included documentation again as well.

---

### Post by chili555 on 2010-12-03
> should put source=madwifi_g,ath0,madwifi > description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: [COLOR="Red"]wlan0[/COLOR]
       version: 01
       serial: 00:03:7f:8e:5c:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR="Red"]ath9k[/COLOR] I believe I might try:```
source=ath9k,wlan0,Atheros
```The documentation doesn't mention *ath9k* as a supported driver, but give it a try and post any errors or warnings.

---

### Post by pizzaholic on 2010-12-03
Using **source=madwifi_g,ath0,madwifi**:

```
inkzoid@ZOIDDG-PC:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (madwifi): Enabling monitor mode for madwifi_g source interface ath0 channel 6...
ERROR:  Unable to create VAP: No such device
ERROR:  Unable to create monitor-mode VAP
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: GetIFFlags: interface ath0: No such device
debug - open failed: /sys/class/net/ath0/device/ No such file or directory
Done.

```

**Using source=ath9k,wlan0,Atheros**:

```
inkzoid@ZOIDDG-PC:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ath9k' in source 'ath9k,wlan0,Atheros'
Done.

```

A few hours back I put in **source=hostap,wlan0,Atheros** and got:

```
inkzoid@ZOIDDG-PC:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Atheros): Enabling monitor mode for hostap source interface wlan0 channel 6...
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
Done.

```

---

### Post by chili555 on 2010-12-04
Can you put the interface in monitor mode manually and then run kismet?```
sudo iwconfig wlan0 mode monitor
sudo kismet
```

---

### Post by pizzaholic on 2010-12-04
```
inkzoid@ZOIDDG-PC:~$ sudo iwconfig wlan0 mode monitor
[sudo] password for inkzoid: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

```

Does this mean that I have one of the unsupported wireless cards that simply won't go into monitor mode?

---

### Post by chili555 on 2010-12-04
> SET failed on device wlan0 ; Device or resource busy.Please try to take the interface down first:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo kismet
```If it doesn't work this time, then...> Does this mean that I have one of the unsupported wireless cards that simply won't go into monitor mode? ...probably yes.

---

### Post by pizzaholic on 2010-12-04
[B]inkzoid@ZOIDDG-PC:~$ sudo ifconfig wlan0 down
inkzoid@ZOIDDG-PC:~$ sudo iwconfig wlan0 mode monitor
inkzoid@ZOIDDG-PC:~$ sudo kismet[/B]
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Atheros): Enabling monitor mode for hostap source interface wlan0 channel 6...
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
Done.
**inkzoid@ZOIDDG-PC:~$ **

---

### Post by pizzaholic on 2010-12-04
Just running a Google search to see what this ioctls 95 error code is all about

---

### Post by pizzaholic on 2010-12-05
Hey chill555 I hear that there are no compatibility issues with this card (also identified as 5009) with BackTrack...downloading it now...what's your take on that?

---

### Post by spiky001 on 2010-12-05
Have you edited the Kismet config file and added your card? Have a look at top part of post [http://www.ubuntugeek.com/kismet-an-802-11-wireless-network-detector-sniffer-and-intrusion-detection-system.html](http://www.ubuntugeek.com/kismet-an-802-11-wireless-network-detector-sniffer-and-intrusion-detection-system.html)

---

### Post by chili555 on 2010-12-05
> **pizzaholic said:**
> Hey chill555 I hear that there are no compatibility issues with this card (also identified as 5009) with BackTrack...downloading it now...what's your take on that?I have no experience with the Atheros 9xx cards directly; just what I read here. I will be interested in your report.

---

### Post by pizzaholic on 2010-12-07
> **chili555 said:**
> I have no experience with the Atheros 9xx cards directly; just what I read here. I will be interested in your report.

Well look at that! Works right out of the box when using BackTrack 4. I can see some local wireless connections listed so I know it's working properly. Only downside is that I have no Internet on BT4 and apparently it is set up using some kinda WPA supplicant file (I'm using WPA) that is going to take me quite a long time to understand and configure.

---

### Post by pizzaholic on 2010-12-07
I is on zee Internets. Didn't need any wpa supplicant file. I just connected manually to my wireless connection in Wicd. Go figure.

---

### Post by chili555 on 2010-12-07
There is no doubt that the Atheros 9xx cards connect to the internet in Ubuntu. I thought the issue was whether they could be placed in monitor mode and therefor use Kismet.

---

### Post by pizzaholic on 2010-12-07
Yeah sorry for the confusion heh I just had a problem with connecting to the net in BackTrack4 and included that little rant in this thread by accident.  I couldn't get the wireless card to go into monitor mode using Ubuntu so I installed BackTrack4 instead, and it worked perfectly right out of the box. Not sure why that is but it worked.

---

