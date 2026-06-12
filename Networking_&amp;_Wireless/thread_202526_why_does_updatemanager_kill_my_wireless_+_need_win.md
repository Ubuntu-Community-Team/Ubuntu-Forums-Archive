---
title: "why does updatemanager kill my wireless + need windows boot to fix?"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by skelooth on 2006-06-23
I hate limited space for thread titles :P

I have a BCM4whateverxx wireless card on my laptop....

The driver with firmware works PERFECT.... EXCEPT any time I run update manager or make any sort of system configuration the card completely stops working..... 

The only way to fix it is to boot into windows, disable it, then re-enable it.

This is really.... really unacceptable behavior, especially considering I need this lap top for productivity... not booting into a small winxp partition I luckily decided to hold on to.

I want an explaination of why this happens. Is there some type of flash rom switch on the card it's self? How can I fix this absurd behavior?

---

### Post by egorgry on 2006-06-23
I have no idea what's going on. check the syslog and dmesg for anything odd. Does this affect all pcmcia cards? Did you try restarting the pcmcia services or pop the card out then back in? it's very odd indeed.

---

### Post by skelooth on 2006-06-23
It's an integrated card built into the lap top (the antennae are even positioned along the monitor's border). This is the ONLY piece of hardware that does not work flawlessly on my laptop... and argueabley one of the most important for my purposes.

I was only able to figure out that booting into windows would fix it because someone else had a similar problem. What's VERY troubling about this is that once the card 'dies' in ubuntu.... if I boot into windows it's 'dead' there too. But the drivers on windows for some reason have the ability to bring it back to life.

This leads me to believe there is some sort of flash rom or software switch built onto the card that linux can't see and get to with it's current drivers. When ubuntu makes the system wide changes it must be somehow resetting this switch to the off position.....

that's my only and best guess. In general I have had a VERY hard time with wireless and ubuntu w/ multiple machines.... but this one actually works GREAT as long as I don't foolishly update my system :rolleyes:

---

### Post by skelooth on 2006-06-23
bump, someone must know

---

### Post by skelooth on 2006-06-24
[QUOTE=skelooth]bump, someone must know[/QUOTE]
^ that

---

