---
title: "Atheros AR9285 - can't set txpower above 15dBm when disconnected"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by Drycola on 2013-04-11
Good morning/evening.


[English is not my native language, sorry about any errors in spelling/grammar]


I installed Ubuntu 12.04 (dual-boot with Win7) on my Laptop, I felt that my Atheros AR9285 wireless reception is lower on Ubuntu than on Win7.
I investigated the issue and found that on Windows the txpower is 27dBm while on Ubuntu it is 15dBm.
I tried to change it on Ubuntu using


```

sudo iwconfig wlan0 txpower 27

```


but I get the error:


```

Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.

```


But if I change it to a value less than 15dBm, it changes without error.


I found many suggestions that it is a driver limitation, but what confused me is that I could change it ONLY after I connect to my wireless network!
When I'm connected, I can set txpower to 27 without error, but when I'm not connected, I can set it only to 14 or less.


Here is the output of iwconfig before connection:


```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```


and here is after connection (and changing txpower):


```

wlan0     IEEE 802.11bgn  ESSID:"mywifi"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=150 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:5   Missed beacon:0

```


My wireless router is far outside my room, and I cannot connect to it on 15dBm, so I have to physically move out of my room everytime I have to connect, which is too frustrating and impractical, that's why I need the txpower to remain 27dBm even when disconnected.
So, why is that partial limitation? how can I keep it always 27dBm whether connected or not?
Thanks for your attention.


*Things I tried that didn't solve the problem:
- Disabling/enabling power management
- Disabling ath9k hardware encryption (echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf)
- Changing router mode from n/b/g to b/g

---

### Post by Drycola on 2013-04-12
Am I going on the right track or should I look for something other than iwconfig?

---

