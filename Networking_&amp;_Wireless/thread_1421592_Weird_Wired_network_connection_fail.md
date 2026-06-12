---
title: "Weird Wired network connection fail"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by einherjar573 on 2010-03-04
This morning I ran into an interesting problem.  

I'm running Ubuntu 9.10 on an Asus Revo connected to a Linksys router which is then, obviously, connected to my cable modem.  While testing a theory, I unplugged the Revo's ethernet cable from the router and directly plugged it into the cable modem.  In other words, the Revo was directly connected to the cable modem and my router was sitting to the side looking very left out.  Well, that didn't work at all.  After playing around a little to see if I could fix it (I couldn't), I reconnected everything back to the way it was (Cable modem to router to various PCs).  Still nothing.  I checked the cables and rebooted and nothing has helped.  

I started looking around on various forums, but it seems no one has made the same stupid error I have.  I ran ifconfig and it appears correct EXCEPT no IP address listed.  When I hit ifdown eth0 it says eth0 is not configured.  One last thing I tried before posting is load the LiveCD of Ubuntu 9.10 just to see if it was a hardware problem (like a little static shock from me damaging the ethernet controller when I touched it.  You never know.).  The LiveCD worked fine, no problems.

If you know of a post anywhere that deals quite well with this kind of goofy problem, please point me to it.  I'm always assuming I've missed something.
If anyone wants me to put up any extra information, I will.  I didn't here because the computer I'm using now and the problem computer are in two separate rooms and it's kind of a pain to run back and forth.

As I said, I'm sure it's something small I'm missing.  Any help is greatly appreciated.

UPDATE: Nevermind folks. I disabled and re-enabled the network manager and got it working again. See? I told you it was something small I missed

---

### Post by Iowan on 2010-03-04
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? 
I'd have suggested power-cycling the modem until I got to the part where it started working again. ;)

---

