---
title: "Connection failed: unable to get IP address"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Ninjabba on 2010-04-24
This is my first post on this forum as I really cannot solve this for some reason. I read through a lot of other topics and tried several things to fix my problem but nothing seems to work. 

So I got Ubuntu 9.10 on my laptop working really neat and wanted to upgrade my desktop to 9.10 as well. So I reinstalled Ubuntu there and now I can't connect to my network anymore....

I have a usb wireless adapter (currently Sitecom as I bought a new one today to hopefully fix it, but ended up at exactly the same problem as with my old adapter). The network manager I'm using now is Wicd since some topics I was looking through were about malfunctioning GNOME network-manager (which I removed) and suggested to try this. The GNOME network-manager kept prompting to insert my WEP network key which was a correct one. When I removed all security from the network it didn't prompt anything anymore but just failed to connect. The Wicd network manager is so nice to tell me that it cannot obtain the IP address however, so I suspect that this is my main issue... but I have no idea what I can do about this? Tried using a static IP and then I get the message "Connection failed: Could not contact the wireless access point."

I feel powerless as my knowledge here is just lacking.. so I hope someone can point me into some directions. Thanks in advance.

---

### Post by Ninjabba on 2010-04-25
It seems like I fixed my issue here, although it still doesn't make sense to me. I tried using WPA2 encryption instead of the outdated WEP (I did this because it was needed anyway). For some reason it works now on my desktop as well. The only strange thing is however, that I couldn't connect using NO encryption before. Weird as this sounds to me, I'm happy it works.

---

### Post by Roger Parent on 2010-11-11
Sorry to bring this thread back, but I am having the same problem since going from 9.10 to 10.04.  I submitted this problem on a separate thread a day or two ago but have gotten no answers yet.

1.  I installed wicd and removed network manager per recommendation of other ubuntu user.

2.  I now get the message that wicd is unable to obtain IP address.  If I add a static IP address I get a message that wicd is unable to contact access point.

I have been through several steps to verify that my card is working, and it seems to be.  I have no problem finding and identifying wireless networks, just communicating with them.

---

### Post by LouisaLou on 2010-11-21
Hi,

I have been having the same problem. Wicd sees the wireless connections but -- even on an unsecured network -- gives me the message "connection failed: unable to get IP address". With network manager I don't even see the wireless networks. I am using an HP Mini 5102 (Broadcom drivers), and would appreciate any and all help!

Thanks so much,
Louisa

---

### Post by Walmit on 2010-11-21
I had a similar problem with a Linksys WUSB600N USB adapter. 
The adapter was working (LED blinking) and it could scan all WiFi networks in the neighborhood. All seems in OK, except that I could not connect to any network with Wicd with DHCP or static IP (in the case of DHCP, Wicd gave the similar response "connection failed: unable to get IP address"). The problem was finally solved by blacklisting several generic drivers loaded by Ubuntu:
```
blacklist rt2860sta
blacklist rt2870sta
blacklist rt3090sta

blacklist rt2x00usb
blacklist rt2500usb
blacklist rt2800usb
blacklist rt73usb
```(see [http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/) for the full procedure that solved my problem).

May be this could be related to your problem.

Good luck.

---

### Post by coffeecat on 2011-11-13
Closed to prevent further necromancy.

**EDIT**: necromancing post move to its own thread.

---

