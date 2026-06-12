---
title: "injection"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by madunix on 2011-04-13
How can I enable wireless injection?


Linux pons-Lenovo 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58
UTC 2011 i686 GNU/Linux



sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"linksys"
         Mode:Managed  Frequency:2.457 GHz  Access Point: 00:22:6B:7B:11:AF
         Bit Rate=54 Mb/s   Tx-Power:24 dBm
         Retry min limit:7   RTS thr:off   Fragment thr:off
         Encryption key:off
         Power Managementmode:All packets received
         Link Quality=5/5  Signal level=-40 dBm  Noise level=-89 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pons@pons-Lenovo:~$ sudo airmon-ng stop eth1
[sudo] password for pons:


Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode disabled)

pons@pons-Lenovo:~$ sudo airmon-ng start eth1


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID     Name
845     avahi-daemon
846     avahi-daemon
877     NetworkManager
897     wpa_supplicant
3234    dhclient
Process with PID 3234 (dhclient) is running on interface eth1


Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode enabled)

pons@pons-Lenovo:~$ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either

---

### Post by josephmills on 2011-04-13
> **madunix said:**
> How can I enable wireless injection?


Linux pons-Lenovo 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58
UTC 2011 i686 GNU/Linux



sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"linksys"
         Mode:Managed  Frequency:2.457 GHz  Access Point: 00:22:6B:7B:11:AF
         Bit Rate=54 Mb/s   Tx-Power:24 dBm
         Retry min limit:7   RTS thr:off   Fragment thr:off
         Encryption key:off
         Power Managementmode:All packets received
         Link Quality=5/5  Signal level=-40 dBm  Noise level=-89 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pons@pons-Lenovo:~$ sudo airmon-ng stop eth1
[sudo] password for pons:


Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode disabled)

pons@pons-Lenovo:~$ sudo airmon-ng start eth1


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID     Name
845     avahi-daemon
846     avahi-daemon
877     NetworkManager
897     wpa_supplicant
3234    dhclient
Process with PID 3234 (dhclient) is running on interface eth1


Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode enabled)

pons@pons-Lenovo:~$ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either

try ```
sudo -s
``` then ```
airmon-ng
```could you then paste that here, But after pasting make sure to ```
exit
```

---

### Post by madunix on 2011-04-13
~# airmon-ng 


Interface	Chipset		Driver

eth1		Unknown 		wl

---

### Post by josephmills on 2011-04-13
how about a ```
lspci
``` and a ```
lsusb
```

---

### Post by madunix on 2011-04-13
~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


~# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 5986:0241 Acer, Inc BisonCam, NB Pro
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


my netbook is lenovo S10e

---

### Post by josephmills on 2011-04-13
how about ```
lspci -vnn | grep 14e4
```

---

### Post by madunix on 2011-04-13
~$ lspci -vnn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04b5]

---

### Post by josephmills on 2011-04-13
please take a look at this [http://www.aircrack-ng.org/doku.php?id=b43&DokuWiki=3de1b4e369cadc2b3106a2007971b43e](http://www.aircrack-ng.org/doku.php?id=b43&DokuWiki=3de1b4e369cadc2b3106a2007971b43e)

---

### Post by madunix on 2011-04-13
i will check it now

---

### Post by madunix on 2011-04-13
14e4:4315  is listed .....

---

### Post by josephmills on 2011-04-13
try ```
sudo -s 
```then```
airmon-ng stop eth1
```then```
airmon-ng start eth1
``` then ```
airmon-ng
```please paste the last one

---

### Post by madunix on 2011-04-13
modinfo b43
filename:       /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
firmware:       FW13
license:        GPL
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     5BB41D365A8D4ED2575C4B1
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,led-class,cfg80211
vermagic:       2.6.35-28-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

---

### Post by josephmills on 2011-04-13
please paste ```
airmon-ng
```

---

### Post by madunix on 2011-04-13
airmon-ng
Interface	Chipset		Driver

eth1		Unknown 		wl

---

### Post by josephmills on 2011-04-13
so when you put in airmon-ng stop (wireless card) stop stops it then you put in airmon-ng start (wireless card) starts the card in monitor mode you should get something like ```
Interface	Chipset		Driver

wlan0		Atheros 	ath5k - [phy0]
mon0		Atheros 	ath5k - [phy0]


``` but I think that you still need to read all of that link . [http://www.aircrack-ng.org/doku.php?id=b43&DokuWiki=3de1b4e369cadc2b3106a2007971b43e](http://www.aircrack-ng.org/doku.php?id=b43&DokuWiki=3de1b4e369cadc2b3106a2007971b43e) check out the part that says ** important**

---

