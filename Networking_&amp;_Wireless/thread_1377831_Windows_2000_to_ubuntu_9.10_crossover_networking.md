---
title: "Windows 2000 to ubuntu 9.10 crossover networking"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by bearlythere on 2010-01-10
Greetings!

I'm trying to setup a crossover connection between my windows 2000 (yes, I'm a caveman...) desktop PC and my ubuntu 9.10 laptop.

I managed to get it to work for a while last month but I had to reinstall Ubuntu and I can't seem to repeat the correct procdure. (To be honest, I haven't the slightest idea of what I did right back then).

Since every procedure I attemp seems to screw up something else (The last straw was when my nm-system-setting.conf file decided to remain blank in spite of being modified as su), I'm thinking of reformatting and reinstalling Ubuntu (for the fifth time) and including only what is essential to this procedure and build from there once it works.

In short, I would appreciate any assistance on creating a Step-by-step procedure to set up this connection.

Thanks a lot!

PS No, I do not have a router, I can't even afford high-speed internet at home so I have to set everything up at school and then test it at home

---

### Post by Iowan on 2010-01-10
[This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page should be a good place to start.

---

### Post by bearlythere on 2010-01-13
Hi all

Iowan, thanks for your lightning-fast response, I wish I'd answered as fast!

However, ICS seems somewhat beyond what I'm trying to do for now (from what I understood). 

I simply need to setup a connection for filesharing between two computers in order to use my dinosaur computer as a file backup.

For the moment, I'd just be happy if I were able to ping the computers back and forth.

I forgot to mention, I'm almost a complete newbie at linux, and am trying to wean off Windows, so be gentle...

Thanks!

---

### Post by Forbees on 2010-01-13
well first off, have you gone through windows network setup? (i think 2000 had it too...)

and on ubuntu, can you see the files shared? from my expierance, ubuntu always finds the other computers without a problem, but getting windows to find ubuntu with the whole workgroup crap is another story

---

### Post by Iowan on 2010-01-13
> **bearlythere said:**
> Iowan, thanks for your lightning-fast response, I wish I'd answered as fast!Maybe a li'l *too* fast - since I missed that you didn't really need internet access - only file sharing. Samba is the traditional way to share between Ubuntu and Windows. It's possible to set up static addresses for each machine - then Samba could be set up,
but [FTP]("http://ubuntuforums.org/showthread.php?t=218630") is another option. The zeroconf part should be useful.

---

### Post by bearlythere on 2010-01-16
Thanks for the answers!

I'll add Samba to the list of stuff to reinstall with ubuntu (I sure hope it's the last time I have to do that).

In answer to Forbees, I did go through the Network Setup on Windows 2000. However, I'm not sure whther I should use a gateway adress or not (half my sources say yes, the other half no).

I hope I'll get a chance to work on this next weekend. I'll let you know what happens.

---

### Post by t047 on 2010-04-09
Did you get to connect both computers because i'm having a similar problem. I want to fileshare, using the ubox as storage except I cant get a proper connection.

---

