---
title: "Hardwarecheck"
date: 2010-01-12
forum: Mythbuntu
---

### Post by razon_de on 2010-01-12
Hi!

I'm going to set up a low cost computer with the following hardware.
I want to build a computer for watching and recording TV using mythbuntu for that.
While I watch TV, the current channel should be reccorded automatically. So if I press "stop" on my remote, the TV should stop, so that I can continue watching later.

So... my first question: Is this with the following hardware possible?

CPU: Intel Pentium 4 2.8 GHz
RAM: 1 GB
Motherboard: Fujitsu Siemens D1534
HDD: Maxtor 160 GB
Videocard: NVIDIA Geforce 2 MX 32 MB with s-video out

My last and second question: How good would the perfomance be while recording and watching TV?

Thanks! :)

---

### Post by laffinet on 2010-01-12
You're missing one important ingredient: a TV tuner card.

> While I watch TV, the current channel should be reccorded automatically. So if I press "stop" on my remote, the TV should stop, so that I can continue watching later

That's how mythtv works.

---

### Post by SiHa on 2010-01-13
> **laffinet said:**
> 
> While I watch TV, the current channel should be reccorded automatically. So if I press "stop" on my remote, the TV should stop, so that I can continue watching later 
That's how mythtv works.

Actually, it's been my experience that this is one area where Myth differs from other PVR's.

On my old Digifusion box, if I stopped watching, it carried on recording whatever channel I had last been on, so I could go to the menu, schedule a recording, come back and rewind the couple of minutes I'd missed.

MythTV doesn't seem to do this (by default, at least) if I stop watching TV, it stops buffering to disk, so if I come back to the same channel 5 minutes later there is nothing buffered, and I can't rewind. If this behaviour can be changed (maybe uncheck the 'Open DVB card on demand' box?), I'd be happy to hear about it. AFAIK, The only way to acheive this (kind-of) is to perss 'record' before stopping LiveTV. And then it will only record up to the end of the current show (or half-hour slot if you have no EPG)

---

### Post by razon_de on 2010-01-13
[SIZE=2]First recording and then stopping could be done by a script... so if I press button x on my remote, recording will start first and then the screen shall freece...

I'd like to buy a Medion/Creatix [/SIZE][FONT=Tahoma][SIZE=2]CTX929 (Main Chip:
SD1878/SHA, SAA7134HL, TDA10086HT) as TV tuner card.
[FONT=Tahoma]I have found some articles on the internet like the following one: [/FONT][/SIZE][/FONT][FONT=Tahoma][SIZE=2]
[/SIZE][/FONT][FONT=Tahoma][SIZE=2]> They are already auto detected as card=93, same as the md7134 triple
bridge #2, but are else of course slightly different cards :)So the TV tuner card should work with ubuntu.

The system requirements of that card are the following ones:

Pentium IV 2 GHz or Higher
128MB of system memory or higher
7200rpm hard disk or above CD-ROM or DVD-ROM drive
PCI/AGP VGA graphic card
Full-duplex sound card[/SIZE][/FONT]

---

### Post by SiHa on 2010-01-13
Ah, sorry got the wrong end if the stick. 

If you just want to freeze the screen, then 'Pause' will do that.

---

### Post by Caps18 on 2010-01-13
I think the hard drive is too small.  You can buy 1TB ones for under $100 now.

I would think about 2 tuner cards.  Maybe not today, but in the first 2-3 months, you will notice how much it helps.

---

### Post by hrobinson on 2010-01-13
The question that should be asked is what kind of TV is he recording, HD or Standard Def.

with Standard Def recording he can get away with what he has mentioned.  HD recording takes 7GB and Hour, so the 160gb will not last long.

Second I would recommend a two hard drive system.  a smaller one for OS and Mythtv and the larger one for recording video.  At least if the hard drive fills up, it will not put the operating system in trouble.

Sincerely,

Harold Robinson

---

