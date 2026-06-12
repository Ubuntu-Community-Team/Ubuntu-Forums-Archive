---
title: "MIDI playback with audacious"
date: 2016-03-31
forum: Multimedia Software
---

### Post by asearle on 2016-03-31
Hallo Everyone,

I am trying to get MIDI files to play in Audacious:  At the moment the tracks seem to run/play but no audio output is produced.

I found several links explaining that under "File/Preferences/Plugins/Input/AMIDI-Plug/Preferences" Fluidsynth should be selected ...

[http://redmine.audacious-media-player.org/boards/1/topics/1143](http://redmine.audacious-media-player.org/boards/1/topics/1143)

Here I go to this menu-item but find a screen prompting me to select a Sound-Font file rather than the options (ALSA, FluidSynth, etc.) that I was expecting.

On another site it was mentioned that "audacious-plugins" and "audacious-plugins-extras" need to be installed.  In Synaptic I found the first package but not the second (extras) one.

In Synaptic I installed FluidSynth but this didn't make a difference.

Can anyone help me with this?  Maybe there is another package-source that I need to declare?  Or maybe Audacious no longer supports MIDI?  Or maybe I should work with another tool?

Any tips here would be a great help.

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by Bucky Ball on 2016-03-31
A MIDI track contains no audio. You need to record the synths/sound devices the MIDI track is triggering to get audio.

Playing a MIDI track in any software will produce no audio. You appear to be going about this head over tail.

You would use the MIDI track to trigger sounds from Fluidsynth (or any other MIDI sound generator, soft or external), nothing to do with Audacious, record that to MP3 or whatever then play that regular audio track in Audacious, if you follow me. 

A MIDI track is just a set of instructions, not audio.

---

### Post by asearle on 2016-04-01
Many thanks for this clarification:  Now I understand.

I googled around to find some sound fonts (.sf2), added these under Plugins/AMIDI/Preferences and the track played.  Excellent.

Many thanks,
Alan

---

### Post by Bucky Ball on 2016-04-01
Now you're getting it. :D

Thanks for marking as solved. This will help future travelers.

---

