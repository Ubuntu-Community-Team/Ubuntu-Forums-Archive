---
title: "Wireless - Jaunty ath5K 1Mb Bit Rate"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by bwinfrey on 2009-05-30
I could really use some ideas here...

System Details Follow:

I have had Jaunty running for some time and out of nowhere the wireless started acting up on me...  

A week ago (2009-5-22) I could not authenticate to my WPA1 secured router, but I could access an unsecured router.  The machine dual boots with XP and the same problem existed there.  I removed the wireless card and tried it in another computer(XP) and it worked.  I put that computers card in this computer (they both are the same) and it worked -- for about a day.  It started connecting at 1Mb(ath5k).  

I have messed with many configurations trying to get it back to working correctly, but the best I get is using WICD & Mad WIFI at a whopping 6Mb sometimes 12Mb.


lsb-release :
```
Description:	Ubuntu 9.04
```

uname-mr :
(updated yesterday(2009-05-29) from 28-11-generic. due to this issue)
```
2.6.28-12-generic i686
```

lspci | grep -i net :
```
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
```


**With Mad WIFI ATH_PCI**
lsmod:
```
ath_rate_sample        19840  1 
ath_pci                99224  0 
wlan                  210288  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               198864  3 ath_rate_sample,ath_pci

```

dmesg:
```
[   10.376818] ath_hal: module license 'Proprietary' taints kernel.
[   10.379468] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   10.421189] ath_pci: 0.9.4
[   10.421249] ath_pci 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.004542] ath_rate_sample: 1.2 (0.9.4)
[   11.025770] udev: renamed network interface ath0 to ath1
[  139.268009] ath1: no IPv6 routers present

```

iwlist:
```
ath1      Scan completed :
          Cell 01 - Address: 00:24:56:6A:43:39
                    ESSID:"2WIRE081"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=49/70  Signal level=-46 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

lshw:
```
  *-network:1
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wifi0
       version: 01
       serial: 00:13:46:ff:ca:04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.68 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

ifconfig:
```
ath1      Link encap:Ethernet  HWaddr 00:13:46:ff:ca:04  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:feff:ca04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2158836 (2.1 MB)  TX bytes:344089 (344.0 KB)
wifi0     Link encap:UNSPEC  HWaddr 00-13-46-FF-CA-04-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16932 errors:0 dropped:0 overruns:0 frame:2821
          TX packets:2328 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3967876 (3.9 MB)  TX bytes:445709 (445.7 KB)
          Interrupt:19 

```

iwconfig:
```
ath1      IEEE 802.11g  ESSID:"2WIRE081"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:24:56:6A:43:39   
          Bit Rate:12 Mb/s   Tx-Power:21 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-44 dBm  Noise level=-95 dBm
          Rx invalid nwid:59  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
**With ATH5K**
lsmod:
```
ath5k                 107008  0 
```

dmesg:
```

[  172.187854] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  174.052609] wlan1: authenticate with AP 00:24:56:6a:43:39
[  174.054890] wlan1: authenticated
[  174.054895] wlan1: associate with AP 00:24:56:6a:43:39
[  174.056862] wlan1: deauthenticated
[  175.056026] wlan1: direct probe to AP 00:24:56:6a:43:39 try 1
[  175.057665] wlan1 direct probe responded
[  175.057670] wlan1: authenticate with AP 00:24:56:6a:43:39
[  175.059941] wlan1: authenticated
[  175.059945] wlan1: associate with AP 00:24:56:6a:43:39
[  175.061704] wlan1: deauthenticated
[  176.060030] wlan1: direct probe to AP 00:24:56:6a:43:39 try 2
[  176.061905] wlan1 direct probe responded
[  176.061910] wlan1: authenticate with AP 00:24:56:6a:43:39
[  176.063462] wlan1: authenticated
[  176.063466] wlan1: associate with AP 00:24:56:6a:43:39
[  176.065208] wlan1: deauthenticated
[  177.064023] wlan1: direct probe to AP 00:24:56:6a:43:39 try 3
[  177.065970] wlan1 direct probe responded
[  177.065974] wlan1: authentication with AP 00:24:56:6a:43:39 timed out
[  277.194273] wlan1: authenticate with AP 00:24:56:6a:43:39
[  277.195737] wlan1: authenticated
[  277.195742] wlan1: associate with AP 00:24:56:6a:43:39
[  277.197806] wlan1: RX AssocResp from 00:24:56:6a:43:39 (capab=0x431 status=0 aid=1)
[  277.197810] wlan1: associated
[  277.198139] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  287.380010] wlan1: no IPv6 routers present

```

iwlist:
```
wlan1     Scan completed :
          Cell 01 - Address: 00:24:56:6A:43:39
                    ESSID:"2WIRE081"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=82/100  Signal level:-43 dBm  Noise level=-96 dBm
                    Encryption key:on
                    IE: Unknown: 00083257495245303831
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000212e2721fe
                    Extra: Last beacon: 24ms ago

```

lshw:
```
   *-network:1
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wmaster0
       version: 01
       serial: 00:13:46:ff:ca:04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.68 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

ifconfig:
```
wlan1     Link encap:Ethernet  HWaddr 00:13:46:ff:ca:04  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:feff:ca04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14850 (14.8 KB)  TX bytes:16142 (16.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-46-FF-CA-04-61-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig:
```
wlan1     IEEE 802.11bg  ESSID:"2WIRE081"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:24:56:6A:43:39   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=79/100  Signal level:-44 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



**With out WICD/NetworkManager**
/etc/modprobe.d/blacklist-ath_pci.conf: tried both drivers
```

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath5k

```

/etc/network/interfaces : tried both drivers
```

auto lo
iface lo inet loopback


#linux driver ath5k
#auto wlan1
#iface wlan1 inet dhcp


#madwifi driver ath_pci
auto ath1
iface ath1 inet dhcp

#common
wpa-driver wext
wpa-ssid ?????????
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
#wpa-psk="###########"
wpa-psk ####################################################################

#wpa-conf /etc/network/wpa.conf

```

---

### Post by bwinfrey on 2009-05-30
Additionally, the netwok monitor applet is always showing some trafic.

Current config is Madwifi / wicd / wext

---

