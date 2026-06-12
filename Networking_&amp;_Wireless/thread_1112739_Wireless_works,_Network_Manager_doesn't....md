---
title: "Wireless works, Network Manager doesn't..."
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by Zeosz on 2009-04-01
I got my wireless card to successfully work using ndiswrapper and some moderate trouble shooting.  The only problem I am still having is that Network Manager refuses to realize my wireless card and won't let me enable wireless or set up a connection.

lshw -C network | grep Broadcom returns:
```
WARNING: you should run this program as super-user.
       vendor: Broadcom Corporation
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

iwconfig returns:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

iwlist scan wlan0 returns
```
wlan0     Scan completed :
          Cell 01 - Address: 00:0B:86:E1:4B:20
                    ESSID:"osuwireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x

```
and about 8 other networks so I know the card is working correctly

Network Manager has enable wireless grayed out, I've tried several trouble shooting tips to no avail.  Here are some that I have tried and their results.

```
zeos@zeos:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
zeos@zeos:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
zeos@zeos:~$ sudo ifconfig wlan0 up

```
None of them have helped any.  I don't think this is a completely unique problem but I have yet to see any good advice on how to get things to work properly.

My apologies if this is a noob post, I just figured it would be best to list all available and pertinent information to help get usable advice.

Thank you in advance,
Zeosz

---

