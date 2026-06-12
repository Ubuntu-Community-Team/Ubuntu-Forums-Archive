---
title: "Home network problem"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by BrashMan on 2009-03-01
Hello to all who know more about Linux and Ubuntu than I do!

**Here's my scenario:**
I have a desktop PC running Ubuntu 8.10 Intrepid, and two laptops running the same OS. I want to network the three computers with the desktop being basically the primary point since I have the printer and my main file system on there.

The desktop is connecting to the internet via a wireless USB adaptor. My neighbor and I share the costs of internet, and I'm connecting via wireless to the modem which is in his part of the apartment upstairs.

I have my own wireless router, and what I want to be able to accomplish is this: receive the internet signal through the USB adaptor, and have my wireless router serve as the access point for my two laptops to get on the internet and access my desktop's filesystem and printers.

**Here's the question:**

I have the router configured where I can connect to the desktop's filesystem okay - but ONLY if I disconnect the wireless adaptor and connect to my own wireless router on the desktop - which is connected to the computer via ethernet. There is no internet signal per say going into this wireless adaptor - so basically to access my file system I have to disconnect the internet and connect to the wireless router. Kind of a pain.

I need to be able to essentially have my desktop connected to two connections at once: the wireless for internet purposes, and the router for networking purposes. I'd ideally love to have the wireless connection shared across the wireless router as well.

I'm lost - what should I do to make this work? Thanks in advance!

---

### Post by Iowan on 2009-03-01
If I read correctly, you want to share internet (on wireless adapter) with the wireless router connected via ethernet.  [This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page may help - there's a wireless link near the bottom.  It's possible you may have a few more hoops to jump through to make it work with Network Manager (or around it).

---

### Post by qbox on 2009-03-01
What kind of wireless router do you have? Better solution is to make your router a Bridge. So you router are connected to your neighbor router via wireless. You can connect your computer to the ports on the router (or via wireless). For this you need router with 2 antenas. One for receiving the signal from neighbor router and one to emit the signal in your house. You and you neighbor will be in the same network domain. Post the router version and I will see if I can find you how to make a bridge router. You can google by your self if I didt respond (i dont have much time).
Cheers

---

### Post by qbox on 2009-03-01
Or read this if you can find use it
[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)
[http://ubuntuforums.org/showthread.php?t=1083299](http://ubuntuforums.org/showthread.php?t=1083299)

---

