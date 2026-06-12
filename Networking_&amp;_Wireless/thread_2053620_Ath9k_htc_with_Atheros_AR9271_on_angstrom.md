---
title: "Ath9k_htc with Atheros AR9271 on angstrom"
date: 2012-09-05
forum: Networking &amp; Wireless
---

### Post by charzoc on 2012-09-05
Good Afternoon Everyone,

I am not sure exactly if this is the right forum to ask, as my problem is using Angstrom Ubuntu on a Beaglebone, but I thought it would be worth asking.  My problem is that I am having issues getting my wireless adapter working.  

System:
-Beaglebone v5
-Angstrom Ubuntu (Made from this video: [http://www.youtube.com/watch?v=HJ9nUqYMjqs&noredirect=1](http://www.youtube.com/watch?v=HJ9nUqYMjqs&noredirect=1))

Wireless Adapter:
TP-Link TL-WN422G Wireless Adapter (Atheros AR9271 chipset)

Wireless Driver:
ath9k_htc

Other notes:
-I have had another usb adapter working flawlessly, so I do not think the problem is the beaglebone.  This also tells me that my etc/network/interfaces is setup correctly.  That usb adapter just did not support an access point, which I need for my project.
-The usb wireless adapter *has* worked on occasion.  I would estimate once every twenty or so attempts.  Let me clarify "worked": when I type iwconfig, it shows the wlan0 and its assigned ip address.  I was able to ssh into that ip for a couple seconds before it stalled and I had to reset my setup.
-I have posted this on another forum, not trying to hide that.  Just running into a dead end with someone who has helped me there and I am looking to broaden the crowd of those who may possibly help :)
-it is saying I can't create tags, so some editing has been done (only using code tags, but it is thinking something else is a tag)

My ultimate goal is to use the beaglebone as an access point with the wireless adapter.  My research has me believe that this chipset and driver will allow for the beaglebone to act as an access point. 

My setup is as follows:  The beaglebone is connected by an ethernet cable to a switch, along with my desktop.  I access the beaglebone via ssh with my desktop.  That works without a problem. 

The problem begins when I plug in the usb wireless adapter.  After about 2 seconds, my ssh session stalls.  When I pull the usb adapter out, it resumes.  I have been using that 2 second timeframe to get some debugging in.  (Type in command, plug in usb, hit enter before the 2 seconds)

lsusb gives me:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0cf3:1006 Atheros Communications, Inc. TP-Link TL-WN322G v3 / TL-WN422G v2 802.11g Atheros AR9271

```lsmod gives me:
```

Module                  Size  Used by
aes_generic            27837  2 
arc4                    1111  2 
ath9k_htc              49066  0 
mac80211              227364  1 ath9k_htc
ath9k_common            3111  1 ath9k_htc
ath9k_hw              357489  2 ath9k_htc,ath9k_common
ath                    15700  3 ath9k_htc,ath9k_common,ath9k_hw
cfg80211              167346  3 ath9k_htc,mac80211,ath
rfkill                 16663  1 cfg80211
spidev                  5012  0 
snd_soc_tlv320aic3x    32666  0

```after removing the usb adapter, dmesg gives me:
```

[ 1242.461717] usb 1-1: new high-speed USB device number 8 using musb-hdrc
[ 1242.622727] usb 1-1: New USB device found, idVendor=0cf3, idProduct=1006
[ 1242.622777] usb 1-1: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[ 1242.622816] usb 1-1: Product: USB2.0 WLAN
[ 1242.622844] usb 1-1: Manufacturer: ATHEROS
[ 1242.622870] usb 1-1: SerialNumber: 12345
[ 1242.931272] usb 1-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 1243.167025] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[ 1254.314385] Failed to initialize the device
[ 1254.320176] ath9k_htc: probe of 1-1:1.0 failed with error -22
[ 1254.322241] usb 1-1: USB disconnect, device number 8

```This part loops about a dozen times, im assuming the "Failed to initialize the device" is my problem.  

My guess is that something is conflicting with the initialization of the device, I am just not sure how I would find out what the conflict is.  Any guidance on what I should be investigating would be greatly appreciated!

If anymore information is needed, please let me know and I will post it asap.  

Thanks!

---

### Post by SeijiSensei on 2012-09-05
I have the N version of that TP-Link adapter, and it works well with 12.04.  (I have a 802.11g router, so I'm not using the N feature.)

Are you plugging it into a USB 3.0 port?  Some 2.0 devices don't work well in 3.0 ports.

I found that when I used the device with 10.04 it connected but did not report the correct speed.  That problem disappeared with the driver that is included in 12.04.  I have no idea what version of Ubuntu is the basis for "Angstrom Ubuntu" but perhaps you just need a newer driver?

---

### Post by kurt18947 on 2012-09-05
This seems to indicate that this  chipset is used in my Netgear WNA1100.  It's been plug 'n' play since day 1.   I wonder what the difference is.

```
Bus 003 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]

```

---

### Post by charzoc on 2012-09-06
The device documentation on their website says it is a usb 2.0 device, and the beaglebone usb port is 2.0 also, so I think we can check that off the list.

I have read that rfkill list has caused problems for some people, and after a little research, it is still a little cyptic to me.  Would it be wise to try to remove rfkill?  From what I can tell, people have had their wireless network without it and it is just a small utility library?

Thanks for the input!

---

