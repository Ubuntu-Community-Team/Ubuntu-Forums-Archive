---
title: "Strange LiveTV jerkyness"
date: 2009-01-19
forum: Mythbuntu
---

### Post by scary_jeff on 2009-01-19
Hi

I'm pretty sure I didn't have this problem when I first installed, but now every time I watch LiveTV, and most times I change to a different channel, the video will 'skip' about four times a second. The audio is fine.
To solve the problem, all I have to do is press 'J' and then 'U', to change the playback speed, and return it to 1x. U then J works as well, but pausing and then resuming does not.
This is the frontend log output for changing a channel (which then has jumpy video), then pressing J followed by U, fixing the video:

```
2009-01-19 19:30:14.669 Mixer unable to find control PCM
2009-01-19 19:30:14.670 Mixer unable to find control PCM
2009-01-19 19:30:15.578 NVP: prebuffering pause
2009-01-19 19:30:15.659 WriteAudio: buffer underrun
2009-01-19 19:30:17.504 Mixer unable to find control PCM
2009-01-19 19:30:17.504 Mixer unable to find control PCM
2009-01-19 19:30:18.647 NVP: Prebuffer wait timed out 10 times.
2009-01-19 19:30:20.322 NVP: Prebuffer wait timed out 10 times.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 544 x 576
2009-01-19 19:30:20.904 AFD: Opened codec 0xafa44890, id(MPEG2VIDEO) type(Video)
2009-01-19 19:30:20.904 AFD: codec MP3 has 2 channels
2009-01-19 19:30:20.904 AFD: Opened codec 0xb08917a0, id(MP3) type(Audio)
2009-01-19 19:30:20.904 AFD: Opened codec 0xafa43e80, id(DVB_SUBTITLE) type(Subtitle)
2009-01-19 19:30:20.904 AFD: codec MP3 has 1 channels
2009-01-19 19:30:20.905 AFD: Opened codec 0xafadd4a0, id(MP3) type(Audio)
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 544 x 576
2009-01-19 19:30:40.408 WriteAudio: buffer underrun
```

Any idea what could cause this? I'm happy to post the output of any other log file if required.

---

### Post by scary_jeff on 2009-01-22
I had a look at the backend log and didn't see anything relating in time to when I altered playback speed. The other new bit of information is that entering and exiting the Programme Guide will also solve the jerkness.

Even a hint of an idea of what might cause this would be good.

---

### Post by scary_jeff on 2009-01-26
I just noticed that changing to a channel that is on the same multiplex as the current channel will not lead to a jerky stream. Also, I tried 'MeTV', some gnome TV app, and it does not have any jerkyness problem. Does this prove it's not a hardware issue?

---

### Post by scary_jeff on 2009-01-30
I suppose I'll keep resurrecting this until I find a solution. I have noticed that I will also rarely get the stuttering after pausing LiveTV, then resuming it. Also, sometimes after changing inputs, the stream will NOT be stuttering.
Is there anything I can do to try and diagnose this? Obviously nobody has heard of the problem I'm having, but I don't know where to begin other than checking logfiles (which didn't seem to tell me anything).

---

### Post by scary_jeff on 2009-02-06
OK, now I've changed my fastforward and rewind keys to be sticky. When watching a recording, if I fastforward and then return to normal playback, the same jerkyness will be present. In this case, entering the guide doesn't fix it (I guess because when watching recordings, there's no video thumbnail in the corner?). Does this give any more clue as to what's going on?

---

