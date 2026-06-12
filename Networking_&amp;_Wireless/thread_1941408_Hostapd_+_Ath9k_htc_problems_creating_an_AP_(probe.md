---
title: "Hostapd + Ath9k_htc problems creating an AP (probereq fail)"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by ghostpoint on 2012-03-15
Hi, I'm trying to create an AP using an Atheros card (ath9k_htc) and hostapd, i have the ath9k_htc currectly installed, same as the hostapd.

I'm using Ubuntu 11.10 3.0.0-12-generic i686, and hostapd is v0.7.3.


**Lsusb**
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:5606 ALi Corp. M5606 Video Camera Controller [UVC]
Bus 002 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
```**iwconfig wlan1**
```
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```**lsmod**
```
ath9k_htc              85444  0 
ath9k_common           13781  1 ath9k_htc
ath9k_hw              376604  2 ath9k_htc,ath9k_common
ath                    19187  3 ath9k_htc,ath9k_common,ath9k_hw
mac80211              450395  2 ath9k_htc,iwlwifi
cfg80211              178955  4 ath9k_htc,iwlwifi,ath,mac80211
compat                 13892  9 bnep,rfcomm,bluetooth,ath9k_htc,ath9k_common,iwlwifi,ath9k_hw,mac80211,cfg80211
```**dmesg**
```
[   10.995610] usb 2-4: ath9k_htc: Firmware htc_9271.fw requested
[   10.995625] usbcore: registered new interface driver ath9k_htc
[   11.444482] usb 2-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   11.679476] ath9k_htc 2-4:1.0: ath9k_htc: HTC initialized with 33 credits
[   11.869957] ath9k_htc 2-4:1.0: ath9k_htc: FW Version: 1.3
[   11.869961] ath: EEPROM regdomain: 0x809c
[   11.869962] ath: EEPROM indicates we should expect a country code
[   11.869964] ath: doing EEPROM country->regdmn map search
[   11.869966] ath: country maps to regdmn code: 0x52
[   11.869967] ath: Country alpha2 being used: CN
[   11.869968] ath: Regpair used: 0x52
[   11.873990] Registered led device: ath9k_htc-phy1
```My hostapd configuration file is this :

```
interface=wlan1
driver=nl80211
ssid=test
hw_mode=g
channel=1
```The interface is currectly switched to master and the network is visible in other pcs.

When i run hostapd -d conffile.conf this is the output:

```
root@ubuntu:/home/ghost# hostapd -d hostapd_sho.conf 
Configuration file: hostapd_sho.conf
nl80211: Register Action command failed: ret=-114 (Operation already in progress)
nl80211: Register Action match - hexdump(len=1): 06
nl80211: Failed to register Action frame processing - ignore for now
nl80211: Add own interface ifindex 4
nl80211: New interface mon.wlan1 created: ifindex=17
nl80211: Add own interface ifindex 17
BSS count 1, BSSID mask 00:00:00:00:00:00 (0 bits)
nl80211: Added 802.11b mode based on 802.11g information
RATE[0] rate=10 flags=0x1
RATE[1] rate=20 flags=0x1
RATE[2] rate=55 flags=0x1
RATE[3] rate=110 flags=0x1
RATE[4] rate=60 flags=0x0
RATE[5] rate=90 flags=0x0
RATE[6] rate=120 flags=0x0
RATE[7] rate=180 flags=0x0
RATE[8] rate=240 flags=0x0
RATE[9] rate=360 flags=0x0
RATE[10] rate=480 flags=0x0
RATE[11] rate=540 flags=0x0
Completing interface initialization
Mode: IEEE 802.11g  Channel: 1  Frequency: 2412 MHz
Flushing old station entries
Deauthenticate all stations
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=(nil) key_idx=0 set_tx=1 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=(nil) key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=(nil) key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=(nil) key_idx=3 set_tx=0 seq_len=0 key_len=0
Using interface wlan1 with hwaddr b0:48:7a:8f:e0:59 and ssid 'test'
nl80211: Set beacon (beacon_set=0)
wlan1: Setup of interface done.
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'mon.wlan1' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'mon.wlan1' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Unknown event 5
Could not parse ProbeReq from 74:f0:6d:0e:1d:a4
Could not parse ProbeReq from 74:f0:6d:0e:1d:a4
Could not parse ProbeReq from 74:f0:6d:0e:1d:a4
Could not parse ProbeReq from 74:f0:6d:0e:1d:a4
Could not parse ProbeReq from 00:16:44:12:5d:14
Could not parse ProbeReq from 00:16:44:12:5d:14
Could not parse ProbeReq from 00:16:44:12:5d:14
Could not parse ProbeReq from 00:16:44:12:5d:14
Could not parse ProbeReq from 00:16:44:12:5d:14
Could not parse ProbeReq from 00:16:44:12:5d:14
Could not parse ProbeReq from 00:16:44:12:5d:14
Could not parse ProbeReq from 00:16:44:12:5d:14
Could not parse ProbeReq from 38:59:f9:1b:42:22

