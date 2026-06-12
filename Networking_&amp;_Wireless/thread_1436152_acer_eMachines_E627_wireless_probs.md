---
title: "acer eMachines E627 wireless probs"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by kmgma on 2010-03-22
I am running the 64 bit ubuntu 9.10 and cannot connect to the Internet. Everything appears to be working (and recognized) yet no connection. My Atheros eth0 (wired) works all the time but my eth2 (wireless Broadcom wireless does not under Ubuntu Linux) everything works well under Windows 7 (dual boot). Using WEP security.
Shouldn't eth1 be the next scheme after eth0? Would eth1 be controlled by my wireless switch whereas eth2 not? 
 Any suggestions?

---

### Post by murderslastcrow on 2010-03-27
I have a similar issue with the same model of computer, with 64-bit Karmic. The wireless will connect, but randomly die out, and most of the time I have to restart since putting in the authentication again (which it persistently asks for, for some odd reason, despite this being the default automatic wireless connection) before it'll start working again.

The computer dual-boots with XP, and the wireless is flawless with XP. Also, every other wireless Ubuntu computer I've brought to the same connection connects persistently without any problem.

So it's down to this version of Ubuntu at least, with this specific wireless card/driver. Any help would be greatly appreciated in alleviating this issue for the OP, since it could shed light on the similar issue I'm having.

---

### Post by murderslastcrow on 2010-03-31
I actually found the solution to this- the drivers are relatively new and the newer modules don't have this issue. Let me go look for the solution I found for this...

Well, I'll have to come back to it since I have to go out, but just upgrading to the backport of the wireless modules and generic modules seems to do the trick in Karmic.

I can give you exact package names when I get back.

---

### Post by AlisonRuther on 2010-06-23
I thought it's just about my internet provider. I didn't think that it might have something to do with my hardware. Hope to see possible solutions from this forum?

---

