---
title: "Slow wireless when on batery power."
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by ayenack on 2011-08-20
Hello all.

I am running Ubuntu 11.04 32Bit on an ASUS Eee PC 1015PX.

I have found a strange anomaly concerning wireless connection when running on battery power.

I have been experiencing very slow performance when connecting to my home NAS and also the internet through a wireless connection when using my netbooks internal wireless card (Broadcom Corporation BCM4313 802.11b/g/n (rev 01)) when running on battery power. The card works fine and connects at full speed when running on mains power but as soon as I switch to battery power the card connects to the internet/network fine but the connection speed is very slow indeed.

I am using the Broadcom 802.11 Linux STA propriety wireless driver.

Have not got a clue what's causing this other than maybe a bug in power management so any advice would be appreciated.

Thanks. ayenack.

---

### Post by ayenack on 2011-08-21
OK this is what I thought it might be it's something to do with power saving.

This is what worked for me by putting an empty file called wireless in /etc/pm/power.d everything is working as should be as far as I can tell.

This is what I did. In Terminal:-

Change directory to /etc/pm/power.d:-
**cd /etc/pm/power.d**

Then:-
**sudo su**

Then:-
**nano** (when in nano press Ctrl key and o at the same time to save the file and name it wireless then press Ctrl key and x at the same time to exit.)

Reeboot, That did it for me. It's a bit ugly but it worked.

---

### Post by praseodym on 2011-08-21
Check

```
iwconfig
```

if the power management is "on". You can turn it off with

```
sudo iwconfig wlan0 power off
```
Can you post

```
cat /usr/lib/pm-utils/power.d/wireless
```
The needed changes in that file are shown here:

[http://forum.ubuntuusers.de/post/2651205/](http://forum.ubuntuusers.de/post/2651205/)

Change iwl3945 to wl

---

### Post by ayenack on 2011-08-22
Seems like I've been beaten to the punch.

@praseodym

Just edited this file myself set all the settings the same as ac power supply. I'm not on battery power at the moment so have not tested it out. Will report back with results when battery has a full charge. I can't see why it will not work perfectly.

ayenack.

Have now tested and can say that this is working perfectly for me.

---

### Post by Swashy on 2011-09-08
Hey so I seem to have the same problem on my asus 1215t eee pc and I have the BCM4313 *[14e4:4727]* wifi card as well. Unfortunately it seems that turning off power management isn't supported (it says "operation not supported" when I do *sudo iwconfig wlan0 power off*) but I'm not running the wl drivers, but instead the brcm80211 drivers. I've had endless trouble with wl drivers so I'd preferred to stick with these ones (i forget which one is the proprietary driver?)

Anyway I digress, I'm getting a terrible or random bit rate and I think it *may* not be power management? :???: 

Is this the right place to post this?

edit: just confirmed it.. iwconfig says that power management is off for my interface wlan0, and the bit-rate varies both on and off battery.

*ugh*

---

