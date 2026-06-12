---
title: "Network Adaptor Drivers Problem?"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by rubenba on 2011-06-27
Hi, 
I am totally new to Ubuntu. I love it, it looks rational, firm and sleek though I am about to uninstall it. It's been like 7 hours to connect it to internet, dozens of threads read and no result so far. 

My problem: I have an old laptop (Amilo Pa 1510) and I want to have a dual-boot Ubuntu10.04 - Windows XP to start off using Ubuntu. In XP I have wireless internet connection, in Ubuntu 10.04 I can´t connect, no network signal, nothing at all. There must be a problem with the drivers but I don´t really understand what's wrong. I have the drivers cd but I don´t even now which driver is exactly the right one. I installed several and in Windows it worked out. I think that my network card is Broadcom 802.11g but I am not sure either.

I've been trying to follow this thread [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) but I don´t really understand it. What's b43?What's atheros??? I get stuck at the first steps. I tried to look for ndiswrapper in the Syneptic Package but there's nothing there. Is is because I installed the Ubuntu with a bootable USB instead a CD? Should it make any difference?
 
Please, could anyone tell me the commands I need to run to get Ubuntu with internet. Afterwards I will be able to learn on my own but right now I have to restart the computer everytime I try something and after 7 hours unsuccesfully trying things I am on the edge to give up...

Thank you for your time

Ruben

---

### Post by chili555 on 2011-06-27
There are some commands you can issue in a terminal that will help us identify your wireless card. Once we know that, we can find out how to activate it rather quickly. Please open a terminal and run and post:```
lspci -nn
```Strip away all the items that are not your wireless card. If you have a Broadcom, it will show up pretty clearly. Older Broacom cards will work pretty easily but they require proprietary firmware that's not included by default.

Are you able to get a wired ethernet connection temporarily? If so, you can select System > Administration > Additional Drivers and be offered to install the firmware automagically.

Ndiswrapper is a method to wrap the Windows XP driver and use it in Linux. In my opinion, it's a poor substitute for using the native driver and firmware.

---

### Post by rubenba on 2011-06-28
Hi Chilli555!

I connected with the wire and follow your indications: System/Administration/Hardware Drivers. Then Ubuntu guided me (it looked for existing drivers) and it found two relevant ones: 
1) Broadcom B43 wireless driver
2) Software Modem 

I installed them, restarted the computer and here I am with my wireless connection! The Ndiswrapper and all this is more a source of confusion than solutions...  (It's a pity that it may discourage new users like me :( )

Thank you very much for your help! :D

Ruben

---

### Post by chili555 on 2011-06-28
Awesome, Ruben! I'm glad it's working.

Getting over the wireless driver hurdle is a big step; if new users get over it, they're pretty much set for life because they have access to the internet to search for solutions to all other problems and a sense of confidence.

What makes my job a bit harder is that chipset manufacturers are coming out with new products with new features it seems like daily. Then users are on the forum the next day (!!) demanding connectivity with draft-Z speeds, WPA3, antenna diversity and IPv6 and complaining the Ubuntu developers are all lazy slobs if not. Of course, we depend on the chipset manufacturers to provide Linux drivers; at best a 1% marketplace. The big four, Broadcom, Ralink, Realtek and Intel are actually good Linux supporters. 

It's all fun!

---

### Post by rubenba on 2011-06-28
Hi Chilli555!

You are totally right, once you have internet, it's not such a pain to look for guidance in other forums... but restarting the computer for every single try is a curse. 
I do support Ubuntu for practical but also ethical reasons. I would like Ubuntu to be the market leader and I do believe it is possible because the product is certainly good. It's also why these little hurdles for beginners get me angry...we are discouraging millions of potential users. 
Fortunately we have Ubuntu Forums!

---

