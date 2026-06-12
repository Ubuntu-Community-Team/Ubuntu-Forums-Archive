---
title: "Wireless Problems with WMP54GS v1.1"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by Matthew Wiebelhaus on 2010-01-04
Well Hello again, its been a year since ive even been on these forums and since ive used linux. I came into possesion of some older hardware. Dell E310/3100 - Pentium 4 2.8GHZ, 2GB 533mhz Ram, 80GB Maxtor harddrive, and 8400GT 512MB 64Bit. I have windows 7 rc on it and it works perfect except 1080p video is very buggy in VLC. I wanted to install Ubuntu 9.10 because overall it is a notch faster and to get my 1080p video working correctly. 

So I used Wubi to install it because I wanted to see if it would work before erasing the windows 7 partition and lo and behold its fortunate I had done so because my wireless doesn't work. It is recognized under the network manager and it says not connected, the little green light on the back of the PCI card is on meaning that it is recognized, but no networks show, just (NOT CONNECTED). Im not sure what that means, I have a router in my house with WPA2 Personal security, and my neighbors unsecured linksys network is also usually avaliable. So what is up with this? This card works under windows....and hackintosh, but not on linux...?

---

### Post by Matthew Wiebelhaus on 2010-01-05
> **Matthew Wiebelhaus said:**
> Well Hello again, its been a year since ive even been on these forums and since ive used linux. I came into possesion of some older hardware. Dell E310/3100 - Pentium 4 2.8GHZ, 2GB 533mhz Ram, 80GB Maxtor harddrive, and 8400GT 512MB 64Bit. I have windows 7 rc on it and it works perfect except 1080p video is very buggy in VLC. I wanted to install Ubuntu 9.10 because overall it is a notch faster and to get my 1080p video working correctly. 

So I used Wubi to install it because I wanted to see if it would work before erasing the windows 7 partition and lo and behold its fortunate I had done so because my wireless doesn't work. It is recognized under the network manager and it says not connected, the little green light on the back of the PCI card is on meaning that it is recognized, but no networks show, just (NOT CONNECTED). Im not sure what that means, I have a router in my house with WPA2 Personal security, and my neighbors unsecured linksys network is also usually avaliable. So what is up with this? This card works under windows....and hackintosh, but not on linux...?

Well I love when I come up with the solutions myself......not shown under restricted drivers until I install it manually from synaptic package b43-cutter. Now I can connect to my network.

---

