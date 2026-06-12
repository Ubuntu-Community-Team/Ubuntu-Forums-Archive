---
title: "TL-WNL951N ath9k not working at Wireless N Speeds"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by Cetra on 2011-01-10
Hey guys,

I've recently purchased a TP-WNL951N PCI Card for wireless N stuff.  I have a Netgear WNDR3700 for use with my AP and I've confirmed that within windows XP I can connect at 300mb/s.

Within Ubuntu though, it only goes up to 54mb/s.  Is there something special I need to do to enable wireless N speeds?

Here's some info that I should probably put in:

```

root@Linux:~# lspci -nn | grep Atheros
05:00.0 Network controller [0280]: Atheros Communications Inc. AR5008 Wireless Network Adapter [168c:0023] (rev 01)

root@Linux:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr d8:5d:4c:ad:0e:6f  
          inet addr:192.168.80.188  Bcast:192.168.80.255  Mask:255.255.255.0
          inet6 addr: fe80::da5d:4cff:fead:e6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1923191 (1.9 MB)  TX bytes:270033 (270.0 KB)


root@Linux:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Something"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 30:46:9A:FF:EF:E9   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


root@Linux:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 30:46:9A:FF:EF:E9
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Something"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000001cbacfb
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 0009536F6D657468696E67
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: IEEE 802.11i/WPA2 Version 1


root@Linux:~# lsmod | grep ath9k
ath9k                  71369  0 
ath9k_common            5719  1 ath9k
ath9k_hw              281016  2 ath9k,ath9k_common
ath                     8041  2 ath9k,ath9k_hw
mac80211              232535  2 ath9k,ath9k_common
cfg80211              146764  4 ath9k,ath9k_common,ath,mac80211
led_class               2864  1 ath9k


root@Linux:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04 LTS
Release:        10.04
Codename:       lucid

root@Linux:~# uname -mr
2.6.32-26-generic i686


```

---

### Post by Cetra on 2011-01-11
Bumperage, there seems to be another thread or two about this which also have absolutely no answer:

