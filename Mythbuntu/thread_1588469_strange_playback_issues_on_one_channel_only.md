---
title: "strange playback issues on one channel only"
date: 2010-10-04
forum: Mythbuntu
---

### Post by itlarson on 2010-10-04
I am having strange playback issues on one 720p atsc channel.  Sometimes sound will be normal, but the picture will race ahead far out of sync.  Sometimes sound will play for a few seconds, then stop, restarting when I skip ahead, or back, but again only for a few seconds.  Other times audio will be fast forward.  

Signal strength is good, and other 720p and 1080i channels play well.  Old recordings from this channel play well.

Here are some frontend log messages from during playback:

2010-10-04 22:39:10.933 TV: Attempting to change from None to WatchingRecording
2010-10-04 22:39:11.003 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-10-04 22:39:11.005 Using protocol version 56
2010-10-04 22:39:11.268 AFD: Opened codec 0xa98c1de0, id(MPEG2VIDEO) type(Video)
2010-10-04 22:39:11.268 AFD: codec AC3 has 6 channels
2010-10-04 22:39:11.269 AFD: Opened codec 0xa98c2360, id(AC3) type(Audio)
2010-10-04 22:39:11.269 AFD: codec AC3 has 2 channels
2010-10-04 22:39:11.270 AFD: Opened codec 0xa493f810, id(AC3) type(Audio)
2010-10-04 22:39:11.279 Opening audio device 'spdif'. ch 2(6) sr 48000 (reenc 0)
2010-10-04 22:39:11.279 Opening ALSA audio device 'spdif'.
2010-10-04 22:39:11.312 Opening audio device 'spdif'. ch 2(6) sr 48000 (reenc 0)
2010-10-04 22:39:11.313 Opening ALSA audio device 'spdif'.
2010-10-04 22:39:11.372 Opening audio device 'spdif'. ch 2(2) sr 48000 (reenc 0)
2010-10-04 22:39:11.373 Opening ALSA audio device 'spdif'.
2010-10-04 22:39:12.497 VDPAU: Created 2 output surfaces.
2010-10-04 22:39:12.497 VDPAU: Created VDPAU render device 1920x1080
2010-10-04 22:39:12.677 NVP(7): Forcing decode extra audio option on (Video method requires it).
2010-10-04 22:39:12.678 OSD Theme Dimensions W: 1280 H: 720
2010-10-04 22:39:12.903 The realtime priority setting is not enabled.
2010-10-04 22:39:12.903 TV: Changing from None to WatchingRecording
2010-10-04 22:39:12.916 OpenGLVideoSync()
2010-10-04 22:39:13.231 Video timing method: SGI OpenGL
2010-10-04 22:39:13.263 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-10-04 22:39:14.785 WriteAudio: buffer underrun
2010-10-04 22:39:15.035 WriteAudio: buffer underrun
2010-10-04 22:39:15.250 WriteAudio: buffer underrun
(repeats)

 I've also seen the following repeating message:
 ERROR: Audio buffer overflow, 26897409 audio samples lost!

any ideas?

---

### Post by ian dobson on 2010-10-05
Hi,

It could well be that the channel encoding (from your provider) is abit screwed up. Could you try playing the video with vlc/mplayer to see if it's doing the same.

Also I see you still running version 0.23, the mythbuntu team have a repositry containing the fixes branch (0.23-1), the update fixed afew playback problems on 2 channels on my system.

If you feel "brave" enable the autobuilds and do an update, you'll then get 0.23-1. 

Regards
Ian Dobson

---

### Post by itlarson on 2010-10-05
Thanks.  I'd rather not try anything expirimental I don't have to.  

What's the easiest way to find a recording in the storage directories?  Isn't there some script which makes all the file names human readable?

---

### Post by ian dobson on 2010-10-05
Hi,

The filename is ChannelNumber_StartDateTime so just find a recording with the correct channel number.

The fixes branch is actually fairly safe/stable it just contains bug fixes for 0.23 and no new features.

Regards
Ian Dobson

---

### Post by LowSky on 2010-10-05
just to point out when *buntu was released, it was released with a fairly buggy version of Mythtv. Upgrading to the autobuild fixes many of the issues users have been plagued with.

---

