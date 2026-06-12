---
title: "How is this for WEIRD???"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by djseto on 2007-04-13
I have been trying to get my CD drive to play a CD for days now. I have been chasing what I believe to be a DMA issue and tried everything the Ubuntu DMA help guide but with no luck. When I put a CD in and try to play it, it stutters badly. So tonight, I threw a DVD in and hit play. What happens, the DVD plays and stutters. So then I throw a CD back in and....holy crap, its playing CD's (and ripping them) just fine.

So, now I reboot my machine and what happens? The CD's stutter again. I throw a DVD back in, let it play for a few seconds, take it out, throw a CD in, and bingo, its reading CD's just fine.

Someone PLEASE tell me what I am missing here. I really dont want to resort to a "DVD Boot disk" to get my CD drive to play.

---

### Post by sloggerkhan on 2007-04-13
I agree that your issue sounds really weird.

---

### Post by djseto on 2007-04-17
bump for some help...

---

### Post by Inigo Montoya on 2007-04-17
[LIST=1]
[*]Is the driver working properly on another (whatever) operating system?
[*]Are there any (weird?) messages in /var/log/messages when you try to play any media on the driver?
[*]Do you have more info on the drive model/vendor asf.
[/LIST]

greetings
im

---

### Post by djseto on 2007-04-17
How do I know what driver its using? I assumed its using whatever Ubuntu installed.

---

### Post by Inigo Montoya on 2007-04-18
Sorry, it should have been
"Is the CD/DVD drive working properly on another (whatever) operating system?"

---

### Post by djseto on 2007-04-18
I only have ubuntu running on this box, but i pulled the drive out of my windows machine and it worked fine there.

This is the output of a ```
 sudo hdparm -I /dev/cdrom 
```

```

ATAPI CD-ROM, with removable media
        Model Number:       DVDRW DRW-5S163
        Serial Number:
        Firmware Revision:  YSG5
Standards:
        Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
        Supported: CD-ROM ATAPI-2
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: *sdma0 *sdma1 *sdma2 sdma3 sdma4 sdma7 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 (?)
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    PACKET command feature set
           *    DEVICE_RESET command
           *    Mandatory FLUSH_CACHE

```

---

### Post by Inigo Montoya on 2007-04-18
Did you install ubuntu using that drive?
Is the drive just slow when playing CD/DVD or are there issues while copying data from a CD to your PC too?
What application are you playing your CDs with?
(Sorry for all these questiones but there's no other way...)

---

### Post by djseto on 2007-04-19
I installed using this drive and had no problems. When I first boot up, CD's dont playback properly. It just sounds like crap and garbage. Same thing happens if I try to rip a song from it. Once I throw a DVD in, the playback of the DVD still stinks. It freezes for every second or so for a split second each time. After the DVD comes out, CD playback and ripping works fine. I could care less about DVD playback right now. I am playing and ripping songs using Sound Juicer.

---

