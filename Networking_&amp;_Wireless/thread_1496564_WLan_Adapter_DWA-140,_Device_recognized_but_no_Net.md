---
title: "WLan Adapter DWA-140, Device recognized but no Networks"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by HKei on 2010-05-29
Well, I hope the title already describes my problem. I purchased a D-Link DWA-140 USB WLan Adapter. It has an rt2870sta chipset. I downloaded the driver from Ralink, made some necessary adjustments (has_wpa and has_native_wpa y and added the Id to the Id list), and then compiled and installed the driver. The Adapter itself seems to work (the LED lights up, and the interface ra0 shows up), but I can't see any networks in the network manager (even though there are evidently around 10 visible WLan networks here). Would be great if anyone would help me, here is some of the information that the HOWTO thread requests:

$ifconfig
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:11:d8:05:0b:13  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Basisadresse:0x9800 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  Hardware Adresse 1c:af:f7:67:22:65  
          inet6-Adresse: fe80::1eaf:f7ff:fe67:2265/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2344 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:180248 (180.2 KB)

ra0:avahi Link encap:Ethernet  Hardware Adresse 1c:af:f7:67:22:65  
          inet Adresse:169.254.6.84  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
$iwconfig
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
$sudo lshw -C network
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:05:0b:13
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:ae:88:5a:e2:42
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 1c:af:f7:67:22:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.0.0 multicast=yes wireless=Ralink STA
$lsusb
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 015: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 001 Device 014: ID 0930:0b12 Toshiba Corp. 
Bus 001 Device 013: ID 07d1:3c0a D-Link System 
Bus 001 Device 012: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$lsmod
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ lsmod | grep rt
rt2870sta             562412  1 
parport                42220  2 ppdev,lp
gameport               19340  1 snd_cmipci
iTCO_vendor_support    11652  1 iTCO_wdt
snd_mpu401_uart        15104  1 snd_cmipci
snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
snd                    62628  24 saa7134_alsa,snd_cmipci,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42696  1 intel_agp
$iwlist scan
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ iwlist ra0 scan
ra0       No scan results
$lsb_release -d
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ lsb_release -d
Description:    Ubuntu 9.04
$uname -mr
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ uname -mr
2.6.28-11-generic i686
$sudo /etc/init.d/networking restart
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]

also, tried to connect manually using dhclient:
> 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo ifconfig ra0 down
[sudo] password for hannes: 
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo dhclient -r ra0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/1c:af:f7:67:22:65
Sending on   LPF/ra0/1c:af:f7:67:22:65
Sending on   Socket/fallback
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo ifconfig ra0 up
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo iwconfig ra0 essid "MY_NETWORK_SSID"
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo iwpriv ra0 set AuthMode=WPA2PSK
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo iwpriv ra0 set EncrypType=AES
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo iwpriv ra0 set WPAPSK="MYWPAPASSWORD"
hannes@hannes-desktop:~/driversrc/rt2870sta/RT2870_LinuxSTA_V2.3.0.0$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/1c:af:f7:67:22:65
Sending on   LPF/ra0/1c:af:f7:67:22:65
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by HKei on 2010-05-30
Seriously? Noone wanna help?

---

### Post by hellion_fi on 2010-06-28
Hi, 
similar problems here, at least all the outputs you posted look familiar... Did you get it to associate with an AP? I've been trying to solve this for about 5 days now, and still no joy with the associate wit ap-problem. I'm using a TeleWell USB card, which _should_ contain ralink's rt2870 chip.

---

