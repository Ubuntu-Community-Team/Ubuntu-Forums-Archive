---
title: "wg311v3 installed but not working .. again !"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by MrKlean on 2009-10-24
I had this working before !!!  LOL!!  running Karmic.. latest upgrades..WiCD... card and drivers installed..wg311v3 : driver installed
	device (11AB:1FAA) present

ndis in kernal..[    7.810858] ndiswrapper version 1.55 loaded (smp=yes, preempt=no).[    8.690851] wlan0: ethernet device 00:14:6c:2d:5f:a9 using NDIS driver: wg311v3, version: 0x3010004, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[    8.690868] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
.but I get this lsmod | grep ndiswrapper
ndiswrapper           245248  0 

I also got this from network-config..


$ iwconfig wlan0 mode managed

$ iwconfig wlan0 essid "MERB527QYHJL975MPKDE100FGOM4CZ25"

$ iwconfig wlan0 rate auto

$ iwconfig wlan0 key off

$ pkill wpa_supplicant

$ wpa_supplicant -B -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant/wpa_psk.conf
Unsupported driver 'ndiswrapper'.

$ ifconfig wlan0 up

DHCP may take a while, please wait...
$ dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 28039
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:2d:5f:a9
Sending on   LPF/wlan0/00:14:6c:2d:5f:a9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Configuring device wlan0:avahi :

$ ifconfig wlan0:avahi up

DHCP may take a while, please wait...
$ dhclient wlan0:avahi
There is already a pid file /var/run/dhclient.pid with pid 28316
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device

Configuring device eth1 :

$ ifconfig eth1 down

Configuring device eth0 :

$ ifconfig eth0 down



So... it loads in the kernal, drivers and device are loaded..BUT it doesn't work.. but it does in windows !!  I had it loading before, but can't now...   HELP !!  LOL!!
Thanks !

---

### Post by edwardecl on 2009-11-06
I am also having problems with the wg311v3 and karmic. I had this working on 9.04 fine, even if I reinstall the inf driver it still don't work. I am running an ad-hoc network from ubuntu, the devices (iphone in my case) can see the network and join it but it disappears after you join it and the ESSID changes to a load of random ascii characters which nothing but itself (iwlist scan) can see. 

Setting the essid again makes in visible, but when I join the network again the same thing happens.

I'm thinking the wg311v3 just is broken in 9.10 now :(.

---

