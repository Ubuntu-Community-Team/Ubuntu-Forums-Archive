---
title: "Kubuntu Wireless"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by Tekuzo on 2009-11-07
I just installed Kubuntu 9.10 on a laptop that I plan to give to my girlfriend. Using the Ubuntu Proprietary driver installer I managed to get the wireless driver installed, and its even working, when I bring up KNetworkManager it is able to see all of the SSID's that are in my area, but it is not able to connect to my own SSID

My Router is running with WPA1 Personal security with a pre-shared key and for some reason when I try to connect to this network it doesn't let me. When I select the Network it brings up a menu that says "Secrets for [ssid]", I put in the proper key to connect to the ssid and hit the ok button, and the same screen just displays for another 3 button presses. It will just not connect to the network.

Does anybody know what I am doing wrong? I had even installed Ubuntu 9.10 earlier and the wireless worked just fine, for some reason KDE can see the SSID's just not connect to the network.

---

### Post by pytheas22 on 2009-11-08
If it worked alright in Ubuntu, it's probably a bug in KNetworkManager that causes it to not like your network for some reason.  You'd likely have better luck if you used a different program to connect, such as [wicd]("http://wicd.sourceforge.net"), which you can install using the package manager.

---

### Post by Tekuzo on 2009-11-08
Thanks for the tip, I will give it a try and let you know how it goes.

/edit

Of course, I installed java before I went to bed and gave up on getting the wireless to work for the night, and when I wake up in the morning to give it another shot, its working just fine. Thanks for the tip, but I may not need it now

---

