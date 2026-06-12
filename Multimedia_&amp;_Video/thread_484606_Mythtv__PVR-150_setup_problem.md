---
title: "Mythtv / PVR-150 setup problem"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by smit0737 on 2007-06-26
I'm upgrading my Mythtv machine (stand alone frontend/backend) from Dapper to Feisty.  I previously had mythtv 0.20 working flawlessly with 2 PVR-150 cards.

Now, I'm getting the following message when exiting mythtv-setup:

Card 0 (type ) is set to start on channel 2, which does not exist.
Card 0 (type ) is set to start on channel 2, which does not exist.

Both cards are set as Card type: MPEG-2 encoder card (PVR-x50, PVR-500) in section "2. Capture cards" in mythtv-setup.  The Probed info on that page says: "Hauppauge WinTV PVR-150 [ivtv]" which seems correct.  Both are set to Default input:  Tuner 1.  I am running just standard definition cable.

In section "4. Input connections" I match up with two cards with the same Video source (a Zap2It account that correctly retrieves my account info).  I choose "Fetch channels from listing source" and the see the appropriate channels in "5. Channel Editor"

I have done a mythfilldatabase and can fire up mythbackend and mythfrontend just fine.  I can watch LiveTV no problem and can manually change channels, but when I schedule a recording, the recording fails, and I get the following message in my mythbackend messages:

2007-06-25 23:05:35.417 Channel(/dev/video0): SetInputAndFormat() failed
2007-06-25 23:05:35.417 TVRec(1) Error: Failed to set channel to 2.

I am TOTALLY stumped!  I've been through the setup several times and even reinstalled Feisty just to get a clean slate (in case I messed something else up) and get right back to the error on a clean install.  I would really appreciate any tips that anyone could offer.  Thanks!!!!!!!!!

---

### Post by smit0737 on 2007-07-01
I'm still stuck in the same spot, so I'll post a little bit more information to see if that helps anyone out.

- My install of 7.04 is standard.

- I am logged in as the user I created during the OS install to install mythtv from the repositories (just the mythtv and mythtv-themes packages).  When I first ran mythtv-setup, it added this user to the mythtv group.

- My mythtv library is on an LVM share and I have changed the owner and group of the mount point both to mythtv.

Thanks for looking at this post.  Hopefully, this info is helpful.  If there is anything else I can provide, I'd be happy to post it.

Also, if there is somewhere else I should post this, let me know and I'll give it a shot.  I looked around at mythtv.org but didn't see a forum like this one for asking questions.

Thank you!

---

### Post by newlinux on 2007-07-01
I've looked at this and I can't quite figure it out either. So you can watch TV just fine, but you can't schedule a recording? Can you schedule a recording on any tuner  (by specifying the tuner to record on)? Can you switch to each tuner then hit record? And you are able to tune to channel 2 on all tuners when watching liveTV?

Sorry I have more questions than help. But I do have something to offer - another place you can get help is:

[http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/)

Or you can go to:

[http://www.avsforum.com/avs-vb/forumdisplay.php?f=76](http://www.avsforum.com/avs-vb/forumdisplay.php?f=76)

Good luck

---

### Post by smit0737 on 2007-07-02
Thanks for looking at this.  I appreciate it.

I can watch live TV just fine, and I can record anything I'm watching live, but when I go through the scheduling process, the scheduling immediately fails.  If it's 8:00 and I schedule something at 8:30, it doesn't wait until 8:30 to fail, it conks out right away.

I'm following a couple of threads at the forums posted and haven't gotten anywhere yet, but I'll make sure I provide a link here if I get it resolved.  One of the other threads was due to a bad card setup ... the user chose a different frequency lineup (us-cable-hrc instead of us-cable) and got things to work.  I try all of the reasonable option in mythtv-setup and things don't change, but I'll keep at it.

Thanks again!

---

### Post by newlinux on 2007-07-02
You mentioned you have two tuners. You didn't answer whether or not you can do those things on both tuners. Can you do everything you said on both tuners (maybe one of them is off and that is what is causing your problem, typically the tuner first used for recording is not the tuner first used for viewing, so if one tuner has issues - the recording tuner - and one tuner is working (the one you typically watch) you'd have  the behavior you are talking about.  Something to check. When scheduling a recording pick a specific tuner and test, or when watching live tv switch tuners and record (press the y button while watching live tv to switch tuners). so you just want to make sure both tuners are working similarly. If you already have - my apologies - I just didnt get that from your response.

---

### Post by scoultas on 2007-07-12
I faced a similar problem (just upgraded from Dapper to Feisty, previously working just fine on mythtv 0.20).  I also have two input cards.

I found if I went to schedule a recording, but then through Recording Options changed 'Use any available input' to read 'Prefer Input 2 : Tuner 1' (in my particular instance), then the recording worked okay.

Then I examined the table 'cardinput' in the mythconverg database.  It had two entries for cardid 2, one had an input name of Tuner 0, another with an input name of Tuner 1.

Removing the 'Tuner 0' row (since I'd already specified Tuner 1 in mythtv-setup for that card) from the table made everything start working correctly again.

Hope that helps!

Steve

P.S. Others with a very similar looking problem have found they were missing the recording directory - but it sounds like your problem is more likely to be similar to mine!

---

### Post by Arothian on 2007-07-12
This is a little off topic but its a question I've been googling without any real answer. 

Do the Happauge PVR card work in PowerMacs? I have a PVR-350 that I would love to use in my powermac, but I really don't know if it would work or how much special configuration would be required.


Thanks

---

### Post by smit0737 on 2007-07-14
Thank you scoultas!  My cardinput table had the same entries (more or less) and when I deleted the rows I wasn't using for each card, everything started working again!!

---

### Post by scoultas on 2007-07-14
No problem, glad it worked for you too :-)

---

