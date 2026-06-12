---
title: "EEE PC 701 - low WIFI signal level"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by VictorR on 2009-05-04
I always had 97-100% signal strength on my Asus EEE PC 701 4Gb with Xandros anywhere in my house. Now with Ubuntu 9.04 Netbook Remix it fluctuates between 30 - 70%.
```
iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"octopunia"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:40:F4:D5:D7:98   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=56/100  Signal level:-61 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod | grep ath
ath5k                 107008  0 
mac80211              217464  1 ath5k
led_class              12036  1 ath5k
cfg80211               38032  2 ath5k,mac80211

uname -a
Linux asus-eee-pc 2.6.28-11-generic #43~lp349314apw5 SMP Tue Apr 21 17:26:20 UTC 2009 i686 GNU/Linux

```

Is there any solution for this problem?

---

### Post by kerry_s on 2009-05-04
you can try optimizing your router wireless.

use a different channel than every 1 else, most common are 6 and 11, so don't use those.

shorten your beacon period, most are set to 60 to 100, connections time out at around 30, so try 25, thats what i'm using.

make sure all the channels are set to supported, on my router i have to keep 1 on basic and the rest are set to supported. see pic on that 1, not sure if you have that option.

that's all i can think of right now.

---

### Post by VictorR on 2009-05-04
Thanks, kerry_s,

I checked the settings of my WIFI access point. It is a pretty old and simple model and does not have such advanced tuning.

I am concerned, because nothing was changed - same place, same WIFI Access Point, same netbook. The only thing was replacing Xandros by new Ubuntu 9.04 Netbook Remix. At the far end of my garden Xandros reported more than 80% signal strength, Ubuntu shows only 20%. I have even lost connection once - this never happened before since I had installed WIFI.

That's why I think the problem is in Ubuntu WIFI driver. I see the discussion on the same topic on Easy Peasy forum, as people report same problem as they switched from Xandros to Easy Peasy (eeeUbuntu).

Is there any way to get a better driver for WIFI chip?

---

### Post by VictorR on 2009-05-05
Don't see SOLVED option.

I followed [these recommendations]("http://ubuntuforums.org/showpost.php?p=7200293&postcount=6") and mostly solved my problem.
Although signal strength did not reach 100% all around the house as it was with Xandros, it is definitely higher now and, most importantly, I don't suffer from sudden connection drops, I experienced several times a day; the taskbar indicator showed OK, but I couldn't connect to anywhere.

Also my netbook connects to the network much faster now.

---

