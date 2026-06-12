---
title: "loading soundfonts to sound cards"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by goodmanbrown on 2006-12-09
I recently installed an M-Audio Audiophile 2496 card, and am now trying to get it set up to play midi.  Mostly, I want to be able to play back songs as I am notating them in noteedit.

Noteedit sees the audiophile card as a legitimate destination for midi data, but if I choose the card, and try play my score in noteedit, I hear nothing but silence.

After googling around a bit, I found that this sort of behavior with a SoundBlaster card typically means that midi playback is working, but no soundfont is loaded.  And so you use asfxload to load a soundfont on the the SB card.  I suspect maybe I have a similar problem with my card.

But I can't find any information on the M-Audio card.  Do I need to load a soundfont onto the card?  What program would I use to do this, since asfxload only works for Emu- and SB-based cards?

---

### Post by damu on 2006-12-09
You need to use fluidsynth (with eventually qsynth as a front end). You obvioulsy need some soundfonts . To start with, you can get some free ones [here]("http://www.hammersound.net/").
I never used notedit, but you'll probably need to connect the different pieces of softwares through jack (you can get jack with synaptic). You will probably need to work with timidity if you want to stick to noteedit. 

I guess , an easier way would be to import your midi file in Rosegarden (which by the way has a very good scoring editor) and open fluidsynth from Rosegarden. If you install with Synaptic Rosegarden, fluidsynth, jack, all the dssi packages, you should have something easy to set.

---

### Post by goodmanbrown on 2006-12-09
Does that strategy use the midi capability of my soundcard at all, though?  Before, when I was using onboard sound, I had noteedit send midi to timidity running in server mode, and timidity send audio to the soundcard.

Doesn't fluidsynth do basically the same thing-- convert midi to audio in software?  What I'd really like to be able to do is send midi to the soundcard, and have the soundcard convert it to audio in hardware.

Thanks for the reply!

---

### Post by fritzm on 2006-12-10
> **goodmanbrown said:**
> Does that strategy use the midi capability of my soundcard at all, though?  Before, when I was using onboard sound, I had noteedit send midi to timidity running in server mode, and timidity send audio to the soundcard.

Doesn't fluidsynth do basically the same thing-- convert midi to audio in software?  What I'd really like to be able to do is send midi to the soundcard, and have the soundcard convert it to audio in hardware.

Thanks for the reply!

The M-audio does not have an onboard synth AFAIK. Its MIDI capabilities are only to pass through MIDI data to/from and external device, and to use MIDI timecodes for synchronisation. To play back MIDI, you have to do as you did before with a software synth sending its audio output to the M-audio card.

When the card appears as a MIDI destination, that would be purely to pass the data through to an external device, the card cannot actually play back itself.

Fritz

---

### Post by christhemonkey on 2006-12-10
(nearly) The only MIDI hardware synth on a soundcard that works under linux is the AWE32/64 from sound blaster.

Other than that you have to use software like timidity or fluidsynth.

---

### Post by PatrickMay16 on 2006-12-10
> **christhemonkey said:**
> The only MIDI hardware synth on a soundcard that works under linux is the AWE32/64 from sound blaster.

Or the emu10k1 (Sound Blaster Live!). I know this, because I have one myself and use its hardware MIDI capability within linux.
Even better, you can get a Sound Blaster Live off ebay for a very cheap price. I know this, because I have myself bought a Sound Blaster Live on ebay, for a cheap price. 

And then it's as simple as installing the package "awesfx" and doing "sfxload file.sf2" at the command line. I know this, because I have myself loaded soundfonts to the Sounds Blaster Live in this way.

Ya know... just if anyone's wondering.

Just FYI.

---

### Post by MusicianX on 2008-01-19
Thanks PatrickMay16

I am trying in now, hope it works.

---

