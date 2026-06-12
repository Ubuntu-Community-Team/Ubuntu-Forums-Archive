---
title: "Laptop as wireless access point"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by ooobooontooo on 2009-07-07
Hi,

I have a laptop that is running as a server. I wish for it to also become a wireless access point. Unfortunately, the laptop's default wireless drivers didn't work, so I had to go and get the vendor's packaged driver and now it won't let me set the wireless in master (AP) mode. Am I sunk or is there a way around this? Perhaps I could do something with ndiswrapper to try to get it to work with some other driver? I have hostapd installed, but I don't think that's going to work unless I can get my wireless in master mode first. I appreciate any advice.

P.S. I would prefer not to create any ad-hoc networks...

---

### Post by superprash2003 on 2009-07-07
are you planning to setup a adhoc network
?

---

### Post by ooobooontooo on 2009-07-07
> **superprash2003 said:**
> are you planning to setup a adhoc network
?

Eh?...

> P.S. I would prefer not to create any ad-hoc networks...

I wish to set up my laptop basically like a router. So no, I do not want it in ad-hoc mode.

---

### Post by superprash2003 on 2009-07-07
your laptop can connect to only 1 other machine at a time.. routers can handle multiple connections but not laptops or desktops with a WLAN card..so only adhoc mode would work . here's a tutorial [http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html](http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html)

---

### Post by ooobooontooo on 2009-07-08
> **superprash2003 said:**
> your laptop can connect to only 1 other machine at a time.. routers can handle multiple connections but not laptops or desktops with a WLAN card..so only adhoc mode would work . here's a tutorial [http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html](http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html)

Are you sure?

[http://ubuntuforums.org/showthread.php?t=376283]("http://ubuntuforums.org/showthread.php?t=376283")
[https://help.ubuntu.com/community/Router]("https://help.ubuntu.com/community/Router")

I think the links above imply that laptops can act as routers as long as they have master mode enabled.

Also, if what you say is true about laptops being able to connect to only one other machine at time, wouldn't that mean that the maximum number of nodes in any given ad-hoc network is 2?

That would make [this]("http://www.vias.org/wirelessnetw/wndw_05_04.html") graph untrue....

---

### Post by superprash2003 on 2009-07-09
well very few wifi cards i guess support this feature of an AP , most of them work only in adhoc mode.. does your card support AP mode?

---

### Post by ooobooontooo on 2009-07-10
Now there's a question I have. Is it the wireless cards that don't support this feature or is it the drivers? I would suspect that it's the drivers from the articles that I have read. I mean all the card has to do in AP mode in broadcast it wireless and accept incoming calls right?

---

### Post by superprash2003 on 2009-07-10
i think wifi cards support 2 modes . the AP Mode where it connects to multiple pcs wirelessly ( very few support this ) and the adhoc mode where it connects to only 1 pc ( all cards support this ).now first you need to see if your card actually supports that and then worry about drivers..

---

### Post by ooobooontooo on 2009-07-10
> **superprash2003 said:**
> i think wifi cards support 2 modes . the AP Mode where it connects to multiple pcs wirelessly ( very few support this ) and the adhoc mode where it connects to only 1 pc ( all cards support this ).now first you need to see if your card actually supports that and then worry about drivers..

Are you sure? I know of at least four different modes, (managed, master, monitor, and ad-hoc), but you may be talking about the capabilities of the card itself and not the network driver that supports the cards...also, like I said before if ad-hoc mode only support connection to 1 pc, it's impossible to have an ad-hoc network of size greater than 2. Is this what you're trying to tell me?

Also, are you sure support is determined by the card and not by the driver? From [http://linuxwireless.org/en/users/Drivers]("http://linuxwireless.org/en/users/Drivers") it seems they categorise support by drivers and not cards. Also, I know that they are currently working on adding support for my card on b43, which does allow master mode...

---

### Post by superprash2003 on 2009-07-11
well there are many modes.. i was just listing the 2 main ones.. in adhoc yes only 2 maximum.. im pretty sure about that.. capability wise , it probably has to do with drivers or cards i'm not so sure about that..

---

