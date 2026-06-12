---
title: "Atheros AR5007 monitor mode ( Interpid 8.10 )"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by sagramor on 2009-02-24
First, what I did to get my Atheros working in Intrepid64bit:
```
sudo aptitude install linux-backports-modules-intrepid-generic
```
which if i understand correctly, prohibits my kernel-module from getting updated. Now, don't ask me how, but this is all I had to do to get it working, no madwifi, no madberry, oh and i do believe I disabled driver support for Atheros 5xxx series beforehand through hardware drivers as it is disabled now.

My problem is after I installed and configured kismet:
Source=ath5k,wlan0,wlan0
I cannot change the mode of my atheros without getting:
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

```
i guess I have to install madwifi-tools to get the wlanconfig command to run. I installed it but it still doesn't work. Now I'm pretty lost as to what direction to turn next.

---

