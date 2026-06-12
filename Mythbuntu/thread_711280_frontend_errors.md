---
title: "frontend errors"
date: 2008-02-29
forum: Mythbuntu
---

### Post by 4dognight on 2008-02-29
I get these errors in my frontend log, every once in a while. I do notice pauses when these happen, and beleive they are the cause of the sound and video hiccups I seem to be experiencing.

2008-02-29 11:27:02.301 WriteAudio: buffer underrun
2008-02-29 11:28:52.807 NVP: prebuffering pause
2008-02-29 11:28:53.043 WriteAudio: buffer underrun
2008-02-29 11:28:54.727 NVP: prebuffering pause
2008-02-29 11:29:09.378 NVP: prebuffering pause
2008-02-29 11:29:09.538 WriteAudio: buffer underrun


Anyone got an idea what to do about these?

---

### Post by newlinux on 2008-02-29
These can be caused by a lot of things:

CPU overworked
Playback settings
XvMC
etc...

I know you have probably told me this before, but what are your system specs and what type of programming does this occur on, are you using XvMC, etc...

---

### Post by 4dognight on 2008-02-29
My setup is
Abit An-M2 Mb, has buitin nvidia graphics 7025 with DVI out, and
builtin Audio, both analog ALC883 chipset and HDA SPDIF(not using)
2 GB memory (256 used for video)
AMD be-2300 (dual 1.9 ghz)

I use vmstat while playback is on, and it is usually shows around 60% idle when watching  HD coming from my STB via firewire. I dont think my CPU is being overloaded.

I dont use XvMC, I used libmpeg. I heard XvMC is a no-no for HD.
My Audio is set to ALSA:default with default for mixer.

Anything else I need to provide?

---

### Post by newlinux on 2008-03-01
What about the extra audio buffering setting, use video as a timebase, etc. I recommend you play with those, and even switch from libmpeg to standard and see how that works.

BTW XvMC is most useful for HD, but if your processor is fast enough to run HD without it, don't use it.

Also try playing the same recordings with mplayer, and see if you get the audio and video dropouts. This will let you know if it is myth specific or not. Does this happen on liveTV, recordings or both?

---

