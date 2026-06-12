---
title: "spdif audio out"
date: 2011-07-05
forum: Mythbuntu
---

### Post by remarkosmoc on 2011-07-05
Hello,

I recently upgraded/migrated from mythdora 10.21 to mythbuntu 11.04. My system has two backend/frontends and two frontend onlies.  I was able to get everything working relatively painlessly (thinks to everyone who contributes to mythbuntu) with one exception.  

On my secondary backend/frontend I am unable to get audio out of my spdif port.  My stereo detects a digital connection, but I get no audio.  I have tried all of the output devices that are auto-detected and non work.  I have tried unmuting the spdif output in alsamixer and that didn't help.  

Any tips on where to get started?  I have an nvidia chipset/soundcard.

---

### Post by remarkosmoc on 2011-07-06
I was able to get it working, details here for anyone needing the solution.

Mostly I'll credit Matt from this post [http://forums.whirlpool.net.au/archive/461197](http://forums.whirlpool.net.au/archive/461197)

I uninstalled alsa:  sudo apt-get remove alsa
I reinstalled alsa:  sudo apt-get install alsa

Next I started playing a test .mp3 with vlc while I went into alsamixer to unmute the spdif output.  The next part is strange, but I recall having to do the same thing with Fedora some time ago.  I re-muted spdif and it started playing!

After confirming that sound works with VLC, I set mythtv to use alsa:spdif as its output, enabled both digital passthrough options, and turned off the internal mixer.

---

