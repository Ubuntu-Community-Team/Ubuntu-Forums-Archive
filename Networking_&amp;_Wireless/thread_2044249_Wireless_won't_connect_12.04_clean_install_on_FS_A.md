---
title: "Wireless won't connect: 12.04 clean install on FS Amilo L1310G -not a fsaa1655g issue"
date: 2012-08-19
forum: Networking &amp; Wireless
---

### Post by wunderbier on 2012-08-19
First post, hope it's up to snuff. Two days ago I did a clean install of lubuntu 12.04 after previously using Arch on this old hand-me-down laptop. I had wireless working in Arch using the fsaa1655g module (prevents wlan from being hardware blocked) and wicd. I've added the fsaa1655g module to lubuntu per [these instructions]("http://ubuntuforums.org/showthread.php?t=1530962") and it seems to be working fine.

I can detect wireless networks fine. Network-manager will not connect to my wireless connection however. When prompted I input my sudo password and then the WPA passkey and the little connection icon just spins and spins and then N-M asks for the passwords again. (My account is authorized to make wireless connections.)

I have not tried switching from network-manager to wicd in lubuntu. If it really might make a difference, I'll try that no problem. I've poked around the forums and the internet at large for the last couple days and I can't come up with a fix. So here's my dump of the recommended troubleshooting output...

1 ) Machine Brand and Model (PC/Laptop):
```
Fujitsu-Siemens Amilo L1310G
```2 ) Wireless Brand, Model and Wireless Chipset:
```
02:01.0 Ethernet controller: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01)
```3 ) check interface:
```
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:ad:7b:ce  
          inet6 addr: fe80::2c0:a8ff:fead:7bce/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9831 (9.8 KB)  TX bytes:13485 (13.4 KB)

iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```4 ) Check for modules:
```
lsmod | grep ath5k
ath5k                 138957  0 
ath                    19187  1 ath5k
mac80211              440734  1 ath5k
cfg80211              178818  3 ath5k,ath,mac80211

lsmod | grep fsaa1655g
fsaa1655g              12730  0

```5 ) Kernel boot messages:
```
dmesg | grep wlan0
[  167.598011] wlan0: authenticate with 00:0c:c3:cb:09:b2 (try 1)
[  167.600229] wlan0: authenticated
[  167.600797] wlan0: associate with 00:0c:c3:cb:09:b2 (try 1)
[  167.605487] wlan0: RX ReassocResp from 00:0c:c3:cb:09:b2 (capab=0x411 status=0 aid=1)
[  167.605493] wlan0: associated
[  167.605499] wlan0: moving STA 00:0c:c3:cb:09:b2 to state 1
[  167.605503] wlan0: moving STA 00:0c:c3:cb:09:b2 to state 2
[  173.811847] wlan0: deauthenticated from 00:0c:c3:cb:09:b2 (Reason: 15)
[  173.811978] wlan0: moving STA 00:0c:c3:cb:09:b2 to state 1
[  173.811982] wlan0: moving STA 00:0c:c3:cb:09:b2 to state 0
[  174.711478] wlan0: authenticate with 00:0c:c3:cb:09:b2 (try 1)
[  174.713185] wlan0: authenticated
[  174.713772] wlan0: associate with 00:0c:c3:cb:09:b2 (try 1)
[  174.720058] wlan0: RX ReassocResp from 00:0c:c3:cb:09:b2 (capab=0x411 status=0 aid=1)

```...and so on ad nauseum 

6 ) Network configuration:
```
sudo lshw -C network
*-network:0             
       description: Wireless interface
       product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:ad:7b:ce
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-29-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c0200000-c020ffff

```7 ) Scan for networks:
```
iwlist scan
Cell 02 - Address: 00:0C:C3:CB:09:B2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Elisa-09B0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000021fa3e165
                    Extra: Last beacon: 1944ms ago
                    IE: Unknown: 000A456C6973612D30394230
                    IE: Unknown: 010802048B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000027127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706465220010D10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000

```8 ) Ubuntu Version: 
```
lsb_release -d
Description:    Ubuntu 12.04.1 LTS

```9 ) Kernel/architecture (including 32 vs. 64 bit): 
```
uname -mr
3.2.0-29-generic i686

```10 ) Restarting the network:
```
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                [ OK ]
```

Cheers!

---

### Post by Turalyon on 2012-10-26
Hello Everyone,

**GOOD NEWS:**

I found a way to connect to my wireless router using Lubuntu 12.10.

**BAD NEWS:**

Step 1.  Disable **ALL** security on your wireless router (either by resetting it or through the configuration page)

Step 2. Login to your computer as you always would

Step 3.  Go to your wireless connection and choose your wireless network

Step 4. **Enter your login password from step 2 **when you are asked for a wireless athentication

I wouldn't really call this a "fix" for obvious reasons, but maybe it  will help point someone more knowledgeable about Linux into the right  direction for a real workaround. If anything this would offer a "quick  fix" temporary solution for those needing to get a working  infrastructure up and running in a hurry. 

[B]MAKE SURE:

[/B]You disable SSID Broadcast and make your network hidden if you think  you might be using this solution for a short period of time.

---

