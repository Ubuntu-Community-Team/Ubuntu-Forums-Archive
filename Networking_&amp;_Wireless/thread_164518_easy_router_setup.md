---
title: "easy router setup?"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by helmet on 2006-04-22
Hi all

I've searched and searched but have yet to find some nice explanation as to how I can use my kubuntu machine as a router. I don't usually use it directly, as I use nx and whatnot to login and use it if i have to. it is my print server and webserver for my website and also runs gameservers once in awhile. my actual router however is getting insufficient, mainly due to the fact that there aren't enough spaces to port forward what i need to have forwarded. i have two network cards in the mail (i thought an old one i had worked but guess not).

what do I have to setup to make this work? and if the only way is bloody iptables crap then nevermind...too lazy to bother with that. i use firestarter for my firewall and i know it has an IP forwarding section (greyed out right now). what do i have to do to make this work?

thanx

---

### Post by mips on 2006-04-23
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

If you are worried about IP Tables then look at **fwbuilder** it's in the repos and gives you a gui frontend to setup iptables

---

### Post by adamkane on 2006-04-23
Hey, mips!

Easy router:
Buy a cheap netgear router/firewall, and leave your worries behind.

---

### Post by Jason_25 on 2006-04-23
Check out my post #7 of [this]("http://ubuntuforums.org/showthread.php?t=150842&highlight=access+point+router") page.  It's like a mini wireless routing how-to.

---

### Post by helmet on 2006-04-23
[QUOTE=adamkane]Hey, mips!

Easy router:
Buy a cheap netgear router/firewall, and leave your worries behind.[/QUOTE]

except netgear sucks....i have a linksys but i need to forward more ports...plus i'm gonna be bored for about a week and this sounds like an interesting project...i found an old 486 i can use too!

---

### Post by helmet on 2006-04-23
[QUOTE=mips][http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

If you are worried about IP Tables then look at **fwbuilder** it's in the repos and gives you a gui frontend to setup iptables[/QUOTE]

sweet little program thanx for that tip! it still looks pretty intense i'll have to read up on iptables

---

### Post by mips on 2006-04-24
If you have a spare PC and want to dedicate it as a firewall then look at:

[http://m0n0.ch/wall/](http://m0n0.ch/wall/)
[http://www.shorewall.net/](http://www.shorewall.net/)
[http://www.smoothwall.org/](http://www.smoothwall.org/)
[http://ipcop.org/](http://ipcop.org/)

---

### Post by Iowan on 2006-04-24
In case a single-floppy router sounds interesting:
[http://www.freesco.org/]("http://www.freesco.org/")

---

