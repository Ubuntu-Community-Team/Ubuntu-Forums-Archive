---
title: "Generate Realistic sounding bass lines"
date: 2007-09-17
forum: Multimedia Production
---

### Post by Mickeysofine1972 on 2007-09-17
Hey All

I want to generate a realistic sounding Bass Guitar sound using Ubuntu Studio, any ideas how I can do this?

I also want to be able to generate a song pattern that i can save a wav for importing into Ardour so I suppose thats two questions :)

And help is much appreciated.

Mike :guitar:

---

### Post by Stochastic on 2007-09-18
Well I personally would suggest taking a nice record that has a bass line intro, recording that and pitch-shifting, cutting, fading, etc... until your bass line is good to go.  that method tends to give the most authentic sounding bass and it will already be in wav format.  Unless you're looking for a "synthy" or "electronic" bass in which case grab a synth app and start tweaking until you find the sound your ears love.  I personally use pure data for most of my synth work as it gives the most control (analog, subtractive, fm, etc...) but it does take quite some time to get used to that program and to build synths that you like.  Once you have your synth app up and sounding good, plug it into ardour through jackctl, hit record on ardour and jam away (or hit play on your sequencer app).  Feel free to ask for clarification on any of these steps.

Edit: Whoops, half way through typing that I forgot that you had asked for a realistic sounding bass.  These are difficult to synthesize as many acoustic factors come into play in real instruments but your best bet is to get a sample pack or an elaborate instrument pack (I don't have much experience with either, I tend to just grab from old records like all those hip hop artists do).

---

### Post by stmiller on 2007-09-18
zynaddsubfx has some nice bass synths.

---

### Post by nalmeth on 2007-09-19
> zynaddsubfx has some nice bass synths.
I second this, I've made decent bass sounds with it, the only problem is that you have to physically play the keys in correct time. Its not a midi app. :popcorn:

---

### Post by Mickeysofine1972 on 2007-09-20
Hey Guys

Thanks for all the help! I think I have found a reasonable good answer that lets me  do this with a score then export as wav!

First, use Rosegarden to create a musical score and select the midi instument(s) you need then export as midi.

Second, Use timidity to convert to wav
```
timidity mysong.mid -Ow -o mysong.wav
```

Third, Use Rezound to apply any effects like reverb, (just for added realism of playing in a room etc).

Hey presto! there you have it!

You can then import it into Ardour with your other 'real' audio for mixing etc!

Mike

---

