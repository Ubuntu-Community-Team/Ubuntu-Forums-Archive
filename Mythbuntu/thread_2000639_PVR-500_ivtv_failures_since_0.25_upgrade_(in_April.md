---
title: "PVR-500 ivtv failures since 0.25 upgrade (in April)"
date: 2012-06-09
forum: Mythbuntu
---

### Post by anonymousdog on 2012-06-09
BE/FE (with remote FEs too) on MB 10.04 x86_64 with MythTV 0.25 (currently 2:0.25.0+fixes.20120608.648f0ae-0ubuntu0mythbuntu1) using one PVR-500 connected to Dish Network receiver using tuner0/S-Video1 and an OTA digital receiver feeding NTSC to tuner1/Composite1:

Ever since upgrading to 0.25 a few days after release, I've had never ending trouble with the PVR-500 becoming unresponsive with I/O errors at random times but becoming increasingly likely the longer the BE goes between restarts (and/or ivtv driver reset [with rmmod and modprobe]).  This creates 0-bit recordings in MythTV and breaks LiveTV.  Backend logs show 'StartEnconding Failed' and 'socket went unconnected' errors.

If I quit MyhthTV frontend and stop the backend (and wait for threads to exit), 'cat /dev/video0 > ./test.mpg' also produces 0-bit test.mpg (and cat does not exit cleanly).  v4l2-ctl commands will error out.

Once I do a 'sudo rmmod ivtv' and 'sudo modprobe ivtv', the card will work properly for a random period of time (and may even fail upon its very first use by MythTV).

Within MythTV, no particular pattern of channel changes or other usage scenarios seems to impact the likelihood of the card failing at any particular time; LiveTV is no more likely to create a problem than scheduled recordings.  All capture cards (not just on the BE) have been deleted and reconfigured several times (with at least one iteration of removing all cards, all video sources, and rebuilding channels from scratch).  In fact, I've gotten into the practice of removing and reconfiguring the capture cards after each and every MythTV update...their tuning timeout is the 12s default.  I have tried running with ONLY the /dev/video0 (connected to Dish) configured as well (to no help).

Outside of MythTV I have not been able to bork the card; no amount of channel changes, v4l2-ctl commands, connects/disconnects with vlc/mplayer/whatever elicits the symptoms.

This began immediately on upgrade and has never stopped malfunctioning on any release since.

I've searched and probed:
It is exactly the symptoms noted in this (now closed) bug: [http://code.mythtv.org/trac/ticket/9846](http://code.mythtv.org/trac/ticket/9846), except that it is not confined to LiveTV.  It appears this bug **may** be a duplicate of 9830 which has been fixed, and the fixes are in the version I'm using.  It also may be related to 9177 which is now closed as invalid.

I have no idea how to proceed in debugging this issue other than to try the card in a totally fresh 10.04 or 12.04 installation, but I don't relish that thought much.

Any ideas?

---

### Post by nickrout on 2012-06-09
> **anonymousdog said:**
> BE/FE (with remote FEs too) on MB 10.04 x86_64 with MythTV 0.25 (currently 2:0.25.0+fixes.20120608.648f0ae-0ubuntu0mythbuntu1) using one PVR-500 connected to Dish Network receiver using tuner0/S-Video1 and an OTA digital receiver feeding NTSC to tuner1/Composite1:

Ever since upgrading to 0.25 a few days after release, I've had never ending trouble with the PVR-500 becoming unresponsive with I/O errors at random times but becoming increasingly likely the longer the BE goes between restarts (and/or ivtv driver reset [with rmmod and modprobe]).  This creates 0-bit recordings in MythTV and breaks LiveTV.  Backend logs show 'StartEnconding Failed' and 'socket went unconnected' errors.

If I quit MyhthTV frontend and stop the backend (and wait for threads to exit), 'cat /dev/video0 > ./test.mpg' also produces 0-bit test.mpg (and cat does not exit cleanly).  v4l2-ctl commands will error out.

Once I do a 'sudo rmmod ivtv' and 'sudo modprobe ivtv', the card will work properly for a random period of time (and may even fail upon its very first use by MythTV).

Within MythTV, no particular pattern of channel changes or other usage scenarios seems to impact the likelihood of the card failing at any particular time; LiveTV is no more likely to create a problem than scheduled recordings.  All capture cards (not just on the BE) have been deleted and reconfigured several times (with at least one iteration of removing all cards, all video sources, and rebuilding channels from scratch).  In fact, I've gotten into the practice of removing and reconfiguring the capture cards after each and every MythTV update...their tuning timeout is the 12s default.  I have tried running with ONLY the /dev/video0 (connected to Dish) configured as well (to no help).

Outside of MythTV I have not been able to bork the card; no amount of channel changes, v4l2-ctl commands, connects/disconnects with vlc/mplayer/whatever elicits the symptoms.

This began immediately on upgrade and has never stopped malfunctioning on any release since.

I've searched and probed:
It is exactly the symptoms noted in this (now closed) bug: [http://code.mythtv.org/trac/ticket/9846](http://code.mythtv.org/trac/ticket/9846), except that it is not confined to LiveTV.  It appears this bug **may** be a duplicate of 9830 which has been fixed, and the fixes are in the version I'm using.  It also may be related to 9177 which is now closed as invalid.

I have no idea how to proceed in debugging this issue other than to try the card in a totally fresh 10.04 or 12.04 installation, but I don't relish that thought much.

Any ideas?

Try deleting all your tuners in mythtv and adding them again. Don't worry you won't need to re-tune or anthing, once you have added them again simply reconnect them to their sources.

---

### Post by anonymousdog on 2012-06-09
> **nickrout said:**
> Try deleting all your tuners in mythtv and adding them again. Don't worry you won't need to re-tune or anthing, once you have added them again simply reconnect them to their sources.

Thanks, Nick,

I do that every time symptoms manifest and on every upgrade (as written above)...as per this procedure:
* Stop (frontend[s] and) backend and ensure they are stopped
* If ivtv is broken, rmmod/modprobe ivtv and test card
* Backend setup: delete all cards, exit (just to ensure changes get written to DB), don't restart the service or run mythfilldb
* Backend setup: add cards back, connect to inputs, exit
* Restart backend, run mythfilldb
* Start frontend and test

At least once (and maybe twice) I went so far as to delete all cards and all video sources, then reconfigure and rebuild channels (on the DTV input) from scratch.

The 0.23 timeout on the cards had been (IIRC) 3s; now it's 12s.

It doesn't help.

I've even run with just one card/tuner/input configured...no help.

---

### Post by anonymousdog on 2012-06-09
Also, when both tuners are configured, I can lose one tuner (i.e., making 0-bit recordings, not responding to v4l2-ctl, etc.), but, depending on unknown conditions, I *may* still be able to tune to the other card *once only*.  After that one use, that card too will become unresponsive.  In fact, in many failures with LiveTV, the frontend will fail the first card then tune to the second successfully...the first card will be borked until ivtv is reloaded.

I've only one time seen MythTV fail to tune to the card on it's first use (after ivtv reload or a reboot), and I cannot guaranty that I had successfully reset ivtv that time (i.e., I hadn't done 'cat /dev/video0 > ./test.mpg' to test before starting the backend and trying to tune it with the frontend).

---

### Post by nickrout on 2012-06-09
Sorry I clearly  didn't read your first post fully.

About the only thing I can suggest is that perhaps your card is dying? How do the capacitors look? 

Or different PCI slot?

Or a modprobe -r ivtv && modprobe ivtv in your channel change script? (so it gets executed before each recording).

---

### Post by anonymousdog on 2012-06-10
> **nickrout said:**
> Sorry I clearly  didn't read your first post fully.

About the only thing I can suggest is that perhaps your card is dying? How do the capacitors look? 

Or different PCI slot?

Or a modprobe -r ivtv && modprobe ivtv in your channel change script? (so it gets executed before each recording).

The board looks fine, and I've stressed tested it with other software (including some scripted punishment that did several thousand 'input change, cat to file, file test' loops).  I've left the system running for two days with mythtv-backend off and disabled, running the punishment script periodically.  No misbehavior from the card.

I can't rule out hardware definitively unless I swap it for another card, but I think it's super unlikely to be the cause: The hardware and system were ROCK solid (on 10.04.4 x86_64 0.23) for over a year (with a DB and recordings going back to May 2008), and symptoms started within an hour of upgrading to 0.25.  That much correlation is hard to overlook.

I'll try the modprobe channel change kludge (for testing purposes); at least it's easy to implement.

---

### Post by dnilsson on 2012-06-17
Hi,

Just wanted to confirm that this is a software issue, I have a system that was recently upgraded to 0.25 from 0.24 (using the ppa with the latest fixes, [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)). After the upgrade the system starts showing the same symptoms like the thread-creator has described. In my case though, I have a Hauppauge WinTV PVR-250 but this card is also using the ivtv driver. I also get 0 byte files issuing cat /dev/video0 > ./test.mpg, unloading and loading ivtv kernel module resolved this issue.

The backend and frontend are both running Ubuntu 10.04.4 LTS, with all available updates applied.

Any progress on the root cause?

---

### Post by anonymousdog on 2012-06-19
None.  I've got nothing.

Symptoms persist with MythTV but cannot be elicited with any other use of the card.

Card looks good, temps are cool, lots of air flow.

I have noticed that most failures take about 24-36 hrs to manifest (from the last ivtv restart)...almost never more than 48hrs.

I'm buying a new hard drive so I can try a fresh install (prob 12.04 x86_64 though) without touching the current boot disk.

---

### Post by dnilsson on 2012-06-30
After googling a bit is seems that a lot of users are having this issue. Some have added a cronjob to unload and reload the ivtv drivers every now and then... 

I think this is the actual ticket for this item:

[http://code.mythtv.org/trac/ticket/10732](http://code.mythtv.org/trac/ticket/10732)

It has priority minor and severity medium so this doesn't seem like a bit issue right now for the MytvTV developers.

The ticket has one ides of changing the IO scheduler policy to realtime, this seems to have helper for some users. I will try that now... Wife acceptance is pretty low on this bug...

---

### Post by anonymousdog on 2012-07-01
> **dnilsson said:**
> I think this is the actual ticket for this item:

[http://code.mythtv.org/trac/ticket/10732](http://code.mythtv.org/trac/ticket/10732)

It has priority minor and severity medium so this doesn't seem like a bit issue right now for the MytvTV developers.
...which makes no sense to me since it breaks basic utilization of the most popular, most widely supported, and most recommended family of analog capture cards.  I keep seeing it written that there is an expectation that "almost everyone" will have (by now) abandoned SD for HD capture cards (and that, because of that expectation, problems with SD cards are low or no priority).  I'm willing to bet that expectation is faulty, that there is a huge installed base of SD cards (especially mpeg cards supported by ivtv) still in production in the wild.

> **dnilsson said:**
> The ticket has one ides of changing the IO scheduler policy to realtime, this seems to have helper for some users. I will try that now... Wife acceptance is pretty low on this bug...
Thanks for noting this ticket; I had no found it.  I'm glad to know that this bug effects other distros including MB 12.04 (since I've been arranging to upgrade in an attempt to avoid the bug).

How are you implementing that IO scheduler hack?  Are you adding the above line to the service startup script?

---

### Post by jlp_engineer on 2012-07-02
I will second the line of thinking that SD is **NOT** dead.  I have personally talked with representatives from the local cable company that serves several states (CableONE) and they have no plans to abandon SD analog channels anytime soon.  This means that the PVR-150, 250, and 500's will have a fairly long life ahead of them still. The fact that they are fairly cheap, and will go in very inexpensive systems (PCI bus) is a definite plus.   Any bugs involving these cards will be fairly painful to the installed base, IMHO.

---

### Post by nickrout on 2012-07-02
> **jlp_engineer said:**
> I will second the line of thinking that SD is **NOT** dead.  I have personally talked with representatives from the local cable company that serves several states (CableONE) and they have no plans to abandon SD analog channels anytime soon.  This means that the PVR-150, 250, and 500's will have a fairly long life ahead of them still. The fact that they are fairly cheap, and will go in very inexpensive systems (PCI bus) is a definite plus.   Any bugs involving these cards will be fairly painful to the installed base, IMHO.

well you ain't gonna get it fixed here, mythtv-users or mythtv-dev is the place to draw this to developers' attention.

---

### Post by jlp_engineer on 2012-07-02
> **nickrout said:**
> well you ain't gonna get it fixed here, mythtv-users or mythtv-dev is the place to draw this to developers' attention.

You are right of course.  The IVTV mail list as well.

I can post this thread to those lists, if there are no objections...

---

### Post by nickrout on 2012-07-02
Also if you look at the trac ticket, it is a very easy fix!

---

### Post by anonymousdog on 2012-07-03
There is no confirmed fix.  At best, mamochan on ticket #10732 suggests that ionice to "real time:0" :shock: for the backend may fix the issue.  I am testing this (with more reasonable setting of "best effort:0") but haven't seen enough time pass to know whether it helps.  Periodic reloading of ivtv only decreases the chance of failure; it does not eliminate it.

JLP, feel free to cross post.

---

### Post by nickrout on 2012-07-03
> **anonymousdog said:**
> There is no confirmed fix.  At best, mamochan on ticket #10732 suggests that ionice to "real time:0" :shock: for the backend may fix the issue.  I am testing this (with more reasonable setting of "best effort:0") but haven't seen enough time pass to know whether it helps.  Periodic reloading of ivtv only decreases the chance of failure; it does not eliminate it.

JLP, feel free to cross post.

Look forward to you adding your results to the ticket :)

---

### Post by anonymousdog on 2012-07-03
Let's not do this, Nick.  I do contribute, and, when I have definitive information, I do document.

---

### Post by nickrout on 2012-07-03
> **anonymousdog said:**
> Let's not do this, Nick.  I do contribute, and, when I have definitive information, I do document.

I was not being facetious, sorry if you took it that way. It is important to use the ticketing system though, and add what you can (without posting a simple "me to")

---

### Post by anonymousdog on 2012-07-04
> **nickrout said:**
> I was not being facetious, sorry if you took it that way. It is important to use the ticketing system though, and add what you can (without posting a simple "me to")
Thanks, Nick.  I appreciate that.

---

### Post by dnilsson on 2012-07-05
At least in my case mythbackend and the ivtv drivers failed today even though mythbackend was running with realtime I/O prio (ionice -c1 -n0 -p $(pidof mythbackend))

In this case I was not able to unload the ivtv drivers without first stopping mythbackend since mythbackend had /dev/video0 open. So a script periodically unloading and loading the ivtv drivers wouldn't have been able to solve this either, unless this script first kills mythbackend, unload and load ivtv and then starts mythbackend again. That seems like a questionable workaround to this problem, affecting all frontends regardless of whether they are watching recording, movies, music or LiveTV.

I agree there are probably a lot of users of SD TV out there, I guess the issue is that the mythtv **developers** are no longer part of this group... So in order to have a well supported solution I guess I need to be using whatever the developers are using. So, any ideas what that would be? HDPVR?

---

### Post by anonymousdog on 2012-07-05
That's very frustrating.  I've been less scientific than I should have been in my monitoring, and I **think** I've had one tuner "crash" with ionice at "Best Effort:0", but I wouldn't swear I hadn't fat fingered a service restart right before that.  I WILL say that the frequency of symptoms, at least, has been significantly reduced (even judging by my perceived anxiety at changing channels in LiveTV, LOL).

I actually a bit surprised that mythbackend does NOT run with an elevated ionice level right out of the box (considering what it does).

---

### Post by anonymousdog on 2012-07-12
I've been running mythbackend with ionice "besteffort:0" for a couple of weeks with good results.  Since my last post, I've seen one LiveTV channel change resulting in "Error opening jump program file" message but no failed, scheduled recordings.  Also, in the single instance of LiveTV channel change failure, retrying was successful.  So, while not totally perfect, this solution is "good enough" for me.

0.25 on MB 12.04 (at least comparing my long-used 10.04 build to a clean 12.04) seems to fail a bit differently (and better) than 0.25 on 10.04 (all x86_64): When tuning fails on 12.04, mythbackend exits cleanly when stopped by the "service" utility (as opposed to BE on 10.04 which must be killed as threads perpetually retry the failed connection to the tuner).  Then, about half the time, the ivtv drivers need not be reloaded (i.e., the tuner is responsive).

The way I've implemented the change is by adding ```
post-start exec /usr/bin/ionice -c2 -n0 -p $(/bin/pidof mythbackend)
``` at the end of the /etc/init/mythtv-backend.conf file.  I don't know whether that's the best way to implement this or what the advantages of a 'post-start' action are (vs. just adding the ionice command at the end of the 'script' section that actually starts mythbackend).  Thoughts?

---

### Post by johncc on 2012-07-24
> **anonymousdog said:**
> I've been running mythbackend with ionice "besteffort:0" for a couple of weeks with good results.  Since my last post, I've seen one LiveTV channel change resulting in "Error opening jump program file" message but no failed, scheduled recordings.  Also, in the single instance of LiveTV channel change failure, retrying was successful.  So, while not totally perfect, this solution is "good enough" for me.

0.25 on MB 12.04 (at least comparing my long-used 10.04 build to a clean 12.04) seems to fail a bit differently (and better) than 0.25 on 10.04 (all x86_64): When tuning fails on 12.04, mythbackend exits cleanly when stopped by the "service" utility (as opposed to BE on 10.04 which must be killed as threads perpetually retry the failed connection to the tuner).  Then, about half the time, the ivtv drivers need not be reloaded (i.e., the tuner is responsive).

The way I've implemented the change is by adding ```
post-start exec /usr/bin/ionice -c2 -n0 -p $(/bin/pidof mythbackend)
``` at the end of the /etc/init/mythtv-backend.conf file.  I don't know whether that's the best way to implement this or what the advantages of a 'post-start' action are (vs. just adding the ionice command at the end of the 'script' section that actually starts mythbackend).  Thoughts?

Any update on this subject?  I just found this thread and it is exactly what is happening to me since I upgraded to 12.04 and  0.25 a week ago (currently  2:0.25.1+fixes.20120719).  I will try the ionice workaround.

Thanks,
John

---

### Post by anonymousdog on 2012-07-25
The ionice work around is not 100% effective and is, at best, IMHO, covering up some underlying ivtv problem in 0.25.  I have not tested it extensively with realtime:0, but with besteffort:0 it still fails to tune, especially in LiveTV, at random times though MUCH less often than without the kludge.  In many weeks, no scheduled recordings have failed.  That's major improvement!  Realtime:4 is no better, and I'm reluctant to run anything at a (numerically) lower priority.

The good thing is, for whatever reason, 0.25 on 12.04 is MUCH better at terminating threads which are stuck trying to tune than was 0.25 on 10.04.  In other words I rarely if ever have to restart the backend, and, when I do, it generally works to stop/start (restart almost never works and usually results in two instances running) where I had to stop it then 'kill -9' the BE process in 10.04.

---

### Post by johncc on 2012-07-26
> **anonymousdog said:**
> The ionice work around is not 100% effective and is, at best, IMHO, covering up some underlying ivtv problem in 0.25.  I have not tested it extensively with realtime:0, but with besteffort:0 it still fails to tune, especially in LiveTV, at random times though MUCH less often than without the kludge.  In many weeks, no scheduled recordings have failed.  That's major improvement!  Realtime:4 is no better, and I'm reluctant to run anything at a (numerically) lower priority.

The good thing is, for whatever reason, 0.25 on 12.04 is MUCH better at terminating threads which are stuck trying to tune than was 0.25 on 10.04.  In other words I rarely if ever have to restart the backend, and, when I do, it generally works to stop/start (restart almost never works and usually results in two instances running) where I had to stop it then 'kill -9' the BE process in 10.04.

Thanks for that update, it fits with what I have been seeing since I put in the ionice the other day  (by the way I had to do it like this:
```

post-start script
   sleep 2
   /usr/bin/ionice -c2 -n0 -p $(/bin/pidof mythbackend)
end script
 
```
because it didn't seem to "take" if I did it with an "exec".)

I have been seeing two instances running sometimes too, so thanks for mentioning the stop/start vs restart!   Maybe that explains them.

I never had any problems with 0.24 on 10.04 threads or hanging-- never had much problems with *anything*, really.

Cheers,
John

---

### Post by anonymousdog on 2012-07-27
Yeah, it's been a major blow to usability and severely impacted WAF for a few months.

Minutes after my last post above, I realized the BE had created a zero byte file for a scheduled recording while ioniced to besteffort:0! ](*,)

So, despite my reluctance to do so, I've switched to realtime:0 (i.e. ionice -c1 -n0).
The good news is that it doesn't seem to result in the random system lags which I though it might...yet.  Also, on a FE/BE system built on SSD, it does make the FE **really** snappy! :rolleyes:

I like your post-start script implementation better than my post-start exec; the sleep is key because the init script does NOT seem to wait for the BE to actually exit all threads before starting a new instance.  So, I suspect the ionice command, in instances where a "lingering" BE process remains (at least for a few seconds), just tweaks the ionice level of the "lingering" BE process.

Now, I just watch and pray [-o< With that ticket's target of 0.26, this bug isn't going away any time soon. :cry:

---

### Post by anonymousdog on 2012-08-02
Well praying didn't help, and neither did realtime:0...same behavior as besteffort:0 with periodic (but much less frequent than out of the box) failures on the PVR tuners, especially with LiveTV.  Had one zero byte recording yesterday, and a failed tune today that required bouncing the BE.

---

### Post by emedlin18 on 2012-09-06
Where do you see this bug will be fixed in 0.26?  I am about to do a fresh install of 12.04.1 mythbuntu w/ 0.25 and just found this thread.  Not real thrilled my pvr-150 won't work.  Should I upgrade to the 0.26 development branch, or remove 0.25 as soon as I finish the install and then install 0.24?

---

### Post by anonymousdog on 2012-09-06
> **emedlin18 said:**
> Where do you see this bug will be fixed in 0.26?  I am about to do a fresh install of 12.04.1 mythbuntu w/ 0.25 and just found this thread.  Not real thrilled my pvr-150 won't work.  Should I upgrade to the 0.26 development branch, or remove 0.25 as soon as I finish the install and then install 0.24?

I don't...I wrote that the ticket's **target** is 0.26.

I would characterize the performance as "livable" with the current state of "fixes" code in the MB repos AND the ionice hack; so, the PVR-150 will work.

If you are a heavy LiveTV user and/or the very rare failed recording is a deal breaker, I'd stay on your current release.  If not, and you have reason to do a fresh install, I'd do MB 12.04.1 plus 0.25.x with MB repos enabled and implement and ionice hack in the BE service script.

---

### Post by GaryP2 on 2012-10-04
It appears that this bug has finally been patched!
 
[http://code.mythtv.org/trac/ticket/10732#](http://code.mythtv.org/trac/ticket/10732#)
 
How long does it typically take after a patch is made available like this until it will be in available if I allow my backend to pull down the latest .25-fixes? And will it be available on .25 and not just .26 (I hope because I’m not wanting to jump to .26 yet)?
 
I typically only pull down updates a few times a year when I have time to deal with potential issues. This bug has been frustrating since I upgraded to .24 to .25-fixes about 7 weeks ago. I’m glad to see someone addressed it.

---

### Post by nickrout on 2012-10-05
> **GaryP2 said:**
> It appears that this bug has finally been patched!
 
[http://code.mythtv.org/trac/ticket/10732#](http://code.mythtv.org/trac/ticket/10732#)
 
How long does it typically take after a patch is made available like this until it will be in available if I allow my backend to pull down the latest .25-fixes? And will it be available on .25 and not just .26 (I hope because I’m not wanting to jump to .26 yet)?
 
I typically only pull down updates a few times a year when I have time to deal with potential issues. This bug has been frustrating since I upgraded to .24 to .25-fixes about 7 weeks ago. I’m glad to see someone addressed it.
The patch will have to be accepted and committed by a developer. That will involve some testing, which obviously needs to be done by someone with the relevant hardware. 

You can always make your own packages of course. Whether it is made available in any particular branch will depend on the energy and committment of the dev who "adopts" it.

---

### Post by dannyboy79 on 2012-10-25
I was going to upgrade my server from 10.04 and mythtv .24+fixes to 12.04 and .25 BUT since I have a PVR-500 and a PVR-350, there's no way I am going to upgrade until this bug is fixed. TWC still sends the analog signals over my internet line so I am happy to get analog tv for free. until those stop I am sticking with analog tuners.

---

### Post by GaryP2 on 2012-10-28
Definitely stay on .24-fixes for now. I kind of regret moving to .25 because I still record some analog, although there is really only one show a week that’s semi-important. .25 has been pretty stable in most other respects for me.
 
Not sure when the developers will get around to incorporating the fix. Probably kind of difficult to get motivated into doing it if they no longer use analog themselves.

---

### Post by GaryP2 on 2012-11-29
It looks like [ticket 10732]("http://code.mythtv.org/trac/ticket/10732#") was finally acted on and closed today! Am I reading it correctly in that we will need to upgrade to .26.1 in order to get the fix? If so, does this automatically get incorporated in the Mythbuntu 0.26 repo within a day or so so? 
 
I’m currently on 12.04.01/.25.3 but was contemplating the upgrade sometime real soon anyways. Even though I don’t use analog much anymore, this bug has been the single biggest issue on my system (which speaks positively to the quality of MythTV and .25.3 in general!). Hopefully few new issues will creep in going to .26.

---

### Post by 4partee on 2012-12-05
> **GaryP2 said:**
> It looks like [ticket 10732]("http://code.mythtv.org/trac/ticket/10732#") was finally acted on and closed today! Am I reading it correctly in that we will need to upgrade to .26.1 in order to get the fix? If so, does this automatically get incorporated in the Mythbuntu 0.26 repo within a day or so so? 
 
I’m currently on 12.04.01/.25.3 but was contemplating the upgrade sometime real soon anyways. Even though I don’t use analog much anymore, this bug has been the single biggest issue on my system (which speaks positively to the quality of MythTV and .25.3 in general!). Hopefully few new issues will creep in going to .26.

Well, I just reopened it today. It is NOT fixed for me!

---

### Post by dannyboy79 on 2012-12-05
> **4partee said:**
> Well, I just reopened it today. It is NOT fixed for me!
what Ubuntu version, kernel, mythtv version etc etc? which pvr card?

---

### Post by 4partee on 2012-12-05
> **dannyboy79 said:**
> what Ubuntu version, kernel, mythtv version etc etc? which pvr card?

> 03:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 250
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ivtv
	Kernel modules: ivtv

03:07.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 150
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ivtv
	Kernel modules: ivtv



I have a spare on the shelf and have rotated them all.  I don't think I have a hardware problem.

Thanks;
John

---

### Post by 4partee on 2012-12-05
> **dannyboy79 said:**
> what Ubuntu version, kernel, mythtv version etc etc? which pvr card?

Thank you for your interest.

> uname -a
Linux pvr 3.2.0-34-generic #53-Ubuntu SMP Thu Nov 15 10:48:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


The mythtv version is in my post on [http://code.mythtv.org/trac/ticket/10732#trac-add-comment]("http://code.mythtv.org/trac/ticket/10732#trac-add-comment").

Are you a developer? And shouldn't I/we be recording this info on the official ticket tracking site?

Thank you;
John

---

### Post by 4partee on 2012-12-05
> **GaryP2 said:**
> It looks like [ticket 10732]("http://code.mythtv.org/trac/ticket/10732#") was finally acted on and closed today! Am I reading it correctly in that we will need to upgrade to .26.1 in order to get the fix? If so, does this automatically get incorporated in the Mythbuntu 0.26 repo within a day or so so? 
 


Is this true that the problem is ACTUALLY fixed now in .26 or higher?

I am migrating from 10.04 0.23 on three FEs and a FE/BE.  I started with the FE/BE on 12.04.1 and started with .25 before finding out about this thread.  If I upgrade to .26, then my 3 FEs cannot do .26!

Now I am boxed in with a FE/BE that is broken and no good reason to proceed with my migration.  

Again; "Is this true that the problem is ACTUALLY fixed now in .26 or higher?".

I just want a migration plan.

Thanks;
John

---

### Post by nPoc on 2012-12-05
I upgraded my BE/FE to .26 last Saturday after the fix was supposedly applied to the nightlies, and still had issues.  I did not verify that the fix was indeed included in the build I tried.  

I'm hoping to extract the nightlies sources in the future, and actually verify that the fix is being included.

---

### Post by 4partee on 2012-12-05
> **nPoc said:**
> I upgraded my BE/FE to .26 last Saturday after the fix was supposedly applied to the nightlies, and still had issues.  I did not verify that the fix was indeed included in the build I tried.  

I'm hoping to extract the nightlies sources in the future, and actually verify that the fix is being included.

Noone here should need to verify or track fixes.  The ticket system said it was patched and it was not. 

Your responsibility is to add your comments the the ticket.

I look forward to seeing your comments there.

The developers need your help and may ask you for more info.  That is how things get fixed.  

John

---

### Post by nickrout on 2012-12-05
There are no "nightlies". mythbuntu repos compiles when fixes are applied. The patch is applied to master, o.26-fixes and 0.25-fixes in git on 29 November by stuartm. If you don't believe me for heaven's sake read the git commit pages!

If I update now (0.25-fixes on 10.04) aptitude tell me that I will get:

> 2:0.25.3+fixes.20121202.57baf5b-0ubuntu0mythbuntu1

That commit number (57baf5b) is for 30 November and is AFTER the commit of stuartm's fix. So if you update your 0.25 machine now you will get binaries with that patch incorporated into the source.

Of course that patch may not fix it for you, maybe there is another problem.

[https://github.com/MythTV/mythtv/commits/fixes/0.25](https://github.com/MythTV/mythtv/commits/fixes/0.25)

---

### Post by 4partee on 2012-12-05
Thanks nickrout;

That is what I have been saying; that Update Manager says I am up to date and my pvr-?50 cards do not work right with 0.25.  My prior version was 0.23. 

So far, I am the only one with a comment on the ticket tracking system.

Oops, I just checked and my post is not there.  I did not notice I had followed a link from launchpad to mythtv.org where I did not have a login. My comment is there now.  I thought I was reporting to the MythBuntu team.

I wonder if I will end up as a middleman between Ubuntu, MythBuntu and MythTV?  How do I tell the MythBuntu team?

Maybe this labyrinth is hindering support!  How is anyone supposed to know where to report problems?

John

---

### Post by nickrout on 2012-12-05
> **4partee said:**
> Thanks nickrout;

That is what I have been saying; that Update Manager says I am up to date and my pvr-?50 cards do not work right with 0.25.  My prior version was 0.23. 

So far, I am the only one with a comment on the ticket tracking system.

Oops, I just checked and my post is not there.  I did not notice I had followed a link from launchpad to mythtv.org where I did not have a login. My comment is there now.  I thought I was reporting to the MythBuntu team.

I wonder if I will end up as a middleman between Ubuntu, MythBuntu and MythTV?  How do I tell the MythBuntu team?

Maybe this labyrinth is hindering support!  How is anyone supposed to know where to report problems?

JohnYou report ubuntu problems to launchpad, mythtv problems to mythtv's trac. 

What version are you running. EXACTLY. ```
dpkg -l mythtv-backend 
```and the output of ```
mythbackend --version
```

---

### Post by 4partee on 2012-12-05
> **4partee said:**
> Thanks nickrout;

That is what I have been saying; that Update Manager says I am up to date and my pvr-?50 cards do not work right with 0.25.  My prior version was 0.23. 

So far, I am the only one with a comment on the ticket tracking system.

Oops, I just checked and my post is not there.  I did not notice I had followed a link from launchpad to mythtv.org where I did not have a login. My comment is there now.  I thought I was reporting to the MythBuntu team.

I wonder if I will end up as a middleman between Ubuntu, MythBuntu and MythTV?  How do I tell the MythBuntu team?

Maybe this labyrinth is hindering support!  How is anyone supposed to know where to report problems?

John

Sure enough the finger pointing has already started!

Here is mythtv.orgs's reply and my response back:

> On 12/05/2012 03:08 PM, MythTV wrote:
> #10732: Recordings fail after upgrade to .25
> ----------------------------------+----------------------------
>  Reporter:  daveshome@…           |          Owner:  danielk
>      Type:  Bug Report - General  |         Status:  closed
>  Priority:  minor                 |      Milestone:  0.26.1
> Component:  MythTV - Recording    |        Version:  0.25-fixes
>  Severity:  medium                |     Resolution:  Fixed
>  Keywords:                        |  Ticket locked:  0
> ----------------------------------+----------------------------
> Changes (by danielk):
>
>  * status:  new => closed
>  * resolution:   => Fixed
>
>
> Comment:
>
>  jgelm, this is not the mythbuntu bug tracker. We fix the issue in our
>  source code and then the MythBuntu project picks up the changes a few days
>  later. As soon as it is fixed in our source code the appropriate thing to
>  do is to close our ticket for the issue.
>
> -- Ticket URL: <http://code.mythtv.org/trac/ticket/10732#comment:46> MythTV <http://code.mythtv.org/trac> MythTV Media Center 
OK, thank you for your attention.  I started searching this problem at Ubuntu's general user forum where this ticket # was linked.  I thought I was at launchpad where Ubuntu problems are reported.  I will find out how to report this to MythBuntu.

John Gelm

What do I do next?  Is the MythBuntu team even aware of this?  

Do you see what I mean about a support labyrinth!

John

---

### Post by nickrout on 2012-12-05
Please reply to my last post about your versions.

---

### Post by 4partee on 2012-12-05
> **nickrout said:**
> You report ubuntu problems to launchpad, mythtv problems to mythtv's trac. 

What version are you running. EXACTLY. ```
dpkg -l mythtv-backend 
```and the output of ```
mythbackend --version
```

Thank you for your help:

>  dpkg -l mythtv-backend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
ii  mythtv-backend                         2:0.25.2+fixes.20120802.46cab93-0ubunt A personal video recorder application (server)
gelmjw@pvr:~$ 


>  mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version : v0.25.2-15-g46cab93
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120506-1
QT Version : 4.8.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_iptv using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libxml2 using_lirc using_mheg using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_live using_mheg using_libass using_libxml2


According to my last post, the MythTV team has closed the ticket.  


Per mythtv folks, the ticket is closed and I just hit a normal dead spot in the update process at mythbuntu.  That does not require a Mythbuntu ticket.  

I did search launchpad and could not find anything open on this pvr-?50 issue.  The question now is "How would anyone see the fix status through MythBuntu channels?".  

John

---

### Post by nickrout on 2012-12-05
2:0.25.2+fixes.20120802

You are running old packages. Thats 2 August 2012.

Do you have mythbuntu repos installed and set to 0.25? If not, do it.

If so do ```
sudo apt-get update
sudo apt-get upgrade -V
```

You should end up with the same version as me, which is dated 2 December. You will then have the fix.

The normal ubuntu packages do not get updated after release - ie straight ubuntu 12.04 will always have the mythtv that was current when 12.04 was released. If you want regular -fixes updates you need to use the mythbuntu repos.

---

### Post by 4partee on 2012-12-05
> **nickrout said:**
> 2:0.25.2+fixes.20120802

You are running old packages. Thats 2 August 2012.

Do you have mythbuntu repos installed and set to 0.25? If not, do it.

If so do ```
sudo apt-get update
sudo apt-get upgrade -V
```

You should end up with the same version as me, which is dated 2 December. You will then have the fix.

The normal ubuntu packages do not get updated after release - ie straight ubuntu 12.04 will always have the mythtv that was current when 12.04 was released. If you want regular -fixes updates you need to use the mythbuntu repos.

OK, thanks.

It appears that we have two ways of doing things and they get different results!

I used MCC when I installed 12.04.1 to select 0.25 and in doing that I used the apply button.  I believed that 'set the repos'. And why not?

I ran Update Manager this AM and it reported I was updated.

I am no stranger to cli.  I moved to Ubuntu after 9 years on slackware.  I need to make a point.

It is wrong if there is another way to keep the system updated.  Good on you that you know it. And thank you for telling me.

I mean no offense, but, how do I know who you are? Why should I use this workaround if I have done things the way Mythbuntu is supposed to work?

If you are going to have principles, you must be willing to put your big boy pants on and deal with problems.

I would prefer to know why my system is not up to date while using the official approved method.

Is .25 beta?

Should I post a Mythbuntu problem ticket?

John

---

### Post by nickrout on 2012-12-05
> **4partee said:**
> OK, thanks.

It appears that we have two ways of doing things and they get different results!

I used MCC when I installed 12.04.1 to select 0.25 and in doing that I used the apply button.  I believed that 'set the repos'. And why not?

I ran Update Manager this AM and it reported I was updated.

I am no stranger to cli.  I moved to Ubuntu after 9 years on slackware.  I need to make a point.

It is wrong if there is another way to keep the system updated.  Good on you that you know it. And thank you for telling me.

I mean no offense, but, how do I know who you are? Why should I use this workaround if I have done things the way Mythbuntu is supposed to work?

If you are going to have principles, you must be willing to put your big boy pants on and deal with problems.

I would prefer to know why my system is not up to date while using the official approved method.

Is .25 beta?

Should I post a Mythbuntu problem ticket?

JohnI don't know why update manager isn't working for you. I never use it. However I suggest you simply do it on the command line like I suggested. It is not a workaround, it is a different (and in my experience more reliable) interface to the same underlying apt/deb infrastructure.

I also suggest you check that everything looks right in /etc/apt/sources.list.d/mythbuntu-repos.list. Here is mine:

```
nick@media:~$ cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main

```

You may say you mean no offence, but you are really becoming quite offensive. If you have a problem with update manager I suggest you open another thread, as it is irrelevant to this thread.

---

### Post by 4partee on 2012-12-05
> **nickrout said:**
> 

The normal ubuntu packages do not get updated after release - ie straight ubuntu 12.04 will always have the mythtv that was current when 12.04 was released. If you want regular -fixes updates you need to use the mythbuntu repos.

This contradicts [http://www.mythbuntu.org/repos]("http://www.mythbuntu.org/repos")

> Starting in the 12.04 release, this functionality is included in the Mythbuntu Control Centre (mythbuntu-control-centre). No extra package is necessary, but you do still need to enable it.

---

### Post by nickrout on 2012-12-05
> **4partee said:**
> This contradicts [http://www.mythbuntu.org/repos]("http://www.mythbuntu.org/repos")No it doesn't. Mythbuntu Control Centre activates mythbuntu repos. Have you got the updates installed yet?

---

### Post by 4partee on 2012-12-05
> **nickrout said:**
> I don't know why update manager isn't working for you. I never use it. However I suggest you simply do it on the command line like I suggested. It is not a workaround, it is a different (and in my experience more reliable) interface to the same underlying apt/deb infrastructure.

I also suggest you check that everything looks right in /etc/apt/sources.list.d/mythbuntu-repos.list. Here is mine:

```
nick@media:~$ cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main

```

You may say you mean no offence, but you are really becoming quite offensive. If you have a problem with update manager I suggest you open another thread, as it is irrelevant to this thread.

Here is my output:
```
 cat /etc/apt/sources.list.d/mythbuntu-repos.list
cat: /etc/apt/sources.list.d/mythbuntu-repos.list: No such file or directory

```

Sorry you took offense.  And yes, I do have a rather matter of fact manner when writing. 

I know you have your heart in the right place and gave me a solution for my immediate problem.  I thank you for that.

I don't see where I said I have a problem with Update Manager.  I have never had a problem with it. 

This is the question I would like to have had answered for the good of all. 

> I did search launchpad and could not find anything open on this pvr-?50 issue. The question now is "How would anyone see the fix status through MythBuntu channels?".


---

### Post by nickrout on 2012-12-05
> **4partee said:**
> Here is my output:
```
 cat /etc/apt/sources.list.d/mythbuntu-repos.list
cat: /etc/apt/sources.list.d/mythbuntu-repos.list: No such file or directory

```well then you don't have the mythbuntu repos activated, so no wonder you are not getting fixes. Fix that and you should get your fixes.> 

Sorry you took offense.  And yes, I do have a rather matter of fact manner when writing. 

I know you have your heart in the right place and gave me a solution for my immediate problem.  I thank you for that.

I don't see where I said I have a problem with Update Manager.  I have never had a problem with it.you said it wasn't working, but in fact it appears to be that you don't have the repo activated, so maybe there is nothing wrong with update manager after all :)>  

This is the question I would like to have had answered for the good of all."I did search launchpad and could not find anything open on this pvr-?50 issue. The question now is "How would anyone see the fix status through MythBuntu channels?"."

You wouldn't, because it is not a [myth][u]buntu problem. Launchpad is not designed to duplicate upstream bug trackers. 

Rest assured  that if (when) you have mythbuntu-repos activated you will get all fixes that are applied to your mythtv branch (0.25-fixes in this case) within a day or so of them being applied in mythtv's git repo. If you want to see what is being applied, look in the myth git repo, not launchpad.

---

### Post by 4partee on 2012-12-05
> **nickrout said:**
> No it doesn't. Mythbuntu Control Centre activates mythbuntu repos. Have you got the updates installed yet?

Yep, you're right.  I did not check the activate box.  

I'll do that now and post results.  

How about this instead:
```
cat /etc/apt/sources.list.d/mythbuntu-0_25-precise.list 
deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
deb-src http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main

ls -lR /etc/apt/sources.list.d/
/etc/apt/sources.list.d/:
total 4
-rw-r--r-- 1 root root 132 Dec  5 19:55 mythbuntu-0_25-precise.list


```

It is by name different from yours. The file date is when I did the MCC apply.

Yep, Update Manager check lists MythTV updates.  

Thanks again;
John

---

### Post by nickrout on 2012-12-05
Right well apply the changes and see if it fixes the problem that this thread is actually about. I suggest you start another thread if you continue ti have update problems, and restrict further postings here to the problem in hand.

Cheers.

---

### Post by nPoc on 2012-12-06
> **4partee said:**
> Noone here should need to verify or track fixes.  The ticket system said it was patched and it was not. 

Your responsibility is to add your comments the the ticket.

I look forward to seeing your comments there.

The developers need your help and may ask you for more info.  That is how things get fixed.  

John

First off let me say congrats on figuring out your missing ppa problem.  I hope things work better for you.

Secondly, I am a developer *(albeit not a mythtv dev), and this is open source. The whole beauty of open source is that I can see the code if I wanted.  Sure commenting in a ticket helps devs narrow down the problem, but handing them a fix would be even more helpful.  So please don't discourage people from looking at sources.

So next time grab the source, and see if you can give a little help back to the community.  Very few devs actually get paid to do this kind of stuff, and ever little bit helps.

---

### Post by nPoc on 2012-12-06
> **nickrout said:**
> There are no "nightlies". mythbuntu repos compiles when fixes are applied. The patch is applied to master, o.26-fixes and 0.25-fixes in git on 29 November by stuartm. If you don't believe me for heaven's sake read the git commit pages!


Reading the git commits is what I meant by 
>  verify that the fix is being included
In all honesty, I was actually second guessing the fact that I had actually grabbed a new enough version that included the fix and was not second guessing you at all.  


Also from [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)
> The MythTV-Updates repository will contain updated MythTV software. It is automatically built each day when there are upstream fixes available.

Hmm that certainly sounds like a nightly build to me.  Do you know more specifics on how the mythbuntu repos are getting built so that they auto built with every git commit?

---

### Post by dannyboy79 on 2012-12-06
i have been holding back upgrading my 10.04.4 lucid lynx install which runs Mythbuntu 0.23.1+fixes because of this error. So now is 12.04.1 running the latest Mythbuntu repo's all fixed? Should I activate .25 repos or the .26 repos? I have 2 PVR-X cards, 1 PVR-350 and 1 PVR-500. THanks for any info

---

### Post by nPoc on 2012-12-06
> **dannyboy79 said:**
> i have been holding back upgrading my 10.04.4 lucid lynx install which runs Mythbuntu 0.23.1+fixes because of this error. So now is 12.04.1 running the latest Mythbuntu repo's all fixed? Should I activate .25 repos or the .26 repos? I have 2 PVR-X cards, 1 PVR-350 and 1 PVR-500. THanks for any info

.26 is not working for me, but I can confirm that the problem I have is no longer the problem originally described in this thread.  Now my logs are being flooded with "first frame is no keyframe"

---

### Post by dannyboy79 on 2012-12-06
> **nPoc said:**
> .26 is not working for me, but I can confirm that the problem I have is no longer the problem originally described in this thread.  Now my logs are being flooded with "first frame is no keyframe"
which PVR-X card? so no recordings are being recorded? you're using mythbuntu repos and .26 activated? are you using ubuntu 12.04.1?

---

### Post by nPoc on 2012-12-06
> **dannyboy79 said:**
> which PVR-X card? so no recordings are being recorded? you're using mythbuntu repos and .26 activated? are you using ubuntu 12.04.1?

I have a pvr-250, but I also have a hvr-2250, which doesn't use the ivtv drivers, but seems to have issues of it's own as well *(not sure if they are related).

---

### Post by dannyboy79 on 2012-12-06
> **nPoc said:**
> I have a pvr-250, but I also have a hvr-2250, which doesn't use the ivtv drivers, but seems to have issues of it's own as well *(not sure if they are related).
so no recordings are being recorded? you're using mythbuntu repos and .26 activated? are you using ubuntu 12.04.1?

---

### Post by 4partee on 2012-12-06
> **nPoc said:**
> First off let me say congrats on figuring out your missing ppa problem.  I hope things work better for you.

Secondly, I am a developer *(albeit not a mythtv dev), and this is open source. The whole beauty of open source is that I can see the code if I wanted.  Sure commenting in a ticket helps devs narrow down the problem, but handing them a fix would be even more helpful.  So please don't discourage people from looking at sources.

So next time grab the source, and see if you can give a little help back to the community.  Very few devs actually get paid to do this kind of stuff, and ever little bit helps.

I don't grab sources AFAIK.  I just use the gui tools MCC and Update Manager. 

I am trying to give feedback, but it is not always obvious to whom I should report it.  

Also, I did use MCC to activate the repos, but later Update Manager froze and I never did get the fix.  I have created a new post about that. [http://ubuntuforums.org/showthread.php?t=2091947]("http://ubuntuforums.org/showthread.php?t=2091947")

John

---

### Post by nPoc on 2012-12-06
> **dannyboy79 said:**
> so no recordings are being recorded? you're using mythbuntu repos and .26 activated? are you using ubuntu 12.04.1?

I'm dual booting a mostly-functioning 11.10 and a less functioning 12.04.1, while I debug 12.04.1.  Right now my pvr-250 and hvr-2250 refuse to successfully channel scan, so my mythbox is usually booted into 11.10.  Unfortunately the wife is pretty demanding on the dvr, so I don't get too much time to actually debug it.

---

### Post by nickrout on 2012-12-06
> **nPoc said:**
> I'm dual booting a mostly-functioning 11.10 and a less functioning 12.04.1, while I debug 12.04.1.  Right now my pvr-250 and hvr-2250 refuse to successfully channel scan, so my mythbox is usually booted into 11.10.  Unfortunately the wife is pretty demanding on the dvr, so I don't get too much time to actually debug it.Are you scanning analogue channels - I guess so if you are using a pvr-250. I beleive there has been some change where scanning isn't needed or desirable (or something) on analogue. Sorry to be so vague I don't do analogue. 

But anyway, why do you need to scan if you have an existing database? Have the channels changed?

---

### Post by nPoc on 2012-12-06
The existing database is on the other partition, and is for .24.  I really wanted to start clean with 12.04.1.  

Regardless, I should be able to do an analog channel scan. 

Alright let's stop talking about my issue until I have a chance to actually look at it more closely.

---

### Post by nickrout on 2012-12-06
So you are going to throw away your existing recordings, recording history and recording rules? Seems a bit severe. I'll try and find what I saw about analogue scanning. Cheers.

---

### Post by nickrout on 2012-12-06
Maybe I was thinking of this: [http://www.gossamer-threads.com/lists/mythtv/users/435721#435721](http://www.gossamer-threads.com/lists/mythtv/users/435721#435721)

Which would imply it is only relevant to 0.22.

By your (mis)spelling of analogue :) I am guessing you are in the USA perhaps. Sounds from that same thread that Schedules Direct will set up your analogue without the need to scan.

---

### Post by nPoc on 2012-12-06
Yeah I think the inability to scan is a symptom of something worse.  I'll be running the ivtv tools as soon as I get a chance to see if the problem only exists in myth.  Speaking of which, does anyone have any suggestions on good stand alone tuning applications that aren't mythtv?

---

### Post by 4partee on 2012-12-08
The 12.04.1 system is running again thanks to the CLI tip from nickrout to apply the fix.  

No errors over the last few hours.  I'll report back next week with status unless I have another error beforehand.

nPoc;
I don't need to scan with the pvr-?50 cards.  After fetching the analog channel info from Schedules Direct, the channels are ready to select.  

I have never needed to mess with ivtv either.

HTH;
John

---

### Post by nPoc on 2012-12-08
So after the update it looks like the pvr250 is working fine.  It was actually the analog tuners in my hvr2250 that are still messed up.  I think I'm going to disable those tuners and move up to .26.  They never worked in 10.10 anyways.

---

### Post by dannyboy79 on 2012-12-08
> **4partee said:**
> The 12.04.1 system is running again thanks to the CLI tip from nickrout to apply the fix.  

No errors over the last few hours.  I'll report back next week with status unless I have another error beforehand.

nPoc;
I don't need to scan with the pvr-?50 cards.  After fetching the analog channel info from Schedules Direct, the channels are ready to select.  

I have never needed to mess with ivtv either.

HTH;
Johnso which version of mythtv are you using? exact version? and if you're using the mythbuntu repo's, which version of mythtv is activated?

---

### Post by nickrout on 2012-12-08
He is using 0.25-fixes from the repos. The exact version is I think 0.25-20121205. The fix is in 0.26-fixes as well.

---

### Post by 4partee on 2012-12-08
[QUOTE=nickrout;12394466]He is using 0.25-fixes from the repos. The exact version is I think 0.25-20121205....

Correct.  

From the fixed FE/BE:

```
dpkg -l mythtv-backend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
ii  mythtv-backend                         2:0.25.3+fixes.20121206.0b60406-0ubunt A personal video recorder application (server)
root@pvr:/home/gelmjw# 

```

The other 4 FEs are on U10.04 v.25.

HTH;
John

---

### Post by nPoc on 2012-12-09
So just to update, .26+fixes seems to have been the source of the issues with my hvr-2250. .25+fixes works fantastically.  I really wish I had spare hardware so that I could debug .26 without pissing off the wife.

---

### Post by 4partee on 2012-12-23
> **4partee said:**
> The 12.04.1 system is running again thanks to the CLI tip from nickrout to apply the fix.  

No errors over the last few hours.  I'll report back next week with status unless I have another error beforehand.

HTH;
John

Status report: No recording failures.

HTH;
John

---

### Post by dannyboy79 on 2012-12-23
> **4partee said:**
> Status report: No recording failures.

HTH;
Johnthanks very much for reporting back. will probably make the switch from 10.04.4 MythTV 0.32.1+fixes to 12.04 and MythTV 0.25 or 0.26.

---

### Post by dannyboy79 on 2013-04-16
ok, i am running
```
MythTV Version : v0.25.2-15-g46cab93
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120506-1
QT Version : 4.8.1

```
and my PVR-350 and PVR-500 seem to be working BUT I am getting massive ivtv mpg buffer overflows and it's dropping data. I have added some module options to /etc/modprobe.d/ivtv.conf and /etc/modprobe.conf and they are 
```
options ivtv enc_mpg_buffers=16 enc_yuv_buffers=20 enc_pcm_buffers=640 debug=3
```
I'll report back if that error message stops appearing my dmesg output. The error looks like the following:
```
[15678.012796] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[15678.012804] ivtv0: Cause: the application is not reading fast enough.
[15678.181416] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[15678.181425] ivtv0: Cause: the application is not reading fast enough.
[15678.314549] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[15678.314558] ivtv0: Cause: the application is not reading fast enough.
[15678.678262] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[15678.678270] ivtv0: Cause: the application is not reading fast enough.
[15678.848255] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[15678.848263] ivtv0: Cause: the application is not reading fast enough.
```

---

