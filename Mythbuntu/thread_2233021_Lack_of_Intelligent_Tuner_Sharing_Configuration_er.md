---
title: "Lack of Intelligent Tuner Sharing: Configuration error, or by design?"
date: 2014-07-05
forum: Mythbuntu
---

### Post by mattlach on 2014-07-05
Hey all,

Quick question.

Today I had a scheduled recording of the world cup game.   At the same time I was watching it live on two separate clients.

This was using three tuners, one for the recording and one for each of the live watchers.

Here is a screenshot of what I mean (Showing only two of them, as the scheduled recording ended in overtime)

[img]https://farm3.staticflickr.com/2898/14395778929_7a4b1804b0_b.jpg[/img]

This behavior seems a bit wasteful of my limited tuners.  Is there a way to tell the system to share the same tuner when watching/recording the same thing?  Does this come with any drawbacks?

Thanks,
Matt

---

### Post by aelfric55 on 2014-07-13
Since Mythtv is primarily a PVR by design rather than a TV app, the usual way to do this would have been to schedule the game as a recording (which you did) and then watch the recording-in-progress from the remote clients. The same 3-to-30 second buffer applies to "live" TV as does to a recording-in-progress, and you use 1 tuner as opposed to (in this case) 3.

The drawback is always needing to schedule extra time for a sports recording, to account for overtime. I do all sports events as recordings, though I intend to watch them "live" and usually add an hour for any baseball or football game. Very rarely, as I'm watching in-progress and realize that the extra hour may not be enough, I'll alter the recording end time to even later from the on screen menu (Schedule-->Upcoming Recordings-->Modify Recording Options) as the end of the scheduled time is approaching. 

A second possible drawback may be the reported difficulties some versions of mythtv 0.27 may have with the playback of recordings in-progress. But I haven't ever personally experienced such an issue.

---

### Post by mattlach on 2014-07-13
> **aelfric55 said:**
> Since Mythtv is primarily a PVR by design rather than a TV app, the usual way to do this would have been to schedule the game as a recording (which you did) and then watch the recording-in-progress from the remote clients. The same 3-to-30 second buffer applies to "live" TV as does to a recording-in-progress, and you use 1 tuner as opposed to (in this case) 3.

The drawback is always needing to schedule extra time for a sports recording, to account for overtime. I do all sports events as recordings, though I intend to watch them "live" and usually add an hour for any baseball or football game. Very rarely, as I'm watching in-progress and realize that the extra hour may not be enough, I'll alter the recording end time to even later from the on screen menu (Schedule-->Upcoming Recordings-->Modify Recording Options) as the end of the scheduled time is approaching. 

A second possible drawback may be the reported difficulties some versions of mythtv 0.27 may have with the playback of recordings in-progress. But I haven't ever personally experienced such an issue.

Interesting!   I had no idea recording and playback from the same file was a documented issue!

I'm a relatively new user as of June this year, never had a version prior to 0.27.   I have experienced this "playback and recording problem to the same file" but I was blaming my NAS for it.

I had this peculiar problem.   I was recording both livetv and scheduled recordings directly to my NAS via NFS.  In a test I could successfully record from all six tuners and playback two streams to my clients just fine to my NAS, but only if they were all separate files.   Any playback and recording from the same file would result in occasional freezes.

Troubleshooting this was driving me nuts.  I knew the performance was there to be able to handle it (due to my above test) but eventually I resigned myself to not solving it.  The reason I blamed my NAS was because the problem goes away if I record to my local SSD.

I even tried setting up the SSD as a NFS cache device using cachefilesd, but the problem still persisted over NFS.

My current workaround is to set up multiple storage groups, do all recordings to the SSD, and have a nightly cronjob that moves all the recordings to my archive folder on my NAS.   This is probably going to challenge the write endurance of the SSD though, so it would be fantastic if this bug were fixed.

Can you point me in the direction of where people have been discussing this problem?

---

### Post by aelfric55 on 2014-07-13
I'm not certain this relates to your particular symptoms when attempting to play recordings in-progress. But the complaint I had in mind was stuttering, which began to appear with 0.27, but has supposedly been fixed for the upcoming 0.28 and (maybe?) in the latest 0.27.3-fixes. The developer discussion with links to the appropriate bug-track tickets may be found here: [http://www.gossamer-threads.com/lists/mythtv/commits/561320](http://www.gossamer-threads.com/lists/mythtv/commits/561320) The relevant ticket seems to be [https://code.mythtv.org/trac/ticket/12016](https://code.mythtv.org/trac/ticket/12016)

As I mentioned I've never experienced any particular issues on fairly old hardware with sometimes two remote frontends watching a currently-recording file (mostly HD baseball broadcasts nowadays) stream from a backend-only machine in Myth versions up through 025.3, nor after jumping directly from there to my current version, fixes/0.27 (7e8ca1c), so I concluded I had just leaped over the affected versions. Or maybe that I don't use barriers in the filesystem housing mythconverg (UPS backup) --I just don't know.

---

### Post by mattlach on 2014-07-13
> **aelfric55 said:**
> I'm not certain this relates to your particular symptoms when attempting to play recordings in-progress. But the complaint I had in mind was stuttering, which began to appear with 0.27, but has supposedly been fixed for the upcoming 0.28 and (maybe?) in the latest 0.27.3-fixes. The developer discussion with links to the appropriate bug-track tickets may be found here: [http://www.gossamer-threads.com/lists/mythtv/commits/561320](http://www.gossamer-threads.com/lists/mythtv/commits/561320) The relevant ticket seems to be [https://code.mythtv.org/trac/ticket/12016](https://code.mythtv.org/trac/ticket/12016)

As I mentioned I've never experienced any particular issues on fairly old hardware with sometimes two remote frontends watching a currently-recording file (mostly HD baseball broadcasts nowadays) stream from a backend-only machine in Myth versions up through 025.3, nor after jumping directly from there to my current version, fixes/0.27 (7e8ca1c), so I concluded I had just leaped over the affected versions. Or maybe that I don't use barriers in the filesystem housing mythconverg (UPS backup) --I just don't know.

Interesting, thank you.

As a non programmer IT hobbyist, a lot of that technical database detail went WAY over my head, but it looks like it has been dealt with in .28, which sounds good!

---

### Post by tgm4883 on 2014-07-16
> **mattlach said:**
> This is probably going to challenge **the write endurance of the SSD** though, so it would be fantastic if this bug were fixed.

You'll probably be fine [http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)

---

### Post by mattlach on 2014-07-16
> **tgm4883 said:**
> You'll probably be fine [http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)

I'm comforted by the Samsung 840 Pro doing as well as it did, though mine is a 128GB model, not the 256 which they use, which likely means shorter life.

I got the Pro model for my server for that reason, as I knew it would be more write intensive of an environment than in my desktop.

That being said, at about 60GB of writes per day, it won't last indefinitely, but hgopefully it will last long enough that it's replacement will be cheap when the time comes!

---

### Post by mattlach on 2014-07-16
I consider Anandtech to be the best source for information on all things SSD.

According to [this test comparing TLC (840 EVO) and MLC (840 Pro)](http://www.anandtech.com/show/6459/samsung-ssd-840-testing-the-endurance-of-tlc-nand), the 128GB Pro should last 35 years at 10GB of writes per day.

In my usage scenario with an estimated 60GB per day of writes, I should get ~5.8 years out of it, at which point in time, it will be old, slow and small compared to what can be had cheaply on the market.

---

