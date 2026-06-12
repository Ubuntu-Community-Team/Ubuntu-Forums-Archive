---
title: "New Mythbuntu 14.04 install; &quot;Watch TV&quot; won't work; Prof 7301 DVB-S2 tuner issues"
date: 2014-06-03
forum: Mythbuntu
---

### Post by Mythological on 2014-06-03
I tried posting something about this in the MythTV forum and got no response.  First I should mention that we (me and another guy that are trying to get this to work) have had a Mythbuntu 12.04 setup running successfully for a couple of years but we only had HDHomeRun tuners connected to it.  It was pretty easy to set up and pretty much worked right away.

So now we have installed Mythbuntu 14.04 (primary backend + frontend) on a new box and are having nothing but trouble.  To start with we installed a Prof 7301 DVB-S2 satellite tuner card [(the LinuxTV page for this card is here)]("http://linuxtv.org/wiki/index.php/DVB-S2_7301_PCI").  People on the satellite forums had indicated that we should be able to  install this card and it should just work.  And that is pretty much true  if you are running Windows (which we installed just temporarily to test  the card and make sure it is working correctly), but since installing  Mythbuntu it at first did not appear to recognize the card at all, or  something else was going on, but finally it did manage to find the card  after about the third capture card add/remove cycle.  Since then it seems to find the card but now there are other issues.

The first problem we encountered was that when we scanned a particular frequency (transponder), Mythbuntu appeared to find  and add all the channels associated with that frequency, and they even  had the correct names.  And it added them to the channel list.  Great!   But then we tried to scan the *next* transponder, on a different frequency, and it looked like it  never changed the frequencies - it appeared to scan the exact same group  of channels, which was totally wrong for the frequency, symbol rate,  etc. that we we scanning.

So then we thought that maybe it  actually scanned the right transponder but for some reason used the  names from the previous scan, so we attempted to go into the frontend  and try to watch one of them, and that is when we encountered the second problem. Every time we clicked "Live TV", it  flashed "please wait"  on the screen momentarily and then returned to  the menu!  We never got any kind of channel menu or grid or anything  like that.  The frontend is NOT throwing up any error messages about not  being able to connect to the backend, so we have no idea what the  problem is.  This is the most important issue at the moment because  until we get this figured out we can't tell if it's actually possible to  see video from the card.

I should probably mention that most of the signals on North American satellites  do not come with schedule data, so in my "Satellite" video source I set  my "Listings Grabber" to "No grabber".  The "Channel frequency table" is  set to "Default", and the "Network ID" is "-1".  I don't know if any of  that would make any difference but I do note that when I go to the web  interface for the MythTV backend, it shows the scanned channels but  shows "No data" next to each of them, which is what I would expect.   However, the frontend should still be able to play a live stream from  any working transponder, shouldn't it? On the older system, there was not any schedule data available for some of the low power stations and yet the frontend had no problem playing them.

I have also been trying to get help on one of the satellite forums, but the problem is that most of the guys in that forum don't use Mythbuntu or MythTV.  However one guy did ask me to post some specific information late last night including log outputs, so if you look at [this post]("http://rickcaylor.websitetoolbox.com/post/show_single_post?pid=1283035396&postcount=35") and [this post]("http://rickcaylor.websitetoolbox.com/post/show_single_post?pid=1283042934&postcount=37") you will see a lot more information about this issue (**EDIT:** Actually, just go to [this thread]("http://rickcaylor.websitetoolbox.com/post/just-installed-new-prof-7301-card-and-it-is-not-working-what-now-6924798?trail=45") and see all the posts from #34 on).  I notice what appear to be a lot of error messages in the logs, but have no idea what they mean or how to fix them.

While the guys in that forum have tried to be helpful, most of them  aren't really familiar with Mythbuntu.  And most of them are at the level  where they can compile their own software, whereas we install from the ISO and we hope it works, and if it doesn't I'm kind of  like deer in headlights.  Just so you know, I am definitely a Linux USER - not a developer, not a programmer, and I'm outside my comfort zone when I have to do things from a command prompt rather than a GUI.  I know nothing about Linux internals and spend as little time at the command prompt as possible.  For testing purposes, I can cut and paste things to a command prompt, but I have to have clear instructions on EXACTLY what to paste or type, etc.  One reason I like Mythbuntu (at least the prior version) is that all the configuration is done in a GUI and there are hints for almost everything.  Mythbuntu 12.04 worked so well in the past, I just can't understand why we're having these issues on the new install.