```Those "could not parse probereq from macaddress" messages persist.

When a client tries to connect i also get a 

```
mgmt::auth
handle_auth - too short payload (len=26)
```Id appreciate any input at all, I have no idea what's wrong with this as most of the stuff I find while browsing for problems are related to problems getting an IP from the AP or something like that...
I have tried to switch channels etc, nothing seems to work :(

Thanks in advance, and sorry for the wall of text :)

---

### Post by dimmak on 2012-03-23
I had the same issue on Arch Linux and got hostapd working by installing from git.

[http://hostap.epitest.fi/cvs.html](http://hostap.epitest.fi/cvs.html)

> 
GIT
Using git protocol: git://w1.fi/srv/git/hostap.git
  Using HTTP (if git protocol is firewalled): [http://w1.fi/hostap.git](http://w1.fi/hostap.git)
  (e.g., to get a clone of the repository you can use git with "git clone git://w1.fi/srv/git/hostap.git").
  WWW interface (gitweb) to the repository: [http://w1.fi/gitweb/gitweb.cgi]("http://hostap.epitest.fi/gitweb/gitweb.cgi")


---

### Post by RyanRahl on 2012-03-23
I think that your hostapd daemon is not starting correctly because it should put your wlan1 into master mode if you want to use it as an AP. Mine looks like this

```

iwconfig wlan0
wlan0     IEEE 802.11abgn  Mode:Master  Frequency:2.447 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```

try
```
sudo /etc/init.d/hostapd restart
```
and check the syslog

this is my working hostapd.conf file
```
interface=wlan0
driver=nl80211

ssid=test
channel=8
hw_mode=g

auth_algs=1
wpa=3
wpa_passphrase=password
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```
Your ifconfig should look something like this (without the bridging and tap interface, just look at the wlan0 parts)
```

br0       Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b8  
          inet addr:192.168.49.1  Bcast:192.168.49.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea2:6eb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4186210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3802362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:764895280 (764.8 MB)  TX bytes:3515708703 (3.5 GB)

eth0      Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b7  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea2:6eb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3801671 errors:0 dropped:3 overruns:0 frame:0
          TX packets:3122939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3549038393 (3.5 GB)  TX bytes:771610602 (771.6 MB)
          Interrupt:18 Memory:fe9e0000-fea00000 

eth1      Link encap:Ethernet  HWaddr 00:30:18:a2:6e:b8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4324774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3860348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:879266852 (879.2 MB)  TX bytes:3502760601 (3.5 GB)
          Interrupt:19 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:806227 (806.2 KB)  TX bytes:806227 (806.2 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr D4-9A-20-5A-DB-0C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:703134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74629390 (74.6 MB)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr 4e:ec:c5:41:24:55  
          inet6 addr: fe80::4cec:c5ff:fe41:2455/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1223686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7385869 (7.3 MB)  TX bytes:122054662 (122.0 MB)

wlan0     Link encap:Ethernet  HWaddr d4:9a:20:5a:db:0c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1212632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5882752 (5.8 MB)  TX bytes:168492426 (168.4 MB)


```
Setting up an AP is usually pretty straightforward, post back the results and we should be able to get this solved.

---

