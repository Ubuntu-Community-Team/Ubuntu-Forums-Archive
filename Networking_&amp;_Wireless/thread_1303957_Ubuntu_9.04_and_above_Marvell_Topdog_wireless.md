---
title: "Ubuntu 9.04 and above Marvell Topdog wireless"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by gumshore on 2009-10-28
I have been using Ubuntu 8.10 exclusively because I cannot get my Marvell Topdog wireless driver working in any version above it. I use the drivers that I posted on my skydrive [(link here)]("http://cid-744502a1afe484a4.skydrive.live.com/self.aspx/.Public/NetMW14x.zip")

```
sudo apt-get install ndiswrapper*
```this works just fine.
next i extract the drivers to a subfolder in my home directory and browse in the terminal to them
```
cd DO_NOT_DELETE
cd internet 
```still no problems
next i install the drivers
```
sudo ndiswrapper -i NetMW14x.inf

```then I force the card to work with the drivers
```
sudo ndiswrapper -a 11ab:2a08 netmw14x
this is safe ONLY if driver netmw14x is made for hardware 11ab:2a08
```one again, normal
now, the fun begins when I add aliases for ndiswrapper
this is what happens on karmic RC
```
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi
```next i do the following
```
sudo depmod -a
sudo modprobe ndiswrapper
All config files need .conf: /etc/modprobe.d/ndiswrapper
this will be ignored in a future release
```Then i left-click on the network manager icon in the status area and select my wireless network.  It then prompts me for the WEP password, which I enter correctly. Sometimes it pops up again and asks me for the password. I enter it again, then it gets stuck on the "configuring wireless network" stage and the status indicator spins for infinity. also while it is doing this, if i left-click on the indicatior, it freezes the entire desktop.
PLEASE HELp ASAP!!!!

---

### Post by chili555 on 2009-10-29
> It then prompts me for the WEP password, which I enter correctly.Do you have a HEX key, consisting of 10 or 26 characters? I think Network Manager expects it in 'WEP 40/128 bit HEX' instead of 'WEP password.'

---

### Post by gumshore on 2009-10-29
i checked it. is is indeed a 26 character hex that I am entering, but it does not work. I have tried entering the code using the passphrase and 40/128 bit hex settings, but they dont work. When I get home, I will try it the the final version of karmic to see if the problem is fixed

---

### Post by gumshore on 2009-10-29
I just tried out the final version of Karmic, and i still get the exact same issues.

---

### Post by gumshore on 2009-10-30
i have found that I have the same issue as described [in this thread]("http://ubuntuforums.org/showthread.php?t=1036068")

---

### Post by Bobbake4 on 2009-11-11
I have the same card and the same problem.  I had this problem on Jaunty a couple months back and after working on it for a while I finally came to the realization that it just does not work right with WEP.  I changed my router back to WPA and all was fine.  If you don't have that option maybe a new card that is native on linux will be a good investment.

Bobbake

---

### Post by gumshore on 2009-11-14
> **Bobbake4 said:**
> I have the same card and the same problem.  I had this problem on Jaunty a couple months back and after working on it for a while I finally came to the realization that it just does not work right with WEP.  I changed my router back to WPA and all was fine.  If you don't have that option maybe a new card that is native on linux will be a good investment.

Bobbake

Thanks. I will try that now.

EDIT: OMG, THANK YOU! I can't believe that somthing as little as that made all of the difference! I am so happy right now! THANKS!!!!!!! :)

---

