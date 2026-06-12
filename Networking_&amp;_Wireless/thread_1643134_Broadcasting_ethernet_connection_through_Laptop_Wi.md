---
title: "Broadcasting ethernet connection through Laptop WiFi"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by dukhia on 2010-12-11
Hello Guys :),

I've got an ethernet connection in my home and I wish to use it with my Lappy and PS3.

Now the problem is that the ethernet connection is limited to my bedroom, but not where the TV is making it impossible to connect it to the PS3.

The question is that can I Broadcast my **Ethernet connection** using the WiFi adapter in **Infrastructure** mode so that my PS3 can connect to it.

P.S: I dont have any intention of spending money on a Wireless router :popcorn:.

---

### Post by dukhia on 2010-12-11
bump!

---

### Post by dukhia on 2010-12-12
How come my queries are never answered :(

---

### Post by dukhia on 2010-12-13
:(

---

### Post by Plumtreed on 2010-12-13
The question is not clear to me, you can do an Ad Hoc wireless connection of course. How you connect to that depends on the 'remote' laptops etc.

I have never been succesful with any security doing this so my guess is that you become a wide open hot spot!

In fact, I'm asking that question on another thread, saw your unanswered query and thought i should reply.

---

### Post by baturay on 2010-12-13
Just click network applet, select "Create new wireless network", assign your SSID name and password and voila...

---

### Post by dukhia on 2010-12-13
> **Plumtreed said:**
> The question is not clear to me, you can do an Ad Hoc wireless connection of course. How you connect to that depends on the 'remote' laptops etc.

I have never been succesful with any security doing this so my guess is that you become a wide open hot spot!

In fact, I'm asking that question on another thread, saw your unanswered query and thought i should reply.
I wanted to achieve what this software does on windows

[http://virtualrouter.codeplex.com/](http://virtualrouter.codeplex.com/)

PS3 doesn't support connection sharing through AD Hoc.

---

### Post by dukhia on 2010-12-13
> **baturay said:**
> Just click network applet, select "Create new wireless network", assign your SSID name and password and voila...
An AD Hoc connection doesn't help, wish it could broadcast in Infrastructure Mode. :(

Thanks for the help btw :)

---

### Post by dukhia on 2011-01-03
With the help of [this]("http://www.su-root.eu/computing/turn-your-linux-computer-in-a-wireless-access-point-using-hostapd") article, I've been able to successfully create an access point.

Problem is while bridging both the interfaces, after adding eth0 to the bridge I am no longer able to connect to the internet. What could I be doing wrong.

Help required please.

---

### Post by PatchesTheCaveman on 2011-01-03
That's because bridging just links two interfaces together and transfers all input/output between them.

I think you want just simple Internet connection sharing.  To accomplish that, follow the instructions I provided on this thread:  [http://ubuntuforums.org/showthread.php?t=1655454](http://ubuntuforums.org/showthread.php?t=1655454)

You can also do that with your WLAN in Infrastructure mode, if you have a wireless router.  You will need to turn off the DHCP on the wireless router configuration, however.

---

### Post by dukhia on 2011-01-03
> **PatchesTheCaveman said:**
> That's because bridging just links two interfaces together and transfers all input/output between them.

I think you want just simple Internet connection sharing.  To accomplish that, follow the instructions I provided on this thread:  [http://ubuntuforums.org/showthread.php?t=1655454](http://ubuntuforums.org/showthread.php?t=1655454)

You can also do that with your WLAN in Infrastructure mode, if you have a wireless router.  You will need to turn off the DHCP on the wireless router configuration, however.
Let me try it :D

---

### Post by dukhia on 2011-01-03
> **fanlynne said:**
> Use a cross over ethernet cable to connect the 2 laptop ethernet ports. Configure laptop 1 as a router. It may be easier to assign static IP addresses to the 2 ethernet ports, or make laptop 1 a DHCP server.
Unfortunately, I only have one ethernet port in my laptop.

---

