---
title: "Mythmusic: CD stutter and gapless playback solved in 0.22?"
date: 2009-12-07
forum: Mythbuntu
---

### Post by joho500 on 2009-12-07
In mythtv 0.21 I couldn't get mythmusic to play an audio CD without stuttering every 15 seconds. Does anyone know whether this is solved in 0.22?
The same goes for gapless playback of MP3's. Does this work in 0.22?

Thanks in advance.

Joost

---

### Post by hughes532001 on 2009-12-07
I have the same problem.  I've been trying to solve it for some time.  There does not seem to be much on a "google" search for this problem.

I have tried latest build of Mythbuntu and on a fresh install of Karmic and adding MythTV.

When playing a CD the drive stops and starts at abot 15 second intervals.  Playing outside of MythTV using any application (VLC Rhythmbox etc) works fine

I have not tried a DVD yet.

I'll keep looking and trying.

Trevor

---

### Post by joho500 on 2009-12-07
I found  a post that suggested setting the readahead of the cdrom player to 2048kb with hdparam. Did that but it didn't help. I'm out of ideas.

Hope someone else knows a solution. Perhaps the mythtv devs can make mythmusic use a buffer that would also help with gapless playback?

Cheers,
Joost

---

### Post by hughes532001 on 2009-12-09
Hi Joost
I saw that bit of advice thanks  for letting me know, I won't bother to try that.
Are you using SATA CD/DVD player as well.

If you don't want TV playback I can recommend XBMC it works brilliantly on Karmic with LIRC to give a great media player with remote control.

It plays cds and music files and shows pictures.


([http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)) is a simple guide.

Regards
Trevor

---

### Post by joho500 on 2009-12-10
Hi Trevor,

I've been looking at XBMC a while ago but as you say it doesn't have TV playback and I do use that. Thanks.

My CD-Rom drive is an IDE drive.

I hope someone has a solution for our problem.

Cheers,
Joost

---

### Post by joho500 on 2009-12-23
bump. Anyone?

---

### Post by am4c130d on 2009-12-23
Reported as a bug already (not by me - though I have the same issue).

