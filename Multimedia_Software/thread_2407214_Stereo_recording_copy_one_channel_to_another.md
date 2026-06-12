---
title: "Stereo recording: copy one channel to another"
date: 2018-12-01
forum: Multimedia Software
---

### Post by misterrollton on 2018-12-01
I am using a stereo microphone and the  problem is that it's not working as expected: while recording, left  channel gives me a lot of noise and the right one records just fine.  I've confirmed that my mic is broken, not the PC, but I've found a way  to ignore this problem on Windows: using Equalizer APO, I'm muting the  left channel altogether and then copy a signal from right to left to at  least create an illusion of stereo. This way I don't have to edit my  audio clips when recording AND not experience voice chat problems in  some games which, apparently, only listen to a sound from the left  channel. On (K)Ubuntu, though, I've only found a way to mute one channel by  using PulseAudio Volume Control, but not copy from one to another. So,  is there even a way to do so?

---

### Post by ajgreeny on 2018-12-01
I'm not totally sure but I think you may be able to do this with audacity, though I've never tried.

Look also at the **-map_channel** section in ```
man ffmpeg
``` which can do what you want with a single command by the looks of it.

Though I use ffmpeg a lot I have never needed to do what you want so I can't say anything from personal experience.

EDIT:
To satisfy my own curiosity I have just made a search of the audacity options and it is easy to use Edit -> Duplicate to turn a single mono channel into 2 channels, ie, exactly what you need.

---

### Post by misterrollton on 2018-12-02
AFAIK those two options you provided require recording a clip first and then editing it to duplicate audio. What I want is to copy sound data from one channel to another on the fly so that Skype, Discord and whatever would work flawlessly, too.
One thing I've tried to do is to use a PCM plugin for ALSA named "copy", but never really figured out how it works.

---

### Post by nik.charles on 2018-12-02
Skype only uses left channel, but remixes right channel to left, so can just kill volume on right channel and sound to callers will be no different

for anything else that uses stereo add Pulseaudio module [URL="https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index13h3"]module-remap-source

[/URL]

---

