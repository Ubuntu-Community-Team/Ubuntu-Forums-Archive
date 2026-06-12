---
title: "MicroSDHC 8GB Sandisk card problem"
date: 2010-06-05
forum: Multimedia Software
---

### Post by left 4 shred on 2010-06-05
One day my phone quit reading my MicroSDHC card and when I plug it into Ubuntu 10.04 it pops up a message saying

"Error mounting: mount exited with exit code 18: Error opening '/dev/sdb1': Read-only file system
Failed to mount '/dev/sdb1': Read-only file system"

When plugging it into windows it just doesn't get recognized. I've tried formatting it through Disk Utility but it doesn't allow me too. Do any of you know how to fix this in Ubuntu?

HPFS/NTFS (0X07) is it's partition type.

I'm trying a few things right now. If I figure it out I'll post what I did, until then any help would be much appreciated.

---

### Post by prshah on 2010-06-05
> **left 4 shred said:**
> 
HPFS/NTFS (0X07) is it's partition type.

I'd say this could be your problem. AFAIK, there is no phone that reads NTFS.

I suggest you try to format the microSD card through the phone. If the phone cannot format or see the microSD card, I would think the card is dead.

---

### Post by left 4 shred on 2010-06-05
Thats what I was afraid of. I won't be able to format it through my phone though, it doesn't recognize it when it's inserted. I'm not gonna give up yet though, I don't have money to buy another so I'm gonna look deeper into this.

---

### Post by wilee-nilee on 2010-06-06
Here is a link to the manufacturer with the card used as a search good luck.
[http://kb.sandisk.com/app/answers/list/kw/MicroSDHC%208GB%20Sandisk/r_id/101834/search/1](http://kb.sandisk.com/app/answers/list/kw/MicroSDHC%208GB%20Sandisk/r_id/101834/search/1)
Look at #4

---

### Post by left 4 shred on 2010-06-06
> **wilee-nilee said:**
> Here is a link to the manufacturer with the card used as a search good luck.
[http://kb.sandisk.com/app/answers/list/kw/MicroSDHC%208GB%20Sandisk/r_id/101834/search/1](http://kb.sandisk.com/app/answers/list/kw/MicroSDHC%208GB%20Sandisk/r_id/101834/search/1)
Look at #4

Thx I'll look at that now. I tried looking it up but I failed miserably for some reason. Prob because I'm reading like 20 diff pages.

---

### Post by left 4 shred on 2010-06-06
Alright I found out that my adapter was in the lock position (it didn't indicate which pos was lock and unlock) but it made no difference in Disk Utility for me. Everything was still filled with errors and everything. I did however decide to retry an old method I had done earlier now that I knew the card was unlocked. I put it in my digital camera and tried formatting. It worked, the card can be used again, thank you. 

I still have no idea what killed my card in the first place but at least now it's up and running again.

---

### Post by wilee-nilee on 2010-06-06
> **left 4 shred said:**
> Alright I found out that my adapter was in the lock position (it didn't indicate which pos was lock and unlock) but it made no difference in Disk Utility for me. Everything was still filled with errors and everything. I did however decide to retry an old method I had done earlier now that I knew the card was unlocked. I put it in my digital camera and tried formatting. It worked, the card can be used again, thank you. 

I still have no idea what killed my card in the first place but at least now it's up and running again.

I found that link in about 2 seconds on the net, the net is your best friend at times.;)

---

### Post by left 4 shred on 2010-06-06
> **wilee-nilee said:**
> I found that link in about 2 seconds on the net, the net is your best friend at times.;)

haha yeah, def. I just fail on certain websites at times. Def while under the effects of severe sleep deprivation :P

---

