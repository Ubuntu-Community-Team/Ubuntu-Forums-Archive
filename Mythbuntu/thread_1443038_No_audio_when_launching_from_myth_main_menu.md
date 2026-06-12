---
title: "No audio when launching from myth main menu"
date: 2010-03-30
forum: Mythbuntu
---

### Post by Lepy on 2010-03-30
Yesterday I needed to record some audio on a laptop I use as a frontend. I tried to get recording from the microphone jack to work by fiddling with Mixer and Sound Recorder. I also installed audacity and serpentine. I thought I put all the options back to where they were and used a different laptop.

Now, sound in mythtv is working fine, but if I launch XBMC from the main menu, there is no sound and video plays in slow motion. If I close the mythtv frontend and launch XBMC, sound works and there is no slow motion video. Launching from the main menu worked perfectly before I tried to get recording to work. I only changed options in Mixer and Sound Recorder and perhaps audacity.

I know this is not a mythbuntu specific question, but XBMC works fine when launched separately from mythtv. In Sound Recorder, the laptop device is currently set as Analog Stereo Duplex.

The only difference in XBMC logs are
when launched from the frontend:
```
14:56:16 T:3079157616 M:286195712  NOTICE: GL: NPOT textures are supported through GL_ARB_texture_rectangle extension
14:56:17 T:2491571056 M:271994880   ERROR: CDVDAudio::AddPacketsRenderer - timeout adding data to renderer
14:56:17 T:2491571056 M:271994880   ERROR: AddPackets - failed to add leftover bytes to render
14:56:18 T:2491571056 M:272142336   ERROR: CDVDAudio::AddPacketsRenderer - timeout adding data to renderer
14:56:18 T:2491571056 M:272142336   ERROR: AddPackets - More bytes left than can be stored in buffer
14:56:20 T:2491571056 M:272601088   ERROR: CDVDAudio::AddPacketsRenderer - timeout adding data to renderer
14:56:20 T:2491571056 M:272601088   ERROR: AddPackets - failed to add leftover bytes to render
14:56:21 T:3079157616 M:272449536  NOTICE: CDVDPlayer::CloseFile()
14:56:21 T:3079157616 M:272449536  NOTICE: DVDPlayer: waiting for threads to exit
14:56:21 T:2525137776 M:272449536  NOTICE: CDVDPlayer::OnExit()
14:56:21 T:2525137776 M:272449536  NOTICE: DVDPlayer: closing audio stream
14:56:21 T:2525137776 M:272449536  NOTICE: Closing audio stream
14:56:21 T:2525137776 M:272449536  NOTICE: Waiting for audio thread to exit
14:56:21 T:2491571056 M:272449536  NOTICE: thread end: CDVDPlayerAudio::OnExit()
14:56:21 T:2525137776 M:272449536  NOTICE: Closing audio device
14:56:21 T:2525137776 M:272367616  NOTICE: Deleting audio codec
``` 

and when launched without mythfrontend running
```
15:00:00 T:3078522736 M:382906368  NOTICE: GL: NPOT textures are supported through GL_ARB_texture_rectangle extension
15:00:08 T:3078522736 M:365211648  NOTICE: CDVDPlayer::CloseFile()
15:00:08 T:3078522736 M:365211648  NOTICE: DVDPlayer: waiting for threads to exit
15:00:08 T:2544655216 M:365211648  NOTICE: CDVDPlayer::OnExit()
15:00:08 T:2544655216 M:365211648  NOTICE: DVDPlayer: closing audio stream
15:00:08 T:2544655216 M:365211648  NOTICE: Closing audio stream
15:00:08 T:2544655216 M:365211648  NOTICE: Waiting for audio thread to exit
15:00:08 T:2484714352 M:365211648   ERROR: AddPackets - failed to add leftover bytes to render
15:00:08 T:2484714352 M:365211648  NOTICE: thread end: CDVDPlayerAudio::OnExit()
15:00:08 T:2544655216 M:365211648  NOTICE: Closing audio device
15:00:08 T:2544655216 M:365211648  NOTICE: Deleting audio codec
```

---

### Post by Lepy on 2010-04-02
Oddly, XBMC and Boxee were the only apps to not have sound when launched from the mythfrontend main menu. Hulu, emulators, etc worked fine. However, after a bunch of fudding around, the sound is fixed!

In XBMC, I set the audio device to custom (it used to be perfectly happy with default) and named the device "ALSA:default", the same as found in mythfrontend -> setup -> general.

Still baffled how audio was so fubared with no changes being made inside of myth or xbmc. audacity seems the most likely culprit, but who knows!

---

