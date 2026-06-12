---
title: "Can I change default midi sounds?"
date: 2010-06-26
forum: Multimedia Software
---

### Post by pearldrums on 2010-06-26
I'm not sure what the technical term for the thing that creates midi sounds. Is it the midi sequencer? or midi driver?

Regardless, I'm unhappy with the tones ubuntu produces for its drum midis. Does any one know how to change which tones it uses? I use lilypond to write percussion music and it can be easily translated into a midi file. I like to do this so that I can hear how the music sounds in real life and make sure I didn't make any mistakes. Unfortunately the toms are painfully low and hard to distinguish. The whole drum library is a bunch of junk as far as I'm concerned so finding a new one would be great.

Thanks.

---

### Post by pearldrums on 2010-07-27
I'm sure it can be done, but nobody seems to know how, should I post somewhere else?[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164652&stc=1&d=1280233490[/IMG]

---

### Post by cchhrriiss121212 on 2010-07-27
Technical background: Midi does not make sounds itself, you need to connect a midi signal into something that does (synths etc.).
I think Lilypond will use some kind of basic soundfont (.sf or .sf2) for making sound, so you could look at loading another one if you have one.
Or you could look at Hydrogen which is a nice drum sequencer, if you install the jackd sound server you should be able to use it to link the midi output of lilypond to the input of Hydrogen.

---

