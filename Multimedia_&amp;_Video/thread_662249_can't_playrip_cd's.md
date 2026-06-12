---
title: "can't play/rip cd's"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by Benjiduncan on 2008-01-08
I cannot play any songs off a cd. Any software I use recognizes the files on the cd by name, but when they are played I get a bunch of screeching noise.

This is the case with every media player I try except for VLC.

Physically the cd can be ripped with any of the programs used for ripping/extracting but I get the screeching noise when I try to play the ripped file, even on VLC, regardless of the output file extension. VLC does not rip cds. I need to be able to rip them.

---

### Post by Benjiduncan on 2008-01-08
bump

---

### Post by hugo1967 on 2008-01-09
I've been having the same problem and no luck finding a solution . . . or even anyone else with the same problem.  I was playing/ripping just fine in Feisty, but Gutsy seems to have broken something. 

I get screeches when playing or ripping with SoundJuicer   I can play CDs perfectly with XMMS or Grip (so I know it's not hardware or the CD) but while ripping, Grip returns 'read drift' and the ripped files (both .wav and .ogg)  just give the screeching noises. 

maybe a scsi generic problem? cdrecord -scanbus returns:

scsibus1001:
        1001,0,0 100100) 'LITE-ON ' 'DVDRW SHM-165H6S' 'HS06' Removable CD-ROM

but I don't know how to map this to a /dev/sg?  I installed sg3_utils and ran sg_ident -l, and none of the /dev/sg* seemed to be mapped to scsibus1001.

I can play .mp3, .ogg, and .wav files ripped in Feisty or earlier just fine using Rythmbox and other players, using both PulseAudio and ALSA

---

### Post by Benjiduncan on 2008-01-09
Grip doesn't even work for me in playing the cd's, the only program that seems to work playing the cd's is VLC. This would be fine if VLC ripped cd's but it doesn't.

I should note that I also have a LITE ON drive. And that along with this problem I have also been unable to burn cd's or dvd's. I can record data with my drive and the drive can read the contents of any disk, just not play them. The drive was installed when I had windows on this computer.

---

### Post by Benjiduncan on 2008-01-09
Hugo,

I just went and installed an old cd drive of mine into my computer and the drive worked. It played cd's and allowed me to rip them without the distorted sound. So the problem is definitely LITE ON. Perhaps the LITE ON website has some information.

---

### Post by hugo1967 on 2008-01-09
Hmmmm - that's interesting.  I was able to rip CD's from this drive in Edgy and Feisty so I'm not convinced it's the drive itself . . . maybe the interface is broken . . . I'll see what else I can dig up so stay tuned.

---

### Post by deadgobby on 2008-01-09
You CD drive just  may need a old fashion TLC. Thus it may require to be clean. The lens in the drive may be dirty and it happens. A little dust or scuff can cause the device not to work.

---

### Post by hugo1967 on 2008-01-10
I don't see why the drive would PLAY without any problem but not RIP if it were a dirty lens or mechanical problem.  Also, it screeches EVERY TIME while playing with SoundJuicer in the exact same way as the ripped files, and it plays perfectly EVERY TIME when playing with Grip or XMMS.  Seems like its gotta be the software interface.

Dunno about the others, but I know that Grip uses the /dev/cdrom interface to PLAY the music but uses (via cdda2wav/cdparanoia) a /dev/sg* interface to RIP, which is why I'm thinking the problem may be scsi interface related.  Or it could be an unusual LITE-ON implementation of the software interface that's no longer supported in Gutsy. . . but the drive is only a year old . . .

 BTW BenjiDuncan, what Ubuntu version are you running?

Gotta figure this out soon, my buddy wants his Miles Davis CDs back . . .

---

### Post by hugo1967 on 2008-01-13
Benjiduncan if you're still listening, try the workaround at [https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/134640](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/134640).

I've posted a new thread since this one seems to be dying.
[http://ubuntuforums.org/showthread.php?t=666109](http://ubuntuforums.org/showthread.php?t=666109)

---

### Post by Nero_Flint on 2008-01-13
> **Benjiduncan said:**
> bump

Is that what you did to your head? No wonder you acted out as you did. 3 hours and then a kick. Bumpety, bumpety, bump, bump, bump is done on forums by people who have no patience. It also makes people who would have helped not help you.

Unless your hard drive is bubbling and melting onto your new hardwood floor just relax.

---

