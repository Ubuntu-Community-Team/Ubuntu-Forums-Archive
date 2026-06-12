---
title: "Global Volume Leveling...has it been done?"
date: 2009-12-22
forum: Multimedia Software
---

### Post by mxc1090 on 2009-12-22
I have a somewhat unique problem, but I'm sure others experience it too.  I watch TV shows on my computer at night. I usually put about three episodes in a playlist and fall asleep watching them...sometimes I watch them all, other times I don't make it through the first episode...anyway, I put on different shows a lot.

My problem is that a lot of times some shows are much louder than the previous ones in the playlist so when I'm about to fall asleep I hear a blasting intro to south park and it is at least 3x as loud as the previous file/show and I have no choice but to wake up and turn it down/off. 

I know, I know...it's really not *that *big of a deal, but making my life *that* much easier really helps. Any ideas? I was thinking of an output dB meter or possibly some program that can level the audio output depending what it hears through a microphone hooked up to the computer. Thanks.

---

### Post by VertexPusher on 2009-12-22
A dynamic compressor would do the trick. It can decrease the volume whenever it hits a certain threshold. There are LADSPA plugins to do this, but the problem is how to get one of those between your media player and the sound card. If your media player can use JACK, it's very easy: Launch an effects rack with the compressor plugin and route the media player sound through it. ALSA can do it too if you put a customized .asoundrc file in your home folder.

---

### Post by sebastianabate on 2009-12-22
gmplayer has a "normalize" option in the audio preferences. I cant test it right now because my audio card is broken. But you can give it a try.

---

