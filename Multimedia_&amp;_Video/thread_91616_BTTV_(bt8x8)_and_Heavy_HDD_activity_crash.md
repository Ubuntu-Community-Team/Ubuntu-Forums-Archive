---
title: "BTTV (bt8x8) and Heavy HDD activity crash"
date: 2005-11-17
forum: Multimedia &amp; Video
---

### Post by theToolman on 2005-11-17
Hey guys;

I have a problem that only occurs when watching TV - if I do any large data transfer on any HDD it just crashes. It is reproducible but I have no idea how to debug it.  it just causes the whole system to lock with the HDD light on with no response from CAPSLOCK or anything - needs hard reset to start again.

when the tv isnt on, the system is stable under any load and its really frustrating me!

I have 3 different bt 8x8 cards (Dynalin, pinnacle rave pro, pixelview), and have tried all 3 in every slot with no other cards (except nvidia AGP)  with the same result :(

My MB is an ASUS A7V600-X with an NVidia FX 5200.  I didnt have this problem with my older motherboard so Im thinking it might be some peculiarity with my MB.  Any suggestions on how to proceed narrowing down the issue?

---

### Post by poptones on 2005-11-17
More via chipset flakiness...?

Might be the motherboard, might be a hard drive flaking out. Check system tools>system log and see if there are messages about hd activity.

---

### Post by theToolman on 2005-11-17
Hmm i dont think the drive is 'flaking out' as they work fine when the tuner isnt on - definitely more like to be chipset badness or at least chipset support badness :D

Anyone care to comment on the via KT600/VT8237 support? is it known to be bad?

---

### Post by theToolman on 2005-11-17
Hmm on more investigation it seems that i need to a) have tv going (bttv etc..) and b) use 2 devices on the chipset ie. any combination of sata, pata, eth0 seem to cause the problem..

so it crashes when I scp a file from another box, dd between any 2 discs etc. but I can "dd if=/dev/(hd*|sd*) of=/dev/null" or "dd if=/dev/zero of=/dev/(hd*|sd*)" while watching TV.  (kids dont try that second one on any disc with data u like....)  

I've been thinking about making a little test servlet to make lots of traffic without disc reading to see if eth0 can pass lots of data without reading discs while the TV is on..

So it seems more likely that the chipset doesnt like multitasking with lots of data when bttv is going.   Ug!  I wonder if its a chipset driver/module bug?  I dont really know enough to make a good bug report :(

---

### Post by BoyOfDestiny on 2005-11-18
[QUOTE=theToolman]Hmm on more investigation it seems that i need to a) have tv going (bttv etc..) and b) use 2 devices on the chipset ie. any combination of sata, pata, eth0 seem to cause the problem..

so it crashes when I scp a file from another box, dd between any 2 discs etc. but I can "dd if=/dev/(hd*|sd*) of=/dev/null" or "dd if=/dev/zero of=/dev/(hd*|sd*)" while watching TV.  (kids dont try that second one on any disc with data u like....)  

I've been thinking about making a little test servlet to make lots of traffic without disc reading to see if eth0 can pass lots of data without reading discs while the TV is on..

So it seems more likely that the chipset doesnt like multitasking with lots of data when bttv is going.   Ug!  I wonder if its a chipset driver/module bug?  I dont really know enough to make a good bug report :([/QUOTE]

My last pc had a via board... I avoid via like the plague now... Anyway, my suggestion for every "hardware" problem, try and see if your chipset has a bios update. :)

---

### Post by Teroedni on 2005-11-18
[QUOTE=theToolman]Hmm i dont think the drive is 'flaking out' as they work fine when the tuner isnt on - definitely more like to be chipset badness or at least chipset support badness :D

Anyone care to comment on the via KT600/VT8237 support? is it known to be bad?[/QUOTE]

The last Via motherboard i have was the km133(Windows)
Since then i have also avoided Via. It doesnt seem they care to much about Linux either:( I stick to Nvidia chipset. They are good:)

---

### Post by theToolman on 2005-11-18
Yeah my old motherboard was an nforce and worked perfectly... till it died :(  There aren't many options for athlon MBs nowadays - everyone seems to be moving to 64bit - and I needed a MB in a hurry.  I was hoping that the KT600 was gonna be ok..   Still welcome any suggestions for improving stability!

---

### Post by Teroedni on 2005-11-19
which brand are you using?
[http://techreport.com/reviews/2003q4/kt600s/index.x?pg=14](http://techreport.com/reviews/2003q4/kt600s/index.x?pg=14)

---

### Post by Joeb on 2005-11-19
[QUOTE=theToolman]Hey guys;

I have a problem that only occurs when watching TV - if I do any large data transfer on any HDD it just crashes. It is reproducible but I have no idea how to debug it.  it just causes the whole system to lock with the HDD light on with no response from CAPSLOCK or anything - needs hard reset to start again.

when the tv isnt on, the system is stable under any load and its really frustrating me!

I have 3 different bt 8x8 cards (Dynalin, pinnacle rave pro, pixelview), and have tried all 3 in every slot with no other cards (except nvidia AGP)  with the same result :(

My MB is an ASUS A7V600-X with an NVidia FX 5200.  I didnt have this problem with my older motherboard so Im thinking it might be some peculiarity with my MB.  Any suggestions on how to proceed narrowing down the issue?[/QUOTE]


Does it make a difference if you change the deinterlace settings?  For instance, does using a less resource intensive one reduce the problem?  Also, does it make a difference if you use the generic nv video driver versus the nvidia one?  You might also look for IRQ conflicts.  I once had a bttv card that kept wanting to use my sound card IRQ.  I had to move BOTH the bttv card and the sound card and turn off the "auto" setting for plug and play to get it to work.

Joeb

---

