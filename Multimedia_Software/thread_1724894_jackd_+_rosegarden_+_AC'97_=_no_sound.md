---
title: "jackd + rosegarden + AC'97 = no sound"
date: 2011-04-08
forum: Multimedia Software
---

### Post by maitrebart on 2011-04-08
I installed RoseGarden in order to give it a try.
I also installed jackd and its front-end (JACK Audio Connection Kit).
After a while, everything looks to run fine without any error.
However, no sound outputs from the sound card.

My sound card works ok when I play music with RhythmBox and the system sounds too. But when it comes to RoseGarden, no sound at all.

So here are some screen shots of my JACK setup:

[ATTACH]188528[/ATTACH]

Here are some screenshot of the JACK connections for Audio and Alsa:

[ATTACH]188526[/ATTACH]

[ATTACH]188527[/ATTACH]

According to the JACK Connection screenshots (above), all connections looks ok.

I also tried to change the different Hardware Profiles in the Sound Preferences (Hardware tab). But no success.

I read many threads on the net and could not figure out what is the problem. Hoping someone can help me.

---

### Post by maitrebart on 2011-04-09
Well, after trying multiple ways to get any kind of sound to output from my sound card (nVidia AC97) with RoseGarden in the past few days, I finally succeded.

The only setup that works in my case at the present moment is by using Qsynth, set up with the Jack driver and a soundfont called FluidR3_GM.sf2 .

Another inconvenient I discovered with RoseGarden is that I always have to change all the MIDI devices to the correct output (Qsynth2:0 in my case) everytime I load a new song.

I'll try to see if I can have other working setups with other drivers and soundfonts.

---

### Post by Alfred_McGee on 2011-04-30
Please keep us posted on your progress. I tried everything you say, but still get no sound, although Qsynth was not included among the available MIDI devices offered by Rosegarden. I also have a different soundcard than you, but what you did seemed worth trying anyway, as I have never gotten Rosegarden to produce sound after Ubuntu 9.04.

---

### Post by Alfred_McGee on 2011-05-15
Got Rosegarden to produce sound in Meerkat by installing Qsynth and following this old but handy guide: [http://gauthampai.livejournal.com/62383.html](http://gauthampai.livejournal.com/62383.html)

Rosegarden only has audio playback if I first manually start up Qsynth and JACK audio, but that's a small price to pay. I'm not sure if my success is 100% relevant to all parameters of this thread, but given the huge number of people who get no sound from Rosegarden, it seemed worth trying to share.

---