EDIT: One thing that is REALLY confusing is this error in the frontend log:

Jun  3 14:01:35 myth-backend  mythfrontend.real: mythfrontend[2965]: E CoreContext livetvchain.cpp:289  (GetEntryAt) It appears that your backend may be misconfigured.  Check  your backend logs to determine whether your capture cards, lineups,  channels, or storage configuration are reporting errors.  This issue is  commonly caused by failing to complete all setup steps properly.  You  may wish to review the documentation for mythtv-setup.

But at that same time in the backend log there is nothing that appears to indicate a configuration error:

Jun  3 14:01:35 myth-backend  mythbackend: mythbackend[2905]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Playback
Jun  3 14:01:35  myth-backend mythbackend: mythbackend[2905]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: myth-backend as a client  (events: 0)
Jun  3 14:01:35 myth-backend mythbackend:  mythbackend[2905]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[3]: Changing from None to WatchingLiveTV
Jun  3 14:01:35  myth-backend mythbackend: mythbackend[2905]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[3]: HW Tuner: 3->3
Jun   3 14:01:35 myth-backend mythbackend: mythbackend[2905]: E TVRecEvent  tv_rec.cpp:3792 (TuningFrequency) TVRec[3]: Failed to set channel to 1.  Reverting to kState_None
Jun  3 14:01:35 myth-backend mythbackend:  mythbackend[2905]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[3]: Changing from WatchingLiveTV to None

Note that if I channel the starting channel to a different one, such as 500 which should be good, the message in the next to last line above changes to reflect the new starting channel but it still doesn't work.

---

### Post by blm-ubunet on 2014-06-04
Sorry I don't use dvb-s(2)..

> Could not get inputs for the  capturecard.#012#011#011#011Perhaps you have forgotten to bind  video#012#011#011#011sources to your card's inputs?
That appears in your logs..

Your post reads like you were in the video sources tab but..
After you add a tuner & scan you have to bind that card (& possibly others) to a video source.
The channel lineup/source of program data belongs to the video source.

The tuner card needs direct connection (no biased tee) to LNB to be able to power & control..

---

### Post by Mythological on 2014-06-04
> **blm-ubunet said:**
> Sorry I don't use dvb-s(2)..


That appears in your logs..

Your post reads like you were in the video sources tab but..
After you add a tuner & scan you have to bind that card (& possibly others) to a video source.
The channel lineup/source of program data belongs to the video source.

We did that.  I'm familiar with the need to do that from a previous installation where we set up HDHomeRuns (and we had NO problem getting those to work).  In the video source we tried specifying "No Grabber" and also "EIT", it made no difference either way.

> **blm-ubunet said:**
> The tuner card needs direct connection (no biased tee) to LNB to be able to power & control..

Not sure what you mean by "biased tee" but right now we are not using one - the LNB is connected directly to the tuner card.

---

### Post by blm-ubunet on 2014-06-05
Can you post the stdout/stderr output when running mythtv-setup from terminal ?

```
mythtv-setup -v all --loglevel=debug
```

---

### Post by Mythological on 2014-06-05
Thanks but I don't know what you mean by "stdout/stderr output" - I ran that line in a terminal window and this is all that was displayed:

mythtv-backend stop/waiting
mythtv-backend start/running, process 2338

I'm not really that familiar with doing things like this from the Linux command line so you will have to explain how to get whatever output you want to see, or point me to a page that explains it.

---

### Post by Mythological on 2014-06-05
Well, it seems this is a major bug, or maybe multiple bugs, in Mythbuntu/MythTV.  Please see [this thread]("http://rickcaylor.websitetoolbox.com/post/just-installed-new-prof-7301-card-and-it-is-not-working-what-now-6924798") and in particular [this post]("http://rickcaylor.websitetoolbox.com/post/show_single_post?pid=1283067895&postcount=54") from someone who is very familiar with these cards.  The question now becomes, is there any effective way of reporting these bug(s) to the MythTV developers and is there any chance they might actually be fixed?  I am not in the habit of reporting bugs, except maybe via a once-in-a-blue-moon e-mail message to the developer of a small project, so if there is some particular procedure that should be followed please point me in the right direction.  Thanks.

