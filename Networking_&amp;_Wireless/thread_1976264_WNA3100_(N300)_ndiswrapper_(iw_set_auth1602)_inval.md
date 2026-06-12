---
title: "WNA3100 (N300) ndiswrapper (iw_set_auth:1602): invalid cmd 12"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by Master_Ne0 on 2012-05-08
Anyone have any idea's about this?

```

liam@liam-desktop:~/Downloads/N300_Installer$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 023: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 004: ID 0411:0105 MelCo., Inc. 
Bus 001 Device 021: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 001 Device 006: ID 0fce:6156 Sony Ericsson Mobile Communications AB 
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
liam@liam-desktop:~/Downloads/N300_Installer$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwlhigh5 : driver installed
	device (0846:9020) present
liam@liam-desktop:~/Downloads/N300_Installer$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

liam@liam-desktop:~/Downloads/N300_Installer$ dmesg | grep ndis
.....
[19900.965838] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[20171.016935] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[20191.094950] ndiswrapper (iw_set_auth:1602): invalid cmd 12

```

Cannot connect to the network with this.

Got ndiswrapper-source from the package manager but have no idea where it gets stored?

Was going to try and debug it, but no idea where the source gets put!!

---

