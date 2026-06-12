---
title: "SPDIF audio x seconds before audio starts"
date: 2009-06-09
forum: Multimedia Software
---

### Post by medicineuk on 2009-06-09
Hi Guys and girls I'm new to Linux and have had a pretty good experience so far, what a lovely little OS :D I have one bug left that I would love to get squashed.

I have an ASRock ION 330 with Ubuntu 9.04 and have managed to get sound over SPDIf setup and working using HDA NVidia (Alsa mixer). My Issue is that the sounds takes about 1 second before it starts playing. This is fine when watching a movie or listening to music but it means that I can't not hear any audio from menus or any UI's as they're normally under one second.

When I press enough buttons in quick concession DLOBYPLN is displayed on my AMP but so soon as I stop it goes back to DI. It's seems as though the sound channel is constantly opening and closing and will only stay open if the sound continues for more then 1 second. Is there a way that I can keep it open all the time? If any one could help out that would be amazing, thanks.

---

### Post by Icey7 on 2009-06-10
Hopefully medicineuk won't mind me hijacking this tread to ask a related question.

If anyone has one of these Asrock ION 330 did you manage to get audio over HDMI working in 9.04?

Thanks!

---

### Post by ReddogOne on 2009-07-15
> **medicineuk said:**
> When I press enough buttons in quick concession DLOBYPLN is displayed on my AMP but so soon as I stop it goes back to DI. It's seems as though the sound channel is constantly opening and closing and will only stay open if the sound continues for more then 1 second. Is there a way that I can keep it open all the time? If any one could help out that would be amazing, thanks.

Are you sure this is the sound channel that is constantly opening and closing. Maybe it is your amplifier detecting absolutely nothing and turning the input off and on again after it detects some input.

[Very much] A guess but you might be looking at the wrong thing. Maybe try taking the cable in and out and see what happens, if you still get the delay it might be the amplifier.

---

### Post by igorzwx on 2009-07-15
Do you have PulseAudio?

Google -> "markbuntu ALSA pulseaudio"

---

### Post by medicineuk on 2009-08-13
> **ReddogOne said:**
> Are you sure this is the sound channel that is constantly opening and closing. Maybe it is your amplifier detecting absolutely nothing and turning the input off and on again after it detects some input.

[Very much] A guess but you might be looking at the wrong thing. Maybe try taking the cable in and out and see what happens, if you still get the delay it might be the amplifier.

Sorry you might be right it could be the amplifer detecting nothing a turning the input off. The main reason I'm confused is that it doesn't happen on my windows 7 install on the same box. 


> **igorzwx said:**
> Do you have PulseAudio?

Google -> "markbuntu ALSA pulseaudio"

I have PulseAduio but I'm using alsa mixer

---

### Post by ReddogOne on 2009-08-14
> **medicineuk said:**
> Sorry you might be right it could be the amplifer detecting nothing a turning the input off. The main reason I'm confused is that it doesn't happen on my windows 7 install on the same box. 

Windows may be sending a stream of zero's to represent nothing, where as linux is sending nothing. Yeah you guessed... I'm still guessing.

---

### Post by miki4242 on 2009-12-24
If the lack of sound data is really what causes your amp to shut down, here's a very simple way to have your computer output 'silence' to keep the audio data going. It uses SoX, the Swiss Army Knife of audio manipulation (plug, but true :-) )

First, install SoX using:
```
$ sudo apt-get install sox
```
Then, simply run 'play' (which is part of SoX) as follows:
```
$ play -qn
```

This will play 'silence' out the default sound device, without any status messages, until you kill the process with <Ctrl-C>.
Either PulseAudio or ALSA's 'dmix' should take care of mixing this silence with audio from other apps, so you shouldn't notice any difference from normal use.
It uses very little CPU, and should work with both PulseAudio and pure ALSA.

-Alain

---

