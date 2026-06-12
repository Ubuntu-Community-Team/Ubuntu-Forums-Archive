---
title: "Tascam US-122 Under Hardy - No Initialization"
date: 2008-04-21
forum: Multimedia Production
---

### Post by drewdlephone on 2008-04-21
Hey all. I know there are many how-tos on this subject, and I have gone over all of them, and am at a halt here. The two pieces of software required to make the Tascam work, the ALSA firmware and the usx2yloader, are both updated to the newest versions (1.0.15 & 0.1b, respectively), and yet I can't get an initialization to go through. When I type:

```
usx2yloader
```

I get this output:

```
usx2yloader: no usx2y compatible cards found
```

I'm also having an issue with bus support. I know my motherboard is working fine from a USB standpoint, as I've tested with other devices and had success. But every time I try the initialization command, the bus number on the card changes. So whereas I was at /002/002 when I first tried it, I was at 002/003 afterwards. Here's the output from both the audio card query and lsusb. 

```
drew@GiR:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 001 Device 001: ID 0000:0000  

```
```
drew@GiR:~$ cat /proc/asound/cards
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with ALC658D at 0xfe02a000, irq 22
 1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 001/006)

```

I had this working under Gutsy no problem; I followed the Community Documentation on getting it working, both times with success. So I'm at a bit of a loss here. Especially considering the system sees it under CAT as a USX2Y card, but the initializer says I don't have a compatible card. Anyone have any experience with this?

---

### Post by spanner510 on 2008-06-24
Hi,
This post won't help you really however,!
I had the same problems under gutsy but got my us122 to work eventually.
Ironically under Hardy my tascam us122 wont initialise either.
So it looks like tonight or tomorrow I'll be following the same routine as you!
I remember this though from gutsy the card does change its id in lsub each time and that is normal and you need to get things right before you get to this stage. There are 3 posts on this site that reference this and I found only 1 contained all the required info. 
Anyway I will post back when I have something of use to you! If you crack it before then please let me know that extra step it looks like I'll be needing it too!

---

