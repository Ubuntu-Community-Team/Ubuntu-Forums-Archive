---
title: "Aqualung controls delay"
date: 2009-06-01
forum: Multimedia Software
---

### Post by Darvon on 2009-06-01
Hi!

I was looking for a foobar 2000-like audio player, and found aqualung, that was at least similar to it and matched my needs.

There is only one annoying problem: The Pause and Stop function seems to haver a strange delay: The music is playing, I click un pause/stop, nothing happens, only about 10 seconds afterwards. Start playing a track is working fine. When a track is playing, and I double click on an other, the same delay applies, but the track I clicked on, starts about 10 seconds after the beginning, like it started playing regularly, I just couldn't hear it, because the previous track was still playing.

It seems, that the program has some problem with ending a track, starting one seems to be ok.
Sounds weird, I hope you can understand it

Darvon

---

### Post by Djzn.BR on 2009-07-07
Same here, I can't keep up with the delay responsiveness that Aqualung imposes. I just have compiled a version to make sure it was not a ubuntu issue, and guess what, it's the same. Still waiting 10 seconds for the song to actually jump after a click. Could be a broken library? Dunno... 

I have compiled again aqualung with minimal options, excluding also the libsamplerate which *could* be causing lagging... still no go. There's no IRC channel for Aqualung in freenode, I will try the mailing list and see what happens.

**Update:**
Seems that Aqualung is having a problem with the "default" device that is found in Ubuntu/PulseAudio.

If you specify these parameters in command line:
**aqualung -o alsa -d plughw:0,0**
the lag will be almost gone.
Notice that you might have to change your <device> item, just in case.

I still would like to know an option to know how to make aqualung respond immediately.

I am a foobar2000 addicted and I can tell, aqualung is the "closest" you can get to foobar2000. It can use in-build LADSPA equalizers, it understands replaygain, album art (embedded or folder.jpg) and it is also totally gapless. There is also a CD ripper and an audio converter. The default theme is ugly as hell, but you can change the theme setting to dark (better theme).

---

### Post by Darvon on 2009-08-27
Hey, thank you for the answer!

It works *somehow*... The delay is gone, but when I start aqualung with that command, I can't set the volume in my gnome panel, neither with alsamixer; even the pulseaudio volumepanel doesn't have any effect; it is even impossible to play any other audio source.

I don't know much about that sound stuff, so my clue is, that this command surpasses pulseaudio and goes directly to the hardware-side of alsa? Is that possible, or do I just confuse something?
Well, I'd be grateful, if someone could help me with that.

Darvon

---

