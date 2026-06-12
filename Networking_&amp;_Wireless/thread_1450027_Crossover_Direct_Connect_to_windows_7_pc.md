---
title: "Crossover Direct Connect to windows 7 pc"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by t047 on 2010-04-08
Hi, Ive just installed ubuntu on a small nettop type pc. It can connect to the internet but I want a direct network connection thru gigabit LAN using a crossover (apparently a straight cable would have been sufficient). Anyway, I have no idea where to begin. The network connection manager in Ubuntu shows Autoeth1 which is right and, if I manually set the IPv4 I can get the PCs to somehow see each other and the 7 pc to give a 'network access only' but that's it. Any help would be massively appreciated.

---

### Post by Iowan on 2010-04-08
> **t047 said:**
> (apparently a straight cable would have been sufficient).  Gigabit seems smarter that way...
Might need more details. If I'm reading correctly (not a guarantee tonight) you may need to edit your **route**.

---

### Post by t047 on 2010-04-09
OK, so now I can get the two pcs to see each other and can use VPN. However, I can't access the windows PC from ubuntu. I can see it and connect through the workgroup AND, I can access the ubuntu pc from windows. This is because the windows pc keeps recognising is as an 'unidentified' network and stuffs in public. Im betting this is a windows issue but couldn't the ubuntu pc identify itself?

(Just for ref, I got the 2 pcs to network by A) manually changing the IPv4 and NOT setting a gateway, and I got samba installed.)

Oh yeah another problem is that i used **sudo smbpasswd** and left the 2 fields blank, I got a resulting message saying I got root on, Im guessing this isn't good. 

Anyway thanks for the reply Iowan.

---

