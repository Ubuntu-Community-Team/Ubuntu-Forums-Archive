---
title: "very slow internet connection"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by mrpenguin on 2011-06-07
I have no idea what is going on but I am connected to a friends wi-fi in her home running cable internet, my ubuntu laptop is slower than dail up while her Windsows PC has a super fast connection on the same network, even after shutting hers down mine is still super slow.
I did not have this problem this morning on my wi-fi at home.

any ideas ???

---

### Post by IWantFroyo on 2011-06-07
Try running these, and tell us what happens.
```
sudo iwconfig wlan0 power off
```
This turns off the power management off for your wireless.
```
sudo iwconfig wlan0 rate 54M
```
And this gets it back to speed again.

---

### Post by mrpenguin on 2011-06-07
> **IWantFroyo said:**
> Try running these, and tell us what happens.
```
sudo iwconfig wlan0 power off
```
This turns off the power management off for your wireless.
```
sudo iwconfig wlan0 rate 54M
```
And this gets it back to speed again.


Thanks but still the same

---

### Post by IWantFroyo on 2011-06-07
Does the internet run normally when you plug in an ethernet port? Does it only happen at your friend's house?

---

### Post by mrpenguin on 2011-06-07
> **IWantFroyo said:**
> Does the internet run normally when you plug in an ethernet port? Does it only happen at your friend's house?


I dont have a cable here but i had it here last night and it was working fine, I had it at my house today and it was working fine ......... right now its so slow that I have to use the internet on her computer and use my document files on my computer for work because it takes too long for a web page to open on mine.

---

### Post by IWantFroyo on 2011-06-07
When it was working fine, was it plugged into the power socket? I had a glitch where I had slow internet away from an AC adapter. I'm back at 10.10 now.

---

### Post by nbound on 2011-06-08
Theres several wireless problems in 11.04. Pls post the driver your using. (goto connection information and it will be listed :) )

---

