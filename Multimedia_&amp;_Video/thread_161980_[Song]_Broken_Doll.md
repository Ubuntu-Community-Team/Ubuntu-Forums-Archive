---
title: "[Song] Broken Doll"
date: 2006-04-18
forum: Multimedia &amp; Video
---

### Post by Minyaliel on 2006-04-18
I recorded this thing and edited it in Audacity - couldn't get the background noise away, though (anyone know how to do this without it turning into some bad techie sounding new age glittery thing? That's what happened when I tried the default plug- in...). It's about all those teens who go and drink till they drop during weekends and think it's "cool".
Please tell me what you think :) (Despite my bad recording equipment :P)

[http://h1.ripway.com/Songsbyselene/brokendoll.wav](http://h1.ripway.com/Songsbyselene/brokendoll.wav)

---

### Post by void_false on 2006-04-18
> It's about all those teens who go and drink till they drop during weekends and think it's "cool".
I think it is cool too. And not only during weekends. :twisted: 
Song isnt bad at all. What I cant say about the sound quality. :rolleyes:

---

### Post by dolson on 2006-04-18
I like it how it is, honestly! It sounds like a record playing... If you use that one plugin to add the occasional record cracking and popping, then it'd be perfect.

The only thing I don't like is occasionally I hear clipping (when the vocals get loud).

I know you weren't aiming to get the quality here, but it really is unique, IMHO.

It sounds like your recording levels are way too low. Basically, you want your source to be as loud as possible, and trim in the latter stages of your recording, preferrably in your DAW.

To give an example of what I mean, I have a setup like this:

Microphone -> Mixer input gain -> Mixer EQ -> Mixer channel level -> Mixer master level -> Soundcard line in -> Ardour

My microphone doesn't have a volume level, so it's controlled with the Mixer input gain. You want this high, but without clipping (usually indicated with a red LED on your mixer).

Then you want to trim the EQ to suit your tastes. Always cut; never boost (except in rare circumstances).

Now you want to adjust your mixer's channel output level to be high. I aim for about 80% full.

The mixer's master output should be at 80% or less. Again, check for clipping on the master output meters. If you get clipping, lower the master output.

Now, you want to adjust your ALSA mixer to lower your input levels as low as possible, but preserving the maximum volume. With an SB Live! 5.1, my line input level sits at about 7-10%, and with my Audigy2 ZS, it sits much higher, at about 70-90%. It all depends on your sound card. Basically, if it's too low, you will not get much volume in your recording. If it's too high, then you'll get clipping. You want it set up so that when your mixer is outputting the max level, your soundcard handles it without clipping, but is as close to 0db as possible.

The same thing goes for guitar inputs, only you don't use the input gain pot, you use the output of your effects device.

Hope that helps you in some way... It is pretty general knowledge, but I thought I'd post it anyhow.

---

### Post by Minyaliel on 2006-04-21
Thank you :) 

In fact, that recording was done on my mp3 player (I don't own a microphone - yet) and I've edited it to get rid of the worst disturbances (people walking in the corridor outside and stuff like that). But to add crackling - hey, why not? I'll have to try that when I get onto my own PC :)

---

