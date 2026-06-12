---
title: "Wireless Problems"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by iswear on 2009-03-27
Hi, im new to ubuntu and i cant get my wireless working like everyone else on these forums.

I have a BCM4306 802.11b/g internal driver. Iv tried 2 ndiswrapper tutorials for this specific driver but nether of them worked.

When type iwconfig in the terminal i get this:   
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If anyone can help i would appreciate it.

---

### Post by ronocdh on 2009-03-27
Need more details about what isn't working. From the post it sounds like the wireless would work (given that you can see wlan0 after an iwconfig) if you just:
```
sudo iwconfig wlan0 essid "NETWORKNAMEHERE"
sudo iwconfig wlan0 key type-your-keyx-outx-like-this-xx
sudo ifup wlan0
```
That should do the trick.

---

### Post by superprash2003 on 2009-03-28
which ubuntu version are you using? have you looked at system->admin->hardware drivers

---

### Post by Kevbert on 2009-03-28
Please take a look at [[COLOR="Red"]this.[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")

---

