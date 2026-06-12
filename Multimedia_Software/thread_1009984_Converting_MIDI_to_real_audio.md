---
title: "Converting MIDI to real audio"
date: 2008-12-13
forum: Multimedia Software
---

### Post by davideotape on 2008-12-13
I am a keyboard player, and use midi files on my keyboard. However, I would quite like to be able to listen to these songs on my mp3 player, and for that I need to convert the midis into etither MP3, WAV, or OGG. Does anyone know any free programs that would be capable of doing this for me?

All help appreciated:)

---

### Post by gpsmikey on 2008-12-13
There's probably an easier path, but, at least in windoze, there are utilities like "Total Recorder" that basically will allow you to capture (record) the sound output on the same machine that is playing it.  Basically a "loopback" for the sound.  There may be an equivilent program available under Linux.  This assumes of course the utility on the machine playing the midi file is doing a good job of the playing.

mikey

---

### Post by Gallienus on 2008-12-13
There's a program called Timidity which you can install from the repositories (8.04 definitely, though I can't say for sure about other releases). It's very versatile, though to get the most out of it you need to use the command line.

When you've installed Timidity, the command :-

'timidity -Ow musicfile.mid'

will create musicfile.wav in the same directory as your original musicfile.mid. Note that in '-Ow', it's the letter O for Output, not the digit zero.

---

### Post by ajgreeny on 2008-12-13
Wow!  Thanks Gallienus, I certainly wasn't aware that timidity could do that, and it suddenly makes a great deal of difference to the uses I can put it to.

---