[http://ubuntuforums.org/showthread.php?t=1546545](http://ubuntuforums.org/showthread.php?t=1546545)
[http://ubuntuforums.org/showthread.php?t=1551021](http://ubuntuforums.org/showthread.php?t=1551021)

I tried in 10.10 and it's not working in there either.

Here's the iperf output:


```
root@Linux:~# iperf -t 0 -i 10 -c 192.168.80.99
------------------------------------------------------------
Client connecting to 192.168.80.99, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.80.188 port 53923 connected with 192.168.80.99 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  28.9 MBytes  24.3 Mbits/sec
[  3] 10.0-20.0 sec  28.6 MBytes  24.0 Mbits/sec
[  3] 20.0-30.0 sec  28.0 MBytes  23.5 Mbits/sec
[  3] 30.0-40.0 sec  28.2 MBytes  23.7 Mbits/sec
[  3] 40.0-50.0 sec  27.6 MBytes  23.1 Mbits/sec
[  3] 50.0-60.0 sec  25.5 MBytes  21.4 Mbits/sec
[  3] 60.0-70.0 sec  28.9 MBytes  24.2 Mbits/sec
[  3] 70.0-80.0 sec  28.7 MBytes  24.1 Mbits/sec
[  3] 80.0-90.0 sec  28.9 MBytes  24.2 Mbits/sec
[  3] 90.0-100.0 sec  28.9 MBytes  24.2 Mbits/sec

```

---

### Post by Cetra on 2011-01-12
Bumperage

---

### Post by Cetra on 2011-01-13
Ninja bump

---

### Post by hugmenot on 2011-01-15
Which kernel?

```
iw list
```
```
iw reg get
```
```
iw wlan0 link
```


Post dmesg of loading ath9k module.

---

### Post by hugmenot on 2011-01-15
Saw your kernel now. Could be that Lucid is a little old for N stuff. Ath9k was and still is in flux. If you look at the kernel wireless mailing list you’ll see.

---

### Post by Cetra on 2011-01-17
iw list etc.. don't seem to work.

I've compiled and used the latest ath9k driver and it still doesn't work at the 802.11n speeds

Here are the tidbits in dmesg:


```
root@Linux:~# dmesg | grep ath
[    7.916629] ath9k 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    8.345858] ath: EEPROM regdomain: 0x809c
[    8.345860] ath: EEPROM indicates we should expect a country code
[    8.345862] ath: doing EEPROM country->regdmn map search
[    8.345863] ath: country maps to regdmn code: 0x52
[    8.345864] ath: Country alpha2 being used: CN
[    8.345866] ath: Regpair used: 0x52
[    8.353504] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    8.354035] Registered led device: ath9k-phy0::radio
[    8.354048] Registered led device: ath9k-phy0::assoc
[    8.354059] Registered led device: ath9k-phy0::tx
[    8.354070] Registered led device: ath9k-phy0::rx
```

---

### Post by hugmenot on 2011-01-17
"iw" is a package. Dunno why they don’t install it by default. It’s much more informative than iwconfig.

---

### Post by hugmenot on 2011-01-17
Here’s how it should look

```
$ iw wlan0 link
Connected to 00:0c:*cough*:1c (on wlan0)
	SSID: *parrammpammpamm*
	freq: 2437
	RX: 2511045 bytes (7761 packets)
	TX: 1206664 bytes (3116 packets)
	signal: -48 dBm
	tx bitrate: 300.0 MBit/s MCS 15 40Mhz short GI

```

---

### Post by Cetra on 2011-01-20
Ok, here are the outputs:

**iw list:**
```
Wiphy phy0
        Band 1:
                Capabilities: 0x104e
                        HT20/HT40
                        SM Power Save disabled
                        RX HT40 SGI
                        No RX STBC
                        Max AMSDU length: 7935 bytes
                        DSSS/CCK HT40
                Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
                Minimum RX AMPDU time spacing: 8 usec (0x06)
                HT TX/RX MCS rate indexes supported: 0-15
                Frequencies:
                        * 2412 MHz [1] (20.0 dBm)
                        * 2417 MHz [2] (20.0 dBm)
                        * 2422 MHz [3] (20.0 dBm)
                        * 2427 MHz [4] (20.0 dBm)
                        * 2432 MHz [5] (20.0 dBm)
                        * 2437 MHz [6] (20.0 dBm)
                        * 2442 MHz [7] (20.0 dBm)
                        * 2447 MHz [8] (20.0 dBm)
                        * 2452 MHz [9] (20.0 dBm)
                        * 2457 MHz [10] (20.0 dBm)
                        * 2462 MHz [11] (20.0 dBm)
                        * 2467 MHz [12] (20.0 dBm)
                        * 2472 MHz [13] (20.0 dBm)
                        * 2484 MHz [14] (disabled)
                Bitrates (non-HT):
                        * 1.0 Mbps
                        * 2.0 Mbps (short preamble supported)
                        * 5.5 Mbps (short preamble supported)
                        * 11.0 Mbps (short preamble supported)
                        * 6.0 Mbps
                        * 9.0 Mbps
                        * 12.0 Mbps
                        * 18.0 Mbps
                        * 24.0 Mbps
                        * 36.0 Mbps
                        * 48.0 Mbps
                        * 54.0 Mbps
        max # scan SSIDs: 4
        Supported interface modes:
                 * IBSS
                 * managed
                 * AP
                 * AP/VLAN
                 * WDS
                 * monitor
                 * mesh point
                 * Unknown mode (8)
                 * Unknown mode (9)
        Supported commands:
                 * new_interface
                 * set_interface
                 * new_key
                 * new_beacon
                 * new_station
                 * new_mpath
                 * set_mesh_params
                 * set_bss
                 * authenticate
                 * associate
                 * deauthenticate
                 * disassociate
                 * join_ibss
                 * Unknown command (68)
                 * Unknown command (55)
                 * Unknown command (57)
                 * Unknown command (59)
                 * Unknown command (67)
                 * set_wiphy_netns
                 * Unknown command (65)
                 * Unknown command (66)
                 * connect
                 * disconnect
```

**iw reg get:**
```
country 00:
        (2402 - 2472 @ 40), (3, 20)
        (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
        (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

```

**iw wlan0 link:**
```
Connected to 30:46:9a:ff:ef:e9 (on wlan0)
        SSID: Something
        freq: 2427
        RX: 5665991 bytes (10194 packets)
        TX: 475978 bytes (3245 packets)
        signal: -56 dBm
        tx bitrate: 54.0 MBit/s

```

---

### Post by walt.smith1960 on 2011-01-20
I had a similar problem with N adapters running at G speed.  When I blacklisted the integral G adapter on a  notebook, my speed improved.  The only G device I have left is a wireless printer. That does not seem to cause a problem.  My router keeps track of all wireless devices that have connected to it by PC or other device's name.  I deleted the obsolete ones and now see 130 mb/sec indicated from nominal 150 mb. devices.

---

### Post by Cetra on 2011-02-07
Any clues guys?

---

### Post by andrez1 on 2011-02-07
> **hugmenot said:**
> Here’s how it should look

```
$ iw wlan0 link
Connected to 00:0c:*cough*:1c (on wlan0)
	SSID: *parrammpammpamm*
	freq: 2437
	RX: 2511045 bytes (7761 packets)
	TX: 1206664 bytes (3116 packets)
	signal: -48 dBm
	tx bitrate: 300.0 MBit/s MCS 15 40Mhz short GI

```

Why 40Mhz?

---

