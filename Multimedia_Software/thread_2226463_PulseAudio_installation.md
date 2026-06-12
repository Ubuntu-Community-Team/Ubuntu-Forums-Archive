---
title: "PulseAudio installation"
date: 2014-05-27
forum: Multimedia Software
---

### Post by Andrew_Lucas on 2014-05-27
Hi all,

I'm a bit of a perfectionist, and have decided that _buntus comes with too much 'junk' installed (packages that I don't need or want).

Having looked into Arch, and deciding that the effort/skill required to maintain it is beyond me, I've come round to the idea of setting up a minimal installation. This lets me have to have an 'Arch-like' experience (i.e. only packages I want will be installed), but once set up, I shouldn't have to worry about the rolling release cycle breaking things.

I'm testing things out in VirtualBox currently, but I've not been able to find a guide specifying how to get audio working from a standing start (I'm assuming this won't be done automatically, in line with the 'I-choose-the-packages' mentality, though I'm not quite sure just how 'minimal' the minimal installation is).

Xfce is my DE of choice (the PPA for Cinnamon being down, seemingly permanently, and Cinnamon being pulled from the 14.04 repos). My list of packages to be installed (thus far) is discussed in [this]("http://ubuntuforums.org/showthread.php?t=2226460&p=13034423#post13034423") thread. I've deliberately left out all audio packages, however, some of the ones I *think* I might need are:

```
pulseaudio

 pulseaudio-utils
 pulseaudio-module-x11
 gstreamer0.10-pulseaudio
 pavucontrol

 xfce4-mixer  


```

I've seen various things about *do not under any circumstances* remove Pulse, and as a consequence of that (it seems), no one is giving instructions on how to actually install it. Also, I'm not exactly clear on the relationship between Pulse and ALSA - it seems both need to be installed, since Pulse manages multi-application mixing whereas ALSA just handles the low-level stuff (like interactions with the kernel). My understanding overall is pretty poor, however, and I've no real idea about where to begin.

If someone could either tell me directly how and what to do (eg the function of each package) - or else direct me to a source where I can found out myself, that'd be good! I've had a look at the documentation from the Archwiki, but its pretty dense stuff, and I don't want to spend time figuring it out if its not going to be relevant to my own installation.

I'm no audiophile, so providing there is no obvious crackle and I could play flash videos, and some music/video files (in a variety of formats, VLC takes care of playback of the videos, all of my music is in either .mp3 or .ogg format), Skype, and a couple of steam games, I'll be happy.

Cheers!

---

