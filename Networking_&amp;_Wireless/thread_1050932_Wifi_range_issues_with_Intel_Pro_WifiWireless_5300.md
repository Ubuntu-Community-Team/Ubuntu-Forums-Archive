---
title: "Wifi range issues with Intel Pro Wifi/Wireless 5300AGN"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by biueadieu on 2009-01-26
hi all, i'm new to these forums and linux in general but i recently installed ubuntu 8.10 last week and while everything seems to be working great with a little tweaking, i've noticed something strange regarding my WiFi Range.  

i have ubuntu installed on a custom laptop in a dual boot configuration with vista.  when i'm in vista i am able to see my home's wifi network and connect to it from my room with no problems whatsoever.  but when i fire up ubuntu, sometimes it will see the available networks but won't connect to them or it just won't see the available networks at all. but if i move the laptop to the same room that my wireless router is in, it will see the network and connect very strongly.

of course at first i assumed it would be a driver related issue.  so i went to intellinuxwireless.org and started to go through the steps of installing the iwlwifi-5000 driver from there when i discovered that my kernel already had the driver(iwlagn) and ucode(iwlwifi-5000-1.ucode) on my machine.

so now i am completely stumped as to what might be causing the reduction in wifi range.  i've considered that maybe its just that the driver is not fully optimized yet or perhaps there's a power management issue.  

has anyone here experienced similar issues and if so were you able to fix it?

a little summary of my setup:

Intel Pro Wifi/Wireless 5300AGN card
-iwlwifi-5000-1.ucode and iwlagn.ko already on the machine

from my room to the wireless router is about 20-25 feet and a couple walls.  i have 3 other wireless devices in my room that all connect without any problems.  when running vista on the laptop, i'm able to connect without any problems from my room.  when running ubuntu, sometimes it sees the available network but won't connect(seems to fail at the point where its requesting an ip address) or it won't see any available networks at all.

from the same room that the wireless router is in, ubuntu sees the available network and shows a strong signal strength and will connect without a problem.

thanks in advance!

---

