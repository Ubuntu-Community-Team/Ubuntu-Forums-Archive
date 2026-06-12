---
title: "Can't connect to 802.11n Network , controller: RaLink RT2800"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by bowens44 on 2009-08-22
I am running jaunty. I have a trendnet 300Mbps Dual Band wireless router (TEW-671BR) I have a trendnet TEW-623PI wireless adapter.

kernel 2.6.28-15-generic #49-Ubuntu SMP

The card is recognized by jaunty but will not connect if I set my router to 802.11n only. It connects if I set router to 802.11b/g/n

If i put the adapter in a windows machine it connects at 207Mbps so I am confident that the card and router are working properly. I suspect it's either a driver issue or a configuration issue.

I would like to get this working for 802.11n 

Here's some info:

lshw
```
 *-network:0             
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: ra0
       version: 00
       serial: 00:14:d1:5c:b8:16
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.5.100 latency=32 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"TRENDnet671N"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:D1:AA:15:B8   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-62 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
lspci -v
```
01:07.0 Network controller: RaLink RT2800 802.11n PCI
	Subsystem: RaLink Device 2860
	Flags: bus master, slow devsel, latency 32, IRQ 19
	Memory at e7000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta
```
iwlist scan
```
ra0       Scan completed :
          Cell 01 - Address: 00:14:D1:AA:15:B8
                    ESSID:"TRENDnet671N"
                    Mode:Managed
                    Channel:11
                    Quality:76/100  Signal level:-60 dBm  Noise level:-71 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
```

I see this in dmesg```

 36.271147] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   36.271157] 1. Phy Mode = 0
[   36.271161] 2. Phy Mode = 0
[   36.286527] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   36.291175] 3. Phy Mode = 0
[   36.294602] MCS Set = 00 00 00 00 00
[   36.296166] <==== RTMPInitialize, Status=0
[   36.296234] 0x1300 = 00073200
[   41.335028] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[   46.996017] ra0: no IPv6 routers present
[   61.261605] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[   91.262669] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[   94.496993] ondemand governor failed, too long transition latency of HW, fall
back to performance governor
[  131.266772] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[  181.263833] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[  241.257256] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[  361.264102] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[  372.668824] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[  372.669279] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  421.268469] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[  461.272718] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
[  521.275812] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 88
```

---

### Post by bowens44 on 2009-08-23
No suggestions anyone?

---

### Post by themystic.ca on 2009-08-24
Hi,

I had the same problem with the RaLink driver and an 802.11g network. I switched to the 2.6.28-11-generic kernel. It's in apt/synaptic.

Good luck!

Edit: Actually, my problem was a bit different so this may not be that helpful :(. Sorry.

---

### Post by bowens44 on 2009-09-01
I have finally solved this issue. I had about given up on it. But now, I am connected at 243Mbps in Jaunty using a Trendnet TEW-623PI wireless adapter and a Linksys WRT350n router with DD-WRT firmware!!

Here's what I did , it was really quite easy once I found the info.

1. I renamed the existing  driver from rt2860sta.ko to rt2860sta.bk

2. I downloaded the latest driver , rt2860 Version 2.1.2.0 from
   [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

3. Extracted the directory/files to my desktop

4. modified the config.mk file changing the following entires from n to y
   
    #ifdef WPA_SUPPLICANT_SUPPORT
    # Support Wpa_Supplicant
    HAS_WPA_SUPPLICANT=y
    #endif // WPA_SUPPLICANT_SUPPORT //

    #ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
    # Support Native WpaSupplicant for Network Maganger
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
    #endif // NATIVE_WPA_SUPPLICANT_SUPPORT //

5. did sudo make && make install

6. rebooted the computer and I now see a connect speed of 243Mb/s

---

### Post by sihelset on 2009-10-12
Confirmed it worked for me also, 9.04 x64 (after reboot..). Don't work due to compile error for 9.10x64 due to change in network driver interface.

---

### Post by grantjohnston on 2009-11-02
> **sihelset said:**
> Confirmed it worked for me also, 9.04 x64 (after reboot..). Don't work due to compile error for 9.10x64 due to change in network driver interface.

Any idea when it might be possible for 9.10? I'm tired of only having 54M for my network :(

---

### Post by linghao on 2009-11-06
Hi all,

Any update for this issue? My D-Link DWA 140 also doesn't work in Ubuntu9.10.

---

### Post by abatcher on 2009-11-17
Am I the only one having troubles with downloading the drivers from the Ralink website ? 
This is the third time I try in a timespan of 2 months and always 404.

---

### Post by solca on 2009-11-19
Hey guys, just FYI my Asus EeePC 1000 with Ralink 2860 wireless adapter is successfully locked at 135Mbps to my Linksys WRT160NL (with OpenWRT firmware), iperf reports 80Mbps with 40MHz channel width or 50Mbps with 20MHz channel width.

I'm running completely updated Ubuntu 9.10 with stock 2.6.31-14 kernel and stock rt2860sta wireless driver.

The trick is that you need the proper driver's config file at /etc/Wireless/RT2860STA/RT2860STA.dat that enables HT (High Throughput) mode.

Attached is my drivers config file uploaded as .txt in case you need it. Remember to rename it and put it at the correct location.

:popcorn:

Please, let me know if it works for you.

HTH.

---

### Post by zaphod777 on 2009-11-19
I don't have that wireless directory any ideas?

```
user@computer:~$ cd /
user@computer:/$ ls
bin    dev   initrd.img  lib64       mnt   root     srv  usr
boot   etc   lib         lost+found  opt   sbin     sys  var
cdrom  home  lib32       media       proc  selinux  tmp  vmlinuz
user@computer:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"42"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1D:73:8E:DE:98   
          Bit Rate=0 kb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
computer          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
user@computer:/$ 

```

---

### Post by solca on 2009-11-19
> **zaphod777 said:**
> I don't have that wireless directory any ideas?
Exactly, it's not there, you have to create it.

Download the above config file and we'll asume you put it directly in your home directory, then open a terminal:

become root:
$ sudo -s
(enter your pass here and hit ENTER)

create directory:
# mkdir -p /etc/Wireless/RT2860STA/

move and rename the config file you download to the newly created directory:
# mv ~/RT2860STA.txt /etc/Wireless/RT2860STA/RT2860STA.dat

enjoy 802.11n!

---

### Post by zaphod777 on 2009-11-19
Is it the same folder name even though I have an intel adapter?

---

### Post by solca on 2009-11-19
> **zaphod777 said:**
> Is it the same folder name even though I have an intel adapter?

What do you think? does the subject say RaLink or Intel?

---

### Post by zaphod777 on 2009-11-19
I figured as much do you know what the naming scheme is for the folder?

I have a Intel 4965

Looks like it uses the adapter nickname but I don't have one and I can't seam to set it.

IT seams you have hit it right on the nose regarding the issue.

according to this bug report the CONFIG_IWL4965_HT option needs to be set.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203506](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203506)

but it seams to be an old bug. 

if I can just et the right folder name and file name I bet your fix will work.

```
wlan0     IEEE 802.11abgn  ESSID:"42"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1D:73:8E:DE:98   
          Bit Rate=0 kb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

nvilppu@zaphod:~$ sudo iwconfig wlan0 nickname intel4965
Error for wireless request "Set Nickname" (8B1C) :

SET failed on device wlan0 ; Operation not supported.
nvilppu@zaphod:~$ 

```

---

### Post by bgiannes on 2009-12-09
> **solca said:**
> Hey guys, just FYI my Asus EeePC 1000 with Ralink 2860 wireless adapter is successfully locked at 135Mbps to my Linksys WRT160NL (with OpenWRT firmware), iperf reports 80Mbps with 40MHz channel width or 50Mbps with 20MHz channel width.

I'm running completely updated Ubuntu 9.10 with stock 2.6.31-14 kernel and stock rt2860sta wireless driver.

The trick is that you need the proper driver's config file at /etc/Wireless/RT2860STA/RT2860STA.dat that enables HT (High Throughput) mode.

Attached is my drivers config file uploaded as .txt in case you need it. Remember to rename it and put it at the correct location.

:popcorn:

Please, let me know if it works for you.

HTH.



it works, thanx, kernel 2.6.31.16 now stock driver, but the speed is locked at 64M/b?  Would the new driver at Ralink be better; version 2.2.0.0? Or would trying to install it make a mess of things?

---

### Post by Menthu_Rae on 2009-12-10
> **solca said:**
> Hey guys, just FYI my Asus EeePC 1000 with Ralink 2860 wireless adapter is successfully locked at 135Mbps to my Linksys WRT160NL (with OpenWRT firmware), iperf reports 80Mbps with 40MHz channel width or 50Mbps with 20MHz channel width.

I'm running completely updated Ubuntu 9.10 with stock 2.6.31-14 kernel and stock rt2860sta wireless driver.

The trick is that you need the proper driver's config file at /etc/Wireless/RT2860STA/RT2860STA.dat that enables HT (High Throughput) mode.

Attached is my drivers config file uploaded as .txt in case you need it. Remember to rename it and put it at the correct location.

:popcorn:

Please, let me know if it works for you.

HTH.
> **bgiannes said:**
> it works, thanx, kernel 2.6.31.16 now stock driver, but the speed is locked at 64M/b?  Would the new driver at Ralink be better; version 2.2.0.0? Or would trying to install it make a mess of things?

Also working here after manually making the /etc/Wireless... directories and putting that .dat file in.

Connecting at 135Mbps up from 54Mbps a minute ago (before the "trick"). Hardware is a Billion 7800N on Dual 20MHz/40MHz mode and EeePC 1000HE with Ubuntu 9.10 i386 / stock kernel 2.6.31-16-generic and stock rt2860 module.

Thanks a lot mate!

---

### Post by jsa13 on 2010-01-11
Many thanks for posting the RT2860STA.dat file.  Works awesome!

I was pleased to see that my Linksys Dial-Band Wireless-N PCI Adapter Model no. WMP600N worked with Ubuntu 9.10 Karmic Koala Linux with no additional configuration.  Ubuntu loaded the rt2860 kernel module which showed up as interface ra0.  However on checking the bandwidth, I noticed that I was only able to connect at 2.4Ghz 802.11G (2.2 MB/s).  

There is a driver issue with the WPA2-Personal TKIP/AES option.  On changing exclusively to AES I connected as 2.4Ghz 802.11n (3.3 MB/s).  However I had expressly purchased this card to run multimedia on 5Ghz 802.11n.  Checking dmesg showed a driver option file was missing.  I downloaded and saved the originally posted file as /etc/Wireless/RT2860STA/RT2860STA.dat.

 After a restart the card connected immediately at 5Ghz 802.11n (3.8MB/s).  The DAT text file contains module specific options for enabling 5Ghz radio and preferences.  

Some launchpad bug reports dismiss the RT2860STA.dat file's importance or argue it is incorrect to place a binary file in /etc.  This file is essential to full featured operation and completely ASCII text.

#Filename /etc/Wireless/RT2860STA/RT2860STA.dat
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=
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
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
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

---

### Post by pyjnet on 2010-01-12
Hi, 

Thank's a lot , i've done it on a X64 9.10 Dlink DWA-140 usb stick (RT2870STA) and activated 802.11N !

Pyjnet.

---

### Post by jbcfarina on 2010-01-25
Thanks solca works like a charm in RaLink RT2760 Wireless 802.11n 1T/2R Cardbus ,Now I have N!!!. I'll wait if also fix the problems with disconnects. :popcorn:

---

### Post by Charles Dexter Ward on 2010-01-26
I'm glad I found this thread (of course, after I spent many hours trying to get my Intel card to work at "n" speeds). I ordered the Gigabyte card off eBay and followed the instructions here concerning the .dat file. The card connects to my ZyXel 802.11n router at 270 Mbps. :D

---

### Post by grantjohnston on 2010-02-02
Lately I've been having connectivity issues with the card in Linux. Works okay for a few minutes, then virtually breaks and won't even access the local net

Works okay for the most part in doze, although with one specific driver it won't go outside the local network (but it gives it 270mbps speed). 

Does anyone have any idea? This is kind of getting frustrating.. It worked FINE until about a week and a half ago, and it just started messing up randomly.

Perhaps I need to reinstall the driver? Or maybe a different one?


Thanks for the help in advance


grant

---

### Post by ryyzak on 2010-04-14
> **solca said:**
> Hey guys, just FYI my Asus EeePC 1000 with Ralink 2860 wireless adapter is successfully locked at 135Mbps to my Linksys WRT160NL (with OpenWRT firmware), iperf reports 80Mbps with 40MHz channel width or 50Mbps with 20MHz channel width.

I'm running completely updated Ubuntu 9.10 with stock 2.6.31-14 kernel and stock rt2860sta wireless driver.

The trick is that you need the proper driver's config file at /etc/Wireless/RT2860STA/RT2860STA.dat that enables HT (High Throughput) mode.

Attached is my drivers config file uploaded as .txt in case you need it. Remember to rename it and put it at the correct location.

:popcorn:

Please, let me know if it works for you.

HTH.
Thank you. This works like a charm. I now can connect my WMP600N-EU card to my WRT610N-Ver 2 router at between 240-270Mbps.

---

### Post by Lucretius on 2010-04-16
this should be made sticky

---

### Post by bloodandsoil on 2010-04-23
I have the rt2800pci would this work for me?  Here is my info.

iwlist output:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:FF:1C:77
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=33 dBm  
                    Encryption key:on
                    ESSID:"Evergreen 1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c90a6a180
                    Extra: Last beacon: 2959ms ago
                    IE: Unknown: 000B45766572677265656E2031
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160900180000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340900000000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
          Cell 02 - Address: 00:26:F2:FD:CB:49
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-191 dBm  
                    Encryption key:on
                    ESSID:"Randy's wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000265821ce03
                    Extra: Last beacon: 2841ms ago
                    IE: Unknown: 000C52616E647927732077696669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1602001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A000110104400010210470010000000000000100000000026F2FDCB49103C000103
          Cell 03 - Address: 00:14:BF:AB:F7:70
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=63 dBm  
                    Encryption key:on
                    ESSID:"Monet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e3eb2418b
                    Extra: Last beacon: 2602ms ago
                    IE: Unknown: 00054D6F6E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0
          Cell 04 - Address: 00:21:63:5F:61:84
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=63 dBm  
                    Encryption key:on
                    ESSID:"Firebird"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000110e4be787
                    Extra: Last beacon: 2879ms ago
                    IE: Unknown: 00084669726562697264
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 05 - Address: 00:21:63:5D:9B:6D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=56 dBm  
                    Encryption key:on
                    ESSID:"EMGR4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006aa277d181
                    Extra: Last beacon: 2868ms ago
                    IE: Unknown: 0005454D475234
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 06 - Address: 00:1D:7E:E4:63:DE
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:on
                    ESSID:"URANUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c63a430183
                    Extra: Last beacon: 2414ms ago
                    IE: Unknown: 00065552414E5553
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0105
                    IE: Unknown: 2F0105
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F4000000

```

