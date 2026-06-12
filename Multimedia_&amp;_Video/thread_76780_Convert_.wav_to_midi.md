---
title: "Convert .wav to midi"
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by johannes on 2005-10-15
Does somebody know an easy way to convert .wav files to midi format? I have read that you can use Timidity to do this somehow but I don't know how.

It would be nice to do this since I then can transfer them to my cell phone...

Any help is appreciated. :)

---

### Post by brownknight on 2007-01-26
i too need to know how or what program is needed to do this. will search the web and get back here if i find anything.:confused:

---

### Post by agustin.g on 2007-01-28
Not to ruin your plans, but in my opinion it's not doable... .midi files simply contain information about what "instrument" or sound should be produced at what moment, while the .wav files contain the actual sounds. To split them up and find which "instrument" produces each sound doesn't sound easy at all. 

Newsflash, i'm partially wrong. 
[http://www.pluto.dti.ne.jp/~araki/amazingmidi/](http://www.pluto.dti.ne.jp/~araki/amazingmidi/)
seems like this app can process **single-instrument polyphonic music**.

And here's a nice little app, but it's payware (and pretty expensive)
[http://www.intelliscore.net/](http://www.intelliscore.net/)

hope it helps

---

### Post by gogott on 2007-02-28
[MIDI Converter]("http://www.tomdownload.com/audio_mp3/midi/miditowav_recorder.htm") - Convert MIDI to WAV MP3 OGG MIDI 0/1 - MIDI to WAV Converter 

:guitar:    :lolflag:

---

### Post by rosencrantz on 2007-11-11
From my experience, timidity can't do it. Try googling for a midi file of the specified piece ;-( Or listen carefully and type it - lilypond is a great music typesetter with midi output. 
The other way round is easy: [FONT="Courier New"]timidity -Ow foo.mid[/FONT] generates foo.wav. See the timidity man page for further details.

---

