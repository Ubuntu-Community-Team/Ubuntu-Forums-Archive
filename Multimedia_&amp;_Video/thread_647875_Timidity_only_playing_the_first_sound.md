---
title: "Timidity only playing the first sound"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by Gilven on 2007-12-22
Hi.

I've been trying to get software synthesis for midi working.  I've followed the guide at [https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)

Trying to play a file directly with 'timidity somefile.mid' works perfectly.  However, when I try to use other midi programs (Eg: pmidi and aplaymidi), only the first note of a song is played, and then the program sits around doing nothing.  

Looking at /proc/asound/seq/queues while aplaymidi is running shows something like this:

queue 0: [Queue-0]
owned by client    : 128
lock status        : Locked
queued time events : 0
queued tick events : 0
timer state        : Running
timer PPQ          : 96
current tempo      : 500000
current BPM        : 120
current time       : 0.000000000 s
current tick       : 0

queue 1: [aplaymidi]
owned by client    : 129
lock status        : Locked
queued time events : 0
queued tick events : 500
timer state        : Running
timer PPQ          : 480
current tempo      : 500000
current BPM        : 120
current time       : 0.000000000 s
current tick       : 0

My soundcard is an Intel HD Audio.
From lspci: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I'm using alsa-driver 1.0.15 (the in-kernel ALSA did not work for me.)

Has anyone got any ideas about what could be causing this, and how I can fix it?

Edit: It seems that this isn't a problem with Timidity, but perhaps ALSA.  Using FluidSynth instead of Timidity makes no difference.

---

