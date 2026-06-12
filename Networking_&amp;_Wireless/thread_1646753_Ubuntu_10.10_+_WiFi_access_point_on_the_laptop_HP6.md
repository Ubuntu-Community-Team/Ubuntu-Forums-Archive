---
title: "Ubuntu 10.10 + WiFi access point on the laptop HP6735s"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by aor on 2010-12-16
Hello!

I understand that this was discussed a lot. I googled a lot and read forums, but I never got to solve the following problem:

Ubuntu 10.10 (kernel 2.6.35-23, amd64), Network Manager is installed, the laptop HP 6735s (I am certain that wifi is working, - I can connect to other wireless networks), connected to the Internet through ppp0 (VPN), eth0 looks at LAN interface, WiFi - eth1 (info from iwconfig).

WiFi driver "Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware" is installed.

[B]Objective - to create WiFi access point and connect through it to ppp0 with my phone (HTC Desire) or other devices.
[/B]

My VPN connection (ppp0) and network are registered through my internet provider's script - [http://help.internet.beeline.ru/internet/install/linux/](http://help.internet.beeline.ru/internet/install/linux/), not set up not by Network Manager. If I create a new wireless network in NM (point-to-point or access point, IPv4 set to auto) - laptop can not find the network, Internet immediately fall off. Through the manual settings and complex scripts that I found websites and forums I could not get it to work ... I admit - I am a newbie ... I would not write here if I had not tried to solve the problem yourself.

Please help me. Thanks in advance.

---

### Post by spiky001 on 2010-12-16
Can you explain what you want to do / achieve

---

### Post by aor on 2010-12-16
> **spiky001 said:**
> Can you explain what you want to do / achieve

I want to connect my phone to the Internet through WiFi on the laptop (laptop is connected to the Internet)...

---

### Post by spiky001 on 2010-12-16
On the laptop right click network manager then edit connections open wireless tab in the wireless tab set it to adhoc, in the ipv4 settings set it to shared with other computers,

---

### Post by aor on 2010-12-16
> **spiky001 said:**
> On the laptop right click network manager then edit connections open wireless tab in the wireless tab set it to adhoc, in the ipv4 settings set it to shared with other computers,

Yes, but... I tryed to do like this - [http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html"), but on step "Connecting your Ubuntu session to the new adhoc Network" - laptop can't find this new hidden network and the Internet connection is broken ...

---

### Post by spiky001 on 2010-12-16
ok on my adhoc the laptop has to connect to the adhoc connection, Dont know why so i go on laptop connect to hidden network and connect to that then all the other laptops can connct even my nokia dose as well, if the main pc is not connected then none of the others will (strange!!!)

---

### Post by aor on 2010-12-16
> **spiky001 said:**
> ok on my adhoc the laptop has to connect to the adhoc connection, Dont know why so i go on laptop connect to hidden network and connect to that then all the other laptops can connct even my nokia dose as well, if the main pc is not connected then none of the others will (strange!!!)

:( I don't know... I can connect to other WiFi networks... On the Windows 7, when I used it, I could create such network and connect to it other laptop... in two clicks...

---

### Post by spiky001 on 2010-12-16
Well this is how mine works I use it everyday it has to broadcast

---

### Post by mattman85 on 2010-12-16
If you think about it like ad-hoc networks in the airport that little script-kiddies create on their laptops and sit around to use to try to steal info from nearby wifi devices, its not really that strange..

If you are connected wired (or even wireless), you would need to be connected to the ad-hoc wifi network so that the it gets net connectivity. If you didn't need to connect to the ad-hoc with your laptop, how would it be able to send and receive data packets from the net to your connected devices?

If I create an ad-hoc wifi network on my macbook pro, but I don't connect to it, that ad-hoc network doesn't have net access until I connect, because I'm the access point for that ad-hoc network.

Is that semi-understandable? If not, I'm sorry... But I think that should make sense..

---

### Post by spiky001 on 2010-12-16
mattman85  I think the op expected to see it in the list but mine works as you said, I think lol

---

### Post by mattman85 on 2010-12-16
> **spiky001 said:**
> mattman85  I think the op expected to see it in the list but mine works as you said, I think lol

I was replying to your comment about it being strange! Sorry, I should have quoted it before..

> **spiky001 said:**
> ok on my adhoc the laptop has to connect to the adhoc connection, Dont know why so i go on laptop connect to hidden network and connect to that then all the other laptops can connct even my nokia dose as well, if the main pc is not connected then none of the others will (strange!!!)

Just helping to explain the strangeness ;)

---

### Post by aor on 2010-12-16
> **mattman85 said:**
> I was replying to your comment about it being strange! Sorry, I should have quoted it before..



Just helping to explain the strangeness ;)

Sorry, but in this way - How I created in Windows7 WiFi-network on the Laptop 1 (with Internet) and connected to it through WiFi Laptop 2, and this laptops without problems used common Internet...???

---

### Post by polki@mac.com on 2011-01-04
Android has after almost 3 years not put any work into letting androids connect to adhoc networks. Silly goolge :-(
There are solutions, but they involve rooting your phone and then some more work.

[http://code.google.com/p/android/issues/detail?id=82]("http://code.google.com/p/android/issues/detail?id=82")

---

