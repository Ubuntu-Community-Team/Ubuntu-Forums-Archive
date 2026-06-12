---
title: "Cannot connect to unsecured wireless network"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by cookscake on 2010-01-24
Hey there everyone, how's it going? I'm pretty much brand spankin' new to the world of linux and wireless networking, and haven't got a clue where to start to fix my problem. I've exhausted myself through about 4 hours of searching and about half a pack of smokes (nasty habit, got to quit) and still cannot seem to find any relevant material to get myself through this. Also, I didn't really understand much of it.

Anyways, my problem is that I cannot connect to any available hotspots in my area through Ubuntu 9.10. I have a D-Link adapter (DWA-552) and it is working fine in Windows, and worked once in Ubuntu right after installation. It was automatically recognized, and wireless connections do show up. I just can't connect to any.

I have my box hooked up to my mom's laptop, which is sharing it's wireless connection (which is also the same one I'm trying to connect to.) I disconnect the LAN before trying to connect to wireless, and tries but fails.

So that's about as far as I get, I don't know what to do. Did I mention I'm a noob :P

Here's some info

```
cake@cbx:~$ uname -mr
2.6.31-14-generic i686
cake@cbx:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  Mode:Managed  Frequency:2.412 GHz  
          Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Signal level: 0... wtf?

```
cake@cbx:~$ lsmod | grep "ath9k"
ath9k                 258744  0 
mac80211              181236  1 ath9k
led_class               4096  1 ath9k
ath                     8060  1 ath9k
cfg80211               93052  3 ath9k,mac80211,ath

```I'm assuming the device is using ath9k

Any help on the subject will be greatly appreciated. I'm going to have to buy a book on this stuff...
Thanks.

::EDIT::
I just updated and tried to connect, it did... signal was at -65dbm. Then as soon as I opened firefox and attempted to access google, it dropped. Signal is back to zero, and I'm in the same old boat again.

---

