---
title: "my PC connects to other WiFi, how do I install new my new WiFi router?"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by OrganizedFellow on 2009-01-20
I have been using my wired network after my D-Link wireless router crapped out on me two months ago.

My computer CAN see other wireless networks in my area. Every now and then, I connect to someones unsecured wireless network because I have a few kinks and bends in my ethernet cable, and my connection comes and goes.

I just bought a Linksys wireless router WRT54GL. When I was on windows, I wanted to run Tomato on my other one, the D-Link, but it was not compatible.
The WRT models IS Tomato compatible, but beyond my comprehension.

I just need to get connected to my new router, and have read some of the tutorials here about ndiswrapper.

I am a little lost. Would I still need that (ndiswrapper) to connect to my new router? As I said, my PC can view and connect my neighbors wireless network.

How would I go about getting mine connected?!
The tutorials I've read explain how to get wireless card working, but not what I need specifically.

---

### Post by Kebabman on 2009-01-21
If you are able to connect to wireless networks already then you shouldn't need to touch your PC to get it working with your new router.

Simply set up the router as per the manufacturers instructions and get it up and running, then scan for available networks and connect to yours.

---

### Post by OrganizedFellow on 2009-01-21
> **Kebabman said:**
>  ... Simply set up the router as per the manufacturers instructions and get it up and running, then scan for available networks and connect to yours.
Installation CD runs a .exe.

---

### Post by Kebabman on 2009-01-21
All you should need to do is manually configure it.

Plug it in to the power, connect your pc to it via a normal patch lead and configure it using the web interface, use the username and password your ISP has given you for the ppp settings and it should be able to connect and get an IP, then you just need to configure the wireless network with whatever settings you want (IP address range, WEP/WPA etc etc).

Once that is done you should be able to connect to it.

---

### Post by timcredible on 2009-01-21
ditto to what previous poster said, but let me add that you want to browse to 192.168.1.1 to access your new router.  you should be able to do that with wireless also, just look for the new ssid, which is most probably the brand name of the router.

---

### Post by OrganizedFellow on 2009-01-22
Thanks for the pointers guys!
Got it running tonight.

:D

---

