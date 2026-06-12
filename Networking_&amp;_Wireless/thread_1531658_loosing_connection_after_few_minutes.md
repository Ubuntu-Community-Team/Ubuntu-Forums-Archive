---
title: "loosing connection after few minutes"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by orduek on 2010-07-15
Hi,
I have an LG R-450 laptop with Ubuntu 10.04 installed in it.
When I connect him to a network (either LAN or Wireless) it stays connected for a few minutes and then Just disconnects (without showing any sign of disconnection except no internet/skype/dropbox).
Only way to renew connection is after startup.
The network controller is SIS 191 Gigabit Ethernet adapter.

---

### Post by orduek on 2010-07-18
Another thing I found out - when I'm disabling network the computer freeze with no option to restart - only manually shut it down.

---

### Post by orduek on 2010-07-19
any help?
its really frustrating.
I keep losing connection and can't solve it.
I tried installing ndiswrapper drivers - that caused the eth0 to be lost and the computer to freeze from time to time.
tried setting MTU to 1492 - didn't help.
Maybe upgrading to maverick?

---

### Post by orduek on 2010-07-20
OK,
It seems that my wireless built in card is causing all the problem.
I have realtek semiconductor rtl8192se but when its enabled (from BIOS) the computer is crashing and freezing on startup. So I had to disable it from BIOS.
Does anyone knows if I can solve this one? or should I buy usb wireless?

---

### Post by markcoronado on 2010-07-20
You are not the only one with this problem.
I have an Acer Aspire 7535-5020 & it does the same thing.
When I boot it automatically connects, & after a few minutes it disconnects & I can't reconnect until I reboot.
My system is partitioned with Windows 7 on the other partition where I have no problems staying connected.
Needless to say I don't use Ubuntu very often.
I would like to solve the problem.
Hopefully someone has the answer.

---

### Post by orduek on 2010-07-22
> **markcoronado said:**
> You are not the only one with this problem.
I have an Acer Aspire 7535-5020 & it does the same thing.
When I boot it automatically connects, & after a few minutes it disconnects & I can't reconnect until I reboot.
My system is partitioned with Windows 7 on the other partition where I have no problems staying connected.
Needless to say I don't use Ubuntu very often.
I would like to solve the problem.
Hopefully someone has the answer.

Do you also experiencing system freeze?
I just can't work with the wireless enabled otherwise my system freezes every restart.

---

### Post by dineshs on 2010-07-22
I have heard of wicd.If network manager is not working fine you can try that
You can install it via synaptic.Please read this(I dont know much about that)
[http://en.wikipedia.org/wiki/Wicd](http://en.wikipedia.org/wiki/Wicd)

---

### Post by orduek on 2010-07-22
thank you for the advice but WICD has same effect : whenever he tries to connect he firstly closes all network adaptors and then restarts them - in my computer it causes freeze (I have to physically shut down the laptop).

---

### Post by dineshs on 2010-07-22
wrt this link
[https://bugs.launchpad.net/wicd/+bug/608117](https://bugs.launchpad.net/wicd/+bug/608117)
you can try wicd 1.6
If nothing works
[http://ubuntuforums.org/showthread.php?t=1495908](http://ubuntuforums.org/showthread.php?t=1495908)

---

### Post by markcoronado on 2010-07-22
> **orduek said:**
> Do you also experiencing system freeze?
I just can't work with the wireless enabled otherwise my system freezes every restart.


No freezing, I just lose the internet connection after a few minutes & the only way to get it back is to reboot.

Very frustrating, I wish I knew how to fix it.

---

### Post by orduek on 2010-07-23
> **markcoronado said:**
> No freezing, I just lose the internet connection after a few minutes & the only way to get it back is to reboot.

Very frustrating, I wish I knew how to fix it.

It is frustrating. 
The most frustrating part for me is that I can't enable the wireless otherwise my hole system just freezes and %$^% up.
I use Ubuntu 10.04. 
Does anyone else who uses 10.04 with experience freeze?

---

### Post by chuckydee9 on 2010-07-26
I have the same problem, I keep losing my internet connection after about 5 minuts of browsing. I once just turned on the computer and did nothing and saw that it was connected via wifi for about 6 hours.... other times it losses connection in less than 5 minutes...My computer does not freeze though...... I just have to reboot to get the connection.... I wish there was a solution for this. Are you guys using the 64 bit version or 32 bit version?

---

### Post by markcoronado on 2010-07-27
> **chuckydee9 said:**
> I have the same problem, I keep losing my internet connection after about 5 minuts of browsing. I once just turned on the computer and did nothing and saw that it was connected via wifi for about 6 hours.... other times it losses connection in less than 5 minutes...My computer does not freeze though...... I just have to reboot to get the connection.... I wish there was a solution for this. Are you guys using the 64 bit version or 32 bit version?


I'm using the 64bit version.

---

### Post by chuckydee9 on 2010-07-28
I am usung the 64 bit as well... has anyone using the 32bit encountered this porblem?

---

### Post by orduek on 2010-07-29
I'm using 32bit.

---

