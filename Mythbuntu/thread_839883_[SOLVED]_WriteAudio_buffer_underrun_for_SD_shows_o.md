---
title: "[SOLVED] WriteAudio: buffer underrun for SD shows only (HD plays back fine)"
date: 2008-06-24
forum: Mythbuntu
---

### Post by dsegel on 2008-06-24
My system is based on an ASUS M2NPV-VM mobo with built-in nVidia 6150 graphics and an AMD 64 X2 5000 CPU. The capture cards are a pcHDTV-5000 and a PVR-150. Mythbuntu is the latest, with weekly patches applied. Output is at 1920x1080p.

HD recording and playback works beautifully, but when I record an SD show off of a digital channel it plays back with a great deal of stuttering and the get "WriteAudio: buffer underrun" messages in the mythfrontend.log. CPU usage rarely goes above 11%.

Most threads about this error focus on high CPU usage, but that's clearly not the case here.

Any ideas on what I can tweak/change to fix this?

---

### Post by volkswagner on 2008-06-24
I wish I knew.  

Are you using pulse audio or alsa?  In frontend setup, what are your audio settings?  Do you get any other errors in the log?

Some people had luck changing max channels to 2.  They still received multi channel audio after this.  Odd I know.

EDIT:  Does live TV have the same result for HD and SD?

---

### Post by dsegel on 2008-06-25
Well, I was just typing up answers to all your questions and I noticed it was happening on HD shows recorded in the past day as well, so now I have to assume this is the result of the last update I did.

The logfile for mythfrontend looks like this:

```

2008-06-24 22:31:17.617 TV: Changing from None to WatchingPreRecorded
2008-06-24 22:31:17.618 Using realtime priority.
2008-06-24 22:31:17.720 OpenGLVideoSync()
2008-06-24 22:31:17.750 Video timing method: SGI OpenGL
2008-06-24 22:31:17.795 AO: dropping back audio_buffer_unused
2008-06-24 22:31:17.826 AO: dropping back audio_buffer_unused
2008-06-24 22:31:17.859 AO: dropping back audio_buffer_unused
2008-06-24 22:31:17.864 AO: dropping back audio_buffer_unused
2008-06-24 22:31:17.899 AO: dropping back audio_buffer_unused
2008-06-24 22:31:17.904 AO: dropping back audio_buffer_unused
2008-06-24 22:31:17.909 AO: dropping back audio_buffer_unused
2008-06-24 22:31:17.914 AO: dropping back audio_buffer_unused
```

I'm going to try a different (older) frontend and also look through the recent updates to see if anything sticks out.

---

### Post by dsegel on 2008-06-27
For the benefit of anybody else with a similar problem who finds this thread, I did eventually fix this problem.

It turned out to be caused by me changing the primary audio output to ALSA:default instead of ALSA:hw:0,0

The 'default' device is supposed to be aliased to the hw:0,0 device, but there's clearly some additional processing or translation going on there. Once I switched back to hw:0,0 everything played fine again.

Note that this is for an intel_hda audio chipset on an nVidia mobo. I'm not suggesting that this solution will help anybody else experiencing audio buffer issues, but changing the audio settings in Mythfrontend and/or your ALSA config may help.

---

