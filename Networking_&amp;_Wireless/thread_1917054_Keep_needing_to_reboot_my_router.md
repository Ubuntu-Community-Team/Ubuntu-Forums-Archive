---
title: "Keep needing to reboot my router"
date: 2012-01-29
forum: Networking &amp; Wireless
---

### Post by ddastoor on 2012-01-29
Hi, 
OS:Xubuntu 11.10
Wired LAN Router: Dlink GLB-802C
INternel Connection: DSL through my local phone line company. 

Every now and then, the net stops working and freezes up.
I can't use my router's web interface (or telnet for that matter) to connect to my wired router at 192.168.1.1 to commit/reboot my router.

It seems that the whole TCP stack is screwed up or something (I don't know too much about wired networking).

My only option is to manually and physically reboot/restart my router by pressing the button on it.

My questions:
1) Do I need to upgrade my firmware on the router?
2) Any way in which I can play around with ifconfig so when the freeze up does happen, I can access even 192.158.1.1 and reboot from the command line?

Thanks

---

### Post by dave0109 on 2012-01-29
It's worth trying to see if there's new firmware for the router. It helped with mine which seemed to have some kind of memory leak within it.  That same router lasted about another 12 months, but would also require a restart if I put a large amount of data through it (as I have a NAS hanging off it).  In the end, I bought a new router, which has been fine ever since.  (Of course, it'll crash now :D)

---

### Post by kevdog on 2012-01-29
Not sure what to tell you but try flashing the firmware.  If that doesn't help you could see if you could telnet or ssh into the router (if it comes with these capabilites), but the faster option would be to go buy a new router.  I've had this problem before -- all the time I ended up wasting trying to fix it -- a quick 15 min to the store solved all these problems.

---

### Post by ddastoor on 2012-01-29
Ok Thanks Guys, will try something like that...

---

### Post by misterfixit on 2012-01-29
This is a problem which I have had for years.  I've gone through at least 6 different routers, one after the other, and the problem still exists.  The system works fine for several days or even weeks, then I will see that the workstation has lost the internet conection.  The other PC's in the house and several wireles devices are all still on line.  Usually I will go to the system > administration > network and open the network application.  After doing nothing more than that and entering my root password, the network comes back on.  I am certain that this is something screwed up inside of Ubuntu's network scripts and I seem to recall that there are other postings over the years about this identical problem.  As for me I just see it as an inevitable fault which comes around every so often to cause me a few minutes of extra work.  It is a definite PITA, but I've not found any answers in searching through this forum.

OS;  Ubuntu 11.04
Router:  Dlink Dir-632 (this time)
Provider:  Comcast Cable
Cable Adaptor ("modem"):  Motorola SB-6120

---

### Post by misterfixit on 2012-01-30
> **kevdog said:**
> Not sure what to tell you but try flashing the firmware.  If that doesn't help you could see if you could telnet or ssh into the router (if it comes with these capabilites), but the faster option would be to go buy a new router.  I've had this problem before -- all the time I ended up wasting trying to fix it -- a quick 15 min to the store solved all these problems.

I suppose this is a solution IF your router is the problem.  Personally I feel certain that something inside of Ubuntuy's networking is messed up -- and has been messed up for years.  You can't tell me that for the last 6 or 7 years since I first started using Ubuntu and having worked my way through four or five different workstations and at least a dozen routers, that "the router is the problem".  Maybe for some and maybe some will believe that fairy tale, but I know what empirical testing has shown me and it is something in the way that Ubuntu handles the TCP/IP network between the OS and the actual NAS card.  Prove me wrong and you'll be a star and get your $2.00 plus :-)

---

