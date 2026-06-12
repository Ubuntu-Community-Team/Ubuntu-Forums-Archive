---
title: "Hauppauge 1600 and ATSC OTA"
date: 2009-04-08
forum: Mythbuntu
---

### Post by scott_g on 2009-04-08
Hi,

I have a Hauppauge 1600 card running on Ubuntu 8.04 with a mythtv frontend/backend setup.  I've compile the drivers manually (as they aren't part of the kernel until the 8.10 release), and have the standard cable working with mythtv.  However, now I'm trying to get the ATSC portion of the card to work, using an over the air signal.  I've been Googling for a while, and think this is possible, but I can't seem to get it to work.  Specifically, I've set up the card as a DVB card (like [these]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600") instructions say), then added a video source and input connection.  However, it cannot find any channels when I complete a scan. 

Does anyone have any ideas?  Or know if this is possible?  I can post anything that is needed, I just don't know what this would be right now.

Thanks in advance,
Scott

---

### Post by klc5555 on 2009-04-08
> **scott_g said:**
> Hi,

I have a Hauppauge 1600 card running on Ubuntu 8.04 with a mythtv frontend/backend setup.  I've compile the drivers manually (as they aren't part of the kernel until the 8.10 release), and have the standard cable working with mythtv.  However, now I'm trying to get the ATSC portion of the card to work, using an over the air signal.  I've been Googling for a while, and think this is possible, but I can't seem to get it to work.  Specifically, I've set up the card as a DVB card (like [these]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600") instructions say), then added a video source and input connection.  However, it cannot find any channels when I complete a scan. 

Does anyone have any ideas?  Or know if this is possible?  I can post anything that is needed, I just don't know what this would be right now.

Thanks in advance,
Scott

My own experience with the digital half of the 1600 (on QAM 256 cable) was that the 1600 had such severe signal-strength issues that I finally gave up on it altogether, except as an analog-only solution, and supplemented the card with a cheap AverMedia for digital use.

You might try using the scan app from dvb tools to produce a channels.conf, as described here: [http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada](http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada))  I found that I could get a couple of channels that way. Using a drop amp to boost the signal gave me a handful more, but still barely a third of what I should have been getting, which is why I went to a different digital card.

Good luck.

---

### Post by scott_g on 2009-04-08
Ok, good to know.  I tried installing the scanning utility, and scanned through all the pre-set frequencies for the US, with no luck.  This was more of a; I wonder if this would work?  type of experiment, so I'm not that upset.  If you couldn't get many channels from a cable source, then my selection of over the air channels would be a lot less, I would figure.

If anyone has other ideas, I'd be happy to try though.

Thanks a lot,
Scott

---

