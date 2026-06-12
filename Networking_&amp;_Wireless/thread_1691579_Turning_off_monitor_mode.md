---
title: "Turning off monitor mode"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by TheRaiderNation on 2011-02-20
[SIZE=3]**Short version: How do I turn of my Monitor Mode so I can connect to Access Points again?**[/SIZE]

This one has been stumping me for a while now. First I had trouble getting into monitor mode, with my stupid b4312 broadcom card and all. But finally got all that taken care of, now I'm having trouble getting the monitor mode to turn off so I can connect to access points again. But I can't see to get out of it.

I was able to get into monitor mode by using kismet: 
```
sudo kismet
```I've tried the following to get out of monitor mode:
```
sudo iwconfig wlan0 mode master
```But that always results in the following:
```
Error for wireless requests "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```and some other far fetched stuff that didn't work.

Any help would be appreciated, thanks.

---

### Post by chili555 on 2011-02-20
> I've tried the following to get out of monitor mode:
Code:

sudo iwconfig wlan0 mode master

Master mode is what your router uses; it is master because it hands out IP addresses, sets bitrates, channel, etc. The wireless card in your computer(s) want to be in managed mode; their characteristics are managed by the router. Please try:```
sudo iwconfig wlan0 mode managed
```Some wireless cards require that the interface be brought down first:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```In either case, you need 'managed.'

---

