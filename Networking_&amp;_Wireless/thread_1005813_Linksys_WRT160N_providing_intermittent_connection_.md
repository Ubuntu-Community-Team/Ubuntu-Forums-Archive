---
title: "Linksys WRT160N providing intermittent connection and slowing down system"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by TroisiemeCafe on 2008-12-08
I just installed a Linksys WRT160N wireless router in my home and it's resulted in some strange behaviour on my laptop.  When the wireless connection is activated my whole system slows down noticeably; I also get decent web performance for a little while, then seemingly out of nowhere my Bittorrent transfer rates drop to nil and my browser times out before even loading Google.  When I deactivate my connection, then reactivate it, everything is fine for a while longer and the process repeats, however the degraded overall system performance is a constant.  

I thought my inexperience at setting up secure networks might have caused me to do something weird so I tried resetting the router to factory defaults and disabling WAP, but it's no better.  I'm assuming thate the router is the issue since when I connect directly from the cable modem to my laptop overall system performance is good and transfer speeds/page load times are lightning fast.

For the record, my router is a Linksys WRT160N, I'm running Ubuntu 8.04, and my ISP is Shaw (Canadian).

I appreciate you're help, please let me know any other information you might need!

---

### Post by freelook on 2008-12-08
I have this same router.  I installed DD-WRT on it though.  I've noticed that the router had intermittent connections for me.  I ended up disabling a lot of things on it, such as DHCP and DNS, putting more of the burden on my server.  The other thing I did was to upgrade to the latest version of DD-WRT.

I'm not sure I could say what caused the problems, but thanks to what I did above, there's no longer any problem.

I don't think the wrt160n is a very good router.  If you don't care about spending the money, my advice would be to get something else.  If you can't, then whatever you can do to disable services and reduce the load on it should help, such as throttling back or ceasing the bittorrent traffic.

Sorry, that's all the help I can give.

---

### Post by TroisiemeCafe on 2008-12-10
Thanks for the tip!  Unfortunately, since I have the usual student financial sob story I'll have to stick with the WRT160N for now.  How do I go about installing DD-WRT?  I know next to nothing about networking.  Linksys themselves suggested setting my MTU to 1400, and that seems to have helped a bit. Perhaps this DD-WRT firmware is just the ticket, but I have no idea what to do with it and the website doesn't have much newb oriented content, though I'll browse over their forums.

Thanks again!

- Justin

---

### Post by Kasztelan on 2009-03-23
Hi my name is Rob 
Yes I NEED YOUR HELP wery much I have trouble with the same router but my ISP is wcgwave...
I wil be greatfull to receive any help

---

