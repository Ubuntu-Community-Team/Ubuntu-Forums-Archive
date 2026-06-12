---
title: "Video stopped working right since Hardy upgrade"
date: 2008-04-28
forum: Multimedia Software
---

### Post by sceo on 2008-04-28
My clean install was from Gutsy, and the other day I upgraded to Hardy.  Since then, I can't get video to play back.  Interestingly, it doesn't matter any more if I'm running Compiz or not (which ultimately, despite the fact that it doesn't work, is good news maybe).  I have an Intel 845 on-board video, which had problems with Compiz and video playback in the past and was blacklisted.

Anyway, when I open gstreamer-properties and run the test, everything seems to work fine, whether I pick XV with extensions, XV without extensions, or autodetect.  The "Test" plays bars and static.

However, when I play an actual movie in Totem it is super-chunky... click a frame... click a frame...

When I play a movie in Xine I get about 5-10 seconds of the video, then playback freezes... always in the same spot for each movie I try.

In mplayer, I get about a second of playback before it freezes.

---

### Post by sceo on 2008-04-28
Hmm, so apparently as I change each video player to use ALSA instead of PulseAudio it works fine.  I changed Xine within Xine, and changes the System -> Preferences -> Sound settings to ALSA and then Totem worked fine.

What is the argument for switching to PulseAudio?  I heard it was awesome, but forget why... I'm trying to figure out if it's worth getting to work or if I should just leave ALSA working fine as it is...

---

### Post by eddyr on 2008-04-29
Thanks for that. I have the same problem. ALSA seems to work for me :)

---

