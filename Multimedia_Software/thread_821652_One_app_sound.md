---
title: "One app sound"
date: 2008-06-07
forum: Multimedia Software
---

### Post by Vrekk on 2008-06-07
Ok i can only have one app with sound and it is starting to bug me.  I will open Amarok to listen to some music, then decide to play a game on wine or view a video on youtube.  But i have no sound, even if Amarok is closed.  I have to log out then back in to get sound back. Any help.  Ps, it works the other way around too

---

### Post by mastermindg on 2008-06-07
I use Amarok religiously as my music player. I am able to get sound from multiple applications (amarok, firefox, vlc....) simultaneously. 

**PulseAudio** is now SOP for Ubuntu. In order to give apps priority in the sound scheme you will need to give them access to pulse.

**Amarok** - Settings - Engine - Output plugin - pulseaudio
Firefox - Install libflashsupport
**VLC** - Settings - Preferences - Advanced - Audio - Output Modules - Pulseaudio audio output
**MythTV** - 
1) Install libasound2-plugins
2) asoundconf set-pulse
3) Make sure that your audio device is set to alsa:default

If you have any other specific apps, let me know.

---

### Post by Vrekk on 2008-06-07
Thanks that helped alot, i can hear amarok and firefox at the same time, but still have the problem when crossover or wine is one of thouse apps

EDIT: I got it working fine now thanks for the help

---

