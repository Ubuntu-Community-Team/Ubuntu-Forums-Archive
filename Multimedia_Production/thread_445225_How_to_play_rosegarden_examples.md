---
title: "How to play rosegarden examples?"
date: 2007-05-15
forum: Multimedia Production
---

### Post by jondecker76 on 2007-05-15
I wanted to see what rose garden is capable of, so I opened jack then opened rosegarden. When I go to open, and then select one of the .rg files from the examples folder - the example loads as expected. However,  when i press play in the transport, there is no sound at all. The timeline moves, and I can see the level bars moving on each track but there is still no sound.

Can anybody offer some advice?

thanks,
Jon

---

### Post by drosky on 2007-05-15
> **jondecker76 said:**
> I wanted to see what rose garden is capable of, so I opened jack then opened rosegarden. When I go to open, and then select one of the .rg files from the examples folder - the example loads as expected. However,  when i press play in the transport, there is no sound at all. The timeline moves, and I can see the level bars moving on each track but there is still no sound.

Can anybody offer some advice?

thanks,
Jon

There is a good description of getting Rosegarden to produce sound in their [Tutorial]("http://http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html").

Basically, Rosegarden generates midi, so for Rosegarden to play anything, you must have a midi synthesizer for Rosegarden to connect to.  This can be an external sound source (e.g., a keyboard), a sound card with hardware MIDI support (e.g., SBLive), synth plug-ins, or a software synthesizer like Timidity or Fluidsynth.

Jack is only needed if you want Rosegarden to handle audio.  It is not needed for composing and/or playing back what you have composed via midi in the score or matrix editors.

If you have a SoundBlaster Live or other card with AWE, you will need a soundfont and the sfxload program to load the soundfont into the card.  Many good soundfonts can be downloaded for free from [Hammersound]("http://www.hammersound.net"), among others.  You might want to start with a general midi collection.

If, like me, your sound card doesn't support hardware midi, the quickest way to get started is to use Timidity or Fluidsynth.  I use Timidity since it tends to use less CPU time while idling which is important on laptops.  Install Timidity (which will also install a set of free patches as a dependency).  Then in a shell (without Jack running), type:

timidity -iA -Os

which puts Timidity in alsa server mode.  After this, start Rosegarden and you should be able to hear the music as you enter it or play back existing .rg or midi files.

As a side note, the version of Rosegarden in the Ubuntu repositories is somewhat old (v. 1.4.0).  The current version is 1.5.1, for which there are packages in Debian Testing which seem to work fine on my Feisty system.  Also, Timidity can use soundfonts as well as the built-in free patches.

---

### Post by jondecker76 on 2007-05-15
Thanks for your help, i will give it a go and see what happens.

BTW: I am using an MAudio Delta 1010

---

