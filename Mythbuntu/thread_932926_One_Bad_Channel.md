---
title: "One Bad Channel"
date: 2008-09-28
forum: Mythbuntu
---

### Post by uncle hammy on 2008-09-28
I am having an issue, and I am trying to track down the cause.  I have one channel (and only one with this problem) that the video "spurts" almost like it's in fast forward, then it slows down and catches up, and it keeps doing this.  As a result, the audio gets WAY out of sync, and is about 2 seconds behind the video itself.

I have found that when I set "Enable Open GL veritcal sync for timing" on, the problem seems to disappear.  Now, I have just started playing with this, because I have had 2 shows almost unwatchable with the audio sync problem.   So my tests tonight have been on live tv (which also has the problem) only, as I have nothing else recorded on this station right now. 

My question is, has anyone else seen this issue, and does it make sense that I only have it with one channel?

Could this also be an issue with the tuner itself?  I have 2 HDHomeRuns.  I just purchased the second one and added it to my setup, and have a support ticket in on it, because it is reporting much higher signal strengths than my original one does, and yet experiences a lot of artifacting and sound drops that the first one doesn't (on the same channel at the same time).  Yesterday, it just stopped tuning a station for an hour (the same station that is the problem above), while the original unit was tuning it no problem.  However, this particular station is a problem regardless of the tuner being used to view/record it.

---

### Post by uncle hammy on 2008-09-30
OK, well they are running diagnostics on my HDHomeRun units, but I have a feeling they are going to come back and say it's a Myth issue, because when viewing TV through windows/hdhomerun manager/VLC player (that's how they gather their logs), things seem to be normal.

I managed to record some shows off the bad channel, and the the video was stuttering again, and the audio way out of sync.  When I flipped on the "Enable Open GL veritcal sync for timing" setting, it resolved those issues.  However, enabling that setting produces a horizontal flickering line at the very top of the screen about 30 pixels in height during high motion.  That seems to be reduced by turning off "Sync to VBlank" in the NVidia Setting App.

So I guess I am still with the same question, does it make sense to have this issue with only one channel, requiring these settings to fix it?  Maybe (likely) I am missing something, but I would assume that all streams coming in would be treated the same way.

Thanks

---

### Post by netslacker on 2008-09-30
have you tried using the command line tools under linux? you can use them to record to hdd and review the recording, removing myth from the mix but still operating in linux.  Try that.