iwconfig output:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Evergreen 1"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Tx-Power=8 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

dmesg output:

```

Initializing cgroup subsys cpuset
Initializing cgroup subsys cpu
Linux version 2.6.33.2-57.fc13.x86_64 (mockbuild@xb-01.phx2.fedoraproject.org) (gcc version 4.4.3 20100409 (Red Hat 4.4.3-16) (GCC) ) #1 SMP Tue Apr 20 08:57:50 UTC 2010
Command line: ro root=UUID=43ae9b7f-8997-41ec-b42a-f87926c6669c rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
 BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000007ff90000 (usable)
 BIOS-e820: 000000007ff90000 - 000000007ff9e000 (ACPI data)
 BIOS-e820: 000000007ff9e000 - 000000007ffe0000 (ACPI NVS)
 BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
 BIOS-e820: 0000000100000000 - 0000000180000000 (usable)
NX (Execute Disable) protection: active
DMI 2.4 present.
AMI BIOS detected: BIOS may corrupt low RAM, working around it.
e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
No AGP bridge found
last_pfn = 0x180000 max_arch_pfn = 0x400000000
MTRR default type: uncachable
MTRR fixed ranges enabled:
  00000-9FFFF write-back
  A0000-DFFFF uncachable
  E0000-EFFFF write-through
  F0000-FFFFF write-protect
MTRR variable ranges enabled:
  0 base 080000000 mask F80000000 uncachable
  1 base 000000000 mask F00000000 write-back
  2 base 100000000 mask F80000000 write-back
  3 disabled
  4 disabled
  5 disabled
  6 disabled
  7 disabled
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
original variable MTRRs
reg 0, base: 2GB, range: 2GB, type UC
reg 1, base: 0GB, range: 4GB, type WB
reg 2, base: 4GB, range: 2GB, type WB
total RAM covered: 4096M
Found optimal setting for mtrr clean up
 gran_size: 64K 	chunk_size: 64K 	num_reg: 2  	lose cover RAM: 0G
New variable MTRRs
reg 0, base: 0GB, range: 2GB, type WB
reg 1, base: 4GB, range: 2GB, type WB
e820 update range: 0000000080000000 - 0000000100000000 (usable) ==> (reserved)
last_pfn = 0x7ff90 max_arch_pfn = 0x400000000
initial memory mapped : 0 - 20000000
found SMP MP-table at [ffff8800000ff780] ff780
init_memory_mapping: 0000000000000000-000000007ff90000
 0000000000 - 007fe00000 page 2M
 007fe00000 - 007ff90000 page 4k
kernel direct mapping tables up to 7ff90000 @ 16000-1a000
init_memory_mapping: 0000000100000000-0000000180000000
 0100000000 - 0180000000 page 2M
kernel direct mapping tables up to 180000000 @ 18000-1f000
RAMDISK: 373f5000 - 37feff11
ACPI: RSDP 00000000000fae70 00014 (v00 ACPIAM)
ACPI: RSDT 000000007ff90000 00038 (v01 MSTEST TESTONLY 08000714 MSFT 00000097)
ACPI: FACP 000000007ff90200 00084 (v02 MSTEST OEMFACP  08000714 MSFT 00000097)
ACPI: DSDT 000000007ff905c0 08E7D (v01  A0483 A0483035 00000035 INTL 20060113)
ACPI: FACS 000000007ff9e000 00040
ACPI: APIC 000000007ff90390 0006C (v01 MSTEST OEMAPIC  08000714 MSFT 00000097)
ACPI: MCFG 000000007ff90400 0003C (v01 MSTEST OEMMCFG  08000714 MSFT 00000097)
ACPI: OEMB 000000007ff9e040 0007B (v01 MSTEST AMI_OEM  08000714 MSFT 00000097)
ACPI: HPET 000000007ff99440 00038 (v01 MSTEST OEMHPET  08000714 MSFT 00000097)
ACPI: Local APIC address 0xfee00000
No NUMA configuration found
Faking a node at 0000000000000000-0000000180000000
Bootmem setup node 0 0000000000000000-0000000180000000
  NODE_DATA [000000000001a000 - 0000000000032fff]
  bootmap [0000000000033000 -  0000000000062fff] pages 30
(13 early reservations) ==> bootmem [0000000000 - 0180000000]
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
  #1 [0001000000 - 00029ba138]    TEXT DATA BSS ==> [0001000000 - 00029ba138]
  #2 [00373f5000 - 0037feff11]          RAMDISK ==> [00373f5000 - 0037feff11]
  #3 [00029bb000 - 00029bb290]              BRK ==> [00029bb000 - 00029bb290]
  #4 [00000ff790 - 0000100000]    BIOS reserved ==> [00000ff790 - 0000100000]
  #5 [00000ff780 - 00000ff790]     MP-table mpf ==> [00000ff780 - 00000ff790]
  #6 [000009ec00 - 00000e3e00]    BIOS reserved ==> [000009ec00 - 00000e3e00]
  #7 [00000e3f84 - 00000ff780]    BIOS reserved ==> [00000e3f84 - 00000ff780]
  #8 [00000e3e00 - 00000e3f84]     MP-table mpc ==> [00000e3e00 - 00000e3f84]
  #9 [0000010000 - 0000012000]       TRAMPOLINE ==> [0000010000 - 0000012000]
  #10 [0000012000 - 0000016000]      ACPI WAKEUP ==> [0000012000 - 0000016000]
  #11 [0000016000 - 0000018000]          PGTABLE ==> [0000016000 - 0000018000]
  #12 [0000018000 - 000001a000]          PGTABLE ==> [0000018000 - 000001a000]
 [ffffea0000000000-ffffea00053fffff] PMD -> [ffff880002a00000-ffff8800061fffff] on node 0
Zone PFN ranges:
  DMA      0x00000010 -> 0x00001000
  DMA32    0x00001000 -> 0x00100000
  Normal   0x00100000 -> 0x00180000
Movable zone start PFN for each node
early_node_map[3] active PFN ranges
    0: 0x00000010 -> 0x0000009e
    0: 0x00000100 -> 0x0007ff90
    0: 0x00100000 -> 0x00180000
On node 0 totalpages: 1048350
  DMA zone: 56 pages used for memmap
  DMA zone: 107 pages reserved
  DMA zone: 3819 pages, LIFO batch:0
  DMA32 zone: 14280 pages used for memmap
  DMA32 zone: 505800 pages, LIFO batch:31
  Normal zone: 7168 pages used for memmap
  Normal zone: 517120 pages, LIFO batch:31
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Using ACPI (MADT) for SMP configuration information
ACPI: HPET id: 0x8086a202 base: 0xfed00000
SMP: Allowing 4 CPUs, 2 hotplug CPUs
nr_irqs_gsi: 24
PM: Registered nosave memory: 000000000009e000 - 000000000009f000
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
PM: Registered nosave memory: 000000007ff90000 - 000000007ff9e000
PM: Registered nosave memory: 000000007ff9e000 - 000000007ffe0000
PM: Registered nosave memory: 000000007ffe0000 - 0000000080000000
PM: Registered nosave memory: 0000000080000000 - 00000000fee00000
PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
Booting paravirtualized kernel on bare hardware
setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:4 nr_node_ids:1
PERCPU: Embedded 478 pages/cpu @ffff880006400000 s1927384 r8192 d22312 u2097152
pcpu-alloc: s1927384 r8192 d22312 u2097152 alloc=1*2097152
pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1026739
Policy zone: Normal
Kernel command line: ro root=UUID=43ae9b7f-8997-41ec-b42a-f87926c6669c rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
PID hash table entries: 4096 (order: 3, 32768 bytes)
Checking aperture...
No AGP bridge found
Calgary: detecting Calgary via BIOS EBDA area
Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Memory: 4022668k/6291456k available (4616k kernel code, 2098056k absent, 170732k reserved, 7329k data, 2752k init)
SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Hierarchical RCU implementation.
NR_IRQS:4352 nr_irqs:440
Console: colour VGA+ 80x25
console [tty0] enabled
Lock dependency validator: Copyright (c) 2006 Red Hat, Inc., Ingo Molnar
... MAX_LOCKDEP_SUBCLASSES:  8
... MAX_LOCK_DEPTH:          48
... MAX_LOCKDEP_KEYS:        8191
... CLASSHASH_SIZE:          4096
... MAX_LOCKDEP_ENTRIES:     16384
... MAX_LOCKDEP_CHAINS:      32768
... CHAINHASH_SIZE:          16384
 memory used by lock dependency info: 6367 kB
 per task-struct memory footprint: 2688 bytes
allocated 41943040 bytes of page_cgroup
please try 'cgroup_disable=memory' option if you don't want memory cgroups
ODEBUG: 13 of 13 active objects replaced
hpet clockevent registered
Fast TSC calibration using PIT
Detected 2400.084 MHz processor.
Calibrating delay loop (skipped), value calculated using timer frequency.. 4800.16 BogoMIPS (lpj=2400084)
Security Framework initialized
SELinux:  Initializing.
SELinux:  Starting in permissive mode
Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Mount-cache hash table entries: 256
Initializing cgroup subsys debug
Initializing cgroup subsys ns
Initializing cgroup subsys cpuacct
Initializing cgroup subsys memory
Initializing cgroup subsys devices
Initializing cgroup subsys freezer
Initializing cgroup subsys net_cls
Initializing cgroup subsys blkio
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
mce: CPU supports 6 MCE banks
CPU0: Thermal monitoring enabled (TM2)
using mwait in idle threads.
Performance Events: Core2 events, Intel PMU driver.
... version:                2
... bit width:              40
... generic registers:      2
... value mask:             000000ffffffffff
... max period:             000000007fffffff
... fixed-purpose events:   3
... event mask:             0000000700000003
ACPI: Core revision 20091214
ftrace: converting mcount calls to 0f 1f 44 00 00
ftrace: allocating 21607 entries in 85 pages
Setting APIC routing to flat
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
lockdep: fixing up alternatives.
Booting Node   0, Processors  #1
Brought up 2 CPUs
Total of 2 processors activated (9600.04 BogoMIPS).
sizeof(vma)=176 bytes
sizeof(page)=56 bytes
sizeof(inode)=1168 bytes
sizeof(dentry)=256 bytes
sizeof(ext3inode)=1592 bytes
sizeof(buffer_head)=104 bytes
sizeof(skbuff)=232 bytes
sizeof(task_struct)=9280 bytes
devtmpfs: initialized
regulator: core version 0.5
Time: 23:25:41  Date: 04/23/10
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
PCI: not using MMCONFIG
PCI: Using configuration type 1 for base access
bio: create slab <bio-0> at 0
ACPI: EC: Look up EC in DSDT
ACPI: Executed 1 blocks of module-level executable AML code
ACPI: Interpreter enabled
ACPI: (supports S0 S1 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
ACPI: No dock devices found.
ACPI: PCI Root Bridge [PCI0] (0000:00)
pci_root PNP0A08:00: ignoring host bridge windows from ACPI; boot with "pci=use_crs" to use them
pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xffffffff] (ignored)
pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
pci 0000:00:01.0: PME# disabled
pci 0000:00:1a.0: reg 20: [io  0xe000-0xe01f]
pci 0000:00:1a.1: reg 20: [io  0xe080-0xe09f]
pci 0000:00:1a.7: reg 10: [mem 0xffaff400-0xffaff7ff]
pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
pci 0000:00:1a.7: PME# disabled
pci 0000:00:1b.0: reg 10: [mem 0xffaf8000-0xffafbfff 64bit]
pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1b.0: PME# disabled
pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.0: PME# disabled
pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.4: PME# disabled
pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.5: PME# disabled
pci 0000:00:1d.0: reg 20: [io  0xd800-0xd81f]
pci 0000:00:1d.1: reg 20: [io  0xd880-0xd89f]
pci 0000:00:1d.2: reg 20: [io  0xdc00-0xdc1f]
pci 0000:00:1d.7: reg 10: [mem 0xffaff000-0xffaff3ff]
pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
pci 0000:00:1d.7: PME# disabled
pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
pci 0000:00:1f.2: reg 10: [io  0xec00-0xec07]
pci 0000:00:1f.2: reg 14: [io  0xe880-0xe883]
pci 0000:00:1f.2: reg 18: [io  0xe800-0xe807]
pci 0000:00:1f.2: reg 1c: [io  0xe480-0xe483]
pci 0000:00:1f.2: reg 20: [io  0xe400-0xe41f]
pci 0000:00:1f.2: reg 24: [mem 0xffaff800-0xffafffff]
pci 0000:00:1f.2: PME# supported from D3hot
pci 0000:00:1f.2: PME# disabled
pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff 64bit pref]
pci 0000:01:00.0: reg 18: [mem 0xff6f0000-0xff6fffff 64bit]
pci 0000:01:00.0: reg 20: [io  0x9000-0x90ff]
pci 0000:01:00.0: reg 30: [mem 0xff6c0000-0xff6dffff pref]
pci 0000:01:00.0: supports D1 D2
pci 0000:01:00.1: reg 10: [mem 0xff6ec000-0xff6effff 64bit]
pci 0000:01:00.1: supports D1 D2
pci 0000:00:01.0: PCI bridge to [bus 01-01]
pci 0000:00:01.0:   bridge window [io  0x7000-0x9fff]
pci 0000:00:01.0:   bridge window [mem 0xff600000-0xff6fffff]
pci 0000:00:01.0:   bridge window [mem 0xbfe00000-0xdfdfffff 64bit pref]
pci 0000:00:1c.0: PCI bridge to [bus 04-04]
pci 0000:00:1c.0:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
pci 0000:03:00.0: reg 24: [mem 0xff8fe000-0xff8fffff]
pci 0000:03:00.0: reg 30: [mem 0xff8e0000-0xff8effff pref]
pci 0000:03:00.0: PME# supported from D3hot
pci 0000:03:00.0: PME# disabled
pci 0000:03:00.1: reg 10: [io  0xbc00-0xbc07]
pci 0000:03:00.1: reg 14: [io  0xb880-0xb883]
pci 0000:03:00.1: reg 18: [io  0xb800-0xb807]
pci 0000:03:00.1: reg 1c: [io  0xb480-0xb483]
pci 0000:03:00.1: reg 20: [io  0xb400-0xb40f]
pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
pci 0000:00:1c.4: PCI bridge to [bus 03-03]
pci 0000:00:1c.4:   bridge window [io  0xb000-0xbfff]
pci 0000:00:1c.4:   bridge window [mem 0xff800000-0xff8fffff]
pci 0000:02:00.0: reg 10: [mem 0xff7fc000-0xff7fffff 64bit]
pci 0000:02:00.0: reg 18: [io  0xa800-0xa8ff]
pci 0000:02:00.0: reg 30: [mem 0xff7c0000-0xff7dffff pref]
pci 0000:02:00.0: supports D1 D2
pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:02:00.0: PME# disabled
pci 0000:00:1c.5: PCI bridge to [bus 02-02]
pci 0000:00:1c.5:   bridge window [io  0xa000-0xafff]
pci 0000:00:1c.5:   bridge window [mem 0xff700000-0xff7fffff]
pci 0000:05:02.0: reg 10: [mem 0xff9f0000-0xff9fffff]
pci 0000:05:04.0: reg 10: [mem 0xff9ec000-0xff9effff]
pci 0000:05:04.0: reg 14: [io  0xc800-0xc8ff]
pci 0000:05:04.0: reg 30: [mem 0xff9c0000-0xff9dffff pref]
pci 0000:05:04.0: supports D1 D2
pci 0000:05:04.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:05:04.0: PME# disabled
pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
pci 0000:00:1e.0:   bridge window [mem 0xff900000-0xff9fffff]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
vgaarb: loaded
SCSI subsystem initialized
libata version 3.00 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: pci_cache_line_size set to 64 bytes
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
HPET: 3 timers in total, 0 timers will be used for per-cpu timer
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Switching to clocksource tsc
kstop/1 used greatest stack depth: 6424 bytes left
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp: PnP ACPI: found 12 devices
ACPI: ACPI bus type pnp unregistered
system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
system 00:06: [io  0x0290-0x0297] has been reserved
system 00:07: [io  0x04d0-0x04d1] has been reserved
system 00:07: [io  0x0800-0x087f] has been reserved
system 00:07: [io  0x0480-0x04bf] has been reserved
system 00:07: [mem 0xffafe000-0xffb0cbff] could not be reserved
system 00:07: [mem 0xffb00000-0xffbfffff] has been reserved
system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
system 00:07: [mem 0xfed20000-0xfed8ffff] has been reserved
system 00:07: [mem 0xfff00000-0xfffffffe] has been reserved
system 00:07: [mem 0xfebfe000-0xfebfec00] has been reserved
system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
system 00:0b: [mem 0x000c0000-0x000cffff] has been reserved
system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
system 00:0b: [mem 0x00100000-0x7fffffff] could not be reserved
pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x803fffff]
pci 0000:00:1c.4: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
pci 0000:00:1c.5: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
pci 0000:00:1f.3: BAR 0: assigned [mem 0x80800000-0x808000ff]
pci 0000:00:1f.3: BAR 0: set to [mem 0x80800000-0x808000ff] (PCI address [0x80800000-0x808000ff]
pci 0000:00:01.0: PCI bridge to [bus 01-01]
pci 0000:00:01.0:   bridge window [io  0x7000-0x9fff]
pci 0000:00:01.0:   bridge window [mem 0xff600000-0xff6fffff]
pci 0000:00:01.0:   bridge window [mem 0xbfe00000-0xdfdfffff 64bit pref]
pci 0000:00:1c.0: PCI bridge to [bus 04-04]
pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x803fffff]
pci 0000:00:1c.0:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
pci 0000:00:1c.4: PCI bridge to [bus 03-03]
pci 0000:00:1c.4:   bridge window [io  0xb000-0xbfff]
pci 0000:00:1c.4:   bridge window [mem 0xff800000-0xff8fffff]
pci 0000:00:1c.4:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
pci 0000:00:1c.5: PCI bridge to [bus 02-02]
pci 0000:00:1c.5:   bridge window [io  0xa000-0xafff]
pci 0000:00:1c.5:   bridge window [mem 0xff700000-0xff7fffff]
pci 0000:00:1c.5:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
pci 0000:00:1e.0: PCI bridge to [bus 05-05]
pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
pci 0000:00:1e.0:   bridge window [mem 0xff900000-0xff9fffff]
pci 0000:00:1e.0:   bridge window [mem pref disabled]
  alloc irq_desc for 16 on node -1
  alloc kstat_irqs on node -1
pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
pci 0000:00:01.0: setting latency timer to 64
pci 0000:00:1c.0: enabling device (0106 -> 0107)
pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
pci 0000:00:1c.0: setting latency timer to 64
pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
pci 0000:00:1c.4: setting latency timer to 64
  alloc irq_desc for 17 on node -1
  alloc kstat_irqs on node -1
pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:1c.5: setting latency timer to 64
pci 0000:00:1e.0: setting latency timer to 64
pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
pci_bus 0000:01: resource 0 [io  0x7000-0x9fff]
pci_bus 0000:01: resource 1 [mem 0xff600000-0xff6fffff]
pci_bus 0000:01: resource 2 [mem 0xbfe00000-0xdfdfffff 64bit pref]
pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
pci_bus 0000:04: resource 1 [mem 0x80000000-0x803fffff]
pci_bus 0000:04: resource 2 [mem 0xdfe00000-0xdfefffff 64bit pref]
pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
pci_bus 0000:03: resource 1 [mem 0xff800000-0xff8fffff]
pci_bus 0000:03: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
pci_bus 0000:02: resource 1 [mem 0xff700000-0xff7fffff]
pci_bus 0000:02: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
pci_bus 0000:05: resource 1 [mem 0xff900000-0xff9fffff]
pci_bus 0000:05: resource 3 [io  0x0000-0xffff]
pci_bus 0000:05: resource 4 [mem 0x00000000-0xffffffffffffffff]
NET: Registered protocol family 2
IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
TCP bind hash table entries: 65536 (order: 10, 4718592 bytes)
TCP: Hash tables configured (established 524288 bind 65536)
TCP reno registered
UDP hash table entries: 2048 (order: 6, 327680 bytes)
UDP-Lite hash table entries: 2048 (order: 6, 327680 bytes)
NET: Registered protocol family 1
pci 0000:01:00.0: Boot video device
PCI: CLS 32 bytes, default 64
Trying to unpack rootfs image as initramfs...
Freeing initrd memory: 12267k freed
DMA-API: preallocated 32768 debug entries
DMA-API: debugging enabled by kernel config
PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Placing 64MB software IO TLB between ffff880006bde000 - ffff88000abde000
software IO TLB at phys 0x6bde000 - 0xabde000
Intel PCLMULQDQ-NI instructions are not detected.
audit: initializing netlink socket (disabled)
type=2000 audit(1272065143.111:1): initialized
HugeTLB registered 2 MB page size, pre-allocated 0 pages
VFS: Disk quotas dquot_6.5.2
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
msgmni has been set to 7880
SELinux:  Registering netfilter hooks
cryptomgr_test used greatest stack depth: 5880 bytes left
cryptomgr_test used greatest stack depth: 5816 bytes left
alg: No test for stdrng (krng)
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
pcieport 0000:00:01.0: setting latency timer to 64
  alloc irq_desc for 24 on node -1
  alloc kstat_irqs on node -1
pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
pcieport 0000:00:1c.0: setting latency timer to 64
  alloc irq_desc for 25 on node -1
  alloc kstat_irqs on node -1
pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
pcieport 0000:00:1c.4: setting latency timer to 64
  alloc irq_desc for 26 on node -1
  alloc kstat_irqs on node -1
pcieport 0000:00:1c.4: irq 26 for MSI/MSI-X
pcieport 0000:00:1c.5: setting latency timer to 64
  alloc irq_desc for 27 on node -1
  alloc kstat_irqs on node -1
pcieport 0000:00:1c.5: irq 27 for MSI/MSI-X
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
pci-stub: invalid id string ""
input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
ACPI: Power Button [PWRB]
input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
ACPI: Power Button [PWRF]
Non-volatile memory driver v1.3
Linux agpgart interface v0.103
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
brd: module loaded
loop: module loaded
input: Macintosh mouse button emulation as /devices/virtual/input/input2
ahci 0000:00:1f.2: version 3.0
  alloc irq_desc for 19 on node -1
  alloc kstat_irqs on node -1
ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
  alloc irq_desc for 28 on node -1
  alloc kstat_irqs on node -1
ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
ahci: SSS flag set, parallel bus scan disabled
ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
ahci 0000:00:1f.2: setting latency timer to 64
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
scsi3 : ahci
scsi4 : ahci
scsi5 : ahci
ata1: SATA max UDMA/133 abar m2048@0xffaff800 port 0xffaff900 irq 28
ata2: SATA max UDMA/133 abar m2048@0xffaff800 port 0xffaff980 irq 28
ata3: SATA max UDMA/133 abar m2048@0xffaff800 port 0xffaffa00 irq 28
ata4: SATA max UDMA/133 abar m2048@0xffaff800 port 0xffaffa80 irq 28
ata5: SATA max UDMA/133 abar m2048@0xffaff800 port 0xffaffb00 irq 28
ata6: SATA max UDMA/133 abar m2048@0xffaff800 port 0xffaffb80 irq 28
ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
ahci 0000:03:00.0: setting latency timer to 64
scsi6 : ahci
scsi7 : ahci
ata7: SATA max UDMA/133 abar m8192@0xff8fe000 port 0xff8fe100 irq 16
ata8: SATA max UDMA/133 abar m8192@0xff8fe000 port 0xff8fe180 irq 16
Fixed MDIO Bus: probed
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
  alloc irq_desc for 18 on node -1
  alloc kstat_irqs on node -1
ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
ehci_hcd 0000:00:1a.7: setting latency timer to 64
ehci_hcd 0000:00:1a.7: EHCI Host Controller
ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:1a.7: debug port 1
ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
ehci_hcd 0000:00:1a.7: irq 18, io mem 0xffaff400
ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: EHCI Host Controller
usb usb1: Manufacturer: Linux 2.6.33.2-57.fc13.x86_64 ehci_hcd
usb usb1: SerialNumber: 0000:00:1a.7
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 4 ports detected
  alloc irq_desc for 23 on node -1
  alloc kstat_irqs on node -1
ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: setting latency timer to 64
ehci_hcd 0000:00:1d.7: EHCI Host Controller
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
ehci_hcd 0000:00:1d.7: debug port 1
ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffaff000
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb2: Product: EHCI Host Controller
usb usb2: Manufacturer: Linux 2.6.33.2-57.fc13.x86_64 ehci_hcd
usb usb2: SerialNumber: 0000:00:1d.7
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 6 ports detected
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
uhci_hcd: USB Universal Host Controller Interface driver
uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1a.0: setting latency timer to 64
uhci_hcd 0000:00:1a.0: UHCI Host Controller
uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb3: Product: UHCI Host Controller
usb usb3: Manufacturer: Linux 2.6.33.2-57.fc13.x86_64 uhci_hcd
usb usb3: SerialNumber: 0000:00:1a.0
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
uhci_hcd 0000:00:1a.1: setting latency timer to 64
uhci_hcd 0000:00:1a.1: UHCI Host Controller
uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000e080
usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb4: Product: UHCI Host Controller
usb usb4: Manufacturer: Linux 2.6.33.2-57.fc13.x86_64 uhci_hcd
usb usb4: SerialNumber: 0000:00:1a.1
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1d.0: setting latency timer to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d800
usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb5: Product: UHCI Host Controller
usb usb5: Manufacturer: Linux 2.6.33.2-57.fc13.x86_64 uhci_hcd
usb usb5: SerialNumber: 0000:00:1d.0
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: setting latency timer to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb6: Product: UHCI Host Controller
usb usb6: Manufacturer: Linux 2.6.33.2-57.fc13.x86_64 uhci_hcd
usb usb6: SerialNumber: 0000:00:1d.1
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: setting latency timer to 64
uhci_hcd 0000:00:1d.2: UHCI Host Controller
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000dc00
usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb7: Product: UHCI Host Controller
usb usb7: Manufacturer: Linux 2.6.33.2-57.fc13.x86_64 uhci_hcd
usb usb7: SerialNumber: 0000:00:1d.2
hub 7-0:1.0: USB hub found
hub 7-0:1.0: 2 ports detected
PNP: No PS/2 controller found. Probing ports directly.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
rtc_cmos 00:03: RTC can wake from S4
rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.16.0-ioctl (2009-11-05) initialised: dm-devel@redhat.com
cpuidle: using governor ladder
cpuidle: using governor menu
usbcore: registered new interface driver hiddev
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
ip_tables: (C) 2000-2006 Netfilter Core Team
TCP cubic registered
Initializing XFRM netlink socket
NET: Registered protocol family 17
PM: Resume from disk failed.
registered taskstats version 1
No TPM chip found, activating TPM-bypass!
  Magic number: 6:531:454
rtc_cmos 00:03: setting system clock to 2010-04-23 23:25:43 UTC (1272065143)
Initalizing network drop monitor service
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: ATA-8: WDC WD10EADS-00L5B1, 01.01A01, max UDMA/133
ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
ata1.00: configured for UDMA/133
ata8: SATA link down (SStatus 0 SControl 300)
ata7: SATA link down (SStatus 0 SControl 300)
scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EADS-00L 01.0 PQ: 0 ANSI: 5
sd 0:0:0:0: Attached scsi generic sg0 type 0
sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 sda3 sda4
sd 0:0:0:0: [sda] Attached SCSI disk
usb 6-1: new low speed USB device using uhci_hcd and address 2
ata2: SATA link down (SStatus 0 SControl 300)
usb 6-1: New USB device found, idVendor=f617, idProduct=0905
usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 6-1: Product: Endura Keyboard 
usb 6-1: Manufacturer: Unicomp 
input: Unicomp  Endura Keyboard  as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input3
generic-usb 0003:F617:0905.0001: input,hidraw0: USB HID v1.10 Keyboard [Unicomp  Endura Keyboard ] on usb-0000:00:1d.1-1/input0
ata3: SATA link down (SStatus 0 SControl 300)
usb 6-2: new full speed USB device using uhci_hcd and address 3
usb 6-2: New USB device found, idVendor=046d, idProduct=c066
usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 6-2: Product: G9x Laser Mouse
usb 6-2: Manufacturer: Logitech
usb 6-2: SerialNumber: 867926FEE30018
input: Logitech G9x Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input4
generic-usb 0003:046D:C066.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech G9x Laser Mouse] on usb-0000:00:1d.1-2/input0
input: Logitech G9x Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input5
generic-usb 0003:046D:C066.0003: input,hiddev96,hidraw2: USB HID v1.11 Keyboard [Logitech G9x Laser Mouse] on usb-0000:00:1d.1-2/input1
ata4: SATA link down (SStatus 0 SControl 300)
async/0 used greatest stack depth: 4040 bytes left
ata5: SATA link down (SStatus 0 SControl 300)
ata6: SATA link down (SStatus 0 SControl 300)
Freeing unused kernel memory: 2752k freed
Write protecting the kernel read-only data: 10240k
Freeing unused kernel memory: 1508k freed
Freeing unused kernel memory: 1832k freed
dracut: dracut-005-3.fc13
dracut: rd_NO_LUKS: removing cryptoluks activation
dracut: rd_NO_LVM: removing LVM activation
udev: starting version 151
[drm] Initialized drm 1.1.0 20060810
[drm] radeon defaulting to kernel modesetting.
[drm] radeon kernel modesetting enabled.
radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
radeon 0000:01:00.0: setting latency timer to 64
[drm] radeon: Initializing kernel modesetting.
[drm] register mmio base: 0xFF6F0000
[drm] register mmio size: 65536
ATOM BIOS: HD4850
[drm] Clocks initialized !
mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[drm] Detected VRAM RAM=256M, BAR=256M
[drm] RAM width 256bits DDR
[TTM] Zone  kernel: Available graphics memory: 2020514 kiB.
[ttm] Initializing pool allocator.
[drm] radeon: 256M of VRAM memory ready
[drm] radeon: 512M of GTT memory ready.
  alloc irq_desc for 29 on node -1
  alloc kstat_irqs on node -1
radeon 0000:01:00.0: irq 29 for MSI/MSI-X
[drm] radeon: using MSI.
[drm] radeon: irq initialized.
[drm] GART: num cpu pages 131072, num gpu pages 131072
[drm] Loading RV770 Microcode
platform radeon_cp.0: firmware: requesting radeon/RV770_pfp.bin
platform radeon_cp.0: firmware: requesting radeon/RV770_me.bin
platform radeon_cp.0: firmware: requesting radeon/R700_rlc.bin
[drm] ring test succeeded in 0 usecs
[drm] radeon: ib pool ready.
[drm] ib test succeeded in 0 usecs
[drm] Radeon Display Connectors
[drm] Connector 0:
[drm]   DVI-I
[drm]   HPD2
[drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[drm]   Encoders:
[drm]     CRT1: INTERNAL_KLDSCP_DAC1
[drm]     DFP2: INTERNAL_KLDSCP_LVTMA
[drm] Connector 1:
[drm]   HDMI-A
[drm]   HPD3
[drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[drm]   Encoders:
[drm]     DFP1: INTERNAL_UNIPHY
[drm] Connector 2:
[drm]   VGA
[drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[drm]   Encoders:
[drm]     CRT2: INTERNAL_KLDSCP_DAC2
[drm] fb mappable at 0xC0141000
[drm] vram apper at 0xC0000000
[drm] size 7257600
[drm] fb depth is 24
[drm]    pitch is 6912
fbcon: radeondrmfb (fb0) is primary device
Console: switching to colour frame buffer device 210x65
fb0: radeondrmfb frame buffer device
registered panic notifier
[drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
modprobe used greatest stack depth: 3184 bytes left
dracut: Starting plymouth daemon
dracut: rd_NO_DM: removing DM RAID activation
dracut: rd_NO_MD: removing MD RAID activation
pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pata_jmicron 0000:03:00.1: setting latency timer to 64
scsi8 : pata_jmicron
scsi9 : pata_jmicron
ata9: PATA max UDMA/100 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 17
ata10: PATA max UDMA/100 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 17
ata9.01: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB03, max UDMA/33
ata9.01: configured for UDMA/33
scsi 8:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB03 PQ: 0 ANSI: 5
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 8:0:1:0: Attached scsi CD-ROM sr0
sr 8:0:1:0: Attached scsi generic sg1 type 5
EXT4-fs (sda2): mounted filesystem with ordered data mode
dracut: Mounted root filesystem /dev/sda2
dracut: Loading SELinux policy
type=1404 audit(1272065147.166:2): enforcing=1 old_enforcing=0 auid=4294967295 ses=4294967295
SELinux: 8192 avtab hash slots, 194816 rules.
SELinux: 8192 avtab hash slots, 194816 rules.
SELinux:  9 users, 13 roles, 3202 types, 155 bools, 1 sens, 1024 cats
SELinux:  77 classes, 194816 rules
SELinux:  Completing initialization.
SELinux:  Setting up existing superblocks.
SELinux: initialized (dev sda2, type ext4), uses xattr
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
SELinux: initialized (dev securityfs, type securityfs), uses genfs_contexts
SELinux: initialized (dev usbfs, type usbfs), uses genfs_contexts
SELinux: initialized (dev selinuxfs, type selinuxfs), uses genfs_contexts
SELinux: initialized (dev mqueue, type mqueue), uses transition SIDs
SELinux: initialized (dev hugetlbfs, type hugetlbfs), uses transition SIDs
SELinux: initialized (dev devpts, type devpts), uses transition SIDs
SELinux: initialized (dev inotifyfs, type inotifyfs), uses genfs_contexts
SELinux: initialized (dev anon_inodefs, type anon_inodefs), uses genfs_contexts
SELinux: initialized (dev pipefs, type pipefs), uses task SIDs
SELinux: initialized (dev debugfs, type debugfs), uses genfs_contexts
SELinux: initialized (dev sockfs, type sockfs), uses task SIDs
SELinux: initialized (dev devtmpfs, type devtmpfs), uses transition SIDs
SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
SELinux: initialized (dev proc, type proc), uses genfs_contexts
SELinux: initialized (dev bdev, type bdev), uses genfs_contexts
SELinux: initialized (dev rootfs, type rootfs), uses genfs_contexts
SELinux: initialized (dev sysfs, type sysfs), uses genfs_contexts
type=1403 audit(1272065148.091:3): policy loaded auid=4294967295 ses=4294967295
load_policy used greatest stack depth: 3088 bytes left
dracut: Switching root
readahead: starting
udev: starting version 151
microcode: CPU0 sig=0x6f6, pf=0x1, revision=0xc6
microcode: CPU1 sig=0x6f6, pf=0x1, revision=0xc6
microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
i801_smbus 0000:00:1f.3: enabling device (0001 -> 0003)
i801_smbus 0000:00:1f.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
ACPI: I/O resource 0000:00:1f.3 [0x400-0x41f] conflicts with ACPI region SMRG [0x400-0x40f]
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
sky2 driver version 1.26
sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
sky2 0000:02:00.0: setting latency timer to 64
sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 2
  alloc irq_desc for 30 on node -1
  alloc kstat_irqs on node -1
sky2 0000:02:00.0: irq 30 for MSI/MSI-X
sky2 eth0: addr 00:18:f3:44:d3:f5
iTCO_vendor_support: vendor-support=0
iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0860)
iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
skge 0000:05:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
skge 1.13 addr 0xff9ec000 irq 19 chip Yukon-Lite rev 9
skge eth1: addr 00:18:f3:44:c7:75
microcode: CPU0 updated to revision 0xcb, date = 2007-09-16 
type=1400 audit(1272065150.835:4): avc:  denied  { mmap_zero } for  pid=450 comm="vbetool" scontext=system_u:system_r:vbetool_t:s0-s0:c0.c1023 tcontext=system_u:system_r:vbetool_t:s0-s0:c0.c1023 tclass=memprotect
microcode: CPU1 updated to revision 0xcb, date = 2007-09-16 
cfg80211: Calling CRDA to update world regulatory domain
  alloc irq_desc for 22 on node -1
  alloc kstat_irqs on node -1
HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
  alloc irq_desc for 31 on node -1
  alloc kstat_irqs on node -1
HDA Intel 0000:00:1b.0: irq 31 for MSI/MSI-X
HDA Intel 0000:00:1b.0: setting latency timer to 64
HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
  alloc irq_desc for 32 on node -1
  alloc kstat_irqs on node -1
HDA Intel 0000:01:00.1: irq 32 for MSI/MSI-X
HDA Intel 0000:01:00.1: setting latency timer to 64
rt2800pci 0000:05:02.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
phy0: Selected rate control algorithm 'minstrel'
Registered led device: rt2800pci-phy0::radio
Registered led device: rt2800pci-phy0::assoc
Registered led device: rt2800pci-phy0::quality
cfg80211: Calling CRDA for country: CA
cfg80211: Regulatory domain changed to country: CA
    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
    (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
    (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
    (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
EXT4-fs (sda1): mounted filesystem with ordered data mode
SELinux: initialized (dev sda1, type ext4), uses xattr
EXT4-fs (sda4): mounted filesystem with ordered data mode
SELinux: initialized (dev sda4, type ext4), uses xattr
Adding 8393952k swap on /dev/sda3.  Priority:-1 extents:1 across:8393952k 
SELinux: initialized (dev binfmt_misc, type binfmt_misc), uses genfs_contexts
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ip6_tables: (C) 2000-2006 Netfilter Core Team
rt2800pci 0000:05:02.0: firmware: requesting rt2860.bin
phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
ADDRCONF(NETDEV_UP): wlan0: link is not ready
sky2 eth0: enabling interface
ADDRCONF(NETDEV_UP): eth0: link is not ready
p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
skge eth1: enabling interface
ADDRCONF(NETDEV_UP): eth1: link is not ready
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
SELinux: initialized (dev rpc_pipefs, type rpc_pipefs), uses genfs_contexts
hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
fuse init (API version 7.13)
SELinux: initialized (dev fuse, type fuse), uses genfs_contexts
wlan0: direct probe to AP 00:21:91:ff:1c:77 (try 1)
wlan0: direct probe to AP 00:21:91:ff:1c:77 (try 2)
wlan0: direct probe to AP 00:21:91:ff:1c:77 (try 3)
wlan0: direct probe to AP 00:21:91:ff:1c:77 timed out
wlan0: direct probe to AP 00:21:91:ff:1c:77 (try 1)
wlan0: direct probe to AP 00:21:91:ff:1c:77 (try 2)
wlan0: direct probe to AP 00:21:91:ff:1c:77 (try 3)
wlan0: direct probe to AP 00:21:91:ff:1c:77 timed out
usb 1-3: new high speed USB device using ehci_hcd and address 2
usb 1-3: New USB device found, idVendor=0718, idProduct=0077
usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-3: Product: USB Mass Storage Device
usb 1-3: Manufacturer: USBest Technology
usb 1-3: SerialNumber: AA407081631091
Initializing USB Mass Storage driver...
scsi10 : usb-storage 1-3:1.0
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
scsi 10:0:0:0: Direct-Access     Imation  USB Flash Drive  0.00 PQ: 0 ANSI: 2
sd 10:0:0:0: Attached scsi generic sg2 type 0
sd 10:0:0:0: [sdb] 8060927 512-byte logical blocks: (4.12 GB/3.84 GiB)
sd 10:0:0:0: [sdb] Write Protect is off
sd 10:0:0:0: [sdb] Mode Sense: 00 00 00 00
sd 10:0:0:0: [sdb] Assuming drive cache: write through
sd 10:0:0:0: [sdb] Assuming drive cache: write through
 sdb: sdb1
sd 10:0:0:0: [sdb] Assuming drive cache: write through
sd 10:0:0:0: [sdb] Attached SCSI removable disk
SELinux: initialized (dev sdb1, type vfat), uses genfs_contexts

=============================================
[ INFO: possible recursive locking detected ]
2.6.33.2-57.fc13.x86_64 #1
---------------------------------------------
udisks-helper-d/27921 is trying to acquire lock:
 (s_active){++++.+}, at: [<ffffffff811785ba>] sysfs_addrm_finish+0x36/0x55

but task is already holding lock:
 (s_active){++++.+}, at: [<ffffffff81178776>] sysfs_get_active_two+0x24/0x48

other info that might help us debug this:
3 locks held by udisks-helper-d/27921:
 #0:  (&buffer->mutex){+.+.+.}, at: [<ffffffff81177163>] sysfs_write_file+0x3c/0x144
 #1:  (s_active){++++.+}, at: [<ffffffff81178776>] sysfs_get_active_two+0x24/0x48
 #2:  (s_active){++++.+}, at: [<ffffffff81178783>] sysfs_get_active_two+0x31/0x48

stack backtrace:
Pid: 27921, comm: udisks-helper-d Not tainted 2.6.33.2-57.fc13.x86_64 #1
Call Trace:
 [<ffffffff8107f94f>] __lock_acquire+0xcb5/0xd2c
 [<ffffffff8107df48>] ? mark_held_locks+0x52/0x70
 [<ffffffff8107e329>] ? debug_check_no_locks_freed+0x12e/0x145
 [<ffffffff8107e1c8>] ? trace_hardirqs_on_caller+0x111/0x135
 [<ffffffff8107faa2>] lock_acquire+0xdc/0x102
 [<ffffffff811785ba>] ? sysfs_addrm_finish+0x36/0x55
 [<ffffffff8107d300>] ? lockdep_init_map+0x9e/0x113
 [<ffffffff81177d8a>] sysfs_deactivate+0x9a/0x103
 [<ffffffff811785ba>] ? sysfs_addrm_finish+0x36/0x55
 [<ffffffff8107220a>] ? sched_clock_cpu+0xc3/0xce
 [<ffffffff81478d6c>] ? __mutex_unlock_slowpath+0x120/0x132
 [<ffffffff811785ba>] sysfs_addrm_finish+0x36/0x55
 [<ffffffff81176818>] sysfs_hash_and_remove+0x53/0x6a
 [<ffffffff81178b43>] sysfs_remove_link+0x21/0x23
 [<ffffffff812ee901>] driver_sysfs_remove+0x2a/0x3e
 [<ffffffff812ee948>] __device_release_driver+0x33/0xd1
 [<ffffffff812eeac7>] device_release_driver+0x23/0x30
 [<ffffffff812edfeb>] driver_unbind+0x5c/0x91
 [<ffffffff812ed617>] drv_attr_store+0x2c/0x2e
 [<ffffffff8117722f>] sysfs_write_file+0x108/0x144
 [<ffffffff81120199>] vfs_write+0xae/0x10b
 [<ffffffff8107e1c8>] ? trace_hardirqs_on_caller+0x111/0x135
 [<ffffffff811202b6>] sys_write+0x4a/0x6e
 [<ffffffff81009c72>] system_call_fastpath+0x16/0x1b
usb 1-3: USB disconnect, address 2
usb 1-3: new high speed USB device using ehci_hcd and address 3
usb 1-3: New USB device found, idVendor=0718, idProduct=0077
usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-3: Product: USB Mass Storage Device
usb 1-3: Manufacturer: USBest Technology
usb 1-3: SerialNumber: AA407081631091
scsi11 : usb-storage 1-3:1.0
scsi 11:0:0:0: Direct-Access     Imation  USB Flash Drive  0.00 PQ: 0 ANSI: 2
sd 11:0:0:0: Attached scsi generic sg2 type 0
sd 11:0:0:0: [sdb] Attached SCSI removable disk
sd 11:0:0:0: [sdb] 8060927 512-byte logical blocks: (4.12 GB/3.84 GiB)
sd 11:0:0:0: [sdb] Write Protect is on
sd 11:0:0:0: [sdb] Mode Sense: 0b 00 80 00
sd 11:0:0:0: [sdb] Assuming drive cache: write through
sd 11:0:0:0: [sdb] Assuming drive cache: write through
 sdb: sdb1
SELinux: initialized (dev sdb1, type vfat), uses genfs_contexts
usb 1-3: USB disconnect, address 3
usb 1-4: new high speed USB device using ehci_hcd and address 4
usb 1-4: New USB device found, idVendor=0718, idProduct=0077
usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-4: Product: USB Mass Storage Device
usb 1-4: Manufacturer: USBest Technology
usb 1-4: SerialNumber: AA407081631091
scsi12 : usb-storage 1-4:1.0
scsi 12:0:0:0: Direct-Access     Imation  USB Flash Drive  0.00 PQ: 0 ANSI: 2
sd 12:0:0:0: Attached scsi generic sg2 type 0
sd 12:0:0:0: [sdb] 8060927 512-byte logical blocks: (4.12 GB/3.84 GiB)
sd 12:0:0:0: [sdb] Write Protect is off
sd 12:0:0:0: [sdb] Mode Sense: 00 00 00 00
sd 12:0:0:0: [sdb] Assuming drive cache: write through
sd 12:0:0:0: [sdb] Assuming drive cache: write through
 sdb: sdb1
sd 12:0:0:0: [sdb] Assuming drive cache: write through
sd 12:0:0:0: [sdb] Attached SCSI removable disk
SELinux: initialized (dev sdb1, type vfat), uses genfs_contexts

```

