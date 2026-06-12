---
title: "Linksys WUSB11 V2.6 802.11b Adapter"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by rkphibb on 2009-02-03
I have read through all of the links I can find including:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I installed CVS as detailed here:

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)

and played around here:

[http://ubuntuforums.org/showthread.php?t=943848](http://ubuntuforums.org/showthread.php?t=943848)

I have no security, ESSID is simply linksys

Here are my outputs:

lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

/etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys

sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:03:3E:AA
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Signal level=90/100  
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s


ndiswrapper -l
lswlusb : driver installed

Latest version of ubuntu:  uname -a
2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:06:25:08:37:77
Sending on   LPF/wlan0/00:06:25:08:37:77
Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:06:25:08:37:77  
          inet6 addr: fe80::206:25ff:fe08:3777/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:26230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5239558 (5.2 MB)  TX bytes:1120596 (1.1 MB)


What am I missing?  Can anyone steer me in the right direction?

Thanks.

---

### Post by rkphibb on 2009-02-03
Oh I forgot this:
lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

---

### Post by rkphibb on 2009-02-03
More output

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:16:76:b3:c0:07
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.104 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:06:25:08:37:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.2-84 wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 4e:9b:c9:c4:dd:fb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by rkphibb on 2009-02-03
I think my problem lies here?

dmesg | grep -e ndis -e wlan
[   15.484560] at76_usb: wlan0 disconnecting
[   16.438742] at76_usb: registered wlan0
[   98.616026] wlan0: no IPv6 routers present

---

### Post by rkphibb on 2009-02-03
I fixed this.

Any help???

ndiswrapper -l
netusb : driver installed
	device (077B:2219) present (alternate driver: at76_usb)

---

### Post by rkphibb on 2009-02-03
And this

dmesg | grep -e ndis -e wlan
[   13.127993] at76_usb: registered wlan0
[   14.080699] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.126176] usbcore: registered new interface driver ndiswrapper

---

### Post by mb_webguy on 2009-02-03
It looks to me that the at76_usb is claiming your wireless.  Is that the driver you're trying to use?  Have you followed the [ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847")?

---

### Post by rkphibb on 2009-02-04
> **mb_webguy said:**
> It looks to me that the at76_usb is claiming your wireless.  Is that the driver you're trying to use?  Have you followed the [ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847")?

Yes I believe that's the driver I am trying to use and yes I went through the troubleshooting guide.  Does anything in my output look wrong?

---

