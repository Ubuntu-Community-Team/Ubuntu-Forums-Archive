---
title: "MIDI Playback?"
date: 2020-07-23
forum: Multimedia Software
---

### Post by timonoj on 2020-07-23
Hi guys!

I recently received my first MIDI keyboard. It's a crappy Worlde Panda Mini. First thing for testing, I guess. It doesn't come with its own speakers, and relies on other devices for audio rendering. I was getting a bit frustrated as I get basically nothing.
But then, I just tried to play a basic audio file, and that one also plays no sound whatsoever. I downloaded Kmidimon, and I can see the audio is supposed to be playing on the .mid file, but no audio comes out. Then I hit record, and I can see it's actually also registering the keyboards keystrokes when I hit any. It's just not rendering any audio. What should I do? I tried the procedure repeatedly shown on other places:
-Install/Open and Start Qjacktl, leave running
-Install/Open Qsynth. Choose Soundfont FluidR3_GM.sf2. Leave running
-Back on Qjactl, connect. On ALSA tab, Drag your instrument (it does show a 0:WORLDE MIDI 1) to 130:FLUID SYNTH. 
-If you hit any key, you should get audio...But I get nothing.
I'm not sure it's related to the audio server maybe? Or what else I might be doing wrong? Is Qjactl compatible with my distro's audio server?

I'm currently running KDE Neon, not sure if it makes any difference regarding the audio server it uses.

---

### Post by timonoj on 2020-07-23
Hmmm. I guess putting into text made me think a bit through. Some findings:
I can go to Setup in Qsynth, in Audio tab. The default was Jack. That seems to do jack...crap for me. Choosing ALSA gave me garbled audio overall, but the keys register some noises now. Pulseaudio (which I reckon must be my current audio server) does play some keystrokes. The pads seem to register consistently different drum sounds. The normal keys however don't seem to play consistently. The Qsynth message log registers them instantly, though.

EDIT: Changing Qjackctl Setup - Settings - Driver to ALSA and the sample rate to 48khz both on Qjackctl and Qsynth made the audio a bit less garbled, but still some sort of background noise whenever playing any sound. Also, still not registering most of the keys with sound. Only three black keys, and the 8 drum pads. ALL the key events seem logged in the log, it's just most of them don't render any audio...
Oh. And rather unreliable audio delays, so it makes it impossible to follow any rhythm.

---

