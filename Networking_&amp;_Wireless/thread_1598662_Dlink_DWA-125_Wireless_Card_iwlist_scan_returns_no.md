---
title: "Dlink DWA-125 Wireless Card iwlist scan returns no result and I cannot connect..."
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by EmreSevinc on 2010-10-16
Hello,

I'm trying to connect to my wireless connection using my D-Link DWA-125   (N 150) Wireless USB Adapter. So far I was able to download, compile  and  install the driver provided by RALINK. The current situation is:

```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```I assume that I'm using the correct driver, right?:

```
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I'm trying to up the ra0 interface and then do a scan, but I cannot see any networks:

```
$ sudo ifconfig ra0 up

$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:11:2f:e9:81:08  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fee9:8108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5241984 (5.2 MB)  TX bytes:886749 (886.7 KB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ra0       Link encap:Ethernet  HWaddr f0:7d:68:14:19:b0  
          inet6 addr: fe80::f27d:68ff:fe14:19b0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:858032 (858.0 KB)

ra0:avahi Link encap:Ethernet  HWaddr f0:7d:68:14:19:b0  
          inet addr:169.254.6.94  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results
```I also tried to "down" the eth0, again   no list scan result. I even tried from the Network Manager to connect to   a hidden network (even though it is not hidden, e.g. I can see my   network when I click on the Network Manager applet running on another   laptop, it lists my network among available networks and I can easily   connect) but without success. The point is this: I cannot see any  wireless networks when I click on the NM applet, I only see Wired  Network Auto eth0  and then Wireless networks disconnected and no list  of networks :sad:

Here's some probably relevant output from $ sudo cat /var/log/syslog | grep -i network:

```

Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'ssid' value 'emretanya'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'scan_ssid' value '1'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'psk' value '<omitted>'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]:   nm_setting_802_1x_get_pkcs11_engine_path: assertion   `NM_IS_SETTING_802_1X (setting)' failed
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]:   nm_setting_802_1x_get_pkcs11_module_path: assertion   `NM_IS_SETTING_802_1X (setting)' failed
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: set interface ap_scan to 2
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  disconnected -> scanning
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  associating -> disconnected
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  disconnected -> scanning
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0/wireless): association took too long.
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0/wireless): asking for new secrets
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  associating -> disconnected
Oct 17 01:51:30 yusuf-desktop NetworkManager[1694]: <warn> (ra0): link timed out.
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <info> (ra0): device state change: 6 -> 9 (reason 7)
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0) failed for access point (emretanya)
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <info> Marking connection 'emretanya' invalid.
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <warn>   Activation (ra0) failed.
```Am I missing something, or doing   something wrong?

I'm using Ubuntu 10.10 with latest updates and:

```
$ uname -a
Linux yusuf-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

```Also the led light on my adapter is flashing constantly (I take   this as a sign that is somehow active because before I installed the   driver correctly it was not flashing).

I also copied RT2870STA.dat to /etc/Wireless/RT2870STA/ and did not change it, so it is as below:
```

#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0
```

---

### Post by vel_tins on 2010-11-07
exactly the same problem here, but with ubuntu 10.4
Any ideas?

---

### Post by rk_misra on 2010-11-30
> **EmreSevinc said:**
> Hello,

I'm trying to connect to my wireless connection using my D-Link DWA-125   (N 150) Wireless USB Adapter. So far I was able to download, compile  and  install the driver provided by RALINK. The current situation is:

```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```I assume that I'm using the correct driver, right?:

```
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I'm trying to up the ra0 interface and then do a scan, but I cannot see any networks:

```
$ sudo ifconfig ra0 up

$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:11:2f:e9:81:08  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fee9:8108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5241984 (5.2 MB)  TX bytes:886749 (886.7 KB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ra0       Link encap:Ethernet  HWaddr f0:7d:68:14:19:b0  
          inet6 addr: fe80::f27d:68ff:fe14:19b0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:858032 (858.0 KB)

ra0:avahi Link encap:Ethernet  HWaddr f0:7d:68:14:19:b0  
          inet addr:169.254.6.94  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results
```I also tried to "down" the eth0, again   no list scan result. I even tried from the Network Manager to connect to   a hidden network (even though it is not hidden, e.g. I can see my   network when I click on the Network Manager applet running on another   laptop, it lists my network among available networks and I can easily   connect) but without success. The point is this: I cannot see any  wireless networks when I click on the NM applet, I only see Wired  Network Auto eth0  and then Wireless networks disconnected and no list  of networks :sad:

Here's some probably relevant output from $ sudo cat /var/log/syslog | grep -i network:

```

Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'ssid' value 'emretanya'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'scan_ssid' value '1'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'psk' value '<omitted>'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]:   nm_setting_802_1x_get_pkcs11_engine_path: assertion   `NM_IS_SETTING_802_1X (setting)' failed
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]:   nm_setting_802_1x_get_pkcs11_module_path: assertion   `NM_IS_SETTING_802_1X (setting)' failed
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: set interface ap_scan to 2
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  disconnected -> scanning
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  associating -> disconnected
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  disconnected -> scanning
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0/wireless): association took too long.
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0/wireless): asking for new secrets
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  associating -> disconnected
Oct 17 01:51:30 yusuf-desktop NetworkManager[1694]: <warn> (ra0): link timed out.
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <info> (ra0): device state change: 6 -> 9 (reason 7)
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0) failed for access point (emretanya)
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <info> Marking connection 'emretanya' invalid.
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <warn>   Activation (ra0) failed.
```Am I missing something, or doing   something wrong?

I'm using Ubuntu 10.10 with latest updates and:

```
$ uname -a
Linux yusuf-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

```Also the led light on my adapter is flashing constantly (I take   this as a sign that is somehow active because before I installed the   driver correctly it was not flashing).

I also copied RT2870STA.dat to /etc/Wireless/RT2870STA/ and did not change it, so it is as below:
```

#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0
```

you need to change SSID=11n-AP to your wireless ssid value, also modify 

AuthMode=OPEN
EncrypType=NONE

If you are using WPA2 please set

AuthMode=WPA2PSK
EncrypType=AES

If you are using WPA

Please set

AuthMode=WPAPSK
EncrypType=TKIP

Hope above will help.

---

### Post by alistair1946 on 2011-05-23
Hi. As a 65yr nube I wish to say a big THANKS for providing this info. I have been trying endlessly to remedy non connect issues with my D-Link DWA125n Vs a2 Dongle without permanent success until now. I changed the SSIP entry to my WAP ID and the WPA2PSK and TKIP entries as suggested and immediate success.:smile:

---

