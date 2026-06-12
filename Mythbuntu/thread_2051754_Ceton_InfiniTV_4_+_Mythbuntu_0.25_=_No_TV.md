---
title: "Ceton InfiniTV 4 + Mythbuntu 0.25 = No TV"
date: 2012-09-01
forum: Mythbuntu
---

### Post by Anaximander Thales on 2012-09-01
I have installed Mythbuntu twice, installed the linux drivers twice.

The first time was to see mythtv and to begin getting the settings put in place for when my cable card finally arrived.

I spent a day once the card arrived to get the pairing only to find out that I needed a replacement Ceton card.

Replacement came, installed, paired.  Could not get Live TV to work.  Found out there was a way to display a channel on mplayer.  Figured this was my best bet to see if I was receiving a signal before delving into settings in MythTV.  Couldn't get anything to play through mplayer.

Figured that maybe it was my messing around with things, so I'd reinstall.  Got Mythbuntu back up, got the drivers installed.  Verified that I was still authenticated (figured I would be from all that I've seen on the web).  Still am unable to display anything through mplayer.

I use: mplayer -cache 8192 /dev/ceton/ctn91xx_mpeg0_0

So, off to investigate.

I have nothing to go on other than the tuner resolver is disabled, in fact everything is unavailable or zero on the whole tuning adapter page, and I get 'no programs' when I go to Tuner under one - four on the Ceton InfiniTV web manager.

Help! Please?  What information is needed?

Thank you,
AT

---

### Post by Akriss on 2012-09-02
The tuning adapter page is telling me that the "TA" is not hooked up or not working.

However, does your cable Co. actually require a "TA" to be used with CC tuners?

If yes then thats where my knowledge on setting up a Ceton stops, my cable Co. does not require a "TA".

---

### Post by nickrout on 2012-09-02
1. There are a lot more ceton users on the mailing list. You could both try there.

2. I assume you have read this: [http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4)

---

### Post by Akriss on 2012-09-02
> **nickrout said:**
> 1. There are a lot more ceton users on the mailing list. You could both try there.



The mailing list in my morning read with coffee.  :D

I've had my 2 Ceton cards working very well under Mythbuntu 12.04 since its release. 

I just like to help when I can.

---

### Post by Anaximander Thales on 2012-09-07
[QUOTE=AKRISS]The tuning adapter page is telling me that the "TA" is not hooked up or not working.

However, does your cable Co. actually require a "TA" to be used with CC tuners?

If yes then thats where my knowledge on setting up a Ceton stops, my cable Co. does not require a "TA". [/QUOTE]


[QUOTE=nickrout]
1. There are a lot more ceton users on the mailing list. You could both try there.

2. I assume you have read this: [http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4)[/QUOTE]

Thank you both so much for your responses.  This was really a "new to cableCards/watching tv through the computer" issue; I wasn't sure what to expect, nor had any idea what to look for.  I'll go into detail so others running into the same problems with the same level of MythTV experience can get some benefit.

I decided to just go with Windows since Ceton supports it through regular channels and I was finding more support information related to my issue in other forums.  That was where things started clicking.  Even in windows, the TA was still disabled.  However, I just decided I was going to go through all channels to see if even one was working. This was my 'Ah-ha' moment.  I saw that I was in fact getting in some channels.  I got 100 to tune in (this is via the webpage where you can choose 'program' and 'channel' and [QAM256, QAM64, NTSC-M] (I can't remember how those are referred to)), 300, some of the HD channels in the 900 range.  So, okay -- this is working.  I'm happy.  Let's try MB and see if it still works.

So, I went back with MB 12.04 (Oh, how I love the fact that I have so much space left on my 32G SSD - on windows I had less 7 G left).  I started testing with the channels I knew were coming in and things were working.  But not everything I expected to be working.  Called Knology, my CC.  Spoke with them for a 30 or so minutes.  Nothing working, but did set an appt for a tech to come out.  This led to more answers.  Unfortunately, he knew nothing about setting up a computer; it's sometimes the blind leading the blind in cases like this, but I prodded and asked questions and was able to piece together the information.  No, my CC doesn't require a TA.  That said, on Knology Cable, nothing below channel 65 is being transmitted in digital; the channels that I was attempting to connect to that led to my initial post on here.  The tech told me that within a year, those would be broadcast in digital.

nickrout -- yes, I hit that page multiple times.  It was baffling because that seems to be talking about MythTV 0.24 and how to set up the ceton card with it.  The article talks about setting each Device to RTP. However, Apparently there were some great strides in MythTV 0.25 because in my MythBackEnd setup, I enter the IP, then 0 for the device, and 0 for first tuner. Then apparently, magic occurs (best way for me to describe it right now since I'm so much a novice with MythTV) and the other 3 tuners can be accessed.  But, that's just my take on it right now -- I haven't even begun to attempt to record programs or set up schedules.  So, maybe I need to setup 3 more devices with the respective tuners and just don't know it yet.

So, most everything is now solved.  I am able to get channels, though I'm running in to that little hiccup on a channel or two hanging because they don't lock in. I've successfully navigated around that and know what to do, though it is inconvenient to reset the starting channel, and figure editing out those channels will be sufficient.  I figure that editing the MySQL back end (after a back-up of course) will probably be the quickest way to remove the unavailable channels.  I'm well on my way of having a nice little media server.

---

### Post by speed32219 on 2012-09-11
That page should be removed from a future posting!  I mentioned 3-4 months ago that it was outdated and only refers to mythtv .24.  We are in later releases now with .25 and .26.  So please refrain from posting garbage links to old outdated information, if you do not have the products actually working.  It is really no help to anyone and the person that has that website should take it down. IMHO

---

### Post by nickrout on 2012-09-12
> **speed32219 said:**
> That page should be removed from a future posting!  I mentioned 3-4 months ago that it was outdated and only refers to mythtv .24.  We are in later releases now with .25 and .26.  So please refrain from posting garbage links to old outdated information, if you do not have the products actually working.  It is really no help to anyone and the person that has that website should take it down. IMHO

As there is only one link posted in this thread, I take it you are referring to the one I posted, ie [http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4) . I am sorry if it is the wrong one.

Instead of your snarky post, why don't you do something useful like:

[LIST=1]
[*]posting the correct wiki link; or
[*]updating the wiki page. (that's what a wiki is all about, an opportunity for cleverer people than the rest of us to post useful information, and change outdated stuff.
[/LIST]

---

