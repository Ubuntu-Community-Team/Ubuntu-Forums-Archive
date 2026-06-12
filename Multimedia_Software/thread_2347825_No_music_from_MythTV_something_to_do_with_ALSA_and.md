---
title: "No music from MythTV: something to do with ALSA and prealloc?"
date: 2016-12-29
forum: Multimedia Software
---

### Post by Adam_Jacobs on 2016-12-29
I have a MythTV 0.27 system running on Ubuntu 14.04, which will not play music.

The sound is obviously working at some level, because I can play TV and watch TV recordings and the sound works just fine. But when I try to play music, it looks like it's playing, but no sound comes out of the speakers.

Here is what I found in the mythfrontend log when I tried:

```

Dec 29 08:41:47 htpc mythfrontend.real: mythfrontend[2261]: I CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse: PulseAudio suspend OK
Dec 29 08:41:47 htpc mythfrontend.real: mythfrontend[2261]: I CoreContext audio/audiooutputbase.cpp:792 (Reconfigure) AOBase: Opening audio device 'iec958:CARD=CMI8768,DEV=0' ch 2(2) sr 44100 sf signed 32 bit reenc 0
Dec 29 08:41:47 htpc mythfrontend.real: mythfrontend[2261]: E CoreContext audio/audiooutputalsa.cpp:783 (SetParameters) ALSA: Requested 500000us got 185759 buffer time
Dec 29 08:41:47 htpc mythfrontend.real: mythfrontend[2261]: E CoreContext audio/audiooutputalsa.cpp:242 (IncPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm2p/sub0/prealloc
Dec 29 08:41:47 htpc mythfrontend.real: mythfrontend[2261]: N CoreContext mythmainwindow.cpp:2737 (PauseIdleTimer) Suspending idle timer

```

I was mightily impressed that the log file not only reported an error, but even gave a suggestion for fixing it! So I tried its suggestion and executed the following command:

```
echo 128 | sudo tee /proc/asound/card0/pcm2p/sub0/prealloc
```

When I tried again, there was still no sound, but the log file was subtly different:

```

Dec 29 08:54:39 htpc mythfrontend.real: mythfrontend[2261]: I CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse: PulseAudio suspend OK
Dec 29 08:54:39 htpc mythfrontend.real: mythfrontend[2261]: I CoreContext audio/audiooutputbase.cpp:792 (Reconfigure) AOBase: Opening audio device 'iec958:CARD=CMI8768,DEV=0' ch 2(2) sr 44100 sf signed 32 bit reenc 0
Dec 29 08:54:39 htpc mythfrontend.real: mythfrontend[2261]: E CoreContext audio/audiooutputalsa.cpp:783 (SetParameters) ALSA: Requested 500000us got 371519 buffer time
Dec 29 08:54:39 htpc mythfrontend.real: mythfrontend[2261]: N CoreContext mythmainwindow.cpp:2737 (PauseIdleTimer) Suspending idle timer

```

So it seems that ALSA is requesting 500000us and not getting it. After executing the command above, it got twice as much as it did before, but it still wasn't enough.

So I figured that perhaps I could increase whatever I had increased before (I don't really understand what ALSA is doing here, just following the instruction in the log file and hoping for the best) some more and then it would be enough.

```
echo 256 | sudo tee /proc/asound/card0/pcm2p/sub0/prealloc
```

However, that didn't actually change the contents of the prealloc file. I then noticed that there was another file called prealloc_max which was set to 128, so I wondered if 128 was some kind of limit above which prealloc can't go. So I tried to change the contents of prealloc_max in the same way, but it was ignored. Manually editing it also didn't work: it just immediately reverted to 128.

I am now stumped. ALSA is requesting something bigger than my system is prepared to give it. I assume that is the reason why I don't get any sound from the music?

How can I either tell my system to give ALSA what it wants or tell ALSA not to ask for so much?

Or have I completely misunderstood what's going on here anyway?

---

### Post by Adam_Jacobs on 2016-12-30
I thought having useful suggestions in the log file for how to fix errors looked too good to be true. Turns out this had nothing to do with the prealloc file.

I tried fiddling with some of the audio settings to see if that helped, and there was a box for "upscale stereo to 5.1 surround" (or words to that effect) in the audio settings, which was not ticked. Ticking it fixed the problem.

---

