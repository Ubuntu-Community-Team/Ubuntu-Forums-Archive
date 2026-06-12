---
title: "Can't set up wireless"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by usafmom04 on 2010-11-17
I am new to Ubuntu and I can not for the life of me figure out how to set up a wireless account. I can get online with the ethernet connection, but I want to be able to get on wireless. I have a built in wireless card. I have figured out how to get my webcam and microphone working. And I am loving this OS but if I can not get wireless I will have to resort back to windows 7, which I am dreading. Please help. Is there a video out there?

---

### Post by TBABill on 2010-11-17
Ok, upper right on the top panel there is an icon for the network manager. If you right click it you can make sure wireless is enabled. Then if you left click it there should be a choice to connect to your wireless network, whatever you named it. If you do not see your (or any) wireless networks to choose, then it is likely you need a proprietary driver installed, which is not a major ordeal normally.
 
If you cannot see any networks and you are sure your network is on (router is on and transmitting), type the following into a terminal and post the output back here for more assistance:
```
lspci
``` Then we will know which wireless adapter you are trying to enable.

---

### Post by usafmom04 on 2010-11-17
it has been enabled but it is not picking up on it 
i typed that in the terminal and it gave me this Ralink rt3090 wireless 802.11n 1t/1r pcie

---

### Post by TBABill on 2010-11-17
Are you on Maverick or are you on Lucid? (10.10 or 10.04)

---

### Post by TBABill on 2010-11-17
I have not tried this but another user has recommended this link to a .deb file, which will run like a .exe file would in Windows. It should install the appropriate driver once you save the file then double click it. [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

---

### Post by usafmom04 on 2010-11-17
i am using the newest version of Ubuntu i guess 10.10
 i will try your second post but i am having an issue setting up a wireless account i do not know what to put in the boxes ex  ssid  mode infrastructure or ad-hoc   bbsid    i have a wep key but do not know if i need to choose wep 40/128 bit key or wep 128 bit key or dynamic wep (802.1x) and the list goes on

---

### Post by TBABill on 2010-11-17
you don't need to fill all that in. if your router already works for windows xp then all you need to do is get the system to recognize your router, then tell it to connect. it should detect what level of encryption it is using and prompt you only for the key (hexidecimal pass code) that is generated through the router configuration page (URL to see it is 192.168.1.1 from a computer already connected to the network)

---

### Post by usafmom04 on 2010-11-17
got it thanks

---

