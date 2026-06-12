---
title: "alsamixer not allowing &quot;mic&quot; to be set to capture"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by spydirweb on 2008-04-08
I, like others I assume, have been trying for ages to get my microphone to work in Ubuntu.  My sound card is a SBLive Audigy2 Value (using ALSA's emu10k1 driver) I've had for ages and works just fine for sound output.  I never tried the Mic much when I used other distros before Ubuntu so I never had much experience making sure it was "properly" set up.  Anyways, I have been able to set up the microphone so it SEEMS to be picking up some sound. The following is advice I've seen REPEATEDLY in other forums posts, howtos, etc that I've tried.  Note I'm ignoring the seemingly obvious "turn mic playback to mute" because I've been using it to make sure that the mic is actually functioning, I know it's there and to turn it off, and it has nothing to do with the problem.

1. Ensure volume control is displaying all devices (volume control's preferences, make sure everything is ticked)
2. In capture tab, max out mic volume.  Switches tab, mic boost on and capture microphone on (problem lies here)
3. if above fails, load alsamixer in a console window
4. go to capture "tab", turn mic all the way, make sure it's not muted, enable capture by pressing space bar (problem lies here).

I believe my problems lie in the fact that alsamixer nor gnome-volume-control is not displaying any tickable options for capturing.  The only thing available is a slider for the microphone capture and the micboost.  When I'm in alsamixer's capture tab if I hit spacebar on my mic volume slider, it does nothing.  There is no red text saying "DUDE YOU'RE CAPTURING THE MICROPHONE NOW! GRATS!" (I tend to get upset and a little angry with my computer when I can't figure out a problem, and I respond with sarcasm)

All this has lead me to believe that there is a fault between my alsa configuration ( .conf files, not volume settings), modules being loaded, or some kernel options.  I upgraded to alsa 1.0.16 (the driver, libs, tools, utils) and alsa-oss to 1.0.15.  I've done an alsaconf again just for fun.  All together it has added up to no further advances.  All that remains is that in audacity it records but as completely unreasonable levels.  I have to throw the playback volume up so high it's more static than me talking.

I'm sure I'm missing something, some errant alsa module, something in the .conf's that I should be looking at.  Note, I'm not posting my .conf's because I haven't messed with them at all, simply because I don't know where to being looking for things to mess with.  Any help would be GREATLY appreciated.

---

