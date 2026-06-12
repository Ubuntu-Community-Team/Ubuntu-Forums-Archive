---
title: "Ethernet connection to Windows XP"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by Vlodec on 2009-08-01
Just installed xubuntu on my laptop on the recommendation of a colleague and I've already hit a brick wall. I need to connect it via ethernet to my desktop for printer and internet access but I'm finding it impossible. I had thought that by now ubuntu would be idiot friendly but perhaps I'm too big an idiot.

Can someone give me noddy instructions ?

(I've found "instructions" of one sort or another that purport to solve the problem but they all require a level of knowledge which, if I had it, I wouldn't need help.)

P.S. Should have mentioned, the desktop runs Windows XP. The 2 machines are wired and I had them connected ok when both ran Windows.

P.P.S. And it's xubuntu 9.04, just downloaded today.

---

### Post by Vlodec on 2009-08-02
Oh I get the picture. This is a 'geeks only' forum, right ? Sorry guys, didn't mean to intrude. 

:)

---

### Post by Iowan on 2009-08-02
Apparently you missed the picture, however, it does seem a li'l sad that your thread has drawn no response, yet. I'm not sure if "noddy instructions" are good ones or not-so-good.  Which "instructions" have you tried (lest I link to the same ones)? How have you set up IP addressing? (When the machines were both Windows boxes, were they connected with static (manually set) IP addresses?) Is Ubuntu set up for static (manual) address?  
Or... is there a DHCP server somewhere on the network that is supposed to hand out addresses?
If I'm going to fast, just say so (I can always type slower) ;)
It might be helpful to see results of **ifconfig -a** (entered in a terminal). That will help determine if the machine has an address. If it has one (other than 169.254.X.X), it would be good to check **ipconfig** on the XP box to verify that the addresses are in the same subnet.

---

