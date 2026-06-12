---
title: "Convert MIDI to Sound Output for Broadcast"
date: 2016-04-01
forum: Multimedia Software
---

### Post by firefly2442 on 2016-04-01
Hello,

I have a Yamaha digital piano that I connected to via USB.  I installed [timidity](https://wiki.archlinux.org/index.php/timidity) and [rosegarden](http://www.rosegardenmusic.com/).  The piano shows up:

```

aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'Clavinova' [type=kernel]
    0 'Clavinova MIDI 1'

```

And I can use rosegarden to record MIDI and play back the recording through the piano.  I know very little about MIDI.  My understanding is that it's just a signal with information on what note is being played.  It has no actual sound.  What I would like to do is somehow (synthesize I think?) pipe the MIDI from the piano and have it as an output for use via [OBS](https://obsproject.com/).  Is that possible?

---

