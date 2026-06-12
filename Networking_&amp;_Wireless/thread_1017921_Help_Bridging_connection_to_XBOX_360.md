---
title: "Help Bridging connection to XBOX 360"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Depressed Man on 2008-12-21
So I have a bridge setup in Windows to the 360 (NAT is open since I DMZed my computer). However, I'm not a huge fan of using Windows (I just keep it around for the games) and after upgrading my desktop to Interprid I want to setup a network bridge in Ubuntu as well. Being in Ubuntu would also be more secure even with a DMZed computer. 

I have a wireless connection ATH0 (or is it wifi0?) that I am connected to that I want to bridge to eth0.

I looked around the FAQs and Guides and I see that it requires using bridge-utils but I am confused as how to set it up after installing bridge-utils. Any help would be appreciated.

---

### Post by Depressed Man on 2008-12-21
ifconfig eth0 0.0.0.0
ifconfig ath0 0.0.0.0
brctl addbr br01
brctl addif br01 eth0
brctl addif br01 ath0
dhclient br01

Is this even close to being remotely right? I tried it and it just stopped my internet connection and my 360 couldn't even connect to the desktop.

---

