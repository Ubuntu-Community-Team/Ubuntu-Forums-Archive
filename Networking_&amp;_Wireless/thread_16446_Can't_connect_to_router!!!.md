---
title: "Can't connect to router!!!"
date: 2005-02-21
forum: Networking &amp; Wireless
---

### Post by nickmages on 2005-02-21
I'm new to linux but am fairly familliar with Windows networking.

I am unable to connect to my router (D-Link DI-624) with a 3COM NIC over cable.  When Ubuntu boots up, all my hardware seems to be detected and when I run ifconfig it lists the loopback (which looks fine) and "eth0", however "eth0" doesn't have an IP address.  Here's what it lists (typing this by hand so it may not be complete)

eth0 Link encap:Ethernet  HWaddr 00:50:DA:7A:EB:A2
       inet6 addr: fe80::250:daff:fe7a:eba2/64\ Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500 METRIC:1
       RX packets:0 errors:13 dropped:0 overruns:0 frame:26
       TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000

Running the network config and trying to get the card to use DHCP hangs for about 20 secs, then fails and configuring manually doesn't let me ping my router.  Also, after trying to configure the card, I am unable to load any applications (ubuntu only).  I can't open firefox, launch a console, nothing.  I click the icons and nothing comes up until I reboot.

I'm pretty sure the problem isn't hardware, when I boot back into windows everything works fine.  I've also tried booting into knoppix and get the same results.  Why does my card not work under linux?  I've read a few threads on the knoppix board that suggest that Windows service pack 2 may overwrite some of the settings on my card's EEPROM but the posts don't explain a clear way of telling if this is the case.  I've also booted both knoppix and ubuntu on my laptop (which has a PCMCIA wireless lan card (Lucent Technologies)) and it works flawlessly.  So, these are my half-baked conclusions:

-I can't imagine that BOTH flavors of linux I've tried not being able to support a 3COM card, and it seems to me that it's being detected (though I'm a newb, so I can't be sure).
-The problem can't be that the card is bunk, as it works when I boot into windows.  The only hardware problem I could imagine is that it is this EEPROM issue, but I have no idea how I would be able to tell.

Any help would be appriciated.

---

### Post by moonshot on 2005-06-08
I'm having the same problem.  I just did a fresh install.  I used to have Xandros and it worked fine.  HELP!

---

### Post by kleeman on 2005-06-08
What happens when you do

sudo dhclient eth0

---

