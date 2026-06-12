---
title: "RT2860sta drivers not working"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by surajrajpurohit on 2011-07-31
hello
      I'm using ubuntu with kernel 2.6.38 which is not supporting my RALINK wifi card. i have installed rt2860sta drivers from ralink website and blacklisted all others remaning drivers. but still Wicd is not detecting any wifi drivers and ifconfig and iwconfig are also not showing any wireless extension.

lsmod | grep rt2860sta showing
rt2860sta 816407 o
its showing program using this drivers 0;

i have also tried by loading another kernel 2.6.35 which is having rt2860 drivers inbuilt...but the said part of story is GRUB is not loading new kernel.

im trying to install this drivers from last 2 months...i would b very thankful if anybody here help me...

---

### Post by surajrajpurohit on 2011-07-31
plz........help

---

### Post by chili555 on 2011-07-31
Let's see what wireless card you have. Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by surajrajpurohit on 2011-07-31
> **chili555 said:**
> Let's see what wireless card you have. Please run and post:```
lspci -nn | grep 0280
```Thanks.
for lspci -nn | grep 0280 i got
01:06.0 Network controller {0280} ralink devic [1814: 3060]

---

### Post by chili555 on 2011-07-31
rt2860sta is not correct for your device; you need rt3562sta. Here is a pretty good tutorial: [http://ubuntuforums.org/showthread.php?t=1608095&highlight=rt3562sta](http://ubuntuforums.org/showthread.php?t=1608095&highlight=rt3562sta)

Post back if you get stuck or need further assistance.

---

### Post by surajrajpurohit on 2011-08-01
thanks chilli555,
the drivers rt3562sta got loaded n working.
iwlist is showing the network available....
i got new interfrence ra0;
iwconfig is showing
ra0   RAlink STA ESSID: "" nickname; "RT3562sta"
mode:auto
& son on
**BUT**

My wicd network manager is not, its not showing any APs
i tried connecting using 
iwconfig ra0 essid "suraj" key "hs6837" 
but the output is Error for wireless request "set Encode" (8B2A)
invalid arument......

---

### Post by chili555 on 2011-08-01
> iwconfig ra0 essid "suraj" key "hs6837" Is it incorrect because WEP keys can be 5, 10, 13 or 26 characters and yours appears to be 6?

Does it scan?```
sudo iwlist ra0 scan
```Did you make the changes to config.mk to be managed by Network Manager when you are actually using Wicd and *not* NM?

---

### Post by surajrajpurohit on 2011-08-01
my wireless router has WPA2psk protection.
i have made the changes in config.mk i have change WPA_supplicants=y and nxt line also =y..
dat's it..
and yes iwlist scan is working fine..im getting available networks...
and also i have blacklisted remaining drivers...rt2800pci,rt2899lib etc...

---

### Post by chili555 on 2011-08-01
> **surajrajpurohit said:**
> my wireless router has WPA2psk protection.
i have made the changes in config.mk i have change WPA_supplicants=y and nxt line also =y..
dat's it..
and yes iwlist scan is working fine..im getting available networks...
and also i have blacklisted remaining drivers...rt2800pci,rt2899lib etc...It sounds to me like it's working fine! Does Network Manager see those same networks? Can you click the icon and connect?

---

### Post by surajrajpurohit on 2011-08-01
im using KDE so der is no network manager...ii hve wicd manager instwdd of network manager... the problem is my wicd is not showing any networks.....to get connect..?

---

### Post by chili555 on 2011-08-01
When you click the Wicd icon, do you see the tab for Preferences? Is it set to use ra0 instead of wlan0?

---

### Post by surajrajpurohit on 2011-08-01
Hurry!!
Its working....thank q very much......i'm very thankful to you for ur cooperation and patience....
i've renamed wlan0 to ra0 in wicd and its working.....
it's like my dream come true........and its dediceted to u...chilli555....thank q once again.....

---

### Post by chili555 on 2011-08-01
Great job. You were very patient and understanding, too. Glad it's working. Would you please use thread tools at the top and Mark Solved?

---

### Post by surajrajpurohit on 2011-08-01
thnaks once again 4 advicing.....i hve marked..as solved

---

