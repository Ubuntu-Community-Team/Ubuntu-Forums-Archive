---
title: "Can't Connect to WPA / WPA2"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by Tinieblas on 2009-10-24
I have a Compaq nx6125 running Ubuntu 9.04. When I initially installed Ubuntu my wireless did not work. I finally found this post - *[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) - * and following all of the steps my wireless now works. I cannot, however, connect to any wireless network that requires WPA or WPA2 authentication. My router at home was initially set up as WPA2, but I reset it to WEP and I can connect without any problems. That seems to be the case everywhere I go. I can connect to unsecured and WEP networks, but I cannot connect to WPA or WPA2. The wireless network in my office at work is, of course, WPA2, which means that I have to have my laptop connected to a wired network, and that defeats the whole purpose of having a laptop... Any help would be greatly appreciated. Thanks!

I am using WICD as my network manager if that makes a difference...

---

### Post by Tinieblas on 2009-10-26
I've been looking but so far I haven't found any solutions on my own. Any help?

---

### Post by bkratz on 2009-10-26
> **Tinieblas said:**
> I've been looking but so far I haven't found any solutions on my own. Any help?



Not knowing what card you are using you could check through this long (long) posting and see if it applies.

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by Tinieblas on 2009-10-28
> **bkratz said:**
> Not knowing what card you are using you could check through this long (long) posting and see if it applies.

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

I'm checking it out right now... we'll see...

While I'm doing that, this is my card:

02:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

... if that helps.

Thanks!

---

### Post by bkratz on 2009-10-28
You can make life easier by using the thread tools search function to search for BCM4318 once you are in the thread.

Good luck

---

### Post by teward on 2009-10-28
A question:  Is it at all possible that the routers/networks with the configuration are denying you access because you use Ubuntu/Linux?  (this was the problem with my home network until I changed the settings on the router/network)

Or, did you have problems previously with connecting to WPA2-encrypted connections?

---

### Post by Tinieblas on 2009-10-28
> **TrekCaptainUSA said:**
> A question:  Is it at all possible that the routers/networks with the configuration are denying you access because you use Ubuntu/Linux?  (this was the problem with my home network until I changed the settings on the router/network)

Or, did you have problems previously with connecting to WPA2-encrypted connections?

My laptop was previously running Windows XP and I could connect to WPA2, so I know that the card is capable of doing it.

As far as whether the routers/networks are denying Ubuntu access, I'm sure that's not it because I can't connect to ANY WPA or WPA2 network, even ones like at work where everyone is supposed to have access and I know that there are others here that use Ubuntu. Also, I can plug an ethernet cable directly into the router and connect that way, so I assume that means the router does work with Ubuntu...

Thanks for the suggestions though!

---

### Post by teward on 2009-10-28
> **Tinieblas said:**
> My laptop was previously running Windows XP and I could connect to WPA2, so I know that the card is capable of doing it.

As far as whether the routers/networks are denying Ubuntu access, I'm sure that's not it because I can't connect to ANY WPA or WPA2 network, even ones like at work where everyone is supposed to have access and I know that there are others here that use Ubuntu. Also, I can plug an ethernet cable directly into the router and connect that way, so I assume that means the router does work with Ubuntu...

Thanks for the suggestions though!

Okay, noticed something in another thread, thought it might apply.  

Somewhere else (don't remember the thread) they said they were using the WICD and had problems with WPA2 connections.  They replaced it with something else, and it made it work.  Perhaps it's the connection manager you're using?

I just use the Network Manager applet (go to Add/Remove, search "Network Manager", it should be the first one if you select "Show All Available applications"), and it lets me connect to everything (including WPA2, WEP, WPA, etc).  Not sure if that helps with your situation, though.

---

### Post by Tinieblas on 2009-10-30
> **TrekCaptainUSA said:**
> Okay, noticed something in another thread, thought it might apply.  

Somewhere else (don't remember the thread) they said they were using the WICD and had problems with WPA2 connections.  They replaced it with something else, and it made it work.  Perhaps it's the connection manager you're using?

I just use the Network Manager applet (go to Add/Remove, search "Network Manager", it should be the first one if you select "Show All Available applications"), and it lets me connect to everything (including WPA2, WEP, WPA, etc).  Not sure if that helps with your situation, though.

I upgraded last night to 9.10 and figured that while I was at it I'd replace WICD with Network Manager. Still no luck. I do like Network Manager a whole lot more than WICD though. WICD gave me so many problems. The only reason I was running it was because the walk-through I found to get my wireless working initially had WICD as one of the steps. So even though the problem's still not fixed, I am SO glad that you had me switch to Network Manager.

But like I said, still no WPA access... any other ideas?

---

### Post by Tinieblas on 2009-10-31
I found a comment somewhere that said that the problem is likely firmware. It led me to this site: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-lp) ... I followed all the steps listed to update to the most recent firmware for my card and absolutely nothing is different. Still no WPA/WPA2 access... There has to be some way to get this stupid thing to work... Anyone?

---

### Post by Tinieblas on 2009-11-06
I've still been searching all over and can't find anything that works...

---

### Post by Manyette on 2009-11-06
As a newb I can't offer much help, except to tell you than I use WPA2 with my Linksys Router,and have had no problems whatsoever, with either jaunty or karmic.  And I am useing network manager, and an Atheros wireless chip.

---

