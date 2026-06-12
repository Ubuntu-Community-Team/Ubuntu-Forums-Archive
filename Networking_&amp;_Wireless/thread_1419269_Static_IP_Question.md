---
title: "Static IP Question"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by BRFC on 2010-03-01
Hi people of Ubuntu I wonder if someone could lend me a hand.  I've recently set up Mediatomb on my Ubuntu 9.04 machine so I can watch/listen to stuff on my PS3, all works well until I have to shut my machine down or turn the router off for any reason.  When I re-boot my IP address has changed so I have issues with Mediatomb and with the shared printer I set-up so my other half can remote print from her Macbook.  I seem to think having my IP set static would solve these problems but I know little to nothing about how networking and such work so would welcome some guidance.  Sorry if this has been asked before but I couldn't find anything specific enough to give me the confidence to change settings incase I make a real mess of things.  Many thanks in advance Chris.

---

### Post by Iowan on 2010-03-01
Network Manager can be configured with a static address -  you need to insure that the static address is outside the DHCP server's range, but still inside the subnet.

---

### Post by Neezer on 2010-03-01
> **BRFC said:**
> Hi people of Ubuntu I wonder if someone could lend me a hand.  I've recently set up Mediatomb on my Ubuntu 9.04 machine so I can watch/listen to stuff on my PS3, all works well until I have to shut my machine down or turn the router off for any reason.  When I re-boot my IP address has changed so I have issues with Mediatomb and with the shared printer I set-up so my other half can remote print from her Macbook.  I seem to think having my IP set static would solve these problems but I know little to nothing about how networking and such work so would welcome some guidance.  Sorry if this has been asked before but I couldn't find anything specific enough to give me the confidence to change settings incase I make a real mess of things.  Many thanks in advance Chris.

I'll send you a copy of mine tonight if you don't have this fixed by then. It is a simple matter of editing a text file. You can also try right clicking the internet connection button and going to properties or soemting like that...I'm on my work laptop right now, so I don't have access to my ubuntu setup right now. Setting up the server and the PS3 helped me a lot. I kept getting a dlna error if I didn't set both to a static IP address.

You might also be able to do it from your router. I am pretty sure I have an option on my router to assign specific IP address to certain MAC addresses. This will give your device a static IP addres on that network I think.

---

### Post by BRFC on 2010-03-01
Firstly thanks for the quick reply but imagine you're talking to a complete moron, is it possible to guide me through the process in a little more detail, for example, step 1 Open Network Manager, step 2 Click this, step 3 Type this, step 4 TADA! you're done.  Sorry if I come across a little like a simpleton but need all the advice you can give.  Cheers Chris

Thanks for the advice Neezer would be great if I could get it stable.

---

### Post by Iowan on 2010-03-01
I'm willing to take small steps if you are...
First, do you have access to your router setup page? It'd be handy to know what IP addresses are available, and what range to avoid.

By the way, if you can access the router configuration page, you may just want to set up a "reserved" address - a "static lease", based on MAC address. Many (if not most) routers/DHCP servers can be so configured - that'd simplify configuration of the server.

If that sounds viable, the router model would be helpful to know. **ifconfig -a** or **ip addr** will provide the MAC address.

---

### Post by BRFC on 2010-03-03
Okay, thanks to all the advice above I have now configured the router so both my computer and PS3 have static IPs.  I've tested the setup, by re-booting everything invovled and all seems well so a big thank you for the help.  Cheers Chris

---

### Post by Iowan on 2010-03-03
I ws expecting a few more small steps - but won't insist...
Congrats! [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

