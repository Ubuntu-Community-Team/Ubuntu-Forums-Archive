---
title: "Wireless Adapter Cannot Connect After Router Reset in Jaunty / Karmic"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by Jags_FL on 2009-12-27
My Linksys wireless-G USB adapter can't connect to Westell 9100EM router after a router reset (I had to reset for an unrelated problem) in jaunty / Karmic. Though 2 other laptops with Windows can still connect without any problem.

Now when I try to connect the PC _with either Jaunty or Karmic_ using Linksys WUSB54GC to my network, it tries for few minutes and asks for the password again & again. 

I've changed every possible router settings (its on channel 11, WPA2 now), have enter the password 30+ times and also followed this [**WirelessTroubleShootingGuide**]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") but its not helping. Finally I've re-installed both jaunty & Karmic too.

Any help is highly appreciated.

---

### Post by Jags_FL on 2009-12-27
anyone on wireless networking? Many thanks

---

### Post by scotc on 2009-12-27
> **Jags_FL said:**
>  Finally I've re-installed both jaunty & Karmic too.

If you had a separate /home, then the reinstall would not wipe the connection.  Is that so?

In which case my only suggestion is that the network connection is no longer "appropriate" for the router.  Like it's corrupted, but in reverse - it's the router that's changed.  I've had that before.

Anyway.  Delete the connection and remake it manually.

Good luck.

Scot

---

### Post by Jags_FL on 2009-12-27
@ scotc

many thanks for the reply. Before re-installing Jaunty and Karmic I did format the hard drive completely. By now I've even tried Mandriva 2010.0 and Lucid Lynx Dec-26 nightly build too.

And yes, I have also deleted connection (my router name) many times by right clicking on Network Manager Applet.

The thing that bothers me is that wireless works just fine on Windows laptops and prior to resetting the router it was working just fine with Jaunty and Karmic too. Thanks again.

---

### Post by The Ratman on 2010-06-05
I had exactly the same problem - I have a USB wireless adapter which used to connect instantly to my home network, then one day it wouldn't connect and kept asking for the password. It connected fine when security was turned off at the router. I tried all kinds of things I read on forums and nothing worked - I was getting really frustrated. Finally I figured it out - I just unplugged it and plugged it back in and it worked fine again! It was plugged in at the back of the computer so I hadn't really thought of doing that because it was awkward to get at.

I hope this will help someone else with the same problem.

---

