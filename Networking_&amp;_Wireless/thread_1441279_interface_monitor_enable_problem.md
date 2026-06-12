---
title: "interface monitor enable problem"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by thantserpelis on 2010-03-28
hello guys
well here is my problem
i want to use a program and i have to monitor enable ath0
to work so it told me that wlanconfig doesnt exist so it cant 
enable it and it told me to install madwifi-tools
then the process worked but ath0 wasnt enabled it just dissappeared and showed only wifi0
and nothing else any help please??????
i think it must be an error of madwifi
i got an atheros card and i can connect on internet so it is supported


please help:(

---

### Post by chili555 on 2010-03-28
Can you use the program if you enable monitoring on the wireless interface you actually have, if it is not *ath0*? Maybe your wireless interface is *wlan0*. Open a terminal and do:```
iwconfig
```If your interface is *wlan0*, can you simply do:```
sudo iwconfig wlan0 mode monitor
```

---

### Post by adam814 on 2010-03-28
If the OP is using madwifi ath0 is normal (it won't show up as wlan0).  Also wifi0 will be the interface the VAPs are created from.

Maybe this will help:
[http://madwifi-project.org/users-guide/node14.html](http://madwifi-project.org/users-guide/node14.html)

It looks like the command you need to start a new VAP in monitor mode would be:
```
sudo wlanconfig ath create wlandev wifi0 wlanmode monitor
```The new interface will probably be ath1.  Of course it'll be stuck on the same channel as any other VAPs you have, so you can't monitor on a different channel than your main interface is connected to.  Of course you could always put that interface down while you're monitoring.

Hope it helps.

---

### Post by thantserpelis on 2010-03-29
adam i did what u told me and it didnt help me at all
can u give me ur msn so u can help me  better????
and when i click on iwconfig it shows me the interfaces and ath0 is the only one who says about the wireless
also i got wifi0
that is all

---

### Post by adam814 on 2010-03-29
I'm afraid that's about as much as I know about the subject.  I used to have a laptop with an Atheros wifi chipset a couple years back and that worked to get a new interface in monitor mode.  Although I believe I had to patch the drivers and compile them myself to get injection in monitor mode to work, so it'll depend on what you need.

Maybe if you post back the error you're getting someone will be able to help.

---

