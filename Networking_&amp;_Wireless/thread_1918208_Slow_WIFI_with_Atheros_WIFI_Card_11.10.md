---
title: "Slow WIFI with Atheros WIFI Card 11.10"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by wickedpenguinbox on 2012-01-31
Hi All,

I think ubunutu is great and I really want to use it as my main OS, but there one issue standing in my way.

I have intermittently slow WIFI in ubunut. Using speed test.net I get an average speed of 1.8 - 2.0 Mb, but in windows I am getting 16-18Mb.

I am using the ath9k driver and my device is AR5008. 

I have tried the folling, but it has no effect.

> sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

I have also created a ath9k.conf file under modprobe.d and adding the line

> options ath9k nohwcrypt=1
But still no luck.

I also reinstalled the OS, but no luck thier either and I installed Mint linux just to confirm it wasn't os related and once again the same issue.

Does anyone have any suggestions as I am stumped?

Thanks in advance.

---

### Post by wickedpenguinbox on 2012-02-02
100 views and no suggestions ? Anyone?

---

### Post by manvvip on 2012-03-13
I have the same problem, some people are recommending setting BSSID, let me know if that works...

---

### Post by TBABill on 2012-03-13
Mine is an AR9287 and I encounter the same results, but sporadically. Sometimes I can get to 12Mbps, but often I find myself from 200Kbps to 2Mbps. It got so frustrating, even after adding the nohwcrypt setting, that I decided to give 12.04 beta 2 a shot. World of difference. The desktop itself is much more responsive and my wireless is consistently running at 10-12Mbps and I have 12Mbps service. 
 
Not suggesting install a beta, but if you hit the end of all your options, 12.04 releases next month.

---

### Post by Bucky Ball on 2012-03-13
My suggestion is try MadWifi instead of Network Manager. Intended for Atheros cards:

[http://madwifi-project.org/](http://madwifi-project.org/)

As for resorting to 12.04 LTS, yea, might fix wifi on some machines, depending on machine and configuration, but expect breakages and other issues  (even for some time after release) which may include breakages of wifi. ;)

---

### Post by TBABill on 2012-03-13
Very true Bucky Ball. The new Unity was broken and apparently has been fixed as of today so going beta is a risk unto itself. My 11.10 install was new so I had nothing to lose trying the beta, but for those who have heavy configurations or need a stable production machine, trying a beta is risky.

---

### Post by kirusoft on 2012-03-14
If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

It’s work? Then how to make it permanent? 
**gksudo gedit /etc/modprobe.d/iwlagn.conf**
Add this to the file :
```
options iwlagn 11n_disable=1
```
Save & Close Gedit
Then :
**gksudo gedit /etc/pm/power.d/wireless**
Add this to the file :
```
#!/bin/sh
iwconfig wlan0 power off
```
Save and quit gedit
You need to make the script executable :
**sudo chmod +x /etc/pm/power.d/wireless**

Hope it’s help. It’s helped me a lot my Wifi working fine now. :)

---

### Post by Bucky Ball on 2012-03-14
> **kirusoft said:**
> If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.



Not sure if your instructions will be much help, kirusoft, as you have an Intel card and the OP has an Atheros; totally different kettle of fish. They could possibly create further problems. As the iwlagn driver is *specifically* for Intel cards, though, it might be worth a try disabling it (though I can't see how it could be interfering in the OP's problem), but your fix usually solves problems involving wireless N. 

Still wondering, for the OP, have you tried MadWifi instead of Network Manager yet, as I suggested??? This is designed specifically for Atheros cards ...

---

### Post by zinadork on 2012-03-15
After going down this rabbit hole with two of my laptops, I found that disabling wireless N on my router solved the problem.  Sure N offer many advantages, but not until it is properly supported on our hardware.

---

