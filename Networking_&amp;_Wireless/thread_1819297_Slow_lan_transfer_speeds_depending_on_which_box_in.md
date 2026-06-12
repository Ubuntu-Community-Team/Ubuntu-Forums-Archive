---
title: "Slow lan transfer speeds depending on which box inits transfer"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by Croutoncc on 2011-08-05
I just upgraded my home network to gigabit lan.

Here is my problem which I have yet to make headway on:

Ubuntu laptop -> XP desktop file transfer is very slow only when I "send" the file to the XP desktop from the laptop side (~8 Mb/s).

If I am on my XP desktop and "grab" the file from my ubuntu laptop and bring it to the desktop the file transfer is fine (~25-27,Mb/s).  

Any other file transfers are fine....its only sending files to XP desktop from Ubuntu laptop initiated from the laptop end.

Things to know:
Ubuntu 10.10
Laptop and Desktop both have gigabit cards with latest drivers.
I have tried 3 gigabit routers.....so this rules out the router. 
It is not the wired infrastructure in my house.  I tried by connecting Desktop -> router -> laptop with quality cat6 cables bypassing wall plugs - exact same behavior.
I have verified that both connections are indeed connected at gigiabit speeds.

I have profiled hard discs on both ends: 
Desktop read - 32 mb/sec
Dekstop write - 31 mb/sec
Laptop read - 90 mb/sec
Laptop write - 89 mb/sec

All files get transfered on my network between 25-27 mb/sec consistently..except for the problem direction (laptop -> desktop) inited from laptop end when I only get about 8 mb/sec.

I broke down and got Win7 running on the laptop.  Initially it behaved the same way but upon changing the following I was able to get around 18-19mb/sec....not perfect, but livable for now.   In ubuntu how do I change these settings:?

flow control         disable 
interrupt moderation        disable 
ipv4 checksum ofload         disable 
large send offload ipv4        disable 
lareg send offload v2 ipv4        disable 
large sendnoffload v2 ipv6        disable 
tcp/udp checksum offload ipv4        disable 
tcp/udp checksum offload ipv6        disable

Maybe another reason for my problems?

---

