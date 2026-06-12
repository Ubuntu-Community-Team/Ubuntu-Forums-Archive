---
title: "MythTV-Hardware Question"
date: 2008-04-13
forum: Mythbuntu
---

### Post by Jeremy_bk on 2008-04-13
I'm thinking about building a MythTV box soon and I've got a question about tuners.  Here is the hardware I'm thinking about:
CPU:  1.8Ghz P4
Memory: 1gig
Sound Card: Creative Soundblaster Live 5.1
Video Card:  Geforce 6800 GS
Tuner:HauppaugeWinTV-PVR 500 and/or pcHDTV HD-5500
Here's my question.  I'm interested in recording HDTV and SDTV both so would it be possible to buy both the tuners listed above and have the PVR 500 encode SD channels and then have the HD-5500 encode the HD channels?  Would this be hard to setup? 
Thanks

---

### Post by volkswagner on 2008-04-13
> **Jeremy_bk said:**
> I'm thinking about building a MythTV box soon and I've got a question about tuners.  Here is the hardware I'm thinking about:
CPU:  1.8Ghz P4
Memory: 1gig
Sound Card: Creative Soundblaster Live 5.1
Video Card:  Geforce 6800 GS
Tuner:HauppaugeWinTV-PVR 500 and/or pcHDTV HD-5500
Here's my question.  I'm interested in recording HDTV and SDTV both so would it be possible to buy both the tuners listed above and have the PVR 500 encode SD channels and then have the HD-5500 encode the HD channels?  Would this be hard to setup? 
Thanks

Having multiple tuners SD/HD is not an issue when using supported hardware.  Your machine may be able to capture multiple SD recordings (pvr500), even while playing an SD recording.  I do however believe you are under powered to display HD content on that machine.

See here for min. spec guide.

[http://mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1]("http://mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1")

---

### Post by Weidbrewer on 2008-04-14
Here's my two cents on the pcHD-5500:

First off, it was designed and built for Linux, so it is detected installed and set-up with pretty much  no problems at all.  Also, i know that it's still going to be good to go after the digital change-over next year.


However, it does *not* have an on-board encoder, so you will be going off of your computer's specs.   


Now, once I got everything set up and running, I will say that I am very happy with this card.  Granted, I have not used it for any HD TV, since I have just standard cable running in to it, but for what I use it for, I like it.  If I were to do it over again, I'd probably go for something with more on-board horse-power.

---

### Post by tgm4883 on 2008-04-14
> **Weidbrewer said:**
> 
However, it does *not* have an on-board encoder, so you will be going off of your computer's specs.   


While you are technically correct, in reference to the question you are wrong.  The OP was asking about recording HD content with the pcHDTV 5500.  This content is already compressed into an mpeg2 stream and thus does not need to have a hardware encoder.  

Back to the original specs, you are definitly underpowered for displaying HD content.  You either need to get into the 3ghz range, or go dual core.  You can however record it just fine and play it back on a remote frontend (which will need to be more powerful, see above specs)

---

