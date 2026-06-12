---
title: "ALSA, SPDIF, silence and sample rate"
date: 2010-04-12
forum: Multimedia Software
---

### Post by akaIDIOT on 2010-04-12
After some fudging around, I managed to get my 64-bit karmic install to output sound digitally to my amplifier. So far, so good. 

The amplifier indicates a sample rate of 44.1KHz, while it is capable of 48KHz (higher sample rate would be better, i assume). Also, more annoying, it indicates no signal when no applications are producing sounds, causing it to miss the first second of output when I unpause my music. 
Windows 7 outputs everything as 48KHz, apparently also outputting silence as the light doesn't blink when i pause a media player. 

The question then being:
 - How do I override the default sample rate of digital audio output (if this is even possible, googling suggested that this might be overridden by applications); 
[s] - How do I make my sound driver output silence when no application is outputting sound. [/s]

Additional info:
 - Ubuntu Karmic x64 (dist-upgraded from jaunty) 
 - Exaile media player with Normal playback engine and Automatic audio sink 
 - Asus P5Q-E motherboard 
 - Philips DFA888 amplifier

---

### Post by akaIDIOT on 2010-04-12
A friend pointed out a solution to the second issue: as ubuntu uses pulseaudio for everything, simply commenting out the module that suspends the audio device after a timeout causes it to remain outputting nothing when nothing is playing.

---

### Post by cchhrriiss121212 on 2010-04-12
48kHz output is only worth it if you are playing files encoded as 48kHz, and chances are your mp3/flac/etc music files will be 44.1kHz as this is default for CDs. In other words it makes no difference.
If windows upsamples to 48kHz then it will be from a sound card driver interface that allows you to set the rate. I take it you are are using the on board sound from your motherboard? You could look in alsamixer and see if allows you to change the rate in there.

---

### Post by akaIDIOT on 2010-04-12
> **cchhrriiss121212 said:**
> 48kHz output is only worth it if you are playing files encoded as 48kHz, and chances are your mp3/flac/etc music files will be 44.1kHz as this is default for CDs. In other words it makes no difference.

Someone pointed that same fact out just now, but thanks for your reply. As the source of most of my sound is indeed also 44.1KHz, i might just force windows to do that. 

In any case, I think I'm satisfied with the situation as it is; amplifier sounds wonderful anyways :)

---

