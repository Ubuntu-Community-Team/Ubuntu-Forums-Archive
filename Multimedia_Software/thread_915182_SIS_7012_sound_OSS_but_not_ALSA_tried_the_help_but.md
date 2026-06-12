---
title: "SIS 7012 sound? OSS but not ALSA? tried the help but couldn't follow it"
date: 2008-09-09
forum: Multimedia Software
---

### Post by oliverb on 2008-09-09
OK so I've got a system with a SIS 7012 sound chip I think. I know sound basically works because the opening and closing sound works and the music plays in Slune. 

Under "System" anything other than OSS gives 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I've looked at the sound troubleshooting tips, tried uninstalling and reinstalling ALSA. Tried the modprobe command, no drivers found, not sure where to go next.

I also have a USB decice with a C-Media chipset, getting that working would be a bonus but its the mainboard sound I'm interested in.

I'm running Hardy Heron 8.04

---

