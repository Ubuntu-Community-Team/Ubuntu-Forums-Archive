---
title: "Mythtv Digital Audio Problem"
date: 2013-04-30
forum: Mythbuntu
---

### Post by daveshep on 2013-04-30
Gday everyone, hoping someone can help before the mrs kicks me out (for messing up what was a working setup - a big noisy combined backend/frontend - by replacing it with something cool which "should work")...

I'm trying to get a mythtv frontend running (properly) on a Zotac MAG. Its generally working ok, music out my optical spdif to my amp and video+sound through the hdmi cable to my tv. BUT whenever I try and watch HD stuff (TV or DVD) my audio is fine for about the first 10 seconds then it dies. The video works sweet as. Sometimes the audio stutters a bit but generally it goes completely silent. Sometimes it starts a high pitched tone which only disappears if I do something else noisy (eg start another video/change channel/listen to music), otherwise the high pitched tone is there to stay (ie even when just sitting back at the main menu). I am using vdpau but other playback profiles haven't helped... cpu use on the frontend and backend sit at around 10-13%.

there's a few errors and warnings that come up, eg

- ALSA: WriteAudio: buffer underrun
- ALSA try to manually increase audio buffer with echo 128 | sudo tee /proc/asound/card0/pcm1p/sub0/prealloc
- Player(0): Waited 103ms for video buffers

but checking these out hasn't turned up anything. The problem is still there whether i put the audio out through hdmi or spdif, and forcing sampling rate doesn't help. 

any ideas? besides moving my backend/frontend back into the living room to replace the zotac mag? 

cheers!

---

### Post by BicyclerBoy on 2013-05-03
What happens if you do this in a terminal ?
echo 128 | sudo tee /proc/asound/card0/pcm1p/sub0/prealloc

Root cause of this is alsa using the wrong group permissions.

What kernel & nvidia driver versions?

Have you rescanned & tested the audio devices in frontend setup?
Try to use the alsa devices only.

Make sure you haven't ticked to many audio features.
Untick  DTS-MA, upmix, volume control.

As a work-around try use 2 ch PCM output only.. 

Test audio output from terminal
speaker-test -l 2 -r 48000 -c 2 -D iec958
speaker-test -l 2 -r 48000 -c 6 -D hw:CARD=nvidia,DEV=0

---

### Post by daveshep on 2013-05-06
yeah man rescanned... i'd tried to update alsa drivers and the ALSA:hdmi:* and ALSA:iec958* were gone for some reason. i'd unticked the upmix etc etc and still no luck. sorry i can't remember (and didn't record) what the output of the "[COLOR=#000000]echo 128 | sudo tee /proc/asound/card0/pcm1p/sub0/prealloc[/COLOR]" command cause i cracked (after the rescan suggested i'd messed things up by updating alsa drivers) and did a complete reinstall... i made sure i'd unticked the "*Enable Realtime Priority Threads"*[COLOR=#444444][FONT=arial] and now it's working...[/FONT][/COLOR]  

not 100% sure i'd disabled the realtime priority threads initially, but it seems like that was the cause. thanks for your help!

---