[http://svn.mythtv.org/trac/ticket/7784](http://svn.mythtv.org/trac/ticket/7784)  this seems pretty wide spread.

Re DVD playback, there was a similar issue with .21 and into .22, this has been fixed in SVN [http://svn.mythtv.org/trac/ticket/7605](http://svn.mythtv.org/trac/ticket/7605) - and the fix is in the daily builds from mythbuntu...

Hope that helps.

---

### Post by joho500 on 2009-12-24
Thanks for your info on the bug report. Hopefully the devs find a solution for the problem.

Joost

---

### Post by psylencer on 2010-03-16
> **joho500 said:**
> Thanks for your info on the bug report. Hopefully the devs find a solution for the problem.

Joost
Honestly, this bug really ***** me off, especially given the fact MythTV is supposed to be an all in one solution.  Im using .23.  CD playback works fine with a 2.5yr old DVD Pioneer DVD Burner.  As soon as I plug in a brand new LG drive or ASUS drive 15 second buffer underrun issues appear again.

MythTV is touted as the Mythical All In one solution, however it seems from the importance and time its taking them to figure this out once and for all, they have truely dropped the ball and lost sight of their motto.

Im not unique here either...  I'd be suprised to find many people if any who don't have this problem - using new hardware.

One would think CD Playback is a pretty important feature for an all in one "mythical" solution.  

It suprises me the amount of time and importance Myth developers spend on resolving issues which affect minority configurations, while completely ignoring or marking as "unimportant" major problems like this.

---

### Post by fredwong on 2010-03-27
I got the same problem too. But according to the comment by robertm in ticket [http://svn.mythtv.org/trac/ticket/7784]("http://svn.mythtv.org/trac/ticket/7784"), the issue is **minor**. One does not understand how a stuttering CD playback issue on a **media centre** can be considered minor :-x. They have somehow considered the issue to be so minor that they are not going to fix it in the very short term. I have a generic IDE drive. I think the issue only relates to IDE drives. I wonder whether psylencer's new drives are IDE or SATA.

---

### Post by nickrout on 2010-03-28
> **psylencer said:**
> Honestly, this bug really ***** me off, especially given the fact MythTV is supposed to be an all in one solution.  Im using .23.  CD playback works fine with a 2.5yr old DVD Pioneer DVD Burner.  As soon as I plug in a brand new LG drive or ASUS drive 15 second buffer underrun issues appear again.

MythTV is touted as the Mythical All In one solution, however it seems from the importance and time its taking them to figure this out once and for all, they have truely dropped the ball and lost sight of their motto.

Im not unique here either...  I'd be suprised to find many people if any who don't have this problem - using new hardware.

One would think CD Playback is a pretty important feature for an all in one "mythical" solution.  

It suprises me the amount of time and importance Myth developers spend on resolving issues which affect minority configurations, while completely ignoring or marking as "unimportant" major problems like this.

I suggest you get a refund.

Why not rip your music and play the resulting files?

---

### Post by nickrout on 2010-03-28
> **fredwong said:**
> I got the same problem too. But according to the comment by robertm in ticket [http://svn.mythtv.org/trac/ticket/7784]("http://svn.mythtv.org/trac/ticket/7784"), the issue is **minor**. One does not understand how a stuttering CD playback issue on a **media centre** can be considered minor :-x. They have somehow considered the issue to be so minor that they are not going to fix it in the very short term. I have a generic IDE drive. I think the issue only relates to IDE drives. I wonder whether psylencer's new drives are IDE or SATA.

you are entitled to the same refund :)

honestly you are all complaining, but have we seen a log file from any of you?

---

### Post by fredwong on 2010-04-20
Sorry to sound like we are complaining. I have been waiting for this very patiently for a very long time since I upgraded to the 0.22. You obviously have no idea how frustrating it is to not be able to listen to a music CD without first ripping it to the hard disk. This is supposed to be a media box if it doesn't do a simple task as playing music CD what use is it. As to the log file, how many log files do you need. I think one log file posted to the original issue 7784 is plenty enough. You can have a hundred of log files from different sources and they will simply contain the same thing: "WriteAudio: buffer underrun". What more do you need?

---

### Post by iamlindoro on 2010-04-20
> **fredwong said:**
> I got the same problem too. But according to the comment by robertm in ticket [http://svn.mythtv.org/trac/ticket/7784]("http://svn.mythtv.org/trac/ticket/7784"), the issue is **minor**. One does not understand how a stuttering CD playback issue on a **media centre** can be considered minor :-x. They have somehow considered the issue to be so minor that they are not going to fix it in the very short term. I have a generic IDE drive. I think the issue only relates to IDE drives. I wonder whether psylencer's new drives are IDE or SATA.

When the ticket was turned into a stage to complain about ticket administration, the developers politely asked that the discussion move to the dev list, lest the rapidly-spiralling-out-of-control ticket be locked.  That request was immediately ignored, so the ticket was locked.  On top of that, not even a peep on the dev list (which would have been the appropriate forum) about the issue.  If anyone cared that much about it, they would have heeded the very polite request that discussion move to the correct place.

Myth has less than a dozen active devs.  Of those dozen, four have new babies in the house.  Of the eight that remain, one has anything to do with the audio code.  That one spent the greater part of the last two years rewriting Myth's UI, only to have people loudly and rudely complain that they couldn't press right to get a context menu any more, or that they missed their ancient themes and demanded that someone rewrite them for the new UI, or other random, rude, useless, hurtful quibbles.  In short, the Myth devs are human beings too, with human lives and human problems, and we'll be happy to get to your issue when our lives, wives, children, free time, and interests allow for it.  For what it's worth, the issue seems less important all the time when we see threads like this.

---

### Post by fredwong on 2010-04-21
I believe humble pie is on the menu here :redface:. My apology for being rude and impatient. I have been a Linux for a long time and fully understand that the developers are not being paid for what they are doing. I myself have also just had a baby who is now 9 months old and know how busy the MythTV developers must be. I must say that I was waiting very patiently for the fix to come through anytime because the ticket was being looked into. What threw was that suddenly the ticket was closed and it indicated that it would not be investigated further. My thought was that why did they have to fix something that was not broken and why did they say that it was already fixed when it clearly was not. Anyway you get the gist of what I am saying. I still think MythTV is an excellent piece of software and my applaud to all the selfless Myth developers who have poured in numerous hours to make MythTV what it is in their free time. I wish I could contribute to it but time is always an issue :).

---

### Post by iamlindoro on 2010-04-21
The ticket is still open, and thus still up for fixing.  It's locked to prevent offtopic discussion, that's all.  It'll get solved once the right people have the time and inclination to work on it.  Thanks for your understanding.

---

### Post by jbman on 2010-04-21
Someone should put a bounty on mythmusic and see if anyone is keen to drop everything and smash out the ideas and fixes that have been talked about.

I am happy to throw some money into mythmusic and mythtv in general for that matter.

---

### Post by iamlindoro on 2010-04-21
MythMusic is already receiving a full rewrite.  With any luck, some portion of the rewrite will be merged for .24 or on the (hopeful) outside, .25.

---

### Post by carchaias on 2010-11-09
Sorry, but
[http://svn.mythtv.org/trac/ticket/7784](http://svn.mythtv.org/trac/ticket/7784)
says this problem is solved. But it still occurrs in my .23 release. Is there a patch or thelike to solve this?

---

### Post by nickrout on 2010-11-09
The ticket says the fix was merged in trunk 4 months ago, so i don't think it will be in 0.23.

---

### Post by carchaias on 2010-11-10
I, read that, but what does it mean "..merged to trunk..."Do i have to wait for a new Version, is that repaired by automatic updates from ubuntu, is there a patch or bugfix to install or......? My question:" How to use this fix?"

---

### Post by nickrout on 2010-11-10
"trunk" is the experimental code that (at that stage) was destined to be 0.24. So in short you can:

(a) check whether the fix was backported to 0.23-fixes, if so update to the latest 0.23-fixes using autobuilds

(b) move to 0.24 using autobuilds, bearing in mind it is still pre-release and you MAY have some problems

(c) wait for 0.24.

---

### Post by carchaias on 2010-11-10
Thanks for the Info.

---

### Post by carchaias on 2010-11-10
I changed to auto daily builds in Mythbuntu and the fault is gone. Thanks to all, now i've my perfekt multimedia station...:guitar:

---

### Post by nickrout on 2010-11-10
I think other users would be interested to know what version you updated to.

[LIST=1]
[*]So, in autobuilds, did you choose 0.23 or 0.24?

[*]What version did you in fact end up with? ```
dpkg -l mythtv-frontend
``` will tell you.
[/LIST]

---