grep NetworkManager /var/log/messages:

```

Apr 23 15:48:25 asgard NetworkManager: <info> starting...
Apr 23 15:48:25 asgard NetworkManager: <info> trying to start the modem manager...
Apr 23 15:48:25 asgard NetworkManager:    ifcfg-rh: Acquired D-Bus service com.redhat.ifcfgrh1
Apr 23 15:48:25 asgard NetworkManager: <info> Loaded plugin ifcfg-rh: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 23 15:48:25 asgard NetworkManager: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Apr 23 15:48:25 asgard NetworkManager: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 23 15:48:25 asgard NetworkManager: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 23 15:48:25 asgard NetworkManager: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 23 15:48:25 asgard NetworkManager: <info> Networking is enabled by state file
Apr 23 15:48:25 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth0 ... 
Apr 23 15:48:25 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth0'
Apr 23 15:48:25 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-lo ... 
Apr 23 15:48:25 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth1 ... 
Apr 23 15:48:25 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth1'
Apr 23 15:48:25 asgard NetworkManager: <info> Updating /etc/hosts with new system hostname
Apr 23 15:48:25 asgard NetworkManager: <info> (eth0): carrier is OFF
Apr 23 15:48:25 asgard NetworkManager: <info> (eth0): new Ethernet device (driver: 'sky2')
Apr 23 15:48:25 asgard NetworkManager: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 15:48:26 asgard NetworkManager: <info> (eth0): now managed
Apr 23 15:48:26 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 15:48:26 asgard NetworkManager: <info> (eth0): bringing up device.
Apr 23 15:48:26 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 15:48:26 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci')
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): bringing up device.
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 15:48:26 asgard NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Apr 23 15:48:26 asgard NetworkManager: <info> (eth1): carrier is OFF
Apr 23 15:48:26 asgard NetworkManager: <info> (eth1): new Ethernet device (driver: 'skge')
Apr 23 15:48:26 asgard NetworkManager: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 23 15:48:26 asgard NetworkManager: <info> (eth1): now managed
Apr 23 15:48:26 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 15:48:26 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 15:48:26 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 15:48:26 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 15:48:26 asgard NetworkManager: <info> modem-manager is now available
Apr 23 15:48:26 asgard NetworkManager: <info> Trying to start the supplicant...
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): supplicant manager state:  down -> idle
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Apr 23 15:48:26 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 15:48:28 asgard NetworkManager: <info> (eth0): carrier now ON (device state 2)
Apr 23 15:48:28 asgard NetworkManager: <info> (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) starting connection 'System eth0'
Apr 23 15:48:28 asgard NetworkManager: <info> (eth0): device state change: 3 -> 4 (reason 0)
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 23 15:48:28 asgard NetworkManager: <info> (eth0): device state change: 4 -> 5 (reason 0)
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 23 15:48:28 asgard NetworkManager: <info> (eth0): device state change: 5 -> 7 (reason 0)
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 23 15:48:28 asgard NetworkManager: <info> dhclient started with pid 1154
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 23 15:48:28 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 23 15:48:28 asgard NetworkManager: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 23 15:48:30 asgard NetworkManager: <info> (eth0): DHCPv4 state changed preinit -> bound
Apr 23 15:48:30 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 23 15:48:30 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 23 15:48:30 asgard NetworkManager: <info>   address 192.168.0.192
Apr 23 15:48:30 asgard NetworkManager: <info>   prefix 24 (255.255.255.0)
Apr 23 15:48:30 asgard NetworkManager: <info>   gateway 192.168.0.1
Apr 23 15:48:30 asgard NetworkManager: <info>   nameserver '192.168.0.1'
Apr 23 15:48:30 asgard NetworkManager: <info>   domain name 'hsd1.wa.comcast.net.'
Apr 23 15:48:30 asgard NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 23 15:48:30 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 23 15:48:30 asgard NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 23 15:48:31 asgard NetworkManager: <info> (eth0): device state change: 7 -> 8 (reason 0)
Apr 23 15:48:31 asgard NetworkManager: <info> Policy set 'System eth0' (eth0) as default for routing and DNS.
Apr 23 15:48:31 asgard NetworkManager: <info> Activation (eth0) successful, device activated.
Apr 23 15:48:31 asgard NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 23 15:52:24 asgard NetworkManager: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Apr 23 15:52:29 asgard NetworkManager: <info> (eth0): device state change: 8 -> 2 (reason 40)
Apr 23 15:52:29 asgard NetworkManager: <info> (eth0): deactivating device (reason: 40).
Apr 23 15:52:29 asgard NetworkManager: <info> (eth0): canceled DHCP transaction, DHCP client pid 1154
Apr 23 15:52:35 asgard NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Apr 23 15:52:35 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 15:52:35 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 15:52:35 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 15:52:35 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 15:52:35 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 15:52:35 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 15:52:35 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 15:52:35 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 15:52:35 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 15:52:35 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 15:52:35 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 15:53:04 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 15:53:04 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 15:53:04 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 15:53:04 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 15:53:04 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 15:53:04 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 15:53:04 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 15:53:04 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 15:53:04 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 15:53:04 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 15:53:04 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 15:53:04 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 15:53:04 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 15:53:04 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 15:53:04 asgard NetworkManager: <info> (wlan0): supplicant connection state:  inactive -> scanning
Apr 23 15:53:07 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 15:53:27 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 15:53:27 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 15:53:29 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 15:53:29 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 15:53:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 15:53:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 15:53:33 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 15:53:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 15:53:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 15:53:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 15:53:33 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 15:53:33 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 15:53:33 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 15:53:33 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 15:53:33 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 15:53:33 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 15:53:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 15:53:33 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 15:53:33 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> associating
Apr 23 15:53:53 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 15:53:53 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 15:53:56 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 15:53:59 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 15:53:59 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 15:54:11 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 15:54:11 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 15:54:11 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 15:54:11 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1 ... 
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh:     warning: ignoring pairwise cipher 'NONE' (pairwise not used in Ad-Hoc mode)
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh:     read connection 'Auto Evergreen 1'
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh:     warning: ignoring pairwise cipher 'NONE' (pairwise not used in Ad-Hoc mode)
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh:     warning: ignoring pairwise cipher 'NONE' (pairwise not used in Ad-Hoc mode)
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:36 asgard NetworkManager:    ifcfg-rh:     warning: ignoring pairwise cipher 'NONE' (pairwise not used in Ad-Hoc mode)
Apr 23 15:54:54 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:54 asgard NetworkManager:    ifcfg-rh:     warning: ignoring pairwise cipher 'NONE' (pairwise not used in Ad-Hoc mode)
Apr 23 15:54:54 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:54 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:54 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:55 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:55 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:55 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:54:55 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:10 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:10 asgard NetworkManager:    ifcfg-rh:     warning: ignoring pairwise cipher 'NONE' (pairwise not used in Ad-Hoc mode)
Apr 23 15:55:10 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:10 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:10 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:11 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:11 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:11 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:11 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:55:16 asgard NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Apr 23 15:55:16 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 15:55:16 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 15:55:16 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 15:55:16 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 15:55:16 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 15:55:16 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 15:55:16 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 15:55:16 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 15:55:16 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 15:55:16 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 15:55:16 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 15:55:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 15:55:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 15:55:33 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 15:55:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 15:55:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 15:55:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 15:55:33 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 15:55:33 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 15:55:33 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 15:55:33 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 15:55:33 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 15:55:33 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 15:55:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 15:55:33 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 15:55:33 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 15:55:33 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 15:55:36 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 15:55:56 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 15:55:56 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 15:55:59 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 15:55:59 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 15:56:03 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 15:56:03 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 15:56:03 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 15:56:03 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 15:58:06 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:58:06 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:58:06 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:58:06 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:58:06 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 15:58:06 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth1
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh:     error: Couldn't parse file '/etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1'
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh: removed /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1.
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1 ... 
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh:     error: Couldn't parse file '/etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1'
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1 ... 
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh:     error: Couldn't parse file '/etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1'
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh:     error: Missing WPA_PSK for WPA-PSK key management
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh:     error: Missing WPA_PSK for WPA-PSK key management
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1 ... 
Apr 23 15:58:07 asgard NetworkManager:    ifcfg-rh:     error: Couldn't parse file '/etc/sysconfig/network-scripts/ifcfg-Auto_Evergreen_1'
Apr 23 15:58:21 asgard NetworkManager: <info> caught signal 15, shutting down normally.
Apr 23 15:58:21 asgard NetworkManager: <info> (eth0): cleaning up...
Apr 23 15:58:21 asgard NetworkManager: <info> (eth0): taking down device.
Apr 23 15:58:21 asgard NetworkManager: <info> (wlan0): taking down device.
Apr 23 15:58:21 asgard NetworkManager: <info> (eth1): cleaning up...
Apr 23 15:58:21 asgard NetworkManager: <info> (eth1): taking down device.
Apr 23 15:58:21 asgard NetworkManager: <info> exiting (success)
Apr 23 15:59:08 asgard NetworkManager: <info> starting...
Apr 23 15:59:08 asgard NetworkManager: <info> trying to start the modem manager...
Apr 23 15:59:08 asgard NetworkManager:    ifcfg-rh: Acquired D-Bus service com.redhat.ifcfgrh1
Apr 23 15:59:08 asgard NetworkManager: <info> Loaded plugin ifcfg-rh: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 23 15:59:08 asgard NetworkManager: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Apr 23 15:59:08 asgard NetworkManager: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 23 15:59:08 asgard NetworkManager: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 23 15:59:08 asgard NetworkManager: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 23 15:59:08 asgard NetworkManager: <info> Networking is enabled by state file
Apr 23 15:59:08 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth0 ... 
Apr 23 15:59:08 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth0'
Apr 23 15:59:08 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 15:59:08 asgard NetworkManager:    ifcfg-rh:     error: Missing WPA_PSK for WPA-PSK key management
Apr 23 15:59:08 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-lo ... 
Apr 23 15:59:08 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth1 ... 
Apr 23 15:59:08 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth1'
Apr 23 15:59:08 asgard NetworkManager: <info> (eth0): carrier is OFF
Apr 23 15:59:08 asgard NetworkManager: <info> (eth0): new Ethernet device (driver: 'sky2')
Apr 23 15:59:08 asgard NetworkManager: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 15:59:08 asgard NetworkManager: <info> (eth0): now managed
Apr 23 15:59:08 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 15:59:08 asgard NetworkManager: <info> (eth0): bringing up device.
Apr 23 15:59:08 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 15:59:08 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci')
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): bringing up device.
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 15:59:08 asgard NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Apr 23 15:59:08 asgard NetworkManager: <info> (eth1): carrier is OFF
Apr 23 15:59:08 asgard NetworkManager: <info> (eth1): new Ethernet device (driver: 'skge')
Apr 23 15:59:08 asgard NetworkManager: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 23 15:59:08 asgard NetworkManager: <info> (eth1): now managed
Apr 23 15:59:08 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 15:59:08 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 15:59:08 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 15:59:08 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 15:59:08 asgard NetworkManager: <info> modem-manager is now available
Apr 23 15:59:08 asgard NetworkManager: <info> Trying to start the supplicant...
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): supplicant manager state:  down -> idle
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Apr 23 15:59:08 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 15:59:42 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 15:59:42 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 15:59:42 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 15:59:42 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 15:59:42 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 15:59:42 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 15:59:42 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 15:59:42 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 15:59:42 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 15:59:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 15:59:42 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 15:59:42 asgard NetworkManager: <info> (wlan0): supplicant connection state:  inactive -> scanning
Apr 23 15:59:45 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:00:06 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:00:06 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:00:08 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:00:08 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:00:10 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:00:10 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:00:10 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:00:10 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 16:01:25 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 16:01:25 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth1
Apr 23 16:01:39 asgard NetworkManager: <info> caught signal 15, shutting down normally.
Apr 23 16:01:39 asgard NetworkManager: <info> (eth0): cleaning up...
Apr 23 16:01:39 asgard NetworkManager: <info> (eth0): taking down device.
Apr 23 16:01:39 asgard NetworkManager: <info> (wlan0): taking down device.
Apr 23 16:01:39 asgard NetworkManager: <info> (eth1): cleaning up...
Apr 23 16:01:39 asgard NetworkManager: <info> (eth1): taking down device.
Apr 23 16:01:39 asgard NetworkManager: <info> exiting (success)
Apr 23 16:03:19 asgard NetworkManager: <info> starting...
Apr 23 16:03:19 asgard NetworkManager: <info> trying to start the modem manager...
Apr 23 16:03:19 asgard NetworkManager:    ifcfg-rh: Acquired D-Bus service com.redhat.ifcfgrh1
Apr 23 16:03:19 asgard NetworkManager: <info> Loaded plugin ifcfg-rh: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 23 16:03:19 asgard NetworkManager: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Apr 23 16:03:19 asgard NetworkManager: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 23 16:03:19 asgard NetworkManager: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 23 16:03:19 asgard NetworkManager: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 23 16:03:19 asgard NetworkManager: <info> Networking is enabled by state file
Apr 23 16:03:19 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth0 ... 
Apr 23 16:03:19 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth0'
Apr 23 16:03:19 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 16:03:19 asgard NetworkManager:    ifcfg-rh:     error: Missing SSID
Apr 23 16:03:19 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-lo ... 
Apr 23 16:03:19 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth1 ... 
Apr 23 16:03:19 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth1'
Apr 23 16:03:19 asgard NetworkManager: <info> (eth0): carrier is OFF
Apr 23 16:03:19 asgard NetworkManager: <info> (eth0): new Ethernet device (driver: 'sky2')
Apr 23 16:03:19 asgard NetworkManager: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 16:03:19 asgard NetworkManager: <info> (eth0): now managed
Apr 23 16:03:19 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 16:03:19 asgard NetworkManager: <info> (eth0): bringing up device.
Apr 23 16:03:19 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 16:03:19 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci')
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): bringing up device.
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 16:03:19 asgard NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Apr 23 16:03:19 asgard NetworkManager: <info> (eth1): carrier is OFF
Apr 23 16:03:19 asgard NetworkManager: <info> (eth1): new Ethernet device (driver: 'skge')
Apr 23 16:03:19 asgard NetworkManager: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 23 16:03:19 asgard NetworkManager: <info> (eth1): now managed
Apr 23 16:03:19 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 16:03:19 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 16:03:19 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 16:03:19 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 16:03:19 asgard NetworkManager: <info> modem-manager is now available
Apr 23 16:03:19 asgard NetworkManager: <info> Trying to start the supplicant...
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): supplicant manager state:  down -> idle
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Apr 23 16:03:19 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 16:04:13 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:04:13 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:04:13 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:04:13 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:04:13 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:04:13 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:04:13 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:04:13 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:04:13 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:04:13 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:04:13 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:04:15 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:04:15 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:04:15 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:04:15 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:04:15 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:04:15 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:04:15 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:04:15 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:04:15 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:04:15 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:04:15 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:04:15 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:04:15 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:04:15 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:04:15 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:04:15 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> associating
Apr 23 16:04:35 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:04:35 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:04:38 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:04:40 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:04:40 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:04:51 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:04:51 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:04:51 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:04:51 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:04:51 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:04:51 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:04:51 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:04:51 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:04:51 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:04:51 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:04:51 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:04:51 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:04:51 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:04:51 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:04:51 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:04:54 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:05:14 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:05:14 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:05:17 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:05:17 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:05:19 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:05:19 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:05:19 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:05:19 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 16:07:20 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 16:07:20 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth1
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:07:30 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:07:30 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:07:30 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:07:30 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:07:30 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:07:30 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:07:30 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:07:30 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:07:30 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:07:30 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:07:30 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:07:30 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:07:30 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:07:33 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:07:53 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:07:53 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:07:55 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:07:55 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:08:00 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:08:00 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:08:00 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:08:00 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 16:10:36 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 16:10:36 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth1
Apr 23 16:10:43 asgard NetworkManager: <info> sleeping...
Apr 23 16:10:43 asgard NetworkManager: <info> (eth0): now unmanaged
Apr 23 16:10:43 asgard NetworkManager: <info> (eth0): device state change: 2 -> 1 (reason 37)
Apr 23 16:10:43 asgard NetworkManager: <info> (eth0): cleaning up...
Apr 23 16:10:43 asgard NetworkManager: <info> (eth0): taking down device.
Apr 23 16:10:43 asgard NetworkManager: <info> (wlan0): now unmanaged
Apr 23 16:10:43 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 1 (reason 37)
Apr 23 16:10:43 asgard NetworkManager: <info> (wlan0): cleaning up...
Apr 23 16:10:43 asgard NetworkManager: <info> (wlan0): taking down device.
Apr 23 16:10:43 asgard NetworkManager: <info> (eth1): now unmanaged
Apr 23 16:10:43 asgard NetworkManager: <info> (eth1): device state change: 2 -> 1 (reason 37)
Apr 23 16:10:43 asgard NetworkManager: <info> (eth1): cleaning up...
Apr 23 16:10:43 asgard NetworkManager: <info> (eth1): taking down device.
Apr 23 16:10:47 asgard NetworkManager: <info> waking up...
Apr 23 16:10:47 asgard NetworkManager: <info> (eth0): now managed
Apr 23 16:10:47 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 16:10:47 asgard NetworkManager: <info> (eth0): bringing up device.
Apr 23 16:10:47 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 16:10:47 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 16:10:47 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 16:10:47 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 16:10:47 asgard NetworkManager: <info> (wlan0): bringing up device.
Apr 23 16:10:47 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 16:10:47 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 16:10:47 asgard NetworkManager: <info> (eth1): now managed
Apr 23 16:10:47 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 16:10:47 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 16:10:47 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 16:10:47 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 16:10:47 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 16:10:47 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Apr 23 16:10:48 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:10:48 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:10:48 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:10:48 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:10:48 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:10:48 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:10:48 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:10:48 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:10:48 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:10:48 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:10:48 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:10:49 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:10:49 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:10:49 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:10:49 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:10:49 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:10:49 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:10:49 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:10:49 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:10:49 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:10:49 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:10:49 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:10:49 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:10:49 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:10:49 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:10:49 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:10:49 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> associating
Apr 23 16:11:09 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:11:09 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:11:12 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:11:14 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:11:14 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:11:17 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:11:17 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:11:17 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:11:17 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:11:17 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:11:17 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:11:17 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:11:17 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:11:17 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:11:17 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:11:17 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:11:17 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:11:17 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:11:17 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:11:17 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> associating
Apr 23 16:11:37 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:11:37 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:11:40 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:11:42 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:11:42 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:11:44 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:11:44 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:11:44 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:11:44 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 16:12:06 asgard NetworkManager: <info> sleeping...
Apr 23 16:12:06 asgard NetworkManager: <info> (eth0): now unmanaged
Apr 23 16:12:06 asgard NetworkManager: <info> (eth0): device state change: 2 -> 1 (reason 37)
Apr 23 16:12:06 asgard NetworkManager: <info> (eth0): cleaning up...
Apr 23 16:12:06 asgard NetworkManager: <info> (eth0): taking down device.
Apr 23 16:12:06 asgard NetworkManager: <info> (wlan0): now unmanaged
Apr 23 16:12:06 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 1 (reason 37)
Apr 23 16:12:06 asgard NetworkManager: <info> (wlan0): cleaning up...
Apr 23 16:12:06 asgard NetworkManager: <info> (wlan0): taking down device.
Apr 23 16:12:06 asgard NetworkManager: <info> (eth1): now unmanaged
Apr 23 16:12:06 asgard NetworkManager: <info> (eth1): device state change: 2 -> 1 (reason 37)
Apr 23 16:12:06 asgard NetworkManager: <info> (eth1): cleaning up...
Apr 23 16:12:06 asgard NetworkManager: <info> (eth1): taking down device.
Apr 23 16:12:07 asgard NetworkManager: <info> waking up...
Apr 23 16:12:07 asgard NetworkManager: <info> (eth0): now managed
Apr 23 16:12:07 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 16:12:07 asgard NetworkManager: <info> (eth0): bringing up device.
Apr 23 16:12:07 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 16:12:07 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 16:12:07 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 16:12:07 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 16:12:07 asgard NetworkManager: <info> (wlan0): bringing up device.
Apr 23 16:12:07 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 16:12:07 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 16:12:07 asgard NetworkManager: <info> (eth1): now managed
Apr 23 16:12:07 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 16:12:07 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 16:12:07 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 16:12:07 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 16:12:08 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 16:12:08 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:12:12 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:12:12 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:12:12 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:12:12 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:12:12 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:12:12 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:12:12 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:12:12 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:12:12 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:12:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:12:12 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:12:12 asgard NetworkManager: <info> (wlan0): supplicant connection state:  inactive -> associating
Apr 23 16:12:31 asgard NetworkManager: <info> caught signal 15, shutting down normally.
Apr 23 16:12:31 asgard NetworkManager: <info> (eth0): cleaning up...
Apr 23 16:12:31 asgard NetworkManager: <info> (eth0): taking down device.
Apr 23 16:12:31 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 36).
Apr 23 16:12:31 asgard NetworkManager: <info> (wlan0): taking down device.
Apr 23 16:12:31 asgard NetworkManager: <info> (eth1): cleaning up...
Apr 23 16:12:31 asgard NetworkManager: <info> (eth1): taking down device.
Apr 23 16:12:31 asgard NetworkManager: <info> exiting (success)
Apr 23 16:12:32 asgard NetworkManager: <info> starting...
Apr 23 16:12:32 asgard NetworkManager: <info> modem-manager is now available
Apr 23 16:12:32 asgard NetworkManager:    ifcfg-rh: Acquired D-Bus service com.redhat.ifcfgrh1
Apr 23 16:12:32 asgard NetworkManager: <info> Loaded plugin ifcfg-rh: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 23 16:12:32 asgard NetworkManager: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Apr 23 16:12:32 asgard NetworkManager: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 23 16:12:32 asgard NetworkManager: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 23 16:12:32 asgard NetworkManager: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 23 16:12:32 asgard NetworkManager: <info> Networking is enabled by state file
Apr 23 16:12:32 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth0 ... 
Apr 23 16:12:32 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth0'
Apr 23 16:12:32 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 16:12:32 asgard NetworkManager:    ifcfg-rh:     error: Missing SSID
Apr 23 16:12:32 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-lo ... 
Apr 23 16:12:32 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth1 ... 
Apr 23 16:12:32 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth1'
Apr 23 16:12:32 asgard NetworkManager: <info> (eth0): carrier is OFF
Apr 23 16:12:32 asgard NetworkManager: <info> (eth0): new Ethernet device (driver: 'sky2')
Apr 23 16:12:32 asgard NetworkManager: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 16:12:32 asgard NetworkManager: <info> (eth0): now managed
Apr 23 16:12:32 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 16:12:32 asgard NetworkManager: <info> (eth0): bringing up device.
Apr 23 16:12:32 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 16:12:32 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci')
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): bringing up device.
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 16:12:32 asgard NetworkManager: <info> (eth1): carrier is OFF
Apr 23 16:12:32 asgard NetworkManager: <info> (eth1): new Ethernet device (driver: 'skge')
Apr 23 16:12:32 asgard NetworkManager: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 23 16:12:32 asgard NetworkManager: <info> (eth1): now managed
Apr 23 16:12:32 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 16:12:32 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 16:12:32 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 16:12:32 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Apr 23 16:12:32 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:12:32 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:12:32 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:12:32 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:12:32 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:12:32 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:12:32 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:12:32 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:12:32 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:12:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:12:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:12:33 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:12:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:12:33 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:12:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:12:33 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:12:33 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:12:33 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:12:33 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:12:33 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:12:33 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:12:33 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:12:33 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:12:33 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:12:34 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> associating
Apr 23 16:12:54 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:12:54 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:12:57 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:12:59 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:12:59 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:13:02 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:13:02 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:13:02 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:13:02 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 16:14:03 asgard NetworkManager: ******************* START **********************************
Apr 23 16:14:05 asgard NetworkManager: [Thread debugging using libthread_db enabled]
Apr 23 16:14:05 asgard NetworkManager: 0x00007fd2e9c7a4be in waitpid () from /lib64/libpthread.so.0
Apr 23 16:14:05 asgard NetworkManager: #0  0x00007fd2e9c7a4be in waitpid () from /lib64/libpthread.so.0
Apr 23 16:14:05 asgard NetworkManager: #1  0x000000000044ec2b in nm_logging_backtrace ()
Apr 23 16:14:05 asgard NetworkManager: #2  0x000000000043bd79 in ?? ()
Apr 23 16:14:05 asgard NetworkManager: #3  <signal handler called>
Apr 23 16:14:05 asgard NetworkManager: #4  0x00007fd2e84e6955 in raise () from /lib64/libc.so.6
Apr 23 16:14:05 asgard NetworkManager: #5  0x00007fd2e84e8135 in abort () from /lib64/libc.so.6
Apr 23 16:14:05 asgard NetworkManager: #6  0x00007fd2e9eb2905 in ?? () from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: #7  0x00007fd2e9eae7e5 in ?? () from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: #8  0x00007fd2e9ea3601 in dbus_message_new_error () from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: #9  0x00007fd2ea0d5520 in ?? () from /usr/lib64/libdbus-glib-1.so.2
Apr 23 16:14:05 asgard NetworkManager: #10 0x00007fd2ea0d6567 in ?? () from /usr/lib64/libdbus-glib-1.so.2
Apr 23 16:14:05 asgard NetworkManager: #11 0x00007fd2e9ea4d3e in ?? () from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: #12 0x00007fd2e9e98a1c in dbus_connection_dispatch ()
Apr 23 16:14:05 asgard NetworkManager:    from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: #13 0x00007fd2ea0d2a25 in ?? () from /usr/lib64/libdbus-glib-1.so.2
Apr 23 16:14:05 asgard NetworkManager: #14 0x00007fd2e8cfbd02 in g_main_context_dispatch ()
Apr 23 16:14:05 asgard NetworkManager:    from /lib64/libglib-2.0.so.0
Apr 23 16:14:05 asgard NetworkManager: #15 0x00007fd2e8cffae8 in ?? () from /lib64/libglib-2.0.so.0
Apr 23 16:14:05 asgard NetworkManager:  () from /lib64/libglib-2.0.so.0
Apr 23 16:14:05 asgard NetworkManager: #17 0x000000000043d094 in main ()
Apr 23 16:14:05 asgard NetworkManager: 
Apr 23 16:14:05 asgard NetworkManager: Thread 1 (Thread 0x7fd2ec6f07e0 (LWP 2823)):
Apr 23 16:14:05 asgard NetworkManager: #0  0x00007fd2e9c7a4be in waitpid () from /lib64/libpthread.so.0
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: e ()
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #2  0x000000000043bd79 in ?? ()
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #3  <signal handler called>
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #4  0x00007fd2e84e6955 in raise () from /lib64/libc.so.6
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: x00007fd2e84e8135 in abort () from /lib64/libc.so.6
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #6  0x00007fd2e9eb2905 in ?? () from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #7  0x00007fd2e9eae7e5 in ?? () from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: available.
Apr 23 16:14:05 asgard NetworkManager: #8  0x00007fd2e9ea3601 in dbus_message_new_error () from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #9  0x00007fd2ea0d5520 in ?? () from /usr/lib64/libdbus-glib-1.so.2
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: rom /usr/lib64/libdbus-glib-1.so.2
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #11 0x00007fd2e9ea4d3e in ?? () from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #12 0x00007fd2e9e98a1c in dbus_connection_dispatch ()
Apr 23 16:14:05 asgard NetworkManager:    from /lib64/libdbus-1.so.3
Apr 23 16:14:05 asgard NetworkManager: le info available.
Apr 23 16:14:05 asgard NetworkManager: #13 0x00007fd2ea0d2a25 in ?? () from /usr/lib64/libdbus-glib-1.so.2
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #14 0x00007fd2e8cfbd02 in g_main_context_dispatch ()
Apr 23 16:14:05 asgard NetworkManager:    from /lib64/libglib-2.0.so.0
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: ae8 in ?? () from /lib64/libglib-2.0.so.0
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #16 0x00007fd2e8cffff5 in g_main_loop_run () from /lib64/libglib-2.0.so.0
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: #17 0x000000000043d094 in main ()
Apr 23 16:14:05 asgard NetworkManager: No symbol table info available.
Apr 23 16:14:05 asgard NetworkManager: ng session is active.
Apr 23 16:14:05 asgard NetworkManager: 
Apr 23 16:14:05 asgard NetworkManager: #011Inferior 1 [process 2823] will be detached.
Apr 23 16:14:05 asgard NetworkManager: 
Apr 23 16:14:05 asgard NetworkManager: Quit anyway? (y or n) [answered Y; input not from terminal]
Apr 23 16:14:05 asgard NetworkManager: ******************* END **********************************
Apr 23 16:16:25 asgard NetworkManager: <info> starting...
Apr 23 16:16:25 asgard NetworkManager: <info> trying to start the modem manager...
Apr 23 16:16:25 asgard NetworkManager:    ifcfg-rh: Acquired D-Bus service com.redhat.ifcfgrh1
Apr 23 16:16:25 asgard NetworkManager: <info> Loaded plugin ifcfg-rh: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 23 16:16:25 asgard NetworkManager: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Apr 23 16:16:25 asgard NetworkManager: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 23 16:16:25 asgard NetworkManager: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 23 16:16:25 asgard NetworkManager: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 23 16:16:25 asgard NetworkManager: <info> Networking is enabled by state file
Apr 23 16:16:25 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth0 ... 
Apr 23 16:16:25 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth0'
Apr 23 16:16:25 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 16:16:25 asgard NetworkManager:    ifcfg-rh:     error: Missing SSID
Apr 23 16:16:25 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-lo ... 
Apr 23 16:16:25 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth1 ... 
Apr 23 16:16:25 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth1'
Apr 23 16:16:25 asgard NetworkManager: <info> (eth0): carrier is OFF
Apr 23 16:16:25 asgard NetworkManager: <info> (eth0): new Ethernet device (driver: 'sky2')
Apr 23 16:16:25 asgard NetworkManager: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 16:16:25 asgard NetworkManager: <info> (eth0): now managed
Apr 23 16:16:25 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 16:16:25 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 16:16:25 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci')
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 16:16:25 asgard NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Apr 23 16:16:25 asgard NetworkManager: <info> (eth1): carrier is OFF
Apr 23 16:16:25 asgard NetworkManager: <info> (eth1): new Ethernet device (driver: 'skge')
Apr 23 16:16:25 asgard NetworkManager: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 23 16:16:25 asgard NetworkManager: <info> (eth1): now managed
Apr 23 16:16:25 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 16:16:25 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 16:16:25 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 16:16:25 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 16:16:25 asgard NetworkManager: <info> modem-manager is now available
Apr 23 16:16:25 asgard NetworkManager: <info> Trying to start the supplicant...
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): supplicant manager state:  down -> idle
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Apr 23 16:16:25 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:16:42 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:16:42 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:16:42 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:16:42 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:16:42 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:16:42 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:16:42 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:16:42 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:16:42 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:16:42 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:16:42 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:16:42 asgard NetworkManager: <info> (wlan0): supplicant connection state:  inactive -> scanning
Apr 23 16:16:45 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:17:05 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:17:05 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:17:07 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:17:07 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:17:13 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:17:13 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:17:13 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:17:13 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:18:06 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:18:06 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:18:06 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:18:06 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:18:06 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:18:06 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:18:06 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:18:06 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:18:06 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:18:06 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:18:06 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:18:06 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:18:06 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:18:09 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:18:29 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:18:29 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:18:32 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:18:32 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:18:35 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:18:35 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:18:35 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:18:35 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 16:18:53 asgard NetworkManager: <info> (eth0): carrier now ON (device state 2)
Apr 23 16:18:53 asgard NetworkManager: <info> (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) starting connection 'System eth0'
Apr 23 16:18:53 asgard NetworkManager: <info> (eth0): device state change: 3 -> 4 (reason 0)
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:18:53 asgard NetworkManager: <info> (eth0): device state change: 4 -> 5 (reason 0)
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 23 16:18:53 asgard NetworkManager: <info> (eth0): device state change: 5 -> 7 (reason 0)
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 23 16:18:53 asgard NetworkManager: <info> dhclient started with pid 2196
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 23 16:18:53 asgard NetworkManager: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 23 16:18:53 asgard NetworkManager: <info> (eth0): DHCPv4 state changed preinit -> reboot
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 23 16:18:53 asgard NetworkManager: <info>   address 192.168.0.192
Apr 23 16:18:53 asgard NetworkManager: <info>   prefix 24 (255.255.255.0)
Apr 23 16:18:53 asgard NetworkManager: <info>   gateway 192.168.0.1
Apr 23 16:18:53 asgard NetworkManager: <info>   nameserver '192.168.0.1'
Apr 23 16:18:53 asgard NetworkManager: <info>   domain name 'hsd1.wa.comcast.net.'
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 23 16:18:53 asgard NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 23 16:18:54 asgard NetworkManager: <info> (eth0): device state change: 7 -> 8 (reason 0)
Apr 23 16:18:54 asgard NetworkManager: <info> Policy set 'System eth0' (eth0) as default for routing and DNS.
Apr 23 16:18:54 asgard NetworkManager: <info> Activation (eth0) successful, device activated.
Apr 23 16:18:54 asgard NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 23 16:20:09 asgard NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Apr 23 16:20:09 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:20:09 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:20:09 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:20:09 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:20:09 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:20:09 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:20:09 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:20:09 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:20:09 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:20:09 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:20:09 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:20:28 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:20:28 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:20:28 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:20:28 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:20:28 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:20:28 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:20:28 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:20:28 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:20:28 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:20:28 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:20:28 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:20:28 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:20:28 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:20:28 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:20:28 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:20:28 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:20:31 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:20:51 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:20:51 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:20:54 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:20:54 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:23:25 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:23:25 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:23:25 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:23:25 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 16:23:25 asgard NetworkManager: <info> Policy set 'System eth0' (eth0) as default for routing and DNS.
Apr 23 16:24:52 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 16:24:52 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth1
Apr 23 16:25:10 asgard NetworkManager: <info> caught signal 15, shutting down normally.
Apr 23 16:25:10 asgard NetworkManager: <info> (wlan0): taking down device.
Apr 23 16:25:10 asgard NetworkManager: <info> (eth1): cleaning up...
Apr 23 16:25:10 asgard NetworkManager: <info> (eth1): taking down device.
Apr 23 16:25:10 asgard NetworkManager: <info> exiting (success)
Apr 23 16:26:08 asgard NetworkManager: <info> starting...
Apr 23 16:26:08 asgard NetworkManager: <info> trying to start the modem manager...
Apr 23 16:26:08 asgard NetworkManager:    ifcfg-rh: Acquired D-Bus service com.redhat.ifcfgrh1
Apr 23 16:26:08 asgard NetworkManager: <info> Loaded plugin ifcfg-rh: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 23 16:26:08 asgard NetworkManager: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Apr 23 16:26:08 asgard NetworkManager: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 23 16:26:08 asgard NetworkManager: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 23 16:26:08 asgard NetworkManager: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 23 16:26:08 asgard NetworkManager: <info> Networking is enabled by state file
Apr 23 16:26:08 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth0 ... 
Apr 23 16:26:08 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth0'
Apr 23 16:26:08 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 16:26:08 asgard NetworkManager:    ifcfg-rh:     error: Missing SSID
Apr 23 16:26:08 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-lo ... 
Apr 23 16:26:08 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth1 ... 
Apr 23 16:26:08 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth1'
Apr 23 16:26:08 asgard NetworkManager: <info> (eth0): carrier is OFF
Apr 23 16:26:08 asgard NetworkManager: <info> (eth0): new Ethernet device (driver: 'sky2')
Apr 23 16:26:08 asgard NetworkManager: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 16:26:08 asgard NetworkManager: <info> (eth0): now managed
Apr 23 16:26:08 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 16:26:08 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 16:26:08 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci')
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 16:26:08 asgard NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Apr 23 16:26:08 asgard NetworkManager: <info> (eth1): carrier is OFF
Apr 23 16:26:08 asgard NetworkManager: <info> (eth1): new Ethernet device (driver: 'skge')
Apr 23 16:26:08 asgard NetworkManager: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 23 16:26:08 asgard NetworkManager: <info> (eth1): now managed
Apr 23 16:26:08 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 16:26:08 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 16:26:08 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 16:26:08 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 16:26:08 asgard NetworkManager: <info> modem-manager is now available
Apr 23 16:26:08 asgard NetworkManager: <info> Trying to start the supplicant...
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): supplicant manager state:  down -> idle
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Apr 23 16:26:08 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 16:27:22 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:27:22 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 16:27:22 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 16:27:22 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 16:27:22 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 16:27:22 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 16:27:22 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 16:27:22 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 16:27:22 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 16:27:22 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 16:27:22 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 16:27:22 asgard NetworkManager: <info> (wlan0): supplicant connection state:  inactive -> scanning
Apr 23 16:27:25 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 16:27:45 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 16:27:45 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 16:27:48 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 16:27:48 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 16:27:50 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 16:27:50 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 16:27:50 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 16:27:50 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 17:27:12 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:27:12 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 17:27:12 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:27:12 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:27:12 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 17:27:12 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 17:27:12 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 17:27:12 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 17:27:12 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 17:27:12 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:27:12 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 17:27:12 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 17:27:12 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:27:15 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 17:27:35 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 17:27:35 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:27:38 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 17:27:38 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 17:31:51 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 17:31:51 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 17:31:51 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 17:31:51 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 17:44:50 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 17:44:50 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth1
Apr 23 17:44:50 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 17:44:52 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 17:45:52 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth0
Apr 23 17:45:52 asgard NetworkManager:    ifcfg-rh: updating /etc/sysconfig/network-scripts/ifcfg-eth1
Apr 23 17:45:53 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen ... 
Apr 23 17:45:53 asgard NetworkManager:    ifcfg-rh:     error: Missing SSID
Apr 23 17:45:53 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen ... 
Apr 23 17:45:53 asgard NetworkManager:    ifcfg-rh:     error: Missing SSID
Apr 23 17:45:53 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 17:45:53 asgard NetworkManager:    ifcfg-rh:     error: Couldn't parse file '/etc/sysconfig/network-scripts/ifcfg-Evergreen_1'
Apr 23 17:45:53 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen_1 ... 
Apr 23 17:45:53 asgard NetworkManager:    ifcfg-rh:     error: Couldn't parse file '/etc/sysconfig/network-scripts/ifcfg-Evergreen_1'
Apr 23 17:46:04 asgard NetworkManager: <info> caught signal 15, shutting down normally.
Apr 23 17:46:04 asgard NetworkManager: <info> (eth0): cleaning up...
Apr 23 17:46:04 asgard NetworkManager: <info> (eth0): taking down device.
Apr 23 17:46:04 asgard NetworkManager: <info> (wlan0): taking down device.
Apr 23 17:46:04 asgard NetworkManager: <info> (eth1): cleaning up...
Apr 23 17:46:04 asgard NetworkManager: <info> (eth1): taking down device.
Apr 23 17:46:04 asgard NetworkManager: <info> exiting (success)
Apr 23 17:47:00 asgard NetworkManager: <info> starting...
Apr 23 17:47:00 asgard NetworkManager: <info> trying to start the modem manager...
Apr 23 17:47:00 asgard NetworkManager:    ifcfg-rh: Acquired D-Bus service com.redhat.ifcfgrh1
Apr 23 17:47:00 asgard NetworkManager: <info> Loaded plugin ifcfg-rh: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 23 17:47:00 asgard NetworkManager: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Apr 23 17:47:00 asgard NetworkManager: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 23 17:47:00 asgard NetworkManager: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 23 17:47:00 asgard NetworkManager: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 23 17:47:00 asgard NetworkManager: <info> Networking is enabled by state file
Apr 23 17:47:00 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth0 ... 
Apr 23 17:47:00 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth0'
Apr 23 17:47:00 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-Evergreen ... 
Apr 23 17:47:00 asgard NetworkManager:    ifcfg-rh:     error: Missing SSID
Apr 23 17:47:00 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-lo ... 
Apr 23 17:47:00 asgard NetworkManager:    ifcfg-rh: parsing /etc/sysconfig/network-scripts/ifcfg-eth1 ... 
Apr 23 17:47:00 asgard NetworkManager:    ifcfg-rh:     read connection 'System eth1'
Apr 23 17:47:00 asgard NetworkManager: <info> (eth0): carrier is OFF
Apr 23 17:47:00 asgard NetworkManager: <info> (eth0): new Ethernet device (driver: 'sky2')
Apr 23 17:47:00 asgard NetworkManager: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 17:47:00 asgard NetworkManager: <info> (eth0): now managed
Apr 23 17:47:00 asgard NetworkManager: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 23 17:47:00 asgard NetworkManager: <info> (eth0): bringing up device.
Apr 23 17:47:00 asgard NetworkManager: <info> (eth0): preparing device.
Apr 23 17:47:00 asgard NetworkManager: <info> (eth0): deactivating device (reason: 2).
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci')
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): now managed
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): preparing device.
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 2).
Apr 23 17:47:00 asgard NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Apr 23 17:47:00 asgard NetworkManager: <info> (eth1): carrier is OFF
Apr 23 17:47:00 asgard NetworkManager: <info> (eth1): new Ethernet device (driver: 'skge')
Apr 23 17:47:00 asgard NetworkManager: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 23 17:47:00 asgard NetworkManager: <info> (eth1): now managed
Apr 23 17:47:00 asgard NetworkManager: <info> (eth1): device state change: 1 -> 2 (reason 2)
Apr 23 17:47:00 asgard NetworkManager: <info> (eth1): bringing up device.
Apr 23 17:47:00 asgard NetworkManager: <info> (eth1): preparing device.
Apr 23 17:47:00 asgard NetworkManager: <info> (eth1): deactivating device (reason: 2).
Apr 23 17:47:00 asgard NetworkManager: <info> modem-manager is now available
Apr 23 17:47:00 asgard NetworkManager: <info> Trying to start the supplicant...
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): supplicant manager state:  down -> idle
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Apr 23 17:47:00 asgard NetworkManager: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 17:47:19 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:47:19 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 17:47:19 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:47:19 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:47:19 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 17:47:19 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 17:47:19 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 17:47:19 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 17:47:19 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 17:47:19 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:47:19 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 17:47:19 asgard NetworkManager: <info> (wlan0): supplicant connection state:  inactive -> scanning
Apr 23 17:47:22 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 17:47:42 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 17:47:42 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:47:45 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 17:47:45 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 17:48:36 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:48:36 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:48:36 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 17:48:36 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:48:36 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:48:36 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:48:36 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:48:36 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 17:48:36 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 17:48:36 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 17:48:36 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 17:48:36 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 17:48:36 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:48:36 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 17:48:36 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:48:39 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 17:48:59 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 17:48:59 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:49:01 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 17:49:01 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 17:49:02 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 17:49:02 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 17:49:02 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 17:49:02 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 17:49:13 asgard NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Apr 23 17:49:13 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 17:49:13 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 17:49:13 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:49:13 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:49:13 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:49:13 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:49:13 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:49:13 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:49:13 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 17:49:13 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 17:49:13 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:49:27 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:49:27 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:49:27 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 17:49:27 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:49:27 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:49:27 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:49:27 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:49:27 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 17:49:27 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 17:49:27 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 17:49:27 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 17:49:27 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 17:49:27 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:49:27 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 17:49:27 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:49:30 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 17:49:50 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 17:49:50 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:49:53 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 17:49:53 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 17:50:17 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 17:50:17 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 17:50:17 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 17:50:17 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 17:54:10 asgard NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Apr 23 17:54:10 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto default'
Apr 23 17:54:10 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 17:54:10 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:54:10 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:54:10 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:54:10 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:54:10 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:54:10 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:54:10 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto default' requires no security.  No secrets needed.
Apr 23 17:54:10 asgard NetworkManager: <info> Config: added 'ssid' value 'default'
Apr 23 17:54:10 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 17:54:10 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'NONE'
Apr 23 17:54:10 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:54:10 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 17:54:10 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 17:54:10 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:54:36 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 9 (reason 11)
Apr 23 17:54:36 asgard NetworkManager: <info> Marking connection 'Auto default' invalid.
Apr 23 17:54:36 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 17:54:36 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 17:56:44 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto default'
Apr 23 17:56:44 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 17:56:44 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 17:56:44 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 17:56:44 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 17:56:44 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 17:56:44 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 17:56:44 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 17:56:44 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto default' requires no security.  No secrets needed.
Apr 23 17:56:44 asgard NetworkManager: <info> Config: added 'ssid' value 'default'
Apr 23 17:56:44 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 17:56:44 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'NONE'
Apr 23 17:56:44 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 17:56:44 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 17:56:44 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 17:56:44 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 17:57:10 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 9 (reason 11)
Apr 23 17:57:10 asgard NetworkManager: <info> Marking connection 'Auto default' invalid.
Apr 23 17:57:10 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 17:57:10 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) starting connection 'Auto Evergreen 1'
Apr 23 18:09:18 asgard NetworkManager: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 18:09:18 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0/wireless): access point 'Auto Evergreen 1' has security, but secrets are required.
Apr 23 18:09:18 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 23 18:09:18 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 23 18:09:18 asgard NetworkManager: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0/wireless): connection 'Auto Evergreen 1' has security, and secrets exist.  No new secrets needed.
Apr 23 18:09:18 asgard NetworkManager: <info> Config: added 'ssid' value 'Evergreen 1'
Apr 23 18:09:18 asgard NetworkManager: <info> Config: added 'scan_ssid' value '1'
Apr 23 18:09:18 asgard NetworkManager: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 23 18:09:18 asgard NetworkManager: <info> Config: added 'psk' value '<omitted>'
Apr 23 18:09:18 asgard NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 23 18:09:18 asgard NetworkManager: <info> Config: set interface ap_scan to 1
Apr 23 18:09:18 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 18:09:18 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 18:09:21 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 23 18:09:41 asgard NetworkManager: <info> (wlan0): supplicant connection state:  associating -> disconnected
Apr 23 18:09:41 asgard NetworkManager: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 23 18:09:44 asgard NetworkManager: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 23 18:09:44 asgard NetworkManager: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 23 18:09:57 asgard NetworkManager: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Apr 23 18:09:57 asgard NetworkManager: <info> Marking connection 'Auto Evergreen 1' invalid.
Apr 23 18:09:57 asgard NetworkManager: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 23 18:09:57 asgard NetworkManager: <info> (wlan0): deactivating device (reason: 0).

```

