---
title: "I can't stand alsa backend.."
date: 2013-05-31
forum: Multimedia Software
---

### Post by DiabolicalClaptrap on 2013-05-31
Would somebody mind telling me how to set PulseAudio as the default sound server for adobe flash (using the plugin from Ubuntu restricted extras, 11.2 r202) and Skype (v 4.2.0.11)? For Skype, I tried installing PAVU and making sure my settings were correct (as SKype's website instructed), but this didn't work. This is a brand new install of Ubuntu 12.04 x86_64, with only system and driver (graphics) updates applied.
If anybody could help, I'd appreciate it.

---

### Post by kostkon on 2013-05-31
What do you mean exactly?

Skype uses PulseAudio if it is present (Ubuntu has PulseAudio by default, as Xubuntu and Kubuntu, I think).

Also, Flash uses PulseAudio indirectly, through PulseAudio's alsa plugin that redirects all dmix streams to itself.

---

### Post by DiabolicalClaptrap on 2013-05-31
Then colour me confused, because ALSA is set as the default in Skype (installed via .deb package from Skype's website). I can tell because of the selection menu. As for Flash, something's screwy, then.. When voice calling over Skype + playing a youtube video in FF 21.0, Flash freezes. This does not happen when that 1 channel ALSA gives you isn't already in use.

---

### Post by kostkon on 2013-05-31
> **DiabolicalClaptrap said:**
> Then colour me confused, because ALSA is set as the default in Skype (installed via .deb package from Skype's website). I can tell because of the selection menu. As for Flash, something's screwy, then.. When voice calling over Skype + playing a youtube video in FF 21.0, Flash freezes. This does not happen when that 1 channel ALSA gives you isn't already in use.
So you are saying that you are not currently using PulseAudio but wish to enable it.

Are you running Ubuntu or one of its other flavours?

What's the output of
```
ps -A | grep pulse
```
and, also, the output of
```
fuser -fv /dev/snd/*
```

---

### Post by kostkon on 2013-05-31
Also, you can check if pulseaudio is installed with
```
apt-cache policy pulseaudio
```

---

### Post by DiabolicalClaptrap on 2013-05-31
This is a fresh install of 12.04 Ubuntu x86_64. :) Pulse hasn't been uninstalled and should be enabled.

Output of ps -A | grep pulse:
```
1748 ?        00:00:47 pulseaudio
```


fuser -fv /dev/snd/*:
```

                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  ryan       1748 F.... pulseaudio
/dev/snd/controlC1:  ryan       1748 F.... pulseaudio
/dev/snd/controlC2:  ryan       1748 F.... pulseaudio
/dev/snd/pcmC1D0c:   ryan       1748 F...m pulseaudio
/dev/snd/pcmC2D0p:   ryan       1748 F...m pulseaudio

```

---

### Post by Yellow Pasque on 2013-06-01
Maybe has something to do with the fact that skype is 32-bit. If you install the libasound2-plugins:i686 package, does that help?

---

### Post by Cheesemill on 2013-06-01
Pulseaudio ***needs*** either ALSA or OSS installed as it's backend to communicate audio to the hardware.

As a Ubuntu installation doesn't have OSS installed by default if you removed ALSA you would break PulseAudio.

[ATTACH=CONFIG]243374[/ATTACH]

---

### Post by DiabolicalClaptrap on 2013-06-01
I just want access to multiple audio channels. As of now I'm  unable to simultaneously access Youtube thru Flash and voice chat on  Skype. If I open YT while on call, it hangs. If on YT while making a call, the call will fail due to a "hardware playback issue". 

> **Temüjin said:**
> Maybe has something to do with the fact that Skype is 32-bit. If you install the libasound2-plugins:i686 package,  does that help?
Just tried. No go. :(

---

### Post by DiabolicalClaptrap on 2013-06-01
Did some heavy digging and found [this]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/"), which solved my issue (uploaded txt below in case post vanishes)

[ATTACH]243384[/ATTACH]

---

