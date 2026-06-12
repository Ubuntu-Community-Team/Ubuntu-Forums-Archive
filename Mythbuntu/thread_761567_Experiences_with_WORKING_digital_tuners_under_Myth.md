---
title: "Experiences with WORKING digital tuners under Mythbuntu????"
date: 2008-04-21
forum: Mythbuntu
---

### Post by agamotto on 2008-04-21
I have been using Mythbuntu since the first version, and I am very confused about the digital tuner issue.  What experiences do you lot have with digital tuners in the U.S. that 'just work?' 
I currently have a Hauppauge WinTV HVR-1800 that does nothing, despite being told by tech support at Hauppauge that it works with  linux.  If it does, why can't Mythbuntu 7.10 detect the card?  Is this something that will work in the new release, or should I just send the card back to Hauppauge, and find someone else to spend money with?

---

### Post by tgm4883 on 2008-04-21
Get a pcHDTV 5500.  Works pretty good here. Not sure about that hauppauge card.

---

### Post by murchball on 2008-04-21
I have 2 HDHomeRuns, one for OTA and one for QAM. Works out of the box.

---

### Post by tgm4883 on 2008-04-21
> **murchball said:**
> I have 2 HDHomeRuns, one for OTA and one for QAM. Works out of the box.

I'd like to point out that the HDHomeRun is an excellent device, dual tuners, external(connects via ethernet), but with the addition of multirec, may not be needed anymore.

---

### Post by dan_hurst on 2008-04-27
Hi,
I managed to get my Hauppauge Nova T 500 running on 7.10 with the v4l-dvb drivers using this guide:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)


This page says you need the v4l-dvb drivers so maybe it would work for you?
   [http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1800](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1800)
Probably need different firmware though (maybe none at all).

No luck getting it to work in Hardy yet though.

---

### Post by GordonEndersby on 2008-04-27
The page of instructions for getting the Nova T 500's working doesnt work anymore for 7.10. I tried following it last week but something has changed in the V4L sources that wont let it compile properly with those instructions.
I couldnt be bothered at the time to work out what was wrong so installed 8.04 instead.
The Nova T 500 worked out of the box. I believe 8.04 has the latest sorted drivers.

Since I have installed 8.04 the cards have been more stable and perfectly usable so I would recommend the Nova T 500's for Mythbuntu 8.04.
Im running 2 cards with a pentium 4, 1gig ram and Nvidia 6000 series card.
The system isnt working very hard at all.

I have a couple of other issues to sort out, such as DVD playback/ripping and mytharchive, but digital reception and recording is great.

Gordon

---

### Post by Hugolp on 2008-04-28
I will have to disagree about the Nova-t-500. Its a great peace of hardware for the price, that was working fine in linux in edgy and gutsy (after adding the v4l part to the kernel), but its imposible to get to work in Hardy. I mean the two turners get detected automatically in hardy but then they work at random times. They connect and disconnect randomly and makes the whole thing unusable. No one has found the solution yet, as far as I know (please tell me I am wrong).

Hugo

---

### Post by murchball on 2008-04-28
In addition to the HDHomeRun, I can also now vouch for the HD 5500 for QAM. I've had one for a while, but was never able to get it to work (my bad, not due to any fault of the device). I just pulled it out and tried it on Hardy. Very simple setup. I also tried a Hauppauge HVR-1800 which I would not recommend at this point.

---

### Post by agamotto on 2008-04-28
:popcorn:

I can happily announce that with 8.04, the Hauppauge 1800 does get detected!  I am still not sure how to set it up however.

I need help with configuring Mythbuntu as far as using the 150 for recording/playing stuff off of analog cable, and using the 1800 to record OTA...

Any help with this will be greatly appreciated as I am not sure how to proceed from here.  I have created a second line-up in SD for the OTA digital, but how do I get the channels 'seen' by the digital tuner, and how do you sort out the inputs, etc...?

---

