---
title: "Buying USB wireless for Master mode &amp; question about antenna"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by nimdekvan on 2011-07-28
Hi All,

Skip the blue text if you want a short story.

[COLOR=RoyalBlue]I've searched for too many days and nights so many information went through my head. I want to buy a usb wireless which support master mode. (not monitor mode)

Now I'm interested in Alfa AWUS036NEH. I like it because it is small an have a long antenna strong 1000mW. signal. (AWUS036H is a little bit big for me)
However from what i have read AWUS036NEH is not supported in master mode (softAP)
(or may be supported but with hostapd, but again some forum said it doesn't support and some say it does... Totally confused.) -> Actually AWUS036NEH is not expensive but I don't want to invest in something i'm not sure about so I won't buy it until I really know if it works.

So I switch to find out what is for sure
1. supported in master mode in Ubuntu
2. Have a long antenna (like 5" or something. I have no idea about hardware but I think longer antenna should send signal more further)
3. small (about normal USB size don't count antenna)

Sadly I only find Alfa AWUS036NEH the only option for me , the others has no brand.
However TL-WN722N is what most likely to fit. Only it has a shorter antenna.
Can i replace the antenna with a longer one (with some others brand) by myself?
(TL-WN722N can use master mode in kernel 3.0 ? already ? some say it should but i've not seen one that stated clearly)
[/COLOR]
=============================================

Ahh I think the above is totally messed up. I will make long story short.

1. Is AWUS036H or AWUS036NEH support master mode in ubuntu ?
(if yes with hostapd or something?)

2. Is TL-WN722N or TL-WN722NC can work in master mode in Ubuntu ? 
(if yes with hostapd or something?) 

3.Can I replace the original antenna with a longer one ?(with other brand or same brand) Will the signal be stronger?


Really sorry guys I know my questions are a bit messed up.
I have done my own log for what i have already searched but still I'm getting confused 
of this. There are numerous information but yet the information is not so clear.

---

### Post by nimdekvan on 2011-07-28
Ah one more thing. 
I found that AWUS036NEH use chipset Ralink RT2870/3070 rt2800usb
(This mean it use RT2870 or 3070 or rt2800usb right ?)

Just post to give more info to someone who would like to help me.

---

### Post by °-° on 2011-07-29
I don't believe either support master mode, but the antennas can be replaced.

---

### Post by nimdekvan on 2011-07-29
And after replacing with a longer antenna it will have stronger signal right ?

---

### Post by °-° on 2011-07-29
Both Alfa's come with 1000mw 2dbi antennas. You can upgrade to a stronger one but how far away is the AP?

---

### Post by nimdekvan on 2011-07-30
Um. Actually the reason i asked about changing the antenna was i'm not sure about getting AWUS036NEH to work in master mode in ubuntu. 
So I think it would be a good idea to have something that use ath9k_usb driver (This driver support for master mode in linux) as an access point and change the antenna to have a strong signal like AWUS036NEH.   

I remember reading somewhere that TL-WN722N use chipset Atheros AR5416 and use ath9k_htc driver so this might be my choice. 
However the antenna is quite small so I asked if changing to longer antenna would help me with the signal.  

Sorry, long explain to help you understand my view. 
 And I will use this computer as an AP, it's not far from my brother's room but it was blocked by wall.

---

### Post by nimdekvan on 2011-08-05
Ok, I've bought TL-WN722N, chipset AR9271, driver ath9k_htc installed.  I installed hostapd and then :  

> hostapd -dd /etc/hostapd/hostapd.confresult :

> Configuration file: /etc/hostapd/hostapd.conf
Opening raw packet socket for ifindex -1217232908
BSS count 1, BSSID mask ff:ff:ff:ff:ff:ff (0 bits)
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
nl80211: Added 802.11b mode based on 802.11g information
Allowed channel: mode=1 chan=1 freq=2412 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=2 freq=2417 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=3 freq=2422 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=4 freq=2427 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=5 freq=2432 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=6 freq=2437 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=7 freq=2442 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=8 freq=2447 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=9 freq=2452 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=10 freq=2457 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=11 freq=2462 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=12 freq=2467 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=13 freq=2472 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=1 freq=2412 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=2 freq=2417 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=3 freq=2422 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=4 freq=2427 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=5 freq=2432 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=6 freq=2437 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=7 freq=2442 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=8 freq=2447 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=9 freq=2452 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=10 freq=2457 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=11 freq=2462 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=12 freq=2467 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=13 freq=2472 MHz max_tx_power=20 dBm
RATE[0] rate=10 flags=0x2
RATE[1] rate=20 flags=0x6
RATE[2] rate=55 flags=0x6
RATE[3] rate=110 flags=0x6
RATE[4] rate=60 flags=0x0
RATE[5] rate=90 flags=0x0
RATE[6] rate=120 flags=0x0
RATE[7] rate=180 flags=0x0
RATE[8] rate=240 flags=0x0
RATE[9] rate=360 flags=0x0
RATE[10] rate=480 flags=0x0
RATE[11] rate=540 flags=0x0
Passive scanning not supported
Flushing old station entries
Deauthenticate all stations
Mode: IEEE 802.11g  Channel: 11  Frequency: 2462 MHz
Using interface wlan0 with hwaddr 00:27:19:f5:bb:89 and ssid 'VOIDDDD'
Could not set DTIM period for kernel driver
wlan0: Unable to setup interface.
As you can see wlan0 cannot set to Master mode, but when i do "iwconfig"

it gives 
> wlan0     IEEE 802.11bgn  [COLOR=Red]Mode:Master [/COLOR] Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
What ??? 
Anyway I use my laptop to scan for this AP but it cannot be found.
(Same laptop I use vmware as an AP and winXP as client)

Oh, to give more info 
lsmod|grep ath*
gives:
> ath9k_htc              54399  0 
mac80211              268864  1 ath9k_htc
ath9k_common            2112  1 ath9k_htc
ath9k_hw              292282  2 ath9k_htc,ath9k_common
ath                    14092  2 ath9k_htc,ath9k_hw
cfg80211              167077  3 ath9k_htc,mac80211,ath
dmesg | grep ath9k_htc
gives:
> [  121.957586] usb 1-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[  122.388115] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[  127.954281] ath9k_htc 1-1:1.0: ath9k_htc: FW Version: 1.3
[  128.225534] Registered led device: ath9k_htc-phy0
[  128.225666] usb 1-1: ath9k_htc: USB layer initialized
[  128.228060] usbcore: registered new interface driver ath9k_htc
I also installed DHCPD , apache2

Any suggestions?

---

### Post by nimdekvan on 2011-08-09
UPDATE

At last I've figured it out.

If anyone is wondering if TL-WN722N can be use in Master mode or not.

The answer is "Yes" it can be set in master mode. (using hostapd)


The problem in my previous post I use hostapd version 0.6.9
(if you searched for hostapd problem with ath9k_htc there will be a lot of sites saying it's a bug in hostapd 0.6.10 and if you switch back to 0.6.9 there will be no problem,
but that's not for me, I still got an error even if i use 0.6.9 version.)

So I've solved it by using hostapd version 0.7.3
with this guide 
[http://paedi.biche.ch/setupZotac.html](http://paedi.biche.ch/setupZotac.html)

....
Actually when i finished with the guide above 

and launch the command 

> hostapd /etc/hostapd/hostapd.confit still have a little problem saying :

> bash: usr/sbin/hostapd: No such file or directoryAnywat I fixed this by copying hostapd file( in /hostapd-0.7.3/hostapd/) to that directory (/usr/sbin/)

And I can put my TL-WN722N (chipset AR9271, driver ath9k_htc)
in Master mode.

good luck all.

P.S. I post this in order to help anyone facing the same problem with me
hope it can help.

---

