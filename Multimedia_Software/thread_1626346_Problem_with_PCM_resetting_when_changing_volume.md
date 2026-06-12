---
title: "Problem with PCM resetting when changing volume"
date: 2010-11-20
forum: Multimedia Software
---

### Post by antennen on 2010-11-20
I have a surround system which doesn't have a volume knob, so it relies on the computer to set an appropriate volume level. I can open alsamixer from the terminal just fine and set the PCM level of desire, but as soon as I change volume the PCM bumps back up to 100. I'd like to fix PCM somewhere around 40.

I found a tutorial ([http://excid3.com/blog/2010/06/changing-the-ubuntu-10-04-audio-channel-control/](http://excid3.com/blog/2010/06/changing-the-ubuntu-10-04-audio-channel-control/)) that does enable med to do this. However, this causes my sound output to reset on each boot to stereo instead of surround, so I manually have to change it.

This isn't a 10.10 or 64 bit specific bug, I've encountered it since 9.10 32 bit, and I'm not satisfied with having to change sound output manually on every boot.

What causes the PCM level to not stick?

---

### Post by efflandt on 2010-11-20
Do settings stick if select the type of sound you want from the **Hardware** tab of **Sound Preferences** and you use the speaker icon in the top panel to adjust volume?

By default Ubuntu uses pulse audio as a front end to alsa.  So it is possible that when you change something in alsamixer, it gets changed back to what it was by pulse when you reboot.

I discovered something about that while getting HDMI sound working (as an alternate to analog sound), and some apps (notably flash) used the default alsa device instead of pulse settings.

---

### Post by antennen on 2010-11-20
I use the volume buttons on my keyboard to change the volume. All the settings stick, just that PCM is either 100 or 0. If I set things manually using alsamixer it sticks until I press the volume buttons on my keyboard.

All settings stick, but I can't change volume without PCM going up to 100.

---

### Post by mc4man on 2010-11-20
I once filed a bug against this, (either karmic or pre-release/early lucid ), but abandoned for various reasons. The main one being I dumped lucid for 10.10 alpha  and at some point the pcm value on my desktop, (5.1, creative card) has absolutely no effect anyway.
Clearly though with different hardware the pcm level may matter.

The other reason was a bug mooted the whole thing anyway, at that point lucid was booting up to no volume. The reason I'm mentioning is because the workaround, an edit to /etc/pulse/default.pa, also had the effect of preventing the pcm level from being set to 100 on boot, (so you can see why the 'bug' became a futile pursuit.

You may wish to give it a try, there was no unintended consequences that I could see from the edit.
In /etc/pulse/default.pa comment out this line as shown (blue
> ### Automatically restore the volume of streams and devices
[COLOR="Blue"]#load-module module-device-restore[/COLOR]
load-module module-stream-restore
load-module module-card-restore


If the above either doesn't work or is not good then you could create a startup script using amixer to lower the PCM to a certain dB

( In maverick, at least w/ my creative hardware which isn't the best of friends with pulse to begin with, I never open alsamixer or pulseaudo volume control which seem at odds with each other. And as noted the pcm level has no effect, (except, IIRC from the dev install amarok2 which I'll never use.
Fortunatly I have external amplifacation so the sound is pretty good by keeping the level of the sound applet and players down

---

### Post by antennen on 2010-11-21
Unfortunately this had no effect. The PCM still resets to 100 when I press my volume keys. So it doesn't really matter if I create a start up script. It'll be reset anyway once I try to change volume.

EDIT: I found a page on the PulseAudio wiki ([http://pulseaudio.org/wiki/PulseAudioStoleMyVolumes](http://pulseaudio.org/wiki/PulseAudioStoleMyVolumes)) which seems to explain the behavior. Forcing module-alsa-source causes pulse to create another sound output mode, stereo, which it boots into, instead of my prefered surround output.

EDIT 2: I managed to fix PCM to 40 by first following the pulse wiki, then lower it to 40 and then comment out the line mc4man suggested. On every boot I need to mute, unmute and then raise the volume all the way up then down for it to know it's boundaries.

---

