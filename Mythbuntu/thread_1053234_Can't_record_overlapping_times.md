---
title: "Can't record overlapping times"
date: 2009-01-28
forum: Mythbuntu
---

### Post by Boppy3125 on 2009-01-28
I am trying to record both Daily Show and Colbert Report on Comedy Central.  The are back to back.  Originally, I just set them both up to record and everything worked great, except . . .  My wife complains that often times the Daily Show recording stops too early so she has to go to Colbert just to see the last thing from the Daily show.  So I set it to continue for an extra 2 minutes.  Now it shows a conflict with Colbert and doesn't record that.  I thought an overlap on the same channel was possible.  Is there something special I have to do?  All my searches come back with announcements that this is now available in .19 or something.  No apparent issues.  I am running .21 right from the Mythbuntu 8.04.01 install.  Any suggestions of what I can look at?

---

### Post by ian dobson on 2009-01-28
Hi,

You can configure start early/end late recording times in the recording profiles.

I use mythweb to configure myth so I'm not 100% sure where the options are in Myth Frontend.

Regards
Ian Dobson

---

### Post by Boppy3125 on 2009-01-28
Yes, I did that.  That is what caused the problem.  I told the Daily Show to end 2 minutes late, and that caused Colbert to be in conflict.  I thought life would be fine with this since they are the same channel.

---

### Post by ian dobson on 2009-01-28
Hi,

What tuner are you using? Digital (DVB-c,s,t) tuners support recording several programs at the same time (Multirec) as long as their all on the same multiplex.

Regards
Ian Dobson

---

### Post by jMon54 on 2009-01-29
I had a similar issue which I resolved by setting my system's clock to be more accurate.

---

### Post by Caps18 on 2009-01-29
Do you have two tuners?  Then again, I can't remember if it is smart enough to use the second tuner to record the later show.  I think it is.

---

### Post by Boppy3125 on 2009-01-30
It is a single digital tuner doing QAM off cable.  Setting the clock is dicey, if you have ever watched those shows, one flows right to the next with no commercials or anything.

I just thought I read that it should work now, since the tuner should be able to just keep recording that same channel, then the system should be able to use the relevant parts of that feed to populate the files for the individual shows.  The way I read it in the manual it should be automagic.  Since it isn't working, I was wondering if maybe I need to turn something on.  Or maybe there is more to the story of how this works that maybe someone out there can enlighten me on.

---

### Post by jMon54 on 2009-01-30
Here's another thought...  I've done this...  You can start the second program late.  The way you do this is by putting a negative value in for the "start early" amount.  So, you can end the first program late by say 2 minutes, and then start the second program early by "-2" minutes.  Try that - I think this should work to eliminate any overlap.

---

### Post by newlinux on 2009-01-30
> **Boppy3125 said:**
> It is a single digital tuner doing QAM off cable.  Setting the clock is dicey, if you have ever watched those shows, one flows right to the next with no commercials or anything.

I just thought I read that it should work now, since the tuner should be able to just keep recording that same channel, then the system should be able to use the relevant parts of that feed to populate the files for the individual shows.  The way I read it in the manual it should be automagic.  Since it isn't working, I was wondering if maybe I need to turn something on.  Or maybe there is more to the story of how this works that maybe someone out there can enlighten me on.

If it's a QAM digital tuner and you are recording on the same channel, use multi-rec. You can make that digital tuner more than one tuner that can record two shows (or more) at once off the same multiplex (which if they are the same channel, they are).

[http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex](http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex)

This will do what you want.

---

### Post by Boppy3125 on 2009-02-02
I don't know what I was thinking, sorry for mis-leading.  Comedy Central comes to me on and analog cable channel, not QAM.  So, this is coming in through my PVR-150.  I guess what I am understanding then is that this overlap idea only works with digital signals.  Well, I just updated my schedule for Colbert to start -2 minutes early.  It looks right when I update recording, but then when I go to the Upcoming Recordings page, it shows them to be in Conflict.  My guess is that as it gets more listings, it finds things to record, and that is the time it uses the rules to assign times and such.  Since I have 2 weeks worth of listings it will take me 2 weeks to see if this change works.  I think.  In theory.  Any other ideas, let me know, for now I will wait to see if this change affects the recordings.  Thanks for the input to date.

---

### Post by Boppy3125 on 2009-02-03
Also, thought I would share.  Read through the link from newlinux (thanks for that) and it seems that even with QAM, it is unclear if any given hardware will do the MultiRec properly.  So I just did a test.  I set up a recording of Leno on HD with 3 additional minutes, then set it to record Conan on the same channel directly following.  It showed a conflict, and once I got into the time of Conan, it was off my list of upcoming recordings.  So it seems in my case, I need to choose what to record and be careful and watch those conflicts.

---

### Post by newlinux on 2009-02-03
> **Boppy3125 said:**
> Also, thought I would share.  Read through the link from newlinux (thanks for that) and it seems that even with QAM, it is unclear if any given hardware will do the MultiRec properly.  So I just did a test.  I set up a recording of Leno on HD with 3 additional minutes, then set it to record Conan on the same channel directly following.  It showed a conflict, and once I got into the time of Conan, it was off my list of upcoming recordings.  So it seems in my case, I need to choose what to record and be careful and watch those conflicts.

What tuner are you using? how did you setup multi-rec? Did you delete the card and then re-add it and set it up multi-rec. I've got a few different QAM tuners and they all work fine with multirec. When multi-record is setup properly, mythweb will show that extra tuner as if you installed another tuner card.

---

### Post by Boppy3125 on 2009-02-03
> **newlinux said:**
> What tuner are you using? how did you setup multi-rec? Did you delete the card and then re-add it and set it up multi-rec. I've got a few different QAM tuners and they all work fine with multirec. When multi-record is setup properly, mythweb will show that extra tuner as if you installed another tuner card.

Huh?  I thought it was just magical in that Myth just knows how to use the single card.  I definitely need to re-read that link you posted.

I have a DViCI fusion hdtv5 RT and a PVR 150 for the analog stuff.  I have thought of setting up the DViCO to also try and record analog but it sounded dicey given no hardware mpeg encoder.

If that earlier linked article explains the setup for MultiRec then thanks again, if not I will be doing more googling on that.

---

### Post by Boppy3125 on 2009-02-03
Thanks.  I did a little research and it looks fairly straight forward now that I know what to look for.  I will try this out soon, but I just got my new video card today, so that will be my priority over the next few days.

This stuff is pretty fun, when it doesn't piss you off.:D

---

### Post by newlinux on 2009-02-03
Glad you got it. It really is just changing one setting when you first create the capture card. One of the cards I use is a dvico fusion 5 RT lite. Works fine in multirecord, and tha analog is fine too - although it requires direct connection to the sound card for sound. You will need to play V4L recording profile to get good quality analog playback from it - but mine looks almost as good as my pvr-150.

---

