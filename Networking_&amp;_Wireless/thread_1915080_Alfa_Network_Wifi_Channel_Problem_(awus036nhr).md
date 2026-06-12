---
title: "Alfa Network Wifi Channel Problem (awus036nhr)"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by apoc4l1pt0 on 2012-01-25
i have a problem with my awus036nhr. i have installed the rtl8192cu driver. the installation it's ok ! But my Alfa Can't see the wireless network in to channel 12 and 13. these channels are disabled. im in italy, the channel 12 and 13 are allowed. 

How can i enable the channel 12 and 13 ?? 

i try : "iw reg set EU" but the problem is still

PS: i use ubuntu 11.10 32 bit 3.0.0-14-generic

---

### Post by praseodym on 2012-01-25
Hi,

try

```
iw reg get
sudo iw reg set IT #if IT is for italy
```
Otherwise the driver doesnt allow it?

Check:

```
iwlist chan
dmesg | grep country
```

---

### Post by apoc4l1pt0 on 2012-01-26
i have try "iw reg set IT" but the problem is still 

"iwlist chan":
```
wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.452 GHz (Channel 9)

```

"dmesg | grep coutry"

```
[   70.322117] cfg80211: Calling CRDA for country: IT
[   70.324705] cfg80211: Regulatory domain changed to country: IT
[  142.088092] cfg80211: Calling CRDA for country: IT
[  142.095763] cfg80211: Regulatory domain changed to country: IT
x6931x@x6931x-RC530-RC730:~$ 

```

so, i think that the drivers don't allow channel 12 and 13 ....
how can I fix this problem ?

---

