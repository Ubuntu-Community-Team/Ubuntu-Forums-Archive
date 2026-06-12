---
title: "PCMCIA sound card problem"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by mvarga on 2006-10-09
Hello.

The problem is as follows:

I've got a PCMCIA sound card, namely a Digigram VXPocket 440. ALSA supports this card. When pushing it to the slot, nothing happens.
dmesg log:

[17180430.988000] pccard: PCMCIA card inserted into slot 0
[17180430.988000] pcmcia: registering new device pcmcia0.0
[17180430.988000] vxpocket: too many cards found
[17180430.988000] snd-vxpocket: probe of 0.0 failed with error -22
[17180430.988000] vxpocket: too many cards found
[17180430.992000] snd-vxpocket: probe of 0.0 failed with error -22


Configuration:
Edgy 6.10 / Dapper 6.06 (same problem)
IBM T60 with Intel HDA audio.

Any tips?

---

### Post by ibanez88 on 2006-11-26
Hey there.  Maybe too basic a suggestion, but if you have another pcmcia socket do you get the same problem?  Also how many sound cards do you have connected at the same time?  Maybe there's an IRQ conflict.. try removing all other devices if you haven't already.

Sorry to report that I also cannot get my Digigram VXPocket V2 card to work using Linux.  I get a different error than the one you posted.  

See my threads here, maybe they'll help if there's something that you missed..

[http://ubuntuforums.org/showthread.php?t=194494&highlight=Digigram](http://ubuntuforums.org/showthread.php?t=194494&highlight=Digigram)
[http://ubuntuforums.org/showthread.php?t=112707&highlight=Digigram](http://ubuntuforums.org/showthread.php?t=112707&highlight=Digigram)

It appears that the Digigram cards are not that popular, and gaining insight into the problems with these cards is very difficult.  You might want to try the alsa mailing lists - although I haven't found a solution posted there other than to upgrade to the latest Alsa, which didn't change anything for me.. 

Good luck and please post your fix if you find one.  It is a real shame that these excellent sound cards simply do not seem to work, even though there are Alsa packages and firmware loaders for these specifically!  I even emailed Digigram the only help they offered was to use SUSE. (That didn't help either.)  

I've conceded that this is probably just over my head.  Please post any solution that works for you!  Best of luck.

---

