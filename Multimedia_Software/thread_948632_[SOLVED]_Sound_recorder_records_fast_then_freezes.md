---
title: "[SOLVED] Sound recorder records fast then freezes"
date: 2008-10-15
forum: Multimedia Software
---

### Post by sublimation on 2008-10-15
Brand new install of Ubuntu Studio works in the vast majority of situations except for Sound Recorder and Sound Preferences.

When I record a sound in Sound Recorder the file length VERY quickly increases (several minutes in one second real time). And when I hit stop, it freezes. Using gnome-sound-recorder 2.24.0.1

Sound Preferences behaves similarly when I try to test capture capability. It freezes when I hit OK. 

Audacity works (play and record) if I use alsa mixer, rhythmbox works automatically, and most system sounds play. It's my belief that the failure of Sound Recorder to record is probably the reason that Empathy 2.24.0 won't record my voice for VOIP calls. 

According to alsamixer I'm using pulseaudio for the sound card. 

This seems to be an old bug that has resurfaced:
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/36852](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/36852)

```
$asoundconf list
Names of available sound cards:
IXP
Modem

$lspci
...
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
...

```

and I'm on a HP Pavillion dv8000z

any suggestions for either forcing Sound Recorder/Empathy to accept alsamixer for an audio device or getting the current, whatever it may be, to work correctly?

---

### Post by sublimation on 2008-10-18
Turns out that PulseAudio simply wasn't set up correctly by default. A combination of an edit to my ALSA and Gstreamer settings fixed it right up:

adding the following to ~/.asoundrc
```
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

and the following configuration fix for Gstreamer
```
gconftool -t string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool -t string --set /system/gstreamer/0.10/default/audiosrc pulsesrc

```

Instructions for general PulseAudio setup can be found here:
[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

### Post by BobJoe on 2008-11-02
thanks

---

### Post by sublimation on 2008-11-02
no problem, I'm glad my issues might have helped others.

---

