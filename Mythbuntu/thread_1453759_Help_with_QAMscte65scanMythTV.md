---
title: "Help with QAM/scte65scan/MythTV"
date: 2010-04-13
forum: Mythbuntu
---

### Post by JeepFreak on 2010-04-13
OK, I've been searching until I'm in tears, so now I'm begging for somebody's help!

Comcast made the analog to digital switch in my area last week.  I downloaded scte65scan and ran it successfully.  I got a (pretty long) list of channels and imported them into Myth.  Everything looks to be setup perfectly with my card (Hauppauge 2250), Schedules Direct, and MythTV... except most of the channels don't tune in!  

I get a "partial lock" and a black screen on many (but not all) channels above ~35.  The exceptions include 40.1, 58.1, 58.2 (which are really free OTA equivalents to Fox and something else), a bunch of spanish channels also tune in, as well as some strange ones like the Hallmark Movie Channel on 500 (which I didn't know that I ever had before).

So... what the heck am I missing here?

Any help is very much appreciated!

Billy

---

### Post by dibuntux on 2010-04-14
Ehi Billy, welcome to digital switch... and the bitter fruits it brings...: take a look at my thread

[http://ubuntuforums.org/showthread.php?t=1332357](http://ubuntuforums.org/showthread.php?t=1332357)

 and possibly post there, so we can keep track of progress.

Hope it helps you.

Dave

---

### Post by AKADAP on 2010-04-14
At the very least it appears that Comcast intends to encrypt everything beyond limited basic. It may also be that Comcast intends to encrypt limited basic channels as well, leaving only analog limited basic unencrypted.
Comcast was supposed to make the switch on my system yesterday, but so far it has not yet happed, so I do not know for sure what they are doing.

The scte65scan program extracts the mapping between physical channel numbers and Comcast channel numbers that is used on the cheap boxes they give away to extended basic customers to allow them to view the channels on their analog TVs. These boxes are capable of decoding a less secure (read cheaper to implement) form of encryption than the pay channels. It is likely that Comcast has encrypted all but the OTA channels.

---

