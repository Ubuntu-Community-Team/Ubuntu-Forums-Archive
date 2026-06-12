---
title: "Newbie Network Problem on ubuntu/xp dual boot"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by guiltytomb on 2006-05-03
I hope I'm not posting an issue that's already been covered but, I've searched for an answer to this all morning.  I'm hoping this is something easily resolved.  I just installed ubuntu yesterday on a secondary hard drive on a machine that's already running winxp.  I'm not a complete virgin to linux as I've used Fedora Core before.  However, I'm still a newbie.  

Anyhow, my issue is this:  After the installation and updates, Ubuntu worked wonderfully.  I messed around with some of the basic applications (I did not change any system setting...or even bother using the terminal for anything.)  Later, I restarted the machine to check on windows...and that worked well too.  (by the way the my internet connection to this machine was via an onboard ethernet card.)  Both windows and ubuntu recognized my internet connection flawlessly.  I shut the machine down at the end of the night.

When I went to start it up this morning ubuntu started to hang on configuring network.  It passed it fine yesterday...I don't know what could've changed.  Also, now windows says a network cable is unplugged.  I've tried all the basic troubleshooting in windows:

testing the cable connection
testing a different, working, cable
updating drivers
disabling the hardware
unistallng/reinstalling the hardware

Unfortunately, this was all done in windows b/c I don't know how to configure hardware on a linux box yet.

By the way, maybe I'm missing something, but:

it's a Realtek RLT-8169/8110 onboard ethernet
I connect through a wireless router via ethernet (i use the wireless for os x, which is working fine)
I tried a straight connection modem to the machine...same problem.

Why did both xp and ubuntu work yesterday?  Why don't they work now?

I've read some stuff about IPv6 being a problem.  Under System Tools>Network Tools>Devices...the Network Device is set as loop interface (lo) and I can't cofigure.

Any help would be very appreciated.  I'm sorry if this is a repeat post.

---

### Post by Iowan on 2006-05-03
If XP and Ubuntu are both having problems with the NIC, could the NIC have died?

---

### Post by guiltytomb on 2006-05-03
It's very likely.  I'll check that. But that would be one hell of a coincidence, don't you think?  Also, I'm not sure but, Windows says the device is working properly and Ubuntu has all the info on it in the device manager.  I'll try a new pci card in the meantime. Thanks for the reply

---