I have a version 2 hdhomerun for my tuner (version 2 supposedly has better reception, that's why you see better numbers with your second tuner), and had trouble recording one or two channels.  Using the command line diagnostics tool I was able to record super clean tv, but under myth it wasn't working so hot.  A few things to check... there are two ways to tune channels under myth, only one way really works with hdhomeruns (I can't recall for sure what's what, but there is a checkbox in myth setup, check the box) - one way is by program id and the other is by channel - something like that.  After I determined the correct way I rescanned the channels and that helped.

Also, check your de-interlacer that is used.  If you have ATI vid card you can't use bob, which is default on one of the profiles.  Change playback profile to see if that helps.

But seriously, get the command line tool:
```
sudo apt-get install hdhomerun-config
```
then on their site you can get samples on how to use it, or you can type:
```
hdhomerun-config -?
```
for a quick look on how to use it.  You can even use the command line to scan for channels and get signal strengths etc.  It was quite handy for me to diagnose issues.

My other idea, if you have two hdhomeruns on the same 100mb network, could it be that you are saturating the network recording 4 HD shows at once?  and hence, one of the shows is suffering packet drops because the network can't keep up? just another thought, something to keep in mind that a full HD show can be as much as 19mb/s.

---

### Post by uncle hammy on 2008-09-30
I am with you on the network thought, I even ordered a gigabit switch yesterday, just in case.  Though I don't actually think it is the cause, because this video stutter / audio sync issue occurs even when I am only recording that channel alone.  I also have had no problems recording 4 channels at once as long as the bad channel isn't one of them.

I am using Bob, but I have a NVidia 7600GS, never had a problem with Bob.

I am very interested in in your "two ways to tune channels under myth" suggestion.  Do you recall where I would look for this setting?  Is it in backend setup / general perhaps?  I have been all over settings, and don't recall ever seeing anything like you're mentioning.

Thanks,
Scott

---

### Post by netslacker on 2008-09-30
yeah, it's in the backend setup. Under the input connections there is a drop down called: "Use Quick Tuning" and then various selections, I don't recall which one I am using (I'm at work) but try different drop downs.  Then rescan your lineup.  

Although, more importantly, have you tried playing the recorded file using VLC?  If not, try playing the recorded file OUTSIDE of myth.  This will tell you if the recording process is fine or if it's the playback process in myth. Navigate to the recording directory and you'll need to figure out which file it is.. the first four numbers are the channel number so that should help you.  If you play the file using VLC and it is fine, then something is messed w/ myth during playback (change playback settings), if it does not play fine then there is a problem in recording it.. could be myth - maybe not - but the above suggestion may apply to you in this scenario.  Use the tool in my previous post to record 30 seconds or so of video from the command line, play it back and check it for quality. Post back results.

Another tip I learned: uncheck "unencrypted" channels only (when I did this I had more channels than before, apparently some broadcasters incorrectly set this bit so you may be missing channels). Probably will not help your current situation but I tell everyone to uncheck this.

---

### Post by larsolav on 2008-09-30
> **netslacker said:**
> 
My other idea, if you have two hdhomeruns on the same 100mb network, could it be that you are saturating the network recording 4 HD shows at once?  and hence, one of the shows is suffering packet drops because the network can't keep up? just another thought, something to keep in mind that a full HD show can be as much as 19mb/s.

I don't think going to a gigabyte router will help much either, because according to [http://www.silicondust.com/products/hdhomerun](http://www.silicondust.com/products/hdhomerun) it only has a 100 BASE ethernet port (maybe it has changed without them updating the website?).

---

### Post by uncle hammy on 2008-09-30
Yes, it's true the HDHomeRun only has 100Base ethernet port, so a gigabit switch won't increase the volume of traffic the HDHR units can transmit. However, the switch was quite in expensive, and a gigabit connection on the server end will increase the amount of traffic the backend server can handle at once.  Since there are 2 seperate units, each capable of putting out x at the same time, if I increase the amount the single server can accept, it should reduce any bottle neck at the server end.

---

### Post by uncle hammy on 2008-09-30
netslacker,

Thanks for the help!  I have a bunch of stuff recording from the bad channel on Thursday.  I will try playing the raw files with VLC and let you know how it goes.

---

### Post by larsolav on 2008-10-01
> **uncle hammy said:**
> Yes, it's true the HDHomeRun only has 100Base ethernet port, so a gigabit switch won't increase the volume of traffic the HDHR units can transmit. However, the switch was quite in expensive, and a gigabit connection on the server end will increase the amount of traffic the backend server can handle at once.  Since there are 2 seperate units, each capable of putting out x at the same time, if I increase the amount the single server can accept, it should reduce any bottle neck at the server end.

Ahhhh, yeah. That is true. Don't know what I was thinking... I'll put on my dunce hat now....](*,)

Hope the other recordings from the bad channel worked!

---

### Post by uncle hammy on 2008-10-01
OK, well I had some programs recorded on the "bad" channel tonight, and I tried your experiment.  They played just fine with VLC outside of Myth.  Played in myth fine with "Enable OpenGL veritcal sync for timing", and unwatchable audio/video sync without it.  

The issue only seems to occur with HD programs, so I am wondering if it is something in the transport stream in the station is broadcasting its signal?

---

### Post by netslacker on 2008-10-02
is it only 1080 HD programs? or are 720 effected too?

At this point, I'm out of ideas.  I'd say the HDHomeRun is not the problem as recordings playback fine in other programs.  This is really similar to the issue I struggled with but for me it was all channels and wasn't isolated to just one.  Altering some playback options in myth is what resolved it for me... 

Sorry I don't have anything else... good luck though.

---

### Post by uncle hammy on 2008-10-02
The channel is broadcast in 720p.  The audio sync issue only shows up with an actual 720p show (i.e. It's there for Grey's Anatomy and Lost, but not for the local news).  I actually have 2 ABC stations, and the second one does not experience this issue, though it is a much weaker station for me to rely on.

Like I said, the "Enable OpenGL Vertical Sync for Timing" resolves the issue.  I am just one of those weirdos who hates the idea of enabling a setting globally to fix a problem that is only occurring on one station.

Thanks for the help though!

---

### Post by uncle hammy on 2008-10-02
OK, one more thing to throw into the mix here, perhaps it will trigger some ideas. 

I watched the two programs from last night that were recorded off my problem channel.  While "Enable OpenGL Vertical Sync for Timing" has the audio and video playing nicely together, something jumped out at me.  Both shows were one hour shows, however the OSD showed them both as 30 minutes long.  As well, as I was watching, 1 minutes of elapsed watch time only registered 30 seconds in the progress meter.  In other words, something in the playback or recorded stream has the time compressed by a factor of 2.  To really mix it up :), if i hit the jump button (10 minutes forward) it jumped 10 minutes in the compressed time frame (3 jumps to go through the entire hour).  

Does this add up to anything of note to anyone?

---

### Post by uncle hammy on 2008-10-04
Upon further viewing, I have noticed that I have a second channel that has this "time" issue, though not nearly to the extent of the first one ("losing" 30 minutes for every hour).  It consistently "loses" about 10 minutes of time for every hour of recording time.

I have switched TO "Use Quick Tuning" = never, which does not seem to have any effect.  Other than that, with the HDHomeRun, there seems to be very few recording options that can be set.

Does anyone else have any ideas how I can try to resolve this time issue?

---