nmtool output:

```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:18:F3:44:D3:F5

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        00:25:9C:F5:26:D9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Evergreen 1:     Infra, 00:21:91:FF:1C:77, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA2
    cjzj-c:          Infra, 00:14:BF:72:DB:35, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    default:         Infra, 00:13:46:19:F3:A2, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    Randy's wifi:    Infra, 00:26:F2:FD:CB:49, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    EMGR4:           Infra, 00:21:63:5D:9B:6D, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    Monet:           Infra, 00:14:BF:AB:F7:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    Firebird:        Infra, 00:21:63:5F:61:84, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            skge
  State:             unavailable
  Default:           no
  HW Address:        00:18:F3:44:C7:75

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

---

### Post by Sisu7 on 2010-05-09
> **bowens44 said:**
> I have finally solved this issue. I had about given up on it. But now, I am connected at 243Mbps in Jaunty using a Trendnet TEW-623PI wireless adapter and a Linksys WRT350n router with DD-WRT firmware!!

Here's what I did , it was really quite easy once I found the info.

1. I renamed the existing  driver from rt2860sta.ko to rt2860sta.bk

2. I downloaded the latest driver , rt2860 Version 2.1.2.0 from
   [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

3. Extracted the directory/files to my desktop

4. modified the config.mk file changing the following entires from n to y
   
    #ifdef WPA_SUPPLICANT_SUPPORT
    # Support Wpa_Supplicant
    HAS_WPA_SUPPLICANT=y
    #endif // WPA_SUPPLICANT_SUPPORT //

    #ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
    # Support Native WpaSupplicant for Network Maganger
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
    #endif // NATIVE_WPA_SUPPLICANT_SUPPORT //

5. did sudo make && make install

6. rebooted the computer and I now see a connect speed of 243Mb/s

Thanks a lot! That worked for me without any problems on ubuntu 10.04 x64.

I first tried the driver provided by Edimax, but just errors.

Thanks again, now I can surf the net without my other computer sharing its connection via cable ;) =)

---

### Post by Papa Romeo on 2010-06-08
Solca,

This worked without any problems for me on my Linksys WMP600N connected at 130Mbps to my Linksys WRT310N with Linksys firmware.

I'm running completely updated Ubuntu 10.04 LTS with stock 2.6.32-22 kernel  and stock rt2860sta wireless driver.

Many thanks,

Papa Romeo


> **solca said:**
> Hey guys, just FYI my Asus EeePC 1000 with Ralink 2860 wireless adapter is successfully locked at 135Mbps to my Linksys WRT160NL (with OpenWRT firmware), iperf reports 80Mbps with 40MHz channel width or 50Mbps with 20MHz channel width.

I'm running completely updated Ubuntu 9.10 with stock 2.6.31-14 kernel and stock rt2860sta wireless driver.

The trick is that you need the proper driver's config file at /etc/Wireless/RT2860STA/RT2860STA.dat that enables HT (High Throughput) mode.

Attached is my drivers config file uploaded as .txt in case you need it. Remember to rename it and put it at the correct location.

:popcorn:

Please, let me know if it works for you.

HTH.

---

### Post by twaddington on 2010-09-22
> **solca said:**
> Hey guys, just FYI my Asus EeePC 1000 with Ralink 2860 wireless adapter is successfully locked at 135Mbps to my Linksys WRT160NL (with OpenWRT firmware), iperf reports 80Mbps with 40MHz channel width or 50Mbps with 20MHz channel width.

I'm running completely updated Ubuntu 9.10 with stock 2.6.31-14 kernel and stock rt2860sta wireless driver.

The trick is that you need the proper driver's config file at /etc/Wireless/RT2860STA/RT2860STA.dat that enables HT (High Throughput) mode.

Attached is my drivers config file uploaded as .txt in case you need it. Remember to rename it and put it at the correct location.

:popcorn:

Please, let me know if it works for you.

HTH.

Thanks **solca** that worked wonders! I didn't even realize I was only running on 802.11/g speeds until just recently. How did you figure this out?

By the way, I dropped that .dat file into a gist so (hopefully) more people can find it:

[http://gist.github.com/591038](http://gist.github.com/591038)

Here's my config for other user's sake:

```

