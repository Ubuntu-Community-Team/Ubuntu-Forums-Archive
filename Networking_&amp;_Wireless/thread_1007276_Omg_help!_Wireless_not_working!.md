---
title: "Omg help! Wireless not working!"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by sailorpinkfury on 2008-12-10
Hi, I just installed Ubuntu 8.10 linux on my Compaq presarrio c500.

I AM AN ABSOLUTE BEGINNER!

Now I have a broadcom wireless network card, BCM4311 14e4:4311 and I followed these instructions: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver) 

on how to install the drivers, and it worked.  But I opened my computer this morning and now they stopped working!

I can't figure this out!  I tried reinstalling the drivers over and over and over and nothing works!

HELP I'M NEW AND I CAN'T FIGURE THIS OUT BUT I NEED THIS TO WORK.  AHHHAAAA!!
:mad:

---

### Post by nickdbliss on 2008-12-10
> **sailorpinkfury said:**
> Hi, I just installed Ubuntu 8.10 linux on my Compaq presarrio c500.

I AM AN ABSOLUTE BEGINNER!

Now I have a broadcom wireless network card, BCM4311 14e4:4311 and I followed these instructions: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver) 

on how to install the drivers, and it worked.  But I opened my computer this morning and now they stopped working!

I can't figure this out!  I tried reinstalling the drivers over and over and over and nothing works!

HELP I'M NEW AND I CAN'T FIGURE THIS OUT BUT I NEED THIS TO WORK.  AHHHAAAA!!
:mad:

The drivers provided in the restricted hardware (ssb)works for this card. i have tested that myself. Go to system>administration>Restriced Hardware Drivers. Enable that driver there.

I used that method u followed in 8.04 but not in 8.10 since that worked for me. hope u have some luck.thx

---

### Post by Ayuthia on 2008-12-10
In 8.10, there are three different options for you to use for wireless.  Most likely you have an extra wireless driver running that is causing a conflict.  From the guide, it looks like you are trying to use ndiswrapper.  Please try the following to see if it works (it will only work in this session):
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ndiswraper
```
If it does, please post the results of the following:
```
lshw -C network
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper -e wl
cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper -e wl
```
The first command is to check and see what your wired card is.  There is a Broadcom ethernet card that will cause conflicts with ndiswrapper so it needs to be loaded after ndiswrapper.  The second and third commands are checking to see what modules have been blocked out and what have been requested to load.  From there, we can provide the updates needed to make it work.

---