### Post by itlarson on 2010-10-05
I don't think I'm getting how to to enable the autobuilds.  I downloaded the package from  [http://www.mythbuntu.org/auto-builds]("http://www.mythbuntu.org/auto-builds"), went through the dialogs it opened, choosing 0.23.1, updated, and rebooted. My frontend log shows no change though:

2010-09-23 20:00:05.926 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)

2010-10-05 19:00:56.902 mythbackend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)

There is no change in the playback issue.  

Is there a guide on the web how to do this?  I haven't been able to find one.

Oh- I have tried playing a recording in vlc.  It stutters occasionally, but mostly plays acceptably.

---

### Post by itlarson on 2010-10-06
I'm willing to do a full re-install if necessary. Is there any way to know if this would solve the problem?

---

### Post by itlarson on 2010-10-10
Here's a new development.  I checked another mythbox (the one I built for my parents), and it has the exact same problem with that channel.  Both are running 10.4.  When I find the time, I would like to record a short clip, and find a way to post it.  Possibly others can see if it plays on their systems, then.  If it doesn't, I can use it as part of a bug report. What's the best way to post something like that?

---

### Post by marcw on 2010-10-10
> **itlarson said:**
> I am having strange playback issues on one 720p atsc channel.  Sometimes sound will be normal, but the picture will race ahead far out of sync.  Sometimes sound will play for a few seconds, then stop, restarting when I skip ahead, or back, but again only for a few seconds.  Other times audio will be fast forward.  

any ideas?

You wouldn't happen to live in the Twin Cities and be referring to KSTP, would you?

---

### Post by itlarson on 2010-10-11
Yup, that would be it.  Are you having the same problem?

---

### Post by marcw on 2010-10-11
> **itlarson said:**
> Yup, that would be it.  Are you having the same problem?

I was.  Fixed now.  I found this thread:
[http://www.gossamer-threads.com/lists/mythtv/users/455048](http://www.gossamer-threads.com/lists/mythtv/users/455048)

It detailed why we were having problems with just that channel.  Short answer: KSTP's new encoder broke things.  When the debug logs were presented to the myth devs they wrote a workaround and committed it.  I waited a day until those fixes would show up in the Mythbuntu daily AutoBuilds and applied it from there.  Works great.

---

### Post by itlarson on 2010-10-11
I'll try it tonight.  I'm wondering if there's someone's grandmother somewhere with an off brand hd to sd converter box having the same problem.

---

### Post by marcw on 2010-10-11
Good question.  Not sure about the grandmother part but I'll have to test out my own converter that's been gathering dust in the basement.

---

### Post by itlarson on 2010-10-12
Good news!  a fix has been pushed down.  I had to choose .23.1 autobuilds in mythbuntu control center, as .23 didn't work.  Once I did, just running sudo apt-get update;sudo apt-get upgrade did the trick.  My theme was slightly scrambled by this, but going through the "appearance" part of setup redrew it correctly.

---

### Post by jrockinl on 2010-10-15
I am in Twin Cities and ABC channel 5 (KSTP) has been bad for two weeks for me.  (Really sucked when I came to watch the Vikes MNF game)  I thought they changed something, but I haven't contacted them.  I did re-scan all channels and the problem didn't go away.  I then noticed my TV reported low signal strength and thought that may have caused it but I haven't had time to check into this further.  Straight into the TV has one extra splitter that MythTV computer doesn't have.

I will try the VLC idea too.

---

### Post by marcw on 2010-10-15
> **jrockinl said:**
> I am in Twin Cities and ABC channel 5 (KSTP) has been bad for two weeks for me.  (Really sucked when I came to watch the Vikes MNF game)  

Did you even read this thread?  Specifically my post #11?  This issue has been solved.

---

### Post by jrockinl on 2010-10-15
oops, didn't see the second page and therefore missed the solution.

Sorry for the post.

---

### Post by jrockinl on 2010-10-15
BTW: How do you get the "[Solved]" part in the message header?  It would be helpful here.  I needed to do that in the past and didn't see how people do it.

---

### Post by marcw on 2010-10-15
> **jrockinl said:**
> BTW: How do you get the "[Solved]" part in the message header?  It would be helpful here.  I needed to do that in the past and didn't see how people do it.

I agree.  Aside from the original poster editing his post and modifying the thread name (I've done that), I have no idea.  I'll modify this singular post and see if it sticks.

---