The bottom line for anyone searching on this subject:  The Prof 7301 may be a great satellite tuner (and several people have said that it is the best such tuner they've ever tried) but it DOES NOT WORK with Mythbuntu 12.04 or 14.04.  And, unless you are SERIOUS Linux hacker and maybe have access to the MythTV source code, you are NOT going to be able to make it work with MythTV.  I have a feeling this issue may affect other DVB-S(2) tuners as well, but haven't tested anything else personally.  IMHO the problem is entirely in MythTV, and not in the card - see the links above for the discussions that helped form that opinion.

---

### Post by blm-ubunet on 2014-06-05
I run latest git master code & use dvb-t & had to re-scan recently; no problem..
My re-scan was of existing transports & including any signalled new transports.

It is possible the -s2 support is broken.
AFAIK there are many UK users of dvb-s2.

Here's a thread discussing "suggestions for a working card"
[http://www.gossamer-threads.com/lists/mythtv/users/570100](http://www.gossamer-threads.com/lists/mythtv/users/570100)

There is an old bug where the channel import process either does not work or sets networkID set to NULL.
(The mythtv website servers seem to be offline.)

Could use your windows setup to collect all the transport freq/pol/mod/neworkIDs/channel lists etc..
Could then use scan-s2:
[http://www.linuxtv.org/wiki/index.php/Scan-s2](http://www.linuxtv.org/wiki/index.php/Scan-s2)

Possible problems with tuner setup..
- Need to use "delete all tuners on all hosts" after multiple failed attempts.

Can you delete all tuners & then re-add card & scan one transport/multiplex & only once.
Then try to use FE liveTV via the program guide: select a expected channel & then play..

The stdout/stderr is the output from a program (visible in logs or in terminal).
It is a POSIX standardized behaviour.

With mythbuntu (script wrapping of programs):
```
sudo service mythtv-backend stop
mythtv-setup.real -v all --loglevel=debug > mythsetuplog.txt
```
after
```
sudo service mythtv-backend start
```
post log as attachment.

Note: CrazyCat has made available code fixes for dvb-t2 drivers etc, her/his? code does make it way into kernel (linuxTV) media drivers.
Maybe the comment about high bitrate has some relevance.

---

### Post by Mythological on 2014-06-11
I'm replying to my own thread here to say, unless you are a true Linux guru, DO NOT waste your time trying to get a Prof 7301 card to work with Mythbuntu 12.04 or 14.04.  It is just never going to happen.  The only guys who have reported any success are those who are smart enough to recompile software and I get the sense that among that group, by which I mean those who are Linux experts AND have a satellite tuner card, none of them is actively using MythTV.  We struggled with this for several days and never saw one frame of video in Mythbuntu.  Finally gave up and installed Windows and within a couple of hours we were seeing beautiful video from that card.  There is a free Windows program called [SmartDVB]("http://www.smartdvb.net/sdvb/") that does about the best job of anything I have come across of interfacing with that card, unfortunately the current stable version does not operate on a backend/frontend model.

Mythbuntu is a great program in many respects and does a great job of supporting certain devices such as HDHomeRuns, but my opinion of its support for satellite cards couldn't be much lower.  If you are experienced enough to get into the source code and fix things then maybe you can get it to work, but if you are a mere user you will just be batting your head against a brick wall.  And if you DO manage to fix MythTV, PLEASE try to get your fixes into the next distribution!

---

### Post by blm-ubunet on 2014-06-12
All the linux support for tuners is through v4l-dvb (LinuxTV.org).
[http://linuxtv.org/wiki/index.php/DVB-S2_7301_PCI](http://linuxtv.org/wiki/index.php/DVB-S2_7301_PCI)

Mythbuntu & mythtv do not write device drivers.
AFAIK The HDHomerun support was done by an enthusiastic mythtv user & the device is a network device that uses a streaming protocol.

It look like you needed to patch the driver to do highbitrate -s2 & blindscanning..but that could be out of date.

Media build code is here:
[https://bitbucket.org/bluzee/media_build_udl](https://bitbucket.org/bluzee/media_build_udl)
Instructions as well...

I'm no linux guru but this is "a walk in the park"..

---

### Post by Mythological on 2014-06-12
> **blm-ubunet said:**
> I'm no linux guru but this is "a walk in the park"..

I could not possibly disagree with you more on that, but if that's what you believe, I don't suppose I will convince you otherwise.

But if you don't actually have a Prof 7301 tuner AND have been successful in making it work with Mythbuntu, then you just have no idea.  I had some very smart people trying to help me with this in a satellite forum and even they came to the conclusion that the drivers are buggy.  One guy said he had submitted patches to fix driver various issues four years ago and they were never accepted. Personally, I'm nowhere near the level of those guys so if they are saying things like that, I tend to believe them.

The fact that we got it up and running in Windows in a couple of hours speaks volumes to how far Linux has to go with regard to support of these types of devices.

---

### Post by blm-ubunet on 2014-06-12
> The fact that we got it up and running in Windows in a couple of hours  speaks volumes to how far Linux has to go with regard to support of  these types of devices.
I don't disagree with this statement.

But you could have bought supported (subjective?) h/w first.
Your dvb-s2 card has had basic support from kernel 2.6.xxx but the wiki states that you have to patch for blindscan & high bitrate -s2.

There is no commercial imperative to create FOSS linux drivers.
The existing linux drivers (mostly) have been reverse engineered by extremely talented/generous persons.
I believe Haupaggue might have provided some help.

There are closed (blob) drivers from TiVee & TBS for dvb-s2. (still have to compile "media" part of kernel)
But does seem the open source TBS drivers are better for -s2.

---

### Post by jonathan-l-harrison on 2014-06-28
Gosh I can so relate to this thread and the originator...  I am not a programmer or codie and have been using Ubuntu since 2008.  I have just built another machine I want to use as a media server and I am having NOTHING but grief.  All the issues as detailed by the 1st thread.  I have backend problems with Mythbuntu...  Goes in to a set up where location and language selection are required and then just lops round and round.  I have to hold down Exit so that it has so many commands that I have enough time to go in to command to enter xKill to shut it down....

As for adding cards I am struggling with getting my DVB recognised.  Second card from different manufacturer.  All Linux distros have a very long way to go to appeal to users in general.  It is far far far to complex and time consuming for most of us.  I hate Windows but wast far too much time trying to make simple plug n play devices and apps work.

That said..  how do i make my card work?
How do I get Mythubuntu to work?  Any helpers

---

### Post by bullwinkle2 on 2014-06-28
> **jonathan-l-harrison said:**
> That said..  how do i make my card work?

As the OP on this thread, I **REALLY** hate saying this (especially in this forum), but if you want it to work without a lot of grief, install Windows 7 (8 might work also) and run SmartDVB (if you want to watch TV using the same computer) or MediaPortal (if you want to to act as a backend for XBMC).  If you install MediaPortal and you live in North America, you will run into a few issues because of the strange way they do blind scanning - they make some assumptions based on the way FTA works in Europe that are definitely not valid in North America.  I think the MythTV backend makes some of the same assumptions and that caused some of the same problems I saw there.  Hint to software authors - in North America, NEVER assume one transponder is a duplicate of another unless it is on the EXACT same satellite and frequency, which would only happen if you are rescanning a previously scanned satellite.  North American satellite programmers do NOT follow international standards because no one forces them to, thus various ID's that would normally uniquely identify a transponder in Europe tend to get reused with impunity in North America.  If the guy setting up the satellite feed doesn't know what value to use for a particular field, he'll apparently just pick a random number like "1" or his address or kid's age or some such thing.  There are workarounds in MediaPortal, and once you learn its quirks (many of which are documented it their forum) it is relatively easy to set up as a backend.  And it will WORK, and you will see beautiful video, unlike with the MythTV backend.

I wish it were not so, I REALLY wanted MythTV to work, but as someone who is not a Linux guru there was simply no hope.  As I said, a lot smarter people than I concluded that either Linux or MythTV (probably Linux) doesn't interact with the card properly.  This is almost certainly fixable, but not by mere mortals like me, who couldn't successfully fix and recompile a piece of software if my life depended on it.

> **jonathan-l-harrison said:**
> How do I get Mythubuntu to work?  Any helpers

I would really like to be wrong about this, but I think you are going to have a VERY long wait before anyone answers that.  And, again, it may be that some of the problem is in Linux itself, though in a distro like Ubuntu I would assume they could apply any fixes they wanted to. I just don't think they are motivated to do so.

I like the MythTV frontend much better than XBMC, if only because it has better picture quality.  But when you try for a week to get something to work, and it fights you every step of the way, and then put up Windows and have working video immediately thereafter, that indicates that either the Linux or Mythbuntu folks (possibly both) either have no exposure to these types of systems and cards, or they just don't care enough to make it work correctly.

---

### Post by jonathan-l-harrison on 2014-06-28
No, I have great faith in the guys.  Never failed yet.. :)  I shall keep plugging.

I have W7 on VM on another machine and have seen 8, I do not want to go down that path.

---

