---
title: "Ubuntu Networking problems"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by joshlalonde on 2010-04-13
I have not been able to successfully connect to the internet after happily installing my new copy of ubuntu on my existing windows 7 OS. I installed from a burned cd from the .iso file from the website. I have a DELL INSPIRON 1545. My ethernets ip address is 192.168.1.1 I am new to ubuntu but not new to MSDOS commands which seem similiar to the Ubuntu Terminal commands. 

I use these devices/drivers for networking:
Dell Wireless 1397 WLAN Mini-Card
Marvell Yukon 88E8040 PCI-E Fast Ethernet Controller
Microsoft Virtual Wifi Miniport Adapter

Any suggestions? Please Help me!

---

### Post by Iowan on 2010-04-13
Having a background in CLI (command line interface) is always a good thing.:) Is your machine configured for DHCP address? I know you mentioned 192.168.1.1 (which sounds more like a router's address), but I'm curious if you assigned that directly. How do you connect to internet (dialup, router, dsl/cable modem)? More directly - can you ping the device that connects to the internet? Feel free to ask for clarification if any of my crystal clear questions... aren't. :shock:

---

### Post by joshlalonde on 2010-04-14
thanks for your quick reply! i have no clue what that means :P im totally ignorant to networking.. i connect to internet wirelessly through a router i believe then to an ethernet then to my isp. i use a lnksys or whatever its called... and i have cox as my isp which is all through my phone/internet cable (dsl???) 

anyways i have no clue what im doing so basic walkthrough could be usefull... nothing fancy or time-consuming... just do this.. tell me this.. that kinda thing if you could?

---

### Post by Iowan on 2010-04-14
Wireless isn't my forte... fortunately, it works on my laptop. 
From a terminal (Applications>Accessories>Terminal), check ```
ifconfig -a
``` See if you get an IP address (and which interface). *Ordinarily*, **eth0** is the wired interface, and wireless is **wlan0** (although my laptop uses **eth1** for wireless). If nothing shows up, ```
sudo lshw -C network
``` (also from terminal) should show more details about interfaces.

---

### Post by joshlalonde on 2010-04-15
i tried something similiar to that.. but i have concluded that my wireless drivers are incompatible.. im following a tutorial with ndiswrapper or something right now :) ill let you know if it works :) oh and i installed 10.04B to see if it would work better :P

---

### Post by joshlalonde on 2010-04-15
yes!!! the wired connection worked and i obtained the updates and drivers... but sadly.. it didnt work :( it sais the drivers are working but i have no wireless connection at all.. only eth0. ugh i hate life.

i cant ping anything or detect anything wirelessly.. it sais stuff like "not connected" or "cannot find xxxxxx"

---

### Post by joshlalonde on 2010-04-17
im sorry i ignored your advice.. i re-read your comment. and i have a problem. all i have for devices is eth0 and lo <-- loopback?? how can i get wlan0???

---

### Post by joshlalonde on 2010-04-17
bump!

---

### Post by eltonw on 2010-04-17
> **joshlalonde said:**
> yes!!! the wired connection worked and i obtained the updates and drivers... but sadly.. it didnt work :( it sais the drivers are working but i have no wireless connection at all.. only eth0. ugh i hate life.

i cant ping anything or detect anything wirelessly.. it sais stuff like "not connected" or "cannot find xxxxxx"

Tbis should tell you something: [http://ubuntuforums.org/showthread.php?p=9121252#post9121252]("http://ubuntuforums.org/showthread.php?p=9121252#post9121252")

.... [COLOR="Red"][FONT="Franklin Gothic Medium"]_also a word of advice to a newbie_[/FONT][/COLOR]: BETA CODE is meant for *testing*, and things can break. Unless you are prepared for the consequences, you should not install it on a machine where your data is of critical importance ... unless you do a backup FIRST.

The kernel this is present in the current beta is causing all sorts of connection problems, sad to say.
However there are workarounds either by installing drivers, or installing a different kernel, such as HERE:[http://rsalveti.net/pub/ubuntu/kernel/lucid]("http://rsalveti.net/pub/ubuntu/kernel/lucid")

HTH...

---

