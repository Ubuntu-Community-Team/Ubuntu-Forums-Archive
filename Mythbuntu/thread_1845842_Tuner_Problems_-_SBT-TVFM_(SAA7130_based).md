---
title: "Tuner Problems - SBT-TVFM (SAA7130 based)"
date: 2011-09-17
forum: Mythbuntu
---

### Post by ShadowEO on 2011-09-17
I've used all the insmod options, Got Video to work but the tuner modules won't set the frequency, It tries, in dmesg I see Tuner: set tv freq to 61.25 (Channel 3 for my STB) but the tda9887 module reports no change (this is with the relevant debug options on.). I've been wanting to get this working so I can move from a BeyondTV setup to a MythTV based one so I can have streaming to clients. This is obviously a problem with the drivers though as neither XawTV nor TVTime will tune either. If I restart into mythTV after starting BeyondTV's Live TV, it works so it's something with tuning frequencies in Linux. I have used all the Frequency maps available (us-cable, us-bcast, etc.), The softwares are all setup for NTSC, but I'm unable to do this. Searched everywhere for an answer.

I've used all the tuner types in the module configuration, none have worked. It doesn't seem to have an eeprom as it was not auto-detected. The Tuner card itself was a gift so I couldn't complain about it but I can't afford a new one with hardware encoding. So please, if anyone else has gotten this card to work, please tell me :)

---

### Post by nickrout on 2011-09-18
> **ShadowEO said:**
> I've used all the insmod options, Got Video to work but the tuner modules won't set the frequency, It tries, in dmesg I see Tuner: set tv freq to 61.25 (Channel 3 for my STB) but the tda9887 module reports no change (this is with the relevant debug options on.). I've been wanting to get this working so I can move from a BeyondTV setup to a MythTV based one so I can have streaming to clients. This is obviously a problem with the drivers though as neither XawTV nor TVTime will tune either. If I restart into mythTV after starting BeyondTV's Live TV, it works so it's something with tuning frequencies in Linux. I have used all the Frequency maps available (us-cable, us-bcast, etc.), The softwares are all setup for NTSC, but I'm unable to do this. Searched everywhere for an answer.

I've used all the tuner types in the module configuration, none have worked. It doesn't seem to have an eeprom as it was not auto-detected. The Tuner card itself was a gift so I couldn't complain about it but I can't afford a new one with hardware encoding. So please, if anyone else has gotten this card to work, please tell me :)

Is this card supported in linux?

What version of mythtv do you have?

What version of ubuntu?

---

### Post by ShadowEO on 2011-09-18
> **nickrout said:**
> Is this card supported in linux?

What version of mythtv do you have?

What version of ubuntu?

Yes the card is supported by the SAA7134 driver.
Card = 42

MythTV 0.24.1

Ubuntu: MythBuntu 11.04

Like I said, If I restart (not power off, a warm restart) after setting the channel using the Windows applications, I can see the video and sound in XawTV/TVTime. However if I cold boot into Mythbuntu and attempt to view using the aforementioned programs, the channel cannot change and I see nothing but static. It seems as though the tda9887 and tuner modules aren't communicating with the card correctly.

The card is in the cardlist for v4l/v4l2's SAA7134 module. I have tried all the commands like below:

modprobe tuner debug=1
modprobe saa7134 card=42 tuner=17+: I've used every card and tuner number that seems compatible, IR Remote only works on Manli MuchTV type cards but tuner doesn't work, SBT-TVFM as the card number has the tuner work with the problem I already mentioned.

EDIT: I was thinking about trying one of the older versions that has the V4L IOCTLs still in the kernel, can someone point me to a place I can download old versions of MythBuntu?

---

