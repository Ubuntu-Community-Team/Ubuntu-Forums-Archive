---
title: "Lost simultaneous use of ALSA and PulseAudio"
date: 2010-11-07
forum: Multimedia Software
---

### Post by FlameReaper on 2010-11-07
Hello.

I am using Ubuntu 10.04 LTS "Lucid Lynx", and has been encountering problems with audio recently.

I found out for some reason that my system fails to produce sound through PulseAudio, especially when an application is using it (e.g Audacious).

The details of the problem:

1. I am using the PulseAudio Equalizer from the repository, and I set a program (e.g. Audacious) to use PulseAudio so that I can activate the equalizer.

2. While playing, all of my other applications lose the ability to produce any sound, and changing back to ALSA during playback (which is using PulseAudio) in Audacious indicates that the device is busy. Examples include the loss of sound while playing a video from YouTube.

Rough breakdown of what I want to (be able to) do: Have sound for all applications using it, for example being able to play a video in YouTube from my browser AND play music in Audacious simultaneously.

Is there a workaround for this? I'd like to think that there is, but so far my search returned nil.

Any help would be greatly appreciated.

---

### Post by FlameReaper on 2010-11-07
Nevermind, looks like following an old guide to add /etc/asound.conf worked for me, sound's back from everything now. :D

---

