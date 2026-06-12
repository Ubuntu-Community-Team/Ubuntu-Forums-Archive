---
title: "Atheros AR5001 flaky connection (11.04, Samsung NC10)"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by napi on 2011-08-16
Hello all,

I'm having some issues with the wireless on my laptop.

Recently downloaded and installed Ubuntu 11.04. Apart from wireless, no problems.

It will connect to networks, but the connection is VERY flaky - the connection drops continually every 10-15 seconds. But, sometimes after ~20-30 minutes of this, it gets a stable connection and is good for perhaps a few hours. I haven't noticed any sort of pattern with time of day / network activity / laptop activity connecting the issue with the stability (not ruling it out, just that I've not noticed).

The network in question is secured with WPA2. Unfortunately I'm not allowed to turn the security off, but I connected to an open wifi hotspot run from my phone and had no connection issues.

As suggested in [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) here are some details:

Laptop: Samsung NC10

lspci:
```
02:00 0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

iwconfig: (disconnected)
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

iwconfig: (connected)
```
wlan0     IEEE 802.11bg  ESSID:"kizingoninet4"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: C0:C1:C0:09:E3:74   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:29   Missed beacon:0
```

```
matt@indigo:~$ lsmod | grep ath
ath5k                 144412  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
```

Snippet from dmesg
```
[ 1095.363227] wlan0: authenticate with c0:c1:c0:09:e3:74 (try 1)
[ 1095.371833] wlan0: authenticated
[ 1095.371944] wlan0: associate with c0:c1:c0:09:e3:74 (try 1)
[ 1095.374402] wlan0: RX AssocResp from c0:c1:c0:09:e3:74 (capab=0x411 status=0 aid=3)
[ 1095.374418] wlan0: associated
[ 1095.378838] wlan0: deauthenticating from c0:c1:c0:09:e3:74 by local choice (reason=3)
[ 1095.383474] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1095.383500] cfg80211: Restoring regulatory settings
[ 1095.383630] cfg80211: Calling CRDA to update world regulatory domain
[ 1095.402478] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 1095.402504] cfg80211: World regulatory domain updated:
[ 1095.402514] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1095.402530] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1095.402545] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1095.402559] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1095.402573] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1095.402587] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1096.355913] wlan0: authenticate with c0:c1:c0:09:e3:74 (try 1)
[ 1096.366330] wlan0: authenticatedpo
[ 1096.366449] wlan0: associate with c0:c1:c0:09:e3:74 (try 1)
[ 1096.378429] wlan0: RX AssocResp from c0:c1:c0:09:e3:74 (capab=0x411 status=0 aid=3)
[ 1096.378445] wlan0: associated
[ 1096.381983] wlan0: deauthenticating from c0:c1:c0:09:e3:74 by local choice (reason=3)
[ 1096.396356] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1096.396380] cfg80211: Restoring regulatory settings
[ 1096.396508] cfg80211: Calling CRDA to update world regulatory domain
[ 1096.419313] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 1096.419332] cfg80211: World regulatory domain updated:
[ 1096.419339] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1096.419350] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1096.419360] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1096.419370] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1096.419381] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1096.419391] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1096.486963] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1096.692208] sky2 0000:03:00.0: eth0: disabling interface
[ 1096.711331] sky2 0000:03:00.0: eth0: enabling interface
[ 1096.713338] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

```
iwlist scan:
wlan0     Scan completed :
          Cell 01 - Address: C0:C1:C0:09:E3:74
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"kizingoninet4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022d3c71183
                    Extra: Last beacon: 64316ms ago
                    IE: Unknown: 000D6B697A696E676F6E696E657434
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180204F0000000
                    IE: Unknown: DD180050F202010185000364000027A4000041435E0061322F00

```

```
matt@indigo:~$ uname -mr
2.6.38-10-generic i686
```

```
matt@indigo:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                        Ignoring unknown interface wlan0=wlan0.
                                                                                                                       [ OK ]
```

```
matt@indigo:~$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
```


I tried disabling network manager and using wicd instead - wicd could see the network fine, but refused to connect - failed to authenticate every time saying bad password (definitely put in the right one)

I'm unsure what to do next - the various threads I've found are suggest different things:

Change to the ath5k drivers (older threads from 2008/2009, often claiming that ath5k fixes this problem)
Turn off power management (mine is off, but I get an error if I try to set it on or off)
Use Wicd (tried, no success)

I know the signal for the network isn't great, but connection is stable and steady in win7 and my phone stays on at the same spot.

Any advice / suggestions are greatly appreciated!

---

### Post by Bucky Ball on 2011-08-16
Try using MadWifi instead of Network Manager. 

[http://madwifi.org/](http://madwifi.org/)

Sorry, that is the old one, try this:

[http://madwifi-project.org/](http://madwifi-project.org/)

And this tells you all about it:

[http://madwifi-project.org/wiki/About/MadWifi](http://madwifi-project.org/wiki/About/MadWifi)

---

### Post by napi on 2011-08-26
That worked great thanks very much :)

---

