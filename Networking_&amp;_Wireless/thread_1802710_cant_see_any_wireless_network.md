---
title: "cant see any wireless network"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by johnjoshy on 2011-07-12
i was using windows xp..now i partitioned my hp mini and started using ubandu...yeah i have to say its much faster and looks clean...but i am not able to use wifi..when i tried searching networks,,i am not able to find any.but at the same time i am able to use wifi from the same net book via windows xp,,please help

---

### Post by TBABill on 2011-07-12
Working in Win XP doesn't in any way impact working or not working in Ubuntu. Both systems require the correct driver to be installed properly and the drivers and configurations are not shared between the two OS's. Some hardware is supported out of the box with Ubuntu but other hardware requires proprietary drivers and firmware.
 
Can you open a terminal and type in ```
lspci
``` (LSPCI in lowercase letters) and copy/paste here the output you receive? We can look at that and help you get started correcting the problem.
 
If you want to take a shortcut before doing so, if you have ethernet access you can plug your machine into a router and go to Additional Hardware to see if the system detects the card and offers to install a driver. 
 
Please also post what version of Ubuntu you are using.

---

