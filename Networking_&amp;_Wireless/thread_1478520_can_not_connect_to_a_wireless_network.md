---
title: "can not connect to a wireless network"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by custom02 on 2010-05-09
I'm totally new to the Linux Ubuntu world and I install the Ubuntu 10.04 OS on to a new Mac computer. Everything seems to work fine except for my networking icon/system. 
When i open the network connection i can not connect to a wireless network. it doesn't show any wireless networks in the area. it will only work if i connect with a LAN cable to go online.

Any advice would be greatly appreciated!!!!!

---

### Post by andsmi on 2010-05-09
Got exactly the same problem. My  iwconfig output are as following:
[B]
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on[/B]
```

---

### Post by custom02 on 2010-05-09
this is what it says when i run iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by andsmi on 2010-05-09
> **custom02 said:**
> this is what it says when i run iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Nothing about wlan0?

Trying with windows drivers through the ndisgtk package, but no luck.
In my case, it seems like as if the roaming mode has been disabled.

Whats your outpost running; sudo lshw -C network in the terminal?

---

### Post by khianhui on 2010-05-09
Hi,

Did you check what is the chipset of your wifi card?
From your output it seems like it doesn't detect(recognize) by ubuntu.
Try to search more info for compat wireless. You might get answer there.:guitar:

---

### Post by 666j.e.t on 2010-05-12
hi iv had a more or less same problem i was useing ubuntu 8.4 my wireless card worked but now there is nothing i have to use a cable just to use the net and i really need to use wire less cuz the cable keeps tripping me up cuz its going half way across my house

---

### Post by Krovas on 2010-05-12
Widespread connection problems in Lucid are evidently kernel based, so I've read.

---

