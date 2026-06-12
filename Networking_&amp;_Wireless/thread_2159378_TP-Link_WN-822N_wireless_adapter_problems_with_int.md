---
title: "TP-Link WN-822N wireless adapter problems with internet speed? D:"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by alex27894 on 2013-07-02
Hello there people, my problem here is that I am new at ubuntu and I don't know much about how to do much stuff here, i have just learnt just about a couple of basic commands and some (just some) advanced commands and those kind of stuff but my problem right now is about my network, it should be about 10 Mb/s, so basically 1 MB/s but i haven been able to get to even close to that speed, all i reached was about max 0.80 Kb/s =_=, so i concluded if it could be a firmware problem or something like that, but i don't know how to install it :/ so if you guys could help me please

I will send the info about my wireless adapter

alex27894@alex27894-desktop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 125f:a11a A-DATA Technology Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 12cf:ff7f  
Bus 001 Device 005: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 802.11n [Atheros AR9170]
Bus 002 Device 003: ID 04a9:1742 Canon, Inc.

biggest problem here is that it says that it's the TP-Link TL-WN821N v2, tough what i see and i know i have is the TP-Link TL-WN822N v1 :/ tough i think it wouldn't be much of a bother right? since both of theirs firmware are AR9170 i guess... :/

---

### Post by varunendra on 2013-07-03
First of all, Welcome to the forums alex !
> **alex27894 said:**
> 
Bus 001 Device 005: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 802.11n [Atheros AR9170]
Your device is handled by the native carl9170 driver. We can try a parameter available for it to see if it can improve speeds. Please do -
```
sudo modprobe -rfv carl9170
sudo modprobe -v carl9170 nohwcrypt=Y
```
This will be a temporary change that will be lost at reboot. If it helps, we can make it permanent.

However, if it doesn't make any improvement, please follow the "Wireless Script" link in my signature and follow the instructions in the linked post to post back a detailed diagnostics report.

**PS:**
What makes you think that the speed should be 10Mb/s ? And how did you determine the actual speed?

---

