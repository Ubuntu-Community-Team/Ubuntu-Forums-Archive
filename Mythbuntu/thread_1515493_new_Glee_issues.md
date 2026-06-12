---
title: "new Glee issues"
date: 2010-06-22
forum: Mythbuntu
---

### Post by mathog on 2010-06-22
Starting with the season finale Myth 0.21 has been having problems with Glee.  Up until that point it would record reliably, no glitches, and it would show 60 minutes duration.  Starting with the finale, it glitches frequently and the counter only shows 43 minutes or so.  Whole scenes are missing.  Now they are showing reruns and the reruns are glitching the same way - but they were fine when we watched them the first time they were broadcast.  No changes to Myth during this period.  

The broadcast station is KTTV 11 (Los Angeles).  One change is that Fox 11 now broadcasts as 11.1 (KTTV-DT), 11.2 (Fox-SD), and 11.3 (KTTV-DT3).  I do not recall the subchannels previously.  My guess is that when they started broadcasting the subchannels they changed the encoding on 11.1 broadcasts, and that is not sitting well with MythTV.  Presumably they split all the bandwidth which used to be in the one channel into the 3 new ones.  Strangely they are broadcasting the same thing on all 3 channels.  I have not rescanned channels in a while and we don't even have .2 and .3 available on our system.

Anybody experienced something similar and have helpful hints as to how to proceed?  Right now all I can think of is to rescan and then record on 11.1, 11.2, and 11.3 to see which of them is the most reliable.

Thanks.

---

### Post by superm1 on 2010-06-22
> **mathog said:**
> Starting with the season finale Myth 0.21 has been having problems with Glee.  Up until that point it would record reliably, no glitches, and it would show 60 minutes duration.  Starting with the finale, it glitches frequently and the counter only shows 43 minutes or so.  Whole scenes are missing.  Now they are showing reruns and the reruns are glitching the same way - but they were fine when we watched them the first time they were broadcast.  No changes to Myth during this period.  

The broadcast station is KTTV 11 (Los Angeles).  One change is that Fox 11 now broadcasts as 11.1 (KTTV-DT), 11.2 (Fox-SD), and 11.3 (KTTV-DT3).  I do not recall the subchannels previously.  My guess is that when they started broadcasting the subchannels they changed the encoding on 11.1 broadcasts, and that is not sitting well with MythTV.  Presumably they split all the bandwidth which used to be in the one channel into the 3 new ones.  Strangely they are broadcasting the same thing on all 3 channels.  I have not rescanned channels in a while and we don't even have .2 and .3 available on our system.

Anybody experienced something similar and have helpful hints as to how to proceed?  Right now all I can think of is to rescan and then record on 11.1, 11.2, and 11.3 to see which of them is the most reliable.

Thanks.
Sorry to say, but the easiest solution to this is probably to upgrade to a more recent build (0.22, or preferably 0.23).  The more recent builds have more recent ffmpeg in them which generally handles things like this better.

Even if it doesn't handle it better, 0.21 and 0.22 are no longer being looked at for bug reports, the developers have shifted focus to 0.23 and the in development 0.24.  So they'll want a bug report from 0.23  to be able to help fix this issue.

If you are wary of wiping your install or upgrading when it might not solve the issue, i'd recommend popping an extra hard drive in, do an install of 10.04 onto it, add the updated 0.23 auto-builds ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)) and see if the problem persists.  If it does, you can file a bug about it and get the right people looking at it without jeopardizing your current setup.  If it doesn't, then you have a solution to your problem.

---

### Post by LowSky on 2010-06-23
Is the one show the only show having these problems? It could be a tranmission problem during that hour, if you use OTA then maybe there is somekind of frequency issue.

First thing to try is a new channel scan. If you didn't do one since the station went digital or added the extra bands, then it is best that you do. Oddly I would think Fox in LA would have added these extra stations over a year ago when the FCC mandated the digital switch.