tristan@vicious:~$ lspci | grep -i network
05:06.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus

tristan@vicious:~$ iwconfig
wlan0     RT2860 Wireless  ESSID:"starbuck"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:26:5A:B5:EA:55   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-54 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by kainalu on 2010-12-08
This thread helped me. THANKS!!

---

### Post by Lucretius on 2011-02-02
bump... why isn't this stickied?

---

### Post by BBUCommander on 2011-02-21
There is actually a more thorough guide that adds extra steps I found necessary to get throughput up:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1476007](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1476007)

Without these extra steps iwconfig reported a connection speed of 270 Mb/s, but I could only get ~20 Mb/s actual throughput.  Definitely worth editing one more line of code.

---

### Post by PsyWolf on 2011-08-21
> **BBUCommander said:**
> There is actually a more thorough guide that adds extra steps I found necessary to get throughput up:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1476007](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1476007)

Without these extra steps iwconfig reported a connection speed of 270 Mb/s, but I could only get ~20 Mb/s actual throughput.  Definitely worth editing one more line of code.

This guide was way easier to follow and it got everything working for me!

P.S.
I'm using a Linksys WMP600N.  Until I performed these steps it wasn't able to detect my 5Ghz wireless N network

---

### Post by BJCV86 on 2012-04-18
> **bowens44 said:**
> I have finally solved this issue. I had about given up on it. But now, I am connected at 243Mbps in Jaunty using a Trendnet TEW-623PI wireless adapter and a Linksys WRT350n router with DD-WRT firmware!!

Here's what I did , it was really quite easy once I found the info.

1. I renamed the existing  driver from rt2860sta.ko to rt2860sta.bk

2. I downloaded the latest driver , rt2860 Version 2.1.2.0 from
   [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

3. Extracted the directory/files to my desktop

4. modified the config.mk file changing the following entires from n to y
   
    #ifdef WPA_SUPPLICANT_SUPPORT
    # Support Wpa_Supplicant
    HAS_WPA_SUPPLICANT=y
    #endif // WPA_SUPPLICANT_SUPPORT //

    #ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
    # Support Native WpaSupplicant for Network Maganger
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
    #endif // NATIVE_WPA_SUPPLICANT_SUPPORT //

5. did sudo make && make install

6. rebooted the computer and I now see a connect speed of 243Mb/s

what is ifdef? Do I write that in? or do I just change the n's to y's?

---