Also check the logs for errors the tuner card may be failing or another process is taking over the same PCI Bus. Try to disable commercial logging and/or transcoding to see if  the issue lies there.

If you can Upgrade to the newest version is a good idea as well. Better kernel support for tuner cards from the newest verisn of the Linux kerenl and new features for MythTV have been added.

---

### Post by mathog on 2010-06-23
Just for yucks tuned in directly to these three subchannels with the TV set's tuner (not the mythtv tuner).  Interestingly, channel 11.3 is basically unwatchable and has the same sort of skipping/dropping behavior as we are seeing with the Myth tuner.  The other two subchannels seem to be stable.  This was during another show (rerun of "The Simpsons").  However, when MythTV is set to 11.1 (the only one it offers right now) during other shows it doesn't skip/drop like it does when recording Glee.  

So there seems to be more than one issue here.

Will rescan now and hope for the best.

---

### Post by mathog on 2010-06-24
> **mathog said:**
> 
Will rescan now and hope for the best.

Tested 10 minute sections of "So you think you can dance".

```
#     Sig.Str.  Result
11.1  71%       some glitches seen
11.2  94%       (480i) OK, no glitches observed
11.3  100%      glitches constantly

```
So no perfect solution here.  Either record at 480i for a watchable recording or go 720(i?) on 11.1 with glitches.  Maybe updating to the latest myth will help, but I kind of doubt it.

It escapes me what Fox is trying to accomplish with 11.3, which isn't watchable even directly on a TV.  They should drop that channel and put the bandwidth back into 11.1.

---

### Post by LowSky on 2010-06-24
How are you recieving channels?

Over the Air, cable or something else?
What tuner card are you using?

Is only FOX the issue?

---

### Post by mathog on 2010-06-24
> **LowSky said:**
> How are you recieving channels?

Over the Air, cable or something else?
What tuner card are you using?

Is only FOX the issue?

Over the air via HDHomeRun tuner.  

Only FOX (11.x) recordings are glitching. 

It looks to me like when they went from a single subchannel (11.1) to three channels (11.1,11.2,11.3) they changed the encoding/bandwidth such that their only reliable channel is now the SD one.  Checked antennaweb and 11.3 doesn't show up, but both 11.1 and 11.2 are yellow, that is, the antenna is visible on Mt. Wilson from our house.

Ah, they apparently put in a new antenna too:

[http://www.avsforum.com/avs-vb/showthread.php?p=18819368](http://www.avsforum.com/avs-vb/showthread.php?p=18819368)

---

### Post by LowSky on 2010-06-24
I suggest you try adjusting your antenna, or maybe looking for a new one possibly amplified if you dont live very close to the source
here's a great link
[http://www.avsforum.com/avs-vb/showthread.php?t=1037779](http://www.avsforum.com/avs-vb/showthread.php?t=1037779)

---

### Post by mathog on 2010-06-24
> **LowSky said:**
> I suggest you try adjusting your antenna, or maybe looking for a new one possibly amplified if you dont live very close to the source
here's a great link
[http://www.avsforum.com/avs-vb/showthread.php?t=1037779](http://www.avsforum.com/avs-vb/showthread.php?t=1037779)

I don't think a better antenna is the answer here.  Mine works pretty well without amplification - it is is very similar to this one:  [http://uhfhdtvantenna.blogspot.com/](http://uhfhdtvantenna.blogspot.com/)

Signal levels on all 3 subchannels are good to excellent and the transmission antennas are only 7 miles away on top of Mt. Wilson in direct line of sight.  There are a few stations with antennas up there on the far side of a ridge, so not line of sight, plus many many tons of intervening rock, and none of those stations can even be tuned in.

---

### Post by mathog on 2010-06-25
The wife recorded Glee on 11.2 last night and it was OK. Only 480i, but at least no glitches.  The show was transmitted letterboxed, probably sampled down from 720p to fit into the 480i, so there was even less information in that program than for the usual SD broadcasts on that subchannel.

---

